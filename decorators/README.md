
# Get Your Finger Off That @ Key
## or why I hate decorators and you should too


I hate decorators. I don't really hate decorators, but I hate decorators. Once
upon a time, function signatures started with `def` and times were simple. Now,
too many projects have a stack of little `@`-prefixed names piled atop the
signature, like little worms feasting upon the semantic weight of the code.

Bombastic metaphor aside, Python added syntactic sugar for decorating callables
in 2.4. The change was really minor. Programmers could already do an in-place
transformation of a callable object. The `classmethod` and `staticmethod`
built-ins had been added in 2.2, and using those functions looked a little
awkward. This (slightly updated) example from 
[PEP 318](http://legacy.python.org/dev/peps/pep-0318/) illustrates the
awkwardness:

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


