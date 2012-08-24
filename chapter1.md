Chapter 1 - First steps with Snap
=================================

This chapter can be kept very short, thanks to precise documentation on the
Snap homepage [22] and tools that already come with the framework itself.

The installation of the framework is quite easy and can be done with two
command as they can be found on the download page [23] of the framework:

    $ cabal update
    $ cabal install snap

The installation can take some time depending on how much dependency packages
you already installed previously.

After all packages have been downloaded and installed successfully you are 
probably most curious to try Snap straight away, maybe with some small test
applications.

For that Snap offers a scaffolding tool that automatically creates minimal
complete applications. Snap comes with three different applications that can
be created in such a way.

    $ snap init barebones
    
This command creates a minimal runnable example application consisting of
about 20 lines of code. The quickstart quide [24] provides more information
about that variant. If you wish just create a custom folder for a test
application, run that command and have a looks at the created files and
finally run the project either after a cabal installation or simply with
'runhaskell src/Main' if you don't want to install anything for now. You
browser should show a simple 'hello world' response when you request the
'localhost:8000' URL. It might also be helpful to read the Snap API
introduction [25] which explains the created application a bit more in detail.

    $ snap init tutorial

That command creates a minimalistic application that already makes basic use
of so called 'Snaplets' which will be explained later in chapter X. The main
file is written in literate Haskell (.lhs) and is covered by the documentation
page about Snaplets [26] which you don't need to read for now, we will come
back to that (quite important) topic later, no worries.

    $ snap init

The last command creates scaffolds of a standard Snap web application. This
command will certainly used most often for initializing a new Snap
application. It already contains some more code than necessary but it also
shows quite a few technologies working together which will be covered in later
chapters. If you can't wait you could install the created scaffolds via
'cabal install <youprojectname>' and then run it via './<youprojectname>' and
be amazed at what is already possible with less than 65 lines of code. But we
will cover those things later anyway so you don't need to do that for now.


Where to go from here?
----------------------

After we already went the first steps with Snap and (hopefully) everything
worked fine we will continue with the next chapter where we will create the
basis for all further chapters before we explain different techniques that
work together with the framework in more detail.

If you ran into any problems while following the instructions here or in the
referred documentation don't hesitate to ask in the IRC channel or in
the snap mailing list where you will probably receive help very quick. You can
find the contact information on the about page [27] of the framework.


References
----------

[22] http://snapframework.com/

[23] http://snapframework.com/download

[24] http://snapframework.com/docs/quickstart

[25] http://snapframework.com/docs/tutorials/snap-api

[26] http://snapframework.com/docs/tutorials/snaplets-tutorial

[27] http://snapframework.com/about
