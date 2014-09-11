
##Title
Performance by the Numbers: analyzing the performance of web applications

##Description
Everyone knows poor performance when they see it, and performance concerns affect every application -- web applications more than most.  But finding performance problems can be extraordinarily difficult, and requires an analytical approach coupled with good instrumentation. This talk explores approaches to instrumentation and what that instrumentation can tell you.

##Audience:
mainly web engineers

##Objectives:
- have some numbers on the importance of performance
- understand the importance of instrumentation in performance remediation
- familiar with strengths and weakness of profiler as a performance analysis tool
- familiar with "roll your own" monitoring endpoints
- familiar with statsd + graphite for event tracking and timing
- familiar with distributed tracing tools (Zipkin, New Relic, AppNeta, AppDynamics)

##Detailed Abstract:
Businesses can rise or fall on the margins created by application performance. Conversions, revenue, and traffic all increase dramatically as websites get faster. Giant after internet giant has produced metrics reaffirming the importance of fractional seconds of response time.

Performance is not an easy problem to solve, though. Intuitively applying optimizations and hoping for the best produces poor results. Inferring application characteristics from operating system metrics can mislead. Only application instrumentation can provide deep insight into application performance. Instrumenting apps is hard, though, and interpreting the results can be even harder.

Profilers and system metrics are the first tools most engineers reach for, but neither is very good at understanding the performance implications of application behavior. Understanding the performance of production applications requires tools that measure the performance of production applications.

This sort of instrumentation comes in many forms. Developers often write their own monitoring endpoints. Etsy's statsd couples well with graphite as a tool to instrument an application by hand. Distributed tracing tools offer a different way of looking at latency, by putting it in the context of a request/response cycle. Each of these tools has a role in uncovering some aspect of application performance.


##Outline:
1. Performance Matters (4 minutes)
    1. Common sense: like art, we know good performance when we see it, and we like it. (1 minute)
    2. Look at these cool charts. 100ms = 1% conversion! (2 minutes)
    3. But "premature optimization is the root of all evil" so maybe we didn't spend a lot of time thinking about it when we wrote it. (1 minute)

2. Performance is Hard (4 minutes)
    1. The most common antipatterns. Credit Brendan Gregg.
    2. The "drunk man" with a story. (2 min)
    3. The "stoplight" with a story. (2 min)

3. Rigorous Analysis: Profilers (4 minutes)
    1. Everyone thinks of profilers. Because they're awesome! (1 minute)
    2. Story about profiling. (3 minutes)

4. Rigorous Analysis: Host Metrics (3 minutes)
    1. Look at this graph! Credit Brendan Gregg. (2 minutes)
    2. Host metrics don't say much about your code. (1 minute)

5. Rigorous Analysis: Ad Hoc Metrics and Etsy (5 minutes)
    1. Roll yer own! (2 minutes)
        1. Flask, Bottle, Thrift. 
        2. Sample architectures.
    2. Statsd + Graphite (2 minutes)
    3. Weaknesses of approach (1 minute)

6. Rigorous Analysis: Tracing (4 minutes)
    1. Tracing approach (2 minutes)
    2. Tracing tools: Dapper, Zipkin (1 minute)
    3. Tracing vendors: New Relic, AppNeta, AppDynamics (1 minute)

7. Conclusion: Hybrid Approach (1 minute)
8. Questions (5 minutes)


##Additional Notes:
- Previously I have spoken at a handful of meetups, including a well-received talk on Backbone.js + Django at the Boston Django meetup. That event page is [here](http://www.meetup.com/djangoboston/events/39694032/) with [slides here](http://www.slideshare.net/ggerrietts/show-some-spine), and [sample code here](https://github.com/ggerrietts/vertebrate-django).
- I've been on-and-off active in the Python community for years. I contributed regularly to the Python mailing list in the early 2000's, and built/maintained the (now-defunct) LiveJournal client Stoutpamphlet.
- I inherited Jack Diederich's ("Stop Writing Classes") first Python codebase and maintained it for several years.
- I wrote my first performance instrumentation in 2005 as a CORBA service tracking aggregate service response times while building up what would now be called a DevOps group. Performance, scalability, and best practices have been areas of interest ever since.
- Full disclosure: I'm currently a development manager for AppNeta, one of the vendors for tracing solutions. I expect this talk to discount my bias by also identifying our competition, identifying open source alternatives, not actually pitching our product but only showing a screenshot, and emphasizing that no single approach actually covers everything. It's a very fair treatment, though I understand why the committee might be sensitive.
