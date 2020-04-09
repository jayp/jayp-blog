---
title: A weekly changelog makes us go fast 🏃‍♂️
date: 2020-04-08T13:43:43-07:00
tags: ["product"]
---

Neel and I started working on [Herald](https://www.heraldhq.com) in December 2019. It's [the best space for teams to collect, analyze, and collaborate on user feedback](https://www.heraldhq.com). Working feverishly over the winter break, we got the MVP in the hands of our first customer in on January 2nd. From then on, we've maintained a weekly [changelog](https://www.notion.so/herald/What-s-New-2f90a8e462da42758878e34bb5a3371c).

{{< fig2 src="/herald-changelog.png" caption="A screenshot of the Herald changelog"
link="https://www.notion.so/herald/What-s-New-2f90a8e462da42758878e34bb5a3371c" >}}

As you may notice, our changelog is nothing fancy - just a simple Notion document. We also follow a simple format for each update:

- Date of update (always a Friday so far) along with a brief theme of the weekly changes.
- Details on the top 2-3 changes alongside a video/photo artifact exhibiting the change.
- A "Bug Fixes & Other Improvements" section with less important changes. We aim to provide details succintly here.

Every two weeks, we also rollup the changes for the past two updates and send out an email to our users.

As you can imagine, producing the changelog is a fairly taxing task: planning and completing the work, and producing the copy and any associated artifacts demontrating usage. Given that as a super early stage startup that's always stretched for time, we often wondered **why do we maintain this changelog?** This was especially a big question early on, when we only had one customer and it could've been far easier to just show them any changes.

### Cost of Changelogs

Maintaining a changelog _mostly_ requires maintaining a regular cadence. Otherwise, it is too easy to skip it "just this once". As such, we picked a weekly cadence -- which requires us to _**ship some user-facing changes every week**_. This requirement can often be a downside when the right thing to do is to hunker down and solve a larger customer problem. Worse, maybe the best thing that week may not even be feature development but an infrastructure change, or maybe even non-product work like sales or marketing. In other words, a weekly changelog basically forces us to do product work every week even if it's not the best thing for that week.

{{<note Disclaimer>}}
A dogmatic publishing cadence is not a requirement for a good changelog. It
doesn't seem like
[Notion](https://www.notion.so/What-s-New-157765353f2c4705bd45474e5ba8b46c)
has one.
{{</note>}}

An alternative to a dedicated changelog is to simply use the company's blog
to write about major product updates whenever they occur. With this approach,
there is no need to align to a fixed update cadence providing the flexibility
to work on bigger and bolder challenges that may not be shippable in a week.

So, **is a dedicated changelog too much work with plenty of rigidity?**

### Benefits of Changelogs

After maintaining a changelog for the last 3 months, I'd have to say that it's a large net positive. In fact, we'd love to _**maintain our weekly changelog for as long as possible**_. The two primary benefits we're getting out of our changelog are:

- **Accountability**: Make sure we ship at least two customer-facing product
  features every week. As a young startup, we're glad that our product iterations
  adhere to a certain product velocity floor.
- **Iterate with Customers**: A short window to get new features out means
  that we do not have the luxury to come up with grand plans, execute them,
  then reveal it to our customers. From our previous experiences (and
  failures), we've learnt that we are suckers for grand plans that don't pan
  out. With the current model, we descope feature work to something we can ship
  in a max of two days. Often, it means shipping half-baked features, but it
  still seems to be working out for us. When customers engage with the new
  changes, they often ask us for additional features we had descoped -- but now we can
  work on them knowing fully that it will be a meaningful change. However, just as
  often, when customers don't even end up using the new features or ask us
  for entirely different things than we had imagined, we can course correct
  at a far lower cost.

It's still early days for us at Herald, but we are totally loving using the changelog as a mechanism to plan our weekly sprints. You may have noticed that I didn't even mention that the changelog informs our users about new changes as a benefit— **it is just an added bonus** and not our primary motivating factor. Our most engaged users check our changelog religiously and provide us earnest feedback, which we obviously save in our dogfood instance of [Herald](https://www.heraldhq.com).

### An Industry Trend: The Fall and Rise of Changelogs

Historically, changelogs were a given for all software — as software needed
to be installed on a customer's computer. They informed users about the
amazing value they'd get if they _just_ upgraded to the newest version of the
software. The biggest reason for maintaining changelogs was the revenue that
accompanied upgrades. However, with the rise of SaaS and recurring revenue
models, the monetary reasons for maintaining a changelog no longer hold. As
such, we've seen a decline of dedicated changelogs with the rise of SaaS.

However, a new breed of SaaS companies are producing are going back to maintaining a dedicated changelog. Some of my favorites changelogs are: [Notion](https://www.notion.so/What-s-New-157765353f2c4705bd45474e5ba8b46c), [Linear](https://linear.app/changelog), [Tandem](https://www.notion.so/Tandem-Product-Updates-618030187c7843a78ba76ada4f54bd01), and [OpenPhone](https://updates.openphone.co/). I am always looking to read and learn from good changelogs -- [let me know](https://www.twitter.com/jayisms) if
you know of a good one.
