# Designing Babel
## leveraging polyglot architecture

![Tower of Babel](http://www.aquarianradio.com/wp-content/uploads/2013/02/babel.jpg)The story of the Tower of Babel is one of western civilization's earliest
cautionary tales. Encoded in its telling, we find the earliest known argument
against polyglot architectures. The plethora of languages, the argument states,
impedes productivity and detracts from the oneness of the people.

In fact, there's very little argument against polyglot programming or polyglot
architectures in contemporary discussion. It just seems to be an idea that runs
against the grain. Most development shops describe themselves in terms of their
language of choice -- you might work in a Java shop, or a Ruby shop, or a PHP
shop. The indirect evidence of job postings suggests that most development
teams think of themselves like this.

## but you're already polyglot!

Web development teams tend to think of themselves as a mono-language culture, but
very few teams really are. Even if you don't think of HTML or CSS as languages, 
most web development includes at least a little bit of Javascript. Most also
write at least a little SQL. I suppose there are probably a handful of Node
shops that really don't use any language other than Javascript, but I don't
think that's the majority of us.

We're already polyglot because different languages are better at targeting
different problem domains. For instance, it's *possible* to [script the browser
in Python](http://www.brython.info/), but most people don't choose to do so.
While Brython appears excellent, most of us have decided that Javascript has
easier integration, broad support, and superior tooling for client-side scripting.

Web applications are becoming more complex on the client side. Single-page apps
have proliferated, and even more traditional applications have been enhanced
with rich interactivity on each page. Javascript development is no longer the 
province of the Photoshop jockeys; browser-side code uses mature application
frameworks and sophisticated development paradigms. When you weren't looking,
your Ruby shop became a Ruby + Javascript shop.

## some things just work better

Dynamic languages trade performance for power of expression; this tradeoff
underlies their allure. Awareness of this tradeoff drives many technology
decisions. And for many people, once you've picked your path, that's the end of
it: you've chosen which upsides you want, and you've agreed to the downsides.
Polyglot architectures can shave these benefits a little finer, though, pushing
performance-critical passages down into a compiled language, or alternately
using a dynamic language to glue complex components together.

Polyglot architectures enable an application built under one framework, to make
use of components that are only available under others -- they can let your
Python application tap into the rich ecosystem Java enjoys, or they can let
your Ruby application make use of numerical code written in C. Adding
Websockets to your Django app require changing a ton of your stack? Have
Node.js handle the websockets instead, and coordinate with Django through
backchannels.

## and it's (relatively) easy to do

In the dark early days of web development, building a polyglot architecture was
moderately tricky. Extension APIs, subprocess calls, and CORBA were the premier
ways of communicating between executable units. Back then, SOAP still looked
like a good idea! But times have changed; service-oriented architectures are
commonplace and microservices are trending. Apache Thrift has filled in some of
the gaps that CORBA left open, and RESTful APIs are both easy to implement and
well-supported by tooling.

Much of the complexity that remains is operational complexity. Regrettably, it
will never be as simple to run a dozen microservices as it is to run a single
monolithic server process. It will also never be as simple to support two
application stacks as just one. But the rise of DevOps and configuration
management tools like Chef and Puppet help minimize this cost as well. The
complexity cost decreases with these advances.

## the right tool for the job makes for better craftsmanship

Every technical decision comes with a set of tradeoffs, and good engineering
tries to minimize exposure to the down sides. Choosing to introduce a new
language can help with that problem. While adoption of a new language may at
first seem to present challenges, particularly around staffing, most developers
are glad to have an opportunity to learn something new. And rather than
restricting your recruiting base, it actually expands it -- you can hire
experts in any of the languages you work in, and offer them the opportunity to
acquire expertise in others. Some short-term pain can build a stronger product,
and a stronger organization.
