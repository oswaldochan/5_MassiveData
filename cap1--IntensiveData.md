# Chapter 1

## Reliability

### What does it mean that a system is reliable?

> The system should continue to work correctly (performing the correct function at the desired level of performance) even in the face of adversity (hardware or software faults, and even human error)

### What are hardware faults and how can we deal with them?

When hard disks crash, RAM becomes faulty, the power grid has a blackout, someone unplugs the wrong network cable, it is a _hardware fault_.

Commonly, those kind of problems are dealt with redundancy of hardware, like 

> Disks may be set up in a RAID configuration, servers may have dual power supplies and hot-swappable CPUs, and datacenters may have batteries and diesel generators for backup power.

### What are software errors and how can we deal with them?

They are systematic errors that are usually triggered by unusual circumstances. They usually remain hidden until this happens, so they are very difficult to detect from the beginning

Given that, there’s no quick solution to the problem of systematic faults in software, but small things may be helpful to mitigate them:

- Carefully thinking about assumptions and interactions in the system
- Thorough testing
- Process isolation
- Allowing processes to crash and restart
- Measuring, monitoring, and analyzing system behavior in production

## What are human errors and how can we deal with them?

It is the most common cause of outages, and as the name suggests, are human-caused errors, whether they are caused by the person who designs and implements the system, or by the person who maintains it

The best way to deal with them involves several approaches:

-  Design systems in a way that minimizes opportunities for error. _However, if the interfaces are too restrictive people will work around them, negating their benefit, so this is a tricky balance to get right_ 
- Decouple the places where people make the most mistakes from the places where they can cause failures
- Test thoroughly at all levels, from unit tests to whole-system integration tests and manual tests 
- Allow quick and easy recovery from human errors, to minimize the impact in the case of a failure
-  Set up detailed and clear monitoring, such as performance metrics and error rates
- Implement good management practices and training

## Scalability

### What does it mean that a system is scalable?

> As the system grows (in data volume, traffic volume, or complexity), there should be reasonable ways of dealing with that growth

### What is _load_ and how can we describe it?

  Load can be described with a few numbers which we call load **parameters**, and is useful to discuss the growth of the system.

> The best choice of parameters depends on the architecture of your system: it may be requests per second to a web server, the ratio of reads to writes in a database, the number of simultaneously active users in a chat room, the hit rate on a cache, or something else. Perhaps the average case is what matters for you, or perhaps your bottleneck is dominated by a small number of extreme cases. 

![image-20200601010410128](C:\Users\oswaldo\AppData\Roaming\Typora\typora-user-images\image-20200601010410128.png)

> The first version of Twitter used approach 1, but the systems struggled to keep up with the load of home timeline queries, so the company switched to approach 2. This works better because the average rate of published tweets is almost two orders of magnitude lower than the rate of home timeline reads, and so in this case it’s preferable to do more work at write time and less at read time. 

### What is the difference between _latency_ and _response time_?

> The *response time* is what the client sees: besides the actual time to process the request (the service time), it includes network delays and queueing delays. *Latency* is the duration that a request is waiting to be handled—during which it is latent, awaiting service

### Why is it better to use _percentiles_ to measure the response times while evaluating performance?

> It’s common to see the average response time of a service reported. However, the mean is not a very good metric if you want to know your “typical” response time, because it doesn’t tell you how many users actually experienced that delay. 
>
> If you take your list of response times and sort it from fastest to slowest, then the median is the halfway point: for example, if your median response time is 200 ms, that means half your requests return in less than 200 ms, and half your requests take longer than that.
>
> Using percentiles, if the 95th percentile response time is 1.5 seconds, that means 95 out of 100 requests take less than 1.5 seconds, and 5 out of 100 requests take 1.5 seconds or more.

### What are the two types of scaling in a system?

- **Scaling up**: _vertical scaling_, moving to a more powerful machine
- **Scaling out**: _horizontal scaling_, distributing the load across multiple smaller machines

## Maintainability

### What does it mean that a system is maintainable?

> Over time, many different people will work on the system (engineering and operations, both maintaining current behavior and adapting the system to new use cases), and they should all be able to work on it productively

### What is operability?

> It is when you make it easy for operations teams to keep the system running smoothly.
>
> Good operability means making routine tasks easy, allowing the operations team to focus their efforts on high-value activities

#### What situations should be manageable by a good operations team?

> • Monitoring the health of the system and quickly restoring service if it goes into a bad state 
>
> • Tracking down the cause of problems, such as system failures or degraded performance 
>
> • Keeping software and platforms up to date, including security patches 
>
> • Keeping tabs on how different systems affect each other, so that a problematic change can be avoided before it causes damage
> • Anticipating future problems and solving them before they occur (e.g., capacity planning) 
>
> • Establishing good practices and tools for deployment, configuration management, and more 
>
> • Performing complex maintenance tasks, such as moving an application from one platform to another 
>
> • Maintaining the security of the system as configuration changes are made 
>
> • Defining processes that make operations predictable and help keep the production environment stable 
>
> • Preserving the organization’s knowledge about the system, even as individual people come and go

#### If good operability is _making routine tasks easy_, what are some examples of it in a data system?

> • Providing visibility into the runtime behavior and internals of the system, with good monitoring 
>
> • Providing good support for automation and integration with standard tools 
>
> • Avoiding dependency on individual machines (allowing machines to be taken down for maintenance while the system as a whole continues running uninterrupted) 
>
> • Providing good documentation and an easy-to-understand operational model (“If I do X, Y will happen”) 
>
> • Providing good default behavior, but also giving administrators the freedom to override defaults when needed 
>
> • Self-healing where appropriate, but also giving administrators manual control over the system state when needed 
>
> • Exhibiting predictable behavior, minimizing surprises

### What is simplicity?

> Is is when you make it easy for new engineers to understand the system, by removing as much complexity as possible from the system. (Note this is not the same as simplicity of the user interface.)

### What are some symptoms of complexity?

- explosion of the state space

-  tight coupling of modules

-  tangled dependencies

- inconsistent naming and terminology

- hacks aimed at solving performance problems

- special-casing to work around issues elsewhere

- and many more

  > One of the best tools we have for removing accidental complexity is abstraction. A good abstraction can hide a great deal of implementation detail behind a clean, simple-to-understand façade

### What is evolvability?

> It is when you make it easy for engineers to make changes to the system in the future, adapting it for unanticipated use cases as requirements change. Also known as extensibility, modifiability, or plasticity

It is the agility on a data system



