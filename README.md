Snap tutorial
=============

*Note: This tutorial is still heavy work in progress as the writing has just
started which means parts and even the table of contents can still change a
lot, but this will reduce more and more over the time. Everybody is anyway
invited to contribute with ideas or improvements that can be included into
it's development.*


What is this?
-------------

A tutorial to learn how to write high level web applications with the
[Haskell](http://haskell.org) web framework [Snap](http://snapframework.com).

The tutorial will start from the very beginning, assuming that the reader has
never heard of the Snap framework before, and demonstrate by simple examples
how to use Snap for writing web applications. Therefore the tutorial is
divided into multiple parts (chapters). Each chapter tries to contain just one
new feature to learn, to keep single chapters as simple as possible and also
to leave them independent from another. Nothing is worse than if you already
know some basics and you want to learn a new feature xy from chapter 5 but
then you find out it continues with the example demonstrated in chapter 2
(hello Real World Haskell). In this tutorial the applications which are
created in each chapter are not depending each other.


Why do we need this?
--------------------

The nice thing of the Snap framework is, that it already comes with **a lot** of
good documentation. First of all you can find very comprehensive articles on
the framework's homepage itself, like the [quick
start](http://snapframework.com/docs/quickstart), the [Snap
API](http://snapframework.com/docs/tutorials/snap-api), the [Heist
tutorial](http://snapframework.com/docs/tutorials/heist) or the [Snaplets
tutorial](http://snapframework.com/docs/tutorials/snaplets-tutorial).

Secondly the [Snap API on Hackage](http://hackage.haskell.org/package/snap) is
very well documented, sometimes even readable like a
[tutorial](http://hackage.haskell.org/packages/archive/snap/0.9.1.1/doc/html/Snap-Snaplet.html).

Thirdly the open source code of the framework itself can be found on
[Github](https://github.com/snapframework/snap) does not only contain good
documentation in the code itself but also contains some more tutorials and
tests that are a good source to learn from.

Furthermore there exist quite a few slides and other material from
presentations which give a quick or also quite detailed introduction into the
framework, like the one of
[gcollins@CUFP2011](http://gregorycollins.net/posts/2011/10/01/cufp-tutorial-slides),
one about [How to create a StarCraft 2 blog with
Snap](http://bonus500.github.com/sc2blog) or one from the
[Hal7](http://patch-tag.com/r/shahn/hal-snap-2012/snapshot/current/content/pretty/slides.pdf).

And last but not least, there exist plenty of blog entries of the developers
of the framework, like [mightybyte](http://softwaresimply.blogspot.co.uk),
[jaspervdj](http://jaspervdj.be), [norm2782](http://norm2782.github.com) and
probably some others which may have been forgotten here.


So if we already have so many sources of good documentation why should we need
another tutorial? Hum, maybe we wouldn't even need one. But when I started to
learn Snap, which was nearly one year ago from now, I had problems to
understand the framework and - especially - how it works. Despite all good
sources of documentation it was not always easy to find them. I was asking
badly for examples, examples, examples. Show me how this works... show me how
that works. And it was quite cumbersome to look for specific examples and
explanation for every hurdle I ran into. It would have been easier if there
were somebody who takes my hand and leads me through the world of we
development with Snap. One source that contains most of the knowledge that is
necessary when you want to develop your web applications with Snap. This is
exactly what this tutorial here is trying to provide.


Why Snap?
---------

Haskell web development really started off around 2 years ago from now I would
suppose. As Haskell is the worlds most powerful programming language, it's
problem is to find applications where Haskell is really good for and where all
it's purity, laziness and high level really shines. Web development seem to
be a field where a lot of advantages of Haskell can be applied.

Now, it is no secret that there exists not one, but three (plus many many
others) Haskell web frameworks that are currently developed and well
supported: The two others out there are [Yesod](http://yesodweb.com), a very
well developed web framework of mainly Michael Snoyman, Greg Weber and others
and [Happstack](http://happstack.com), a cool framework which developed from
the older HappS framework. Yesod, Happstack and Snap have all advantages and
disadvantages if compared to each other. There already exist
[multiple](http://stackoverflow.com/questions/5645168/comparing-haskells-snap-and-yesod-web-frameworks)
[discussions](http://softwaresimply.blogspot.co.uk/2012/04/hopefully-fair-and-useful-comparison-of.html)
of which one might be better than the other, but the bottom line is that you
can choose for yourself which one fit's best to your own preferences. It is
important to mention that each of the frameworks can be seen as a collection
of libraries that could even be used independently from each other, which
means you are not restricted to use Yesod OR Happstack OR Snap but you can use
libraries of all of the together if you like.

Choosing Snap among the others might be just a matter of taste or religion, but
one could argue that Snap has the 'cleanest' design of all of them. The API is
simple and comprehensive at the same time and after all it is 'pure Haskell'
even when put into a stack of monads, Snap does not need to have it's own DSL
to write easy readable web applications. That's why I've chosen Snap at least,
after trying each of them.


What do I need to bring?
------------------------

This tutorial is supposed to be an introductory documentation into the
framework for beginners of Snap. No reading about this framework is required
in advance, but some parts, like the installation etc. will be referred to
already existing documentation as I don't want to repeat what others already
wrote.

Nevertheless some knowledge has to be premised. I assume you have already
fundamental knowledge in web development. Ideally you have already developed
in PHP or Ruby or even frameworks of 'real' programming languages like Java
(JEE) or C++ (ASP.NET) etc., so you are familiar with concepts of distributed
programs (client server / SOA) but at least you should know the basics of web
development: HTML and CSS as this will be used throughout as 'front end'
markup language without further explanation. In case you are not, there exists
plenty of good learning resources. [W3schools](http://www.w3schools.com) might
be a good place to start with. JavaScript can of course be integrated as front
end language for Snap applications (while Haskell is the back end language) to
spice things up, but is not necessary.

The second thing that is more or less necessary to develop Snap web
applications is fundamental of Haskell. Basics (Haskell type system, higher
order functions, modules etc. etc.) are a must but ideally you have already
reached the intermediate level, means you know how to use type classes,
applicative functors, monads, monad transformers etc. we will need all that
stuff later on. Of course it is even possible to learn those things via
learning Snap, but if you are not familiar with concepts and effects of the
State monad, things can become funny sometimes. I personally noticed quickly
that a 'rough' understanding of monads is not enough and found myself crawling
through tutorials and articles about them while initially wanted to learn
something about Snap. If you run in the same problems, one of the best
collection of learning resources about Haskell on the net is currently the
(closed?) [StackOverflow
resource](http://stackoverflow.com/questions/1012573/getting-started-with-haskell),
but also the [WikiBook about Haskell](http://en.wikibooks.org/wiki/Haskell) is
very well written. If you still have problem with Haskell's type class system
(Functors, Applicative Functors, Monads, Monoids, Arrows, etc.) I can highly
recommend the [Typclassopedia
article](http://www.haskell.org/haskellwiki/Typeclassopedia).


Let's begin!
------------

Okay, but now let's finally start with the actual content. I think we all
learn most effectively by doing and playing. :)

As mentioned at the beginning the tutorial will be structured in separate
chapters, which can be read consecutively. But as they are not depending each
other it is also possible to jump between them or just to pick the one that
looks most interesting to you. The tutorial is structured as follows:

1. [First steps](https://github.com/J-Hannes/snap-tutorial/blob/master/chapter1.md) -
   how a Snap application can be created

2. [Basic infrastructure](https://github.com/J-Hannes/snap-tutorial/blob/master/chapter2.md) -
   how a simple Snap application looks like

3. [Routing and static serving](https://github.com/J-Hannes/snap-tutorial/blob/master/chapter3.md) -
   how Snap serves (static) web pages

4. Heist - use the full power of dynamic templating

5. Snaplets - modularize your application

6. Bootstrap - use external CSS / JS libraries in you app

7. Digestive Functors - create forms a la category theory

8. Authentication - use session and authentication functionality

9. Extended infrastructure - how to MVC you application

10. Persistence - some examples that show the usage of databases

That should be it and might be extended / modified over the time to achieve
best learning results to new readers.

Last but not least feel free to contribute to this tutorial. Complain about
missing parts or such that are not easy to understand. Just modify the code
here yourself or send a mail to me or the [Snap mailing
list](http://groups.google.com/group/snap_framework) or complain in the [snap
IRC channel](http://webchat.freenode.net/?channels=snapframework&uio=d4) on
the freenode server.

Have fun!
