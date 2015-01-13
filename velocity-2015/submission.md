
##Title
Performance by the Numbers: analyzing the performance of web applications

##Description
Everyone knows poor performance when they see it, and performance concerns affect every application -- web applications more than most.  But finding performance problems can be extraordinarily difficult, and requires an analytical approach coupled with good instrumentation. This talk explores approaches to instrumentation and what that instrumentation can tell you.

##Audience:
Web engineers and devops engineers. This talk introduces key concepts in performance analysis.

##Objectives:
When leaving this talk, an attendee should have a sense of how important peformance is to a company's bottom line. They should understand the role of profiling in performance analysis. They should understand what operating system tools can reveal about application performance. They will know approximately how to go about building custom instrumentation tools. They will know what Etsy's statsd package does, and how to leverage it. They will also understand the role of distributed tracing in performance analysis.

##Detailed Abstract:
Performance is not an easy problem to solve. Intuitively applying optimizations and hoping for the best produces poor results. Inferring application characteristics from operating system metrics can mislead. Only application instrumentation can provide deep insight into application performance. Instrumenting apps is hard, though, and interpreting the results can be even harder.

Profilers and system metrics are the first tools most engineers reach for, but neither is very good at understanding the performance implications of application behavior. Understanding the performance of production applications requires tools that measure the performance of production applications.

This sort of instrumentation comes in many forms. Developers often write their own monitoring endpoints. Etsy's statsd couples well with graphite as a tool to instrument an application by hand. Distributed tracing tools offer a different way of looking at latency, by putting it in the context of a request/response cycle. Each of these tools has a role in uncovering some aspect of application performance.

##Outline:
1. Performance is Hard
    1. The most common antipatterns. Credit Brendan Gregg.
    2. The "drunk man" with a story.
    3. The "stoplight" with a story.

2. Rigorous Analysis: Profilers
    1. Everyone thinks of profilers. Because they're awesome!
    2. Story about profiling.

3. Rigorous Analysis: Host Metrics
    1. Look at this graph! Credit Brendan Gregg.
    2. Host metrics don't say much about your code.

4. Rigorous Analysis: Ad Hoc Metrics and Etsy
    1. Roll yer own!
        1. Flask, Bottle, Thrift. 
        2. Sample architectures.
    2. Statsd + Graphite
    3. Weaknesses of approach

5. Rigorous Analysis: Tracing
    1. Tracing approach
    2. Tracing tools: Dapper, Zipkin
    3. Tracing vendors: New Relic, AppNeta, AppDynamics

6. Conclusion: Hybrid Approach
7. Questions


##Additional Notes:
- I'm giving a slightly re-tuned version of this talk at PyCon 2015 in Montreal.
- Previously I have spoken at a handful of meetups, including a well-received talk on Backbone.js + Django at the Boston Django meetup. That event page is [here](http://www.meetup.com/djangoboston/events/39694032/) with [slides here](http://www.slideshare.net/ggerrietts/show-some-spine), and [sample code here](https://github.com/ggerrietts/vertebrate-django).
- I wrote my first performance instrumentation in 2005 as a CORBA service tracking aggregate service response times while building up what would now be called a DevOps group. Performance, scalability, and best practices have been areas of interest ever since.
- I am a development manager at AppNeta, with a ton of performance-related stories and lots of examples of performance done right and done wrong.
