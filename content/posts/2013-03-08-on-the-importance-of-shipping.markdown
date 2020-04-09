---
title: On the importance of shipping
date: 2013-03-08T17:59:00-07:00
tags: ["product"]
---

Earlier today, our team was discussing a newly implemented feature during our
bi-weekly sprint review meeting. The feature introduced a configuration knob
that end users may adjust frequently. This knob was built atop our existing
configuration management system, which required the software to be restarted
for any change to take effect. This had been a known problem, however, as most
prior configuration knobs led to infrequent adjustments, we had avoided
fixing the root cause. Unfortunately, the new configuration knob now brought
this limitation to the forefront.

Our team manager proclaimed that the restart limitation was "embarrassingly
bad." _And, indeed, it was._ However, before anyone could delve any further on
this, a colleague aptly responded with the following lean development mantra:

> If you are not embarrassed by the first version of your product, you've launched too late.
>
> Reid Hoffman, LinkedIn Founder

Without any further discussion, everyone realized that it was acceptable --
maybe even expected -- to be embarrassed by our first release.

On this occasion, at least, we avoided feature creep.
