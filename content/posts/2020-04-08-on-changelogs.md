---
title:  Public changelogs keeps us moving fast 🏃‍♀️🚀
date: 2020-04-08T13:43:43-07:00
tags: ["product"]
---

### The Rise and Fall and Rise Again of Changelogs

**Changelogs** (or **What's New** or **Product Updates**) are used by software
makers to inform their users about changes that were shipped recently.

Historically, changelogs were a given for all software — as software needed
to be installed on a customer's computer. They informed users about the
amazing value they'd get if they *just* upgraded to the newest version of the
software. The biggest reason for maintaining changelogs was the revenue that
accompanied upgrades. However, with the rise of SaaS and recurring revenue
models, the monetary reasons for maintaining a changelog no longer hold. As
such, we've seen a decline of dedicated Changelogs with the rise of SaaS.

However, a new breed of SaaS companies are now maintaining dedicated
changelogs. Some of my favorites are: [Notion](https://www.notion.so/What-s-New-157765353f2c4705bd45474e5ba8b46c),
[Linear](https://linear.app/changelog),
[Tandem](https://www.notion.so/Tandem-Product-Updates-618030187c7843a78ba76ada4f54bd01),
and [OpenPhone](https://updates.openphone.co/). **Why are these companies maintaing changelogs?***

{{<note "Good Changelogs?">}}
I am always looking to read and learn from good changelogs. Let me know if
you know of a particularly good one.
{{</note>}}

### Cost of Changelogs

To maintain a changelog today, SaaS providers have to determine all the
important user-facing changes periodically, and write about it. Maintaining a
changelog almost requires the forcing function of a regular cadence.
Otherwise, it is too easy to skip it "just this once". But a fixed cadence
also forces teams to artificially demonstrate progress by shipping something
in a fixed time window when the better path might be to take more time to
build a more robust feature.

{{<note>}}
A dogmatic publishing cadence is not a requirement for a good changelog. It
doesn't seem like
[Notion](https://www.notion.so/What-s-New-157765353f2c4705bd45474e5ba8b46c)
has one.
{{</note>}}

An alternative to a dedicated changelog is to simply use the company's blog
to write about major product updates whenever they occur. In this approach,
there is no need to align to a fixed cadence. This has another huge benefit —
companies have the flexibility to work on bigger and bolder challenges that
may not be shippable in a fixed amount of time.

So, **is a dedicated changelog too much work and plenty of downsides?**


### Benefits of Changelogs

Neel and I started working on [Herald](https://www.heraldhq.com) in December
2019. We got the MVP in the hands of our first customer in the first week of
January.

{{<note "What is Herald?">}}
[Herald](https://www.heraldhq.com) sets up teams to serve customers first .
It's [the best space for teams to collect, analyze, and collaborate on user
feedback.](https://www.heraldhq.com)
{{</note>}}

From then on, we've maintained a
[changelog](https://www.notion.so/herald/What-s-New-2f90a8e462da42758878e34bb5a3371c)
that Neel updates every week. We continue to maintain this cadence today and
plan to do it for as long as possible. We will continue to evaluate the right
cadence every quarter, and at some point, the right cadence might become
bi-weekly or monthly as our product matures.

{{< figure src="/herald-changelog.png" class="screenshot" caption="**A screenshot of Herald's changelog**"
link="https://www.notion.so/herald/What-s-New-2f90a8e462da42758878e34bb5a3371c"
>}}

Ultimately, we decided on keeping a changelog primarily for two reasons:

- **Accountability**: Make sure we ship at least two customer-facing product
features every week. As a young startup, we wanted our product iterations to
adhere to a certain product velocity floor.
- **Iterate with Customers**: A short window to get new features out means
that we do not have the luxury to come up with grand plans, execute them,
then reveal it to our customers. From our previous experiences (and
failures), we've learnt that we were suckers for grand plans that didn't pan
out. With the current model, we descope feature work to something we can ship
in a max of two days. Often, it means shipping half-baked features, but it
still seems to be working for us. Most customers don't engage with new
features right away — they are busy with a hundred other things. But when
they do, and they ask us for features we descoped, we can work on them
knowing that it is a meaningful change. However, just as often, if customers
don't even end up using the feature, we can just cut it out from the product
and be at peace with the time saved.

It's still early days for us at Herald, but we are totally loving using the
changelog as a mechanism to plan our weekly sprints. You may have noticed that I
didn't even mention that the changelog informs our users about new changes as
a benefit— it is just an added bonus and not the primary motivating factor.

{{<note Feedback>}}
Let me know what you think about this article. Has your team adopted a
changelog-oriented development process? What do you think about it?
{{</note>}}