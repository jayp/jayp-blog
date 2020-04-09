---
title: Exploring property-based testing
date: 2015-01-20T19:19:00-07:00
tags: ["programming", "clojure"]
---

**Prerequisite** If you haven't watched a
[presentation on property-based testing by John Hughes](http://vimeo.com/68383317),
please watch it -- the presentation does a great job of explaining both: (i)
what property-based testing is, and (ii) the power (nay, magic!) of property-based
testing in finding hard-to-discover bugs.

[Reid Draper](http://reiddraper.com/), the primary author of Clojure's
[test.check](https://github.com/clojure/test.check),
describes the core idea behind property-based testing:

> Instead of enumerating expected input and output for unit tests, you write
> properties about your function that should hold true for all inputs. This lets
> you write concise, powerful tests.

If I had to summarize my understanding about property-based testing frameworks,
it would be as such:

- Input data is randomly generated using composable and extensible generators.
- Output data is validated against invariant properties of the target function.
- A user-controlled knob can limit how extensive the testing needs to be, i.e.,
  how many times to test the function with randomly generated data -- hundreds
  of times, thousands of times, millions of times, etc.
- The framework is intelligent enough to generate simple test cases first, and
  gradually grow the complexity of input data as early tests pass.
- When an output violates the property invariant, the framework tries to shrink
  the input set to a minimal input set for which the invariant property is
  still violated. Often, the shrunk input will help directly pinpoint the root
  cause of invariant violation. When this works, one maybe reminded of
  [Arthur C. Clarke's](https://en.wikipedia.org/wiki/Arthur_C._Clarke) famous
  "law":

> Any sufficiently advanced technology is indistinguishable from magic.

## My Initial Take

I have never used a formal property-based testing framework before; though, I
recall authoring unit tests that would validate results using randomly
constructed input. The idea of using generated input seems fairly natural in the
realm of testing and is likely used in many places in an ad hoc manner, i.e.,
without the use of
[composable generators](https://github.com/clojure/test.check/blob/master/doc/generator-examples.md).
However, I've not authored any tests which attempt to shrink the input.

As a person made just learning about property-based testing, I have some doubts
on the (i) efficacy vs. efficiency ("bang for the buck") and (ii)
wide-applicability of property-based (only) testing.

Firstly, on efficacy vs. efficiency: from developer perspective, classical unit
testing (i.e., manually encoding output expectation for a given input) is easy
to formulate (and grasp) as it directly validates the execution of a function.
From computational perspective, classical unit testing also has the ability to
hit key corner cases in a minimal number of tests; whereas, test cases based on
randomly generated input data will reach corner cases in a computationally
inefficient manner.

Secondly, and more importantly, it is not quite obvious to me if one could
provide tightly-bound invariant properties for all functions needing test
coverage. Tightly-bound invariants are required because loosely-bound
invariants allow a faulty function to pass the tests. If we are unable to
provide a set of tightly-bound invariants, property-based testing need to be
augmented with output expectation unit tests.

## Defining Tightly-bound Invariants

[Connor Mendenhall](https://ecmendenhall.github.io/) presents
an excellent introduction to Clojure's property-based testing framework
[test.check](https://github.com/clojure/test.check) in his blog article
[Check Your Work](http://blog.8thlight.com/connor-mendenhall/2013/10/31/check-your-work.html).
If you have not heard of used test.check, you may gain a lot of value by
reading that article before continuing on.

In the article, Connor also expresses his concerns the about wide-applicability
of property-based testing. He describes his experience with using test.check
framework to validate his solution
to the [Making Change](http://craftsmanship.sv.cmu.edu/katas/making-change)
"kata":

> After writing a few Simple-check [now renamed test.check] tests, I was stuck.
> I knew the specific case I was trying to describe—changing 80 cents with
> denominations of 25, 20, and 1 should return four 20 cent coins instead of
> three quarters and five pennies—but I was left scratching my head when I tried
> to generalize it.

I attempt to provide a solution to the problem of writing generalized test
specs for the Making Change kata next.

#### Synopsis

A solution to the "Making Change" kata along with tightly-bound invariants for
property-based tests is available on
[my GitHub](https://github.com/jayp/making-change).

#### Details

I describe the key parts of the test coverage next. However, please refer to
[core_test.clj](https://github.com/jayp/making-change/tree/master/test/making_change/core_test.clj)
for complete implementation details.

Firstly, let's cover the test spec to validate correctness of change, i.e., no
loss of value:

```clojure
;; Change must add up -- or else, *gasp!* -- the function is committing fraud!
(defspec correct-change
         (prop/for-all [coinset gen-coinset
                        amount gen/s-pos-int]
                       (let [change (make-change coinset amount)]
                         (= amount (apply + change)))))
```

In the `correct-change` test spec above, `gen-coinset` is a generator that
yields a random, non-empty set of integers ("coins") each time it is invoked.
The `coinset` is one such instance. Similarly, `amount` is an instance of a
randomly generated positive integer. The invariant states that the change
supplied by the `make-change` function must add up to the original `amount`.

Note that the `correct-change` spec only makes sure the change amount is
correct, but it does not check minimality. Omitting either of the test
specs below would provide only a loose-bound on the invariants, allowing a
faulty function (for instance, one that simply returns `n` 1-cent coins) to
pass the test.

Next, let's discuss the test spec to validate the minimality of the simplest
base case:

```clojure
;; If the amount is one of the coins, that change must be a single coin
(defspec smallest-change
         (prop/for-all [[coinset amount] gen-amount-from-coinset]
                       (let [change (make-change coinset amount)]
                         (= 1 (count change)))))
```

In the `smallest-change` test spec, the `gen-amount-from-coinset` is a
generator that yields a random 2-tuple, consisting of: (i) a non-empty set of
coins, and (ii) an amount (that is equal in value to some coin in the set). For
this type of input, the invariant states that the minimal change should be
exactly one coin.

Next, we build a more "sophisticated" spec that exploits the base case along
with an additional properly:

```clojure
;; The number of coins to change amount1+amount2 together must be no more than
;; the number of coins combined from changing amount1 and amount2 seperately.
(defspec combined-change
         (prop/for-all [coinset gen-coinset
                        amount1 gen/s-pos-int
                        amount2 gen/s-pos-int]
                       ;; NOTE: changing dp-change to greedy-change fails spec
                       (let [f (partial make-change dp-change coinset)
                             change-seperate (concat (f amount1) (f amount2))
                             change-together (f (+ amount1 amount2))]
                         (<= (count change-together) (count change-seperate)))))
```

Combining the last two specs, using a coinset of 25-, 20-, and 1- cent coins
(same as the one used by Connor in his article), we can provide change for
40-cents using two 20-cent coins. Similarly, we can provide change for 80-cents
using four 20-cent coins. A greedy solution that uses two 25-cent coins, one
20-cent coin, and ten 1-cent coins (for a total of 13 coins) would fail the
requirement for the target function to provide change for 80-cents using no
more than 4 coins.

#### Conclusion

Many functions can be tightly-bound using a set of invariants. However, the key
is to apply higher-order thinking than what we are used to with classical unit
testing.

My concerns for wide-applicability of property-based tests are not entirely
eliminated. Nevertheless, with a single short exercise, the universe of
non-applicability has shrunk dramatically. I still need to use property-based
tests in production code to get a better feel for their applicability and
efficiency.

For anyone that is reading this, I would love to know if there is a reason that
prevents the adoption of property-based (only) tests for a project. Please
don't hesitate to get in touch to discuss.
