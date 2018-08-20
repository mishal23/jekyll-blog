---
layout: post
title:  "Chaos Engineering"
date:   2017-12-19 21:32:40 +0530
img: 
description: What does it take to build confidence in your system's behaviour while in production? How do companies like Netflix, Google and Twilio find unknown weaknesses in their production systems?
---

## Introduction

Many of us would have heard about the two major WhatsApp outages recently when it was down for about an hour each time. For the general public, WhatsApp was down for an hour. But for software engineers, WhatsApp was back within an hour. This made me wonder what it was, that enabled the engineers working at WhatsApp to restore the services so fast.

![WhatsApp Outage]({{"/assets/img/whatsapp-outage.png"}})

What if I tell you, it was a very **normal** turbulent production failure for them. Yes, huge companies like [Netflix](https://www.netflix.com/in/), [Facebook](https://www.facebook.com/) and [Google](https://www.google.co.in/) use a method of engineering called **Chaos Engineering**.

To explain Chaos Engineering in layman terms :
To be good at something , if one practices it in extreme conditions then it would get easier for the person to perform in normal conditions. Similarly if a software engineer has seen extreme conditions in production, it becomes a challenge for him/her to code in such a way that their service fails if such an extreme condition occurs. If at all it comes, they would have experienced it before and so it becomes easy to bring the services back.

![Chaos Engineering]({{"/assets/img/chaos-engineering.png"}})

## Principle of Chaos Engineering

The main idea of Chaos Engineering is to intentionally inject failures so as to be prepared for the worst conditions.
A formal definition for Chaos Engineering given by Netflix:
> Chaos Engineering is the discipline of experimenting on a distributed system in order to build confidence in the system’s capability to withstand turbulent conditions in production.

Chaos Engineering can be thought of as the facilitation of experiments to uncover systemic weaknesses. These experiments follow four steps:

1. Start by defining ‘steady state’ as some measurable output of a system that indicates normal behavior.
2. Hypothesize that this steady state will continue in both the control group and the experimental group.
3. Introduce variables that reflect real world events like servers that crash, hard drives that malfunction, network connections that are severed, etc.
4. Try to disprove the hypothesis by looking for a difference in steady state between the control group and the experimental group.

The harder it is to disrupt the steady state, the more confidence we have in the behavior of the system. If a weakness is uncovered, we now have a target for improvement before that behavior manifests in the system at large.
In layman terms: Break your system, see the difference between steady state and experimental state, lesser the difference, lesser it will break in production. If the difference is more, you have a target for improvement before actually experiencing it in production.
	
## Practical Use

Netflix, a pioneer in the field of Chaos Engineering, uses a tool called Chaos Monkey. It randomly picks a server from production deployment on AWS (Amazon Web Services) and kills it. Executives at Netflix knew that server failures are guaranteed to happen and they wanted servers to fail during working-hours so that it could be fixed it in the presence of their engineers. They knew that they could rely on engineers to build resilient solutions if they were given context to expect servers to fail. If they could align their engineers to build services that survive a server failure, then when it actually happened, it wouldn’t be a big deal.

## How can it help you?

Suppose your team has built the next wave of advancement the whole world has been waiting for. You are to launch your service but there are questions rumbling in your mind:

* Is your application ready for production?
* Will the system survive the failures of other companies you are dependent on?
* Will the system survive the failure of your own configurations?

The truth is : You can never be sure . There will always be something that can be wrong or will go wrong. Some things aren’t in your control like denial-of-service attacks or network failures. Sometimes, bad things just happen.

Possibly The only solution for it is to build quality software that is resilient to failures. As the saying goes - *"Hope for the best, prepare for the worst"*
But how can your team be sure that your system is ready for production and is ready to face all difficulties/failures? *This is where Chaos Engineering comes into picture.*

## Does this seem like testing?

It may indeed sound like it, but it definitely isn’t testing. Chaos Engineering is an experiment on the production environment and there is certainly no way to accurately duplicate production environment at scale (as in testing). The experiment itself is going to have a systemic effect that could change your results, so the only way to accurately build conflict in the system that you have now is to experiment on it.

## Conclusion

The purpose of Chaos Engineering is to experience disastrous conditions. This might sound like a difficult task and it does require a lot of creativity but the extra effort is worth it. You must inject failures in your system such that certain part of your infrastructure becomes unavailable. Some examples are : terminate cluster machines, kill worker processes, delete database tables, cut off access to internal-external services, etc. Later you can also simulate events capable of disrupting steady state like high latency due to slow networks.

These experiments are a bit difficult but whatever you decide to do, you’ll be surprised at how much you can learn from chaos.
There are a lot of tools worth mentioning :

* [Chaos Monkey](https://github.com/Netflix/chaosmonkey) - A resiliency tool that helps applications tolerate random instance failures
* [The Simian Army](https://github.com/Netflix/SimianArmy) - A suite of tools for keeping your cloud operating in top form
* [kube-monkey](https://github.com/asobti/kube-monkey) - An implementation of Netflix's Chaos Monkey for Kubernetes clusters
* [Gremlin Inc.](https://www.gremlin.com/) - Failure as a Service
* [Pumba](https://github.com/alexei-led/pumba) - Chaos testing and network emulation for Docker containers (and clusters)
* [Chaos Toolkit](https://github.com/chaostoolkit/chaostoolkit) - A chaos engineering toolkit to help you build confidence in your software system
* [orchestrator](https://github.com/github/orchestrator) - MySQL replication topology management and HA

I hope you got an idea about Chaos Engineering - a powerful approach to build resilient systems!

<!-- You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. You can rebuild the site in many different ways, but the most common way is to run `jekyll serve`, which launches a web server and auto-regenerates your site when a file is updated.

To add new posts, simply add a file in the `_posts` directory that follows the convention `YYYY-MM-DD-name-of-post.ext` and includes the necessary front matter. Take a look at the source for this post to get an idea about how it works.

Jekyll also offers powerful support for code snippets:

{% highlight ruby %}
def print_hi(name)
  puts "Hi, #{name}"
end
print_hi('Tom')
#=> prints 'Hi, Tom' to STDOUT.
{% endhighlight %}

Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
 -->