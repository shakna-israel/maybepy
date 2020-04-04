# maybepy

---

A different way of handling exceptional circumstances in Python.

---

There are two main ways of generating the Maybe containers:

* Decorator (`maybepy.decorate`)
* Direct call (`maybepy.wrap`)

    @maybepy.decorate
    def this_raises(a, b):
        raise SyntaxError

    x = this_raises(1, 2)

    def this_raises(a, b):
        raise SyntaxError

    x = maybepy.wrap(this_raises, 1, 2)

Once you have captured the Maybe object, `x` in our examples above, you can inspect it:

    if x.is_exception() == False:
        x.get()

You can also inspect it for the type of exception:

    if x.is_exception():
        if x.get_exception() == SyntaxError:
            print("We have a syntax problem.")

You can also get a traceback object, to use with Python's traceback tools:

    if x.is_exception():
        obj = x.get_traceback()

Finally, you can unpack it:

    if x.is_exception() == False:
        val = x.get()

If you run the `Maybe.get()` method against an object
that contains an exception and not a value, then it will
immediately raise that exception.

To use it safely, you should always check if it contains the exception first.

---

# License

See the LICENSE file.

CC0 1.0 Universal at time of writing.
