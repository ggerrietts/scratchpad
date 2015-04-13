
# Functions Before Fashions
## keeping decorators in their place


Decorators are a powerful feature in Python, and a popular intermediate
programming topic among Pythonistas. Many blogs and tutorials have been written
about how to use decorators. Not all of them are quite as elucidating on the
topic of *when* to use decorators. I implore you: be selective.

I hate decorators. I don't really hate decorators, but they can definitely make
me cry. Once upon a time, function signatures started with `def` and times were
simple. Now, too many projects have a stack of little `@`-prefixed names piled
atop the signature, like little worms feasting upon the semantic weight of the
code.

Bombastic metaphor aside, Python's support for decorators arrived in 2.4. The
change was really minor. Programmers could decorate functions even back in
1.5.2. Python 2.2 brought the `classmethod` and `staticmethod` functions, which
were intended to decorate callables. The change in 2.4 was to add syntactic
sugar to make using decorators simpler. This (slightly updated) example from 
[PEP 318](http://legacy.python.org/dev/peps/pep-0318/) illustrates the
awkwardness that decorator syntax tried to replace:

```
def foo(cls):
    """" perform method operation """
foo = classmethod(foo)
```

The modern equivalent isn't that much more compelling, but it does help convey
that the decorator modifies the function:

```
@classmethod
def foo(cls):
    """ perform method operation """
```

In its original intention, the decorator syntax wasn't a bad idea. But an
unintended side-effect of special syntax has been a proliferation of decorators
across codebases of all sorts. I've been witness to method signatures that have
a seven deep stack of decorators `@`-pancaked on top. Terrifying!

This is an epidemic, not a bountiful harvest. Decorators have entered the mainstream, and the lightweight syntax they offer has created a sense that the 


