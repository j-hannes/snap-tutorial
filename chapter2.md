Chapter 2 - Basic infrastructure
================================

*Todo: Modify section and explain how to use the snap-examples. As a
minimalistic application scaffold is not available via the snap init command
we have to do a workaround in cloning the 'new' application from the
[snap-examples](https://github.com/J-Hannes/snap-examples) and copying the
source code and modify the cabal file.*

One important thing for me when I was beginning with Snap was to get an idea
how such an application will look like, how things are organized to work
together nicely. Therefore we will start right off with creating our own Snap
application. We actually will do that in every chapter from now, but each time
we will produce an application with a different functionality in the main
focus while we will gradually increase the amount of functionalities that are
involved in each of our application.

In this chapter we only will invoke an initial application skeleton by the
scaffolding tool, have a look at what has been produced there and clean it up
a bit in the end to have a clean and empty project where further applications
are built on.

One more suggestion before we start. As we will produce quite a few
applications during the next chapters you might want to create a specific
folder for them and place the project of each chapter in an own sub folder to
keep things clean and tidy.


Creating our first Snap application
-----------------------------------

Okay, let's start right here. The first thing we need to do is to create a
folder for our first application in our snap tutorial folder, for example

    $ mkdir /home/j-hannes/sites/snaptutorial/chapter1
    $ cd /home/j-hannes/sites/snaptutorial/chapter1

and then run the command to initialize the scaffolds for our first
application.

    $ snap init

The project folder structure should now look like this:

    .
    ├── chapter1.cabal
    ├── log
    │   ├── access.log
    │   └── error.log
    ├── snaplets
    │   └── heist
    │       └── templates
    │           ├── base.tpl
    │           ├── index.tpl
    │           ├── _login.tpl
    │           ├── login.tpl
    │           ├── _new_user.tpl
    │           ├── new_user.tpl
    │           └── userform.tpl
    ├── src
    │   ├── Application.hs
    │   ├── Main.hs
    │   └── Site.hs
    └── static
        └── screen.css

So far so good, now let's go through step by step, what we have produced here:


### chapter1.cabal

This is the file for building and packaging our application. This provides us
two commands which will build our application in two different ways.

    $ cabal install

After building our application via this command, the whole application is
compiled into the executables. The compilation of the whole application
results in a very fast application (means very fast server response time) but
also has the following effects:

* changes that are done in any Haskell source file (.hs) will require a new
  compilation of the application via 'cabal install'

* changes that are done in any Heist template file (we will dive into Heist
  soon) can be recompiled while the application is running, but require a
  request of /admin/reload, see also
  [here](http://snapframework.com/docs/tutorials/snaplets-tutorial#site-reloading)
  for more information

It should be easy to see that this way of building the executable is hence
suitable for production environments, means once our application will be
published on a server we can run it compiled to benefit of the awesome speed
of compiled web applications. (Note that PHP and Ruby for example are
interpreted and thus much much slower.)

But the disadvantage of this method is that we would need to restart and
rebuild our application after each change while we are developing it which
would slow down our developing drastically. For this reason a second command
exists to build our application. So now type

    $ cabal install -fdevelopment

This command compiles the 'Main.hs' file only and uses dynamic recompilation
for the rest of the application source files. That is much slower than the
previous method but now we can leave our application running and every
modification of any source file is automatically taken into account means we
can leave our application running in the background while we develop our
application.


### log

This folder contains two different log files:

* 'access.log' logs all requests that are made to our application
* 'error.log' logs notices and errors that are produced while the application
  is running


### snaplets

The *snaplets* folder contains all Snaplet specific files. For the beginning it
will probably only be important to hold the Heist template files that are
required by our application. Later we might find configuration files and other
files up to complete application file trees in there or finally create files
for our own Snaplets.

### src

This is the core of our application and contains all Haskell source files. For
now we find the following three files in there:

* `Main.hs` the application entry point where the configuration gets loaded and
  the server is started. This file might never been modified, at least not in
  the very beginning. Be aware that changes on this file require a server
  restart even when the application is built in development mode.

* `Site.hs` is the base of our application. Here the application really gets
  initialized and run as well as routes are defined. For small applications
  like the existing it is probably the easiest way to place our handler and
  helper functions right in that file, but later as the application grows it
  is more or less necessary to structure the file system and create separate
  modules for our controller and models. It might be a good idea to follow the
  Model-View-Controller pattern (or as you wish also PAC) to structure our
  modules later on. We will see in further chapters how that works.

* `Application.hs` is the module for our main application Snaplet. What exactly
  this means will be discussed soon in the Snaplets chapter.

You may have noticed that there has another folder been created after our
cabal install, a 'dist/' folder. This folder will contain the compiled
executables of our application.


Using versioning tools
----------------------

In case you want to use a versioning tool now or later on to keep track of you
changes and also as backup tool, the use of [Git](http://git-scm.com/) might
be a good idea and now the right time to initialize your repository. Therefore
create a .gitignore file with the following content

    dist
    .ghci
    *.swp
    *.swo

And place another .gitignore file in the log folder that contains

    *
    !.gitignore

The last two only in case you use Vim as text editor. You might want to add
some more files later on like the session key file, local database files etc.
Once this is done you can initialize your repository via

    git init
    git add .
    git commit -a -m "Initialize project skeleton"

or a similar initial commit message. Versioning is generally a good idea, even
of smaller project because you get used to the work flow of commits and making
small changes only and you also have a nice log of the work you have done plus
a backup of every development step of your application.


Cleaning up the initial application
-----------------------------------

The current state of the project already contains some example code to give
new developers the idea how things work together. This is in general a very
nice feature but as we will explain individual feature here step by step we
don't need that code and thus we can remove it for now.

We begin with cleaning up the `src/Application.hs`. For it is just necessary
to know that this module contains a snaplet which represents the state of our
application and provides access functions for this. Snaplets will be explained
later in chapter X, for now imagine them as modules that provide a certain
functionality and may contain further snaplets. The application snaplet that
has been initialized with the default scaffolding contains three
'subsnaplets': Heist, a session manager and an authentication manager. We will
always need Heist in our upcoming chapters, so we can leave it there, the
others can be removed for now. You can also remove the according imports, so
the final `src/Application.hs` will look like:

```haskell
{-# LANGUAGE TemplateHaskell #-}

-----------------------------------------------------------------------------
-- | This module defines our application's state type and an alias for its
-- handler monad.
module Application where
    
------------------------------------------------------------------------------
import Data.Lens.Template
import Snap.Snaplet
import Snap.Snaplet.Heist

------------------------------------------------------------------------------
data App = App
    { _heist :: Snaplet (Heist App) 
    }

makeLens ''App
    
instance HasHeist App where
    heistLens = subSnaplet heist
    
    
------------------------------------------------------------------------------
type AppHandler = Handler App App
```

As next we can clean up the `src/Site.hs` and remove the example code from it.
This means all the functions with a *handler* suffix can be removed. The
initialization of the session and authentication snaplet must be removed as
well as the according part in the application snaplet has been removed
previously. Finally the imports of modules can be cleaned up as well, so the
result will look like this:

```haskell
{-#LANGUAGE OverloadedStrings #-}

------------------------------------------------------------------------------
-- | This module is where all the routes and handlers are defined for your
-- site. The 'app' function is the initializer that combines everything
-- together and is exported by this module.
module Site
  ( app
  ) where

------------------------------------------------------------------------------
import           Data.ByteString (ByteString)
import           Snap.Snaplet
import           Snap.Snaplet.Heist
import           Snap.Util.FileServe
------------------------------------------------------------------------------
import           Application

    
------------------------------------------------------------------------------
-- | The application's routes.
routes :: [(ByteString, Handler App App ())]
routes = [ ("", serveDirectory "static")
        ]


------------------------------------------------------------------------------
-- | The application initializer.
app :: SnapletInit App App
app = makeSnaplet "app" "A snaplet example application." Nothing $ do
    h <- nestSnaplet "" heist $ heistInit "templates"
    addRoutes routes
    return $ App h
```

As last step we can remove the now redundant heist templates via

    rm snaplets/heist/templates/*    

but we need to provide a template for now which can be served from the root
url of our application. So we create a file in
`snaplets/heist/templates/index.tpl` and fill it with some content, for
example

    initial application scaffold
 
or something like that. We also can remove the predefined css file for now via

    rm static/screen.css

Now the project is cleaned up form the example code and ready to be used as
basis for upcoming applications. You may want to the current files into
another folder which will not be modified or alternatively you can simply
repeat the steps we did just now on a new initialized default project.


Summary
-------

During this chapter we got an overview about the file structure of a fresh
Snap application. We also learned about the two different building types for
production and for development environments. In the end we cleaned up the
example code to prepare it as base for upcoming applications.

In the next chapter we will have a first look 'inside' the Haskell code of our
application and will have a look at the routing mechanism and how static pages
are served.

---
[Next chapter: Routing and static serving](https://github.com/J-Hannes/snap-tutorial/blob/master/chapter3.md)
