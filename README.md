Concept of a new Snap tutorial
==============================

Note: This chapter is a first attempt to write the introduction and will
probably be modified a bit if this tutorial get's published.

What is this?
-------------

A tutorial to learn how to write high level web applications with the
Haskell [1] web framework Snap [2].

The tutorial will start from the very beginning, assuming that the reader has
never heard of the Snap framework before, and demonstrate by simple examples
how to use Snap for writing web applications. Therefore the tutorial is
divided into multiple parts (chapters). Each chapter tries to contain just one
new feature to learn, to keep single chapters as simple as possible and also
to leave them independent from each other. Nothing is worse than already
knowing the basics and wanting to learn a new feature xy from chapter 5 and
finding out it continues with the example demonstrated in chapter 2 (hello
Real World Haskell). Here the chapters are tried to be usable independently.


Why do we need this?
--------------------

The nice thing of the Snap framework is, that it already comes with A LOT of
good documentation. First of all you can find very comprehensive articles on
the framework's homepage itself [3,4,5,6].

Secondly the Snap API which can be found on Hackage [7] is very well
documented, sometimes even readable like a tutorial [8].

Thirdly the open source code of the framework itself can be found on Github
[9] does not only contain good documentation in the code itself but also
contains some more tutorials and tests that are a good source to learn from.

And last but not least, there exist plenty of blog entries of the developers
of the framework, like mightybyte [10], jaspervdj [11], norm2782 [12] and many
others which are forgotten here. Not mentioned even quite a few Snap projects
found on Github, among other one of my humble self [13].

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


Oh snap - why Snap?
-------------------

Haskell web development really started off around 2 years ago from now I would
suppose. As Haskell is the worlds most powerful programming language, it's
problem is to find applications where Haskell is really good for and where all
it's purity, laziness and high level really shines. Web development seem to
be a field where a lot of advantages of Haskell can be applied.

Now, it is no secret that there exists not one, but three (plus many many
others) Haskell web frameworks that are currently developed and well
supported: The two others out there are Yesod [14], a very well developed web
framework of mainly Michael Snoyman, Greg Weber and others and Happstack [15],
a cool framework which developed from the older HappS framework. Yesod,
Happstack and Snap have all advantages and disadvantages if compared to each
other. There already exist multiple discussions [16,17] of which one might be
better than the other, but the bottom line is that you can choose for yourself
which one fit's best to your own preferences. It is important to mention that
each of the frameworks can be seen as a collection of libraries that could
even be used independently from each other, which means you are not restricted
to use Yesod OR Happstack OR Snap but you can use libraries of all of the
together if you like.

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
plenty of good learning resources. W3schools [18] might be a good place to
start with. JavaScript can of course be integrated as front end language for
Snap applications (while Haskell is the back end language) to spice things up,
but is not necessary.

The second thing that is more or less necessary to develop Snap web
applications is fundamental of Haskell. Basics (Haskell type system, higher
order functions, modules etc. etc.) are a must but ideally you have already
reached the intermediate level, means you know about type classes, applicative
functors, monads, monad transformers etc. we will need all that stuff later
on. Of course it is even possible to learn those things via learning Snap, but
if you are not familiar with concepts and effects of the State monad, things
can become funny sometimes. I personally noticed quickly that a 'rough'
understanding of monads is not enough and found myself crawling through
tutorials and articles about them while initially wanted to learn something
about Snap. If you run in the same problems, one of the best collection of
learning resources about Haskell on the net is currently the (closed?)
StackOverflow resource [19], but also the WikiBook page about Haskell [20] is
very well written. If you still have problem with Haskell's type class system
(Functor, Applicative Functors, Monads, Monoids, Arrows, ...) I can strongly
recommend the Typclassopedia article [21].


Let's begin!
------------

Okay, but now let's finally start with the actual content. I think we all
learn most effectively by doing and playing. :)

As mentioned at the beginning the tutorial will be structured in separate
chapters, which can be read consecutively. But as they are not depending each
other it is also possible to jump between them or just to pick the one that
looks interesting. The structure of the tutorial looks as follows:

1. [First steps with Snap](https://github.com/J-Hannes/snap-tutorial/blob/master/chapter1.md) - Write, build and deploy a Snap web application.

2. [Application infrastructure](chapter2.md) - Where to place model, view and
controller 

3. [How things work together](chapter3.md) - Introduction of Heist and Splices

4. Snaplets - Modularize your application.

5. Bootstrap - Use external CSS / JS libraries in you app.

6. Digestive Functors - Create forms a la category theory.

7. Authentication - Use session and authentication functionality.

8. Persistence - Some examples that show the usage of databases.

That should be it and might be extended / modified over the time to achieve
best learning results to new readers.

Last but not least feel free to contribute to this tutorial. Complain about
missing parts or such that are not easy to understand. I try my best to always
stay at the bottom and keep things as simple as possible (after all I see
myself as beginner in Haskell and Snap as well) but as I studied computing
myself I might tend to lift off a bit here and there. Just pull me back to the
bottom wherever you see that, ALL FEEDBACK IS VERY WELCOME! :) Just create a
pull request or send a mail to me or the Snap mailing list or complain at #snapframework on the freenode server.

Happy learning!


References
----------

[1] http://haskell.org

[2] http://snapframework.com

[3] http://snapframework.com/docs/quickstart

[4] http://snapframework.com/docs/tutorials/snap-api

[5] http://snapframework.com/docs/tutorials/heist

[6] http://snapframework.com/docs/tutorials/snaplets-tutorial

[7] http://hackage.haskell.org/package/snap

[8] http://hackage.haskell.org/packages/archive/snap/0.9.1.1/doc/html/Snap-Snaplet.html

[9] https://github.com/snapframework/snap

[10] http://softwaresimply.blogspot.co.uk

[11] http://jaspervdj.be

[12] http://norm2782.github.com

[13] https://github.com/J-Hannes/digestive-functors-snap-auth-example

[14] http://yesodweb.com

[15] http://happstack.com

[16] http://stackoverflow.com/questions/5645168/comparing-haskells-snap-and-yesod-web-frameworks

[17] http://softwaresimply.blogspot.co.uk/2012/04/hopefully-fair-and-useful-comparison-of.html

[18] http://www.w3schools.com

[19] http://stackoverflow.com/questions/1012573/getting-started-with-haskell

[20] http://en.wikibooks.org/wiki/Haskell

[21] http://www.haskell.org/haskellwiki/Typeclassopedia
