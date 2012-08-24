Chapter 1 - First steps with Snap
=================================

This chapter can be kept very short, thanks to precise documentation and tools
provided on the Snap homepage [22].

Firstly the installation is quite easy and can be done with two command as
they can be found on the Download page of the framework [23]:

    $ cabal update
    $ cabal install snap

The installation can take some time depending on how much dependency packages
you already installed previously.

After all packages have been downloaded and installed successfully it is
probably most desired to try Snap straight away, maybe with some small test
applications.

Therefore Snap offers so called scaffolding tools that automatically create a
minimalistic but runnable application. Snap comes with three different
applications that can be created in such a way.

    $ snap init barebones
    
This command creates a minimal runnable example application consisting of
about 20 lines of code. The quickstart quide [24] provides more information
about that variant. If you wish just create a custom folder for a test
application, run that command and have a looks at the created files and
finally run the project either after a cabal installation or simply with
'runhaskell src/Main' if you don't want to install anything for now. You
browser should show a simple 'hello world' response when you request the
'localhost:8000' URL. It might also be helpful to read the Snap API
introduction [25] that explains the created application a bit more in detail.

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
chapters.


Where to go from here?
----------------------

...


References
----------

[22] http://snapframework.com/

[23] http://snapframework.com/download

[24] http://snapframework.com/docs/quickstart

[25] http://snapframework.com/docs/tutorials/snap-api

[26] http://snapframework.com/docs/tutorials/snaplets-tutorial
