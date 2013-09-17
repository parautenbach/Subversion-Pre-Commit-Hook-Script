Subversion pre-commit Hook Script
=================================

A general purpose pre-commit server-side hook script for Subversion (SVN) intended to keep your repository clean, organised and consistent. This is a shell script and will work on *nix-based systems. Although this script was created with Subversion in mind, it can be adapted to work with git, mercurial or other VCSs. 

A script like this can never be fool proof. It rather attempts to prevent obvious mistakes and should be customised according to your needs.

The need for many of the features of this script becomes redundant if you have an automated build environment and use a proper, modern IDE.

# Features
* Prevent empty commit log messages.
* Ensure that all paths up to trunk, tags and branches are lowercase (assuming a C-style naming convention).
* Check that a software copyright notice has been included in all source code files, excluding auto generated code.
* Prevent temporary project files from being committed.
* Prevent binary files created by the project from being committed to a trunk or branch. Such files generate noise unless you're making a release and should be stored in an artifact repository in case of a release.
* Prevent dependencies (such as libraries or tools) from being committed to a trunk or branch. When this script was originally created, package managers weren't the norm and hence a cheap imitation using `svn:externals` properties were used to pull dependencies during checkout into a lib directory. A second check that works in conjunction with this is to check that the lib directory is empty. 
* Ensure that tags have a proper version number. The assumption here is that a 4 part version number and release indicator gets used (e.g. 1.0.0.0-final). This can be customised in many ways. As a second check, it will also abort if any `svn:externals` properties contain references to dependencies that are not final releases. 

Please fork to taste! 

# See also
* [Subversion Repository Hook Reference - pre-commit hook](http://svnbook.red-bean.com/en/1.8/svn.ref.reposhooks.pre-commit.html)
* [Customizing Git - Git Hooks](http://git-scm.com/book/en/Customizing-Git-Git-Hooks)
* [Mercurial: The Definitive Guide - Handling repository events with hooks](http://hgbook.red-bean.com/read/handling-repository-events-with-hooks.html)


