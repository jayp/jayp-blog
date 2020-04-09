---
title: "Don't drop the ring"
date: 2014-11-18T20:30:00-07:00
tags: ["programming", "clojure"]
---

If you are a Clojure newbie ("noob") like myself, you may run into this issue.
I am only writing this since it took me a lot longer to resolve this "issue"
than it should have. My hope in writing this article is to help future noobs
Googling for a solution to the same problem.

As it happens, I am currently developing a web app using
[compojure](https://github.com/weavejester/compojure) on top of
[ring](https://github.com/ring-clojure/ring). As I had done a couple times
before, I made an uberjar to deploy the web app as a standalone server:

```
$ lein uberjar
```

When I ran the jar, I was expecting the webapp to run. Instead I got a Clojure
REPL prompt. Yes, I got a Clojure REPL prompt instead of my webapp deploying.
No Jetty. No Webserver. Nope. Instead, a REPL prompt as follows:

```
$ java -jar webapp-0.1.0-standalone.jar
Clojure 1.6.0
user=>
```

I was perplexed. I tried to investigate the changes I made. Using git, I even
went back to a prior commit which I knew worked. But I was unable to get the
webapp to start. What the &$#!@ was going on?

As such, I unziped the jar file and took a look at the META-INF/MANIFEST.MF
file. The Main-Class value was: clojure.main. Grr!

Long story short: I traced back my bash history and noticed that I had dropped
the ring!  Of course, the command to generate a deployable webapp is the
following:

```
$ lein ring uberjar
```

So, fellow Clojure noobs, the lesson is: don't drop the ring!

