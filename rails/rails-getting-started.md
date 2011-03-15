Rails Getting Started Guide
===========================


This guide was developed for setting up a complete Ruby on Rails development
environment on Mac OS 10.6

##0) First things first##

Make sure your system is completely up-to-date by running Software Update.

Also, it wouldn't hurt to have a backup of your system at the ready, just in case.
(but you are such a good programmer you already have a recent backup, else shame 
on you)

Lastly, you'll want to know that this guide takes about X-X hours to complete.
It varies on how much you already have installed on your system, the speed of
your processor, and your familiarity with the command line.


##1) Install Xcode

The first install you'll need to complete is the Mac developer tools. These
tools include important compilers and libraries that will enable you to install
everything else you'll need.

You can get Xcode from two places:

1. On your Snow Leopard install disc.
2. From http://developer.apple.com.
   You'll need a free Apple developer account to download Xcode.


##2) Install Homebrew

[Homebrew][] Is the missing package manager for OS X. It allows you to install
  some of the necessary packages.
  
<aside class="caution">
  If you already have MacPorts or Fink installed on your machine, you should be
  careful of installing Homebrew too. Either uninstall those package managers &
  use Homebrew or replace any `brew install` command with their install command.
</aside>
  
  Run this command in your terminal:

    ruby -e "$(curl -fsSL https://gist.github.com/raw/323731/install_homebrew.rb)"

You will need to authenticate with your password.

[Homebrew]: http://mxcl.github.com/homebrew/

##3) Install Git

[Git][] is a fantastic version control system. Its also required to install RVM.

    sudo brew install git
    git config --global user.name "Your Name"
    git config --global user.email "youremail@example.com"
    
[Git]: http://git-scm.org

##4) Install RVM

[RVM][] is a command line tool which allows us to easily install, manage and work
with multiple ruby environments from interpreters to sets of gems.

    bash < <( curl http://rvm.beginrescueend.com/releases/rvm-install-head )
    
At the end of the install you'll get some instructions. The most important of
which is to add this line to the end of your `.bash_profile`

    [[ -s "$HOME/.rvm/scripts/rvm" ]] && source "$HOME/.rvm/scripts/rvm"

And then close that terminal window and open a new one to reload the settings.

[RVM]: http://rvm.beginrescueend.com

##5) Install Ruby

    rvm install 1.9.2
    rvm 1.9.2 --default

##6) Install Database server

You need to have at least one type of database server installed. You can install
more than one if you prefer.

###6a) Install PostgreSQL

    brew install postgres

###6b) Install MySQL

    brew install mysql

###6c) Install SQLite3

    brew install sqlite3

##7) Disable gem docs (Optional)

Installing gems can be slow. We can speed it up by telling it not to build the 
documentation for each gem. We don't need to build them locally because they are
already built and hosted on the excellent [Rdoc.info](http://rdoc.info] site.

Create a file `~/.gemrc` and add this to it:

    gem: --no-ri --no-rdoc
    
<aside class="notice">
  If you frequently work offline, you might want these docs to be generated for
  the gems you install. You can see them by running `gem server`
</aside>

##8) Install some global gems

You are pretty much guaranteed to use this gem when creating a rails 3 app.
Its a good idea to install it now.

    rvm 1.9.2@global
    gem install rails

##9) Create a Rails project (the right way)

This is how I setup a new rails project. Its highly opinionated, but is pretty
standard.

You will want to replace all instances of `project_name` with your 
project's name... obviously.

Lets start by creating a rails app.

    rails new project_name
    cd project_name

You will want to create a gemset that will hold all of the dependencies for
your project. This ensures that between two projects you will never have version
or dependency conflicts. This is a good thing! 
    
    rvm --create --rvmrc 1.9.2@project_name

This command will create a gemset and a .rvmrc file. An .rvmrc file just tells 
the rvm to switch to this version of ruby and this gemset every time you `cd`
into this directory. Pretty convenient.

Then you'll want to bundle:

    bundle
    
If you are using git, now would be a good time to initialize the repo.

    git init
    git add .
    git commit -m "Initial commit"





