
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

Profilers are the first tool in the performance remediation toolkit. It's hard to say anything bad about profilers, too: they're an excellent tool for analyzing application performance. Profilers work best "in the lab," though. They are too expensive to run in production. In the lab, it can be hard to recreate runtime conditions sufficiently well to gain broad insight into performance. Profilers are best used later in the analysis process.

Learning about the behavior of production web applications requires tools that measure the behavior of web applications in production. Host metrics, such as can be retrieved from top, strace, lsof, and other such tools provide a common starting point. These tools can help identify problems in under-provisioning, where applications have become starved for resources. But they don't do a great job of finding code paths that should be refactored -- places where your app is slow because the code is slow.

Tools that hunt out slow code are designed to measure the performance of code. These tools could be built by hand without too much difficulty, with technologies like Flask or Bottle or even Apache Thrift. Etsy generalized this approach in the form of statsd, which is designed to talk to Graphite. Graphite plots time series data into charts, making reporting on this data a simple matter of configuration. Instrumenting code paths like this can produce some key insights. But once you've discovered that `Cursor.execute()` is the main source of latency in your application, how do you proceed? That method gets called from almost everywhere. 

This niche is where application tracing comes in. Rather than collect aggregate data about individual method invocations, a trace-based approach samples incoming requests and monitors their progress through the application stack, recording latency at each layer. This approach is laid out in the X-Trace paper, or Google's Dapper paper, and realized in tools like Twitter's Zipkin. Vendors like New Relic, AppNeta, and AppDynamics also provide this kind of tool. Tracing's weak spot comes from its sample-based nature. Tracing uses sampling to reduce its impact on runtime performance, but random sampling can miss outliers, and sometimes outliers are exactly the things you need to catch.

A mature approach to performance analysis and remediation includes all these strategies. Profilers are used to analyze problem code paths. Operating system metrics are used to watch for resource starvation. Ad-hoc metrics are tracked to watch for outliers and keep track of specialized behaviors. Tracing tools provide an understanding of latency throughout the life of a request, within the context of that request. With that toolkit, an engineer can understand an application's latency profile, and make informed decisions about how to address its problems.

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
- Previously I have spoken at a handful of meetups, including a well-received talk on Backbone.js + Django at the Boston Django meetup.
- I've been on-and-off active in the Python community for years. I contributed regularly to the Python mailing list in the early 2000's, and built/maintained the (now-defunct) LiveJournal client Stoutpamphlet.
- I inherited Jack Diederich's ("Stop Writing Classes") first Python codebase and maintained it for several years.
- I wrote my first performance instrumentation in 2005 as a CORBA service tracking aggregate service response times while building up what would now be called a DevOps group. Performance, scalability, and best practices have been areas of interest ever since.
- Full disclosure: I'm currently a development manager for AppNeta, one of the vendors for tracing solutions. I expect this talk to discount my bias by also identifying our competition, identifying open source alternatives, not actually pitching our product but only showing a screenshot, and emphasizing that no single approach actually covers everything. It's a very fair treatment, though I understand why the committee might be sensitive.
