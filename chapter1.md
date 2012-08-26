Chapter 1 - First steps with Snap
=================================

The most difficult part when learning a completely new technology is mostly to
get an idea how things work together at all. Nobody likes to read theoretic
stuff of something he has no idea of anyway yet, but it makes most sense to
dig right into the action and have a look at an easy to understand example.
After we got a feeling about the framework, we can start to analyze and
explain single parts of it to expand our knowledge step by step.

This section will cover the installation of the framework and demonstrate how
to use the scaffolding tool create "built in" applications, three examples
that you can have a quick look at and that you might want to use later when
you want to use parts of it's content. Have a look at the created code and
play around with it a bit if you wish, but you don't need to fully understand
each line of code for now - we will cover everything in further chapters.


Installation
------------

The installation of the framework is quite easy and can be done with two
command as they can be found on the
[download](http://snapframework.com/download) page of the framework:

    $ cabal update
    $ cabal install snap

The installation can take some time depending on how much dependency packages
you already installed previously.

After all packages have been downloaded and installed successfully, you are
probably most curious to try Snap right away, to see that this stuff really
works, especially if you are new to Haskell web development.


Scaffolding
-----------

As at the very beginning you won't have the overview about the framework to
know what to start with, Snap offers a scaffolding tool that automatically
creates minimal complete applications. Snap comes with three different
applications that can be created in such a way:

    $ snap init barebones
    
The first command creates a minimal but runnable example application
consisting of just 20 lines of code. The
[quickstart](http://snapframework.com/docs/quickstart) guide provides more
information about that variant. If you wish, just create a custom folder for a
test application, run that command, maybe have a look at the created files and
finally run the project either after a cabal installation 'cabal install' or
simply with 'runhaskell src/Main' if you don't want to install anything for
now. Your browser should show a simple 'hello world' response when you request
the 'localhost:8000' URL. It might also be helpful to read the [Snap API
introduction](http://snapframework.com/docs/tutorials/snap-api) which explains
the created application a bit more in detail.

    $ snap init tutorial

This command creates a small web application that already makes basic use of
so called 'Snaplets' which will be explained later in chapter X. The main file
is written in literate Haskell (.lhs) and is covered by the documentation page
about [Snaplets](http://snapframework.com/docs/tutorials/snaplets-tutorial)
which you don't need to read for now, we will come back to that (quite
important) topic later, no worries.

    $ snap init

The last command creates scaffolds of a default Snap web application. This
command will certainly be used most often for initializing a new Snap
application. It already contains some more code than necessary but it also
shows quite a few technologies working together which will be covered in later
chapters. If you can't wait you could install the created scaffolds via
'cabal install *youprojectname*' and then run it via './*youprojectname*' and
be amazed at what is already possible with less than 65 lines of code. But we
will cover those things later anyway so you don't need to do that for now.


Deployment
----------

After you now have created your first Snap applications and they (hopefully)
run fine locally [1] you might wonder how you can use Snap / Haskell as
implementation language for your own web application. Deployment is a topic
wich is mostly covered only at the end of tutorials (if even), but I
personally found it quite important to know right at the beginning if the new
technology is usable easily.

[SMALL SECTION ABOUT DEPLOYMENT] - dedicated server / CGI?


Now let's really start
----------------------

Alright, we are already done with the first chapter, which is intended to be
kept very short and simple. We haven't created anything ourselves yet, but
this will change from the next chapter. Again, if you have any feedback for us
how to improve this chapter or this tutorial feel free to contact us or modify
the according part yourself.

---

[1] If you ran into any problems while following the instructions here or in the
referred documentation don't hesitate to ask in the IRC channel or in the snap
mailing list where you will probably receive help very quick. You can find the
contact information on the [about](http://snapframework.com/about) page of the
framework.

[Next chapter: Basic infrastructure](https://github.com/J-Hannes/snap-tutorial/blob/master/chapter2.md)
