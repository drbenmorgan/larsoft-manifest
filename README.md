larsoft-manifest
================

Manage LArSoft repositories using [Google Repo](http://code.google.com/p/git-repo/) manifests.

The FNAL LArSoft software is distributed as a set of modules divided
between several git repositories. This is a test project to demonstrate
checkout of these using Google's repo tool.

Getting Started
===============
First of all you need Git and Python installed. Google Repo itself comes
as a program which you install somewhere convenient, then run in an
empty working directory.

To get Google Repo, do

``` shell
$ curl http://commondatastorage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
$ chmod u+x ~/bin/repo
```

You can use any directory you like to install repo into if `~/bin` isn't
convenient for you.

Now create an *empty* directory where you'll create a repo setup and
clones of the larsoft repositories, for example:

``` shell
$ mkdir ~/larsoft-work
$ cd ~/larsoft-work
$ ~/bin/repo init -u https://github.com/drbenmorgan/larsoft-manifest.git
...
$ ~/bin/repo sync
... this may take some time ...
Fetching projects: 100% (9/9), done.
Checking out files: 100% (224/224), done.ut files:  33% (75/224)
Checking out files: 100% (245/245), done.ut files:  32% (80/245)
Checking out files: 100% (261/261), done.ut files:  42% (111/261)
Checking out files: 100% (241/241), done.ut files:  42% (102/241)
Syncing work tree: 100% (9/9), done.

$
```

You should now have copies of each of the LArSoft repositories in your
working directory:

``` shell
$ ls -a
.   larana   lardata          larevt       larpandora  larsim
..  larcore  lareventdisplay  larexamples  larreco     .repo
$
```

Each directory is a clone of the upstream repo, but are checked out
in a "headless" state. To start following(?) the master branch (not
exactly following git-flow, but I haven't investigated further), do

``` shell
$ ~/bin/repo start master --all
Starting master: 100% (9/9), done.
$
```

Each repository can now be worked on as normal, but how these would fit
in to standard workflows need further study. There's also no combined
build script yet.


