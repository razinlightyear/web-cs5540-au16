---
layout: base/bar-sidebar-none
title: Development Guide

working_directory: web-cse5540-au16
---

# Building a Jekyll Site

This site is implemented in Jekyll, thus requiring Ruby and Node.js. We also use Python in our automation and testing.

Please remember not to attempt to integrate your project site with our build process.
It will be much simpler to submit a static set of pages that can be served from your assigned directory.
You may nevertheless find it helpful to build our site as part of confirming that your file integrate correctly.

## Installing Node.js, Python, Ruby, and Ruby DevKit

We currently use:

- [Node.js 5.1.0 - https://nodejs.org/dist/v5.1.0/node-v5.1.0-x64.msi](https://nodejs.org/dist/v5.1.0/node-v5.1.0-x64.msi)

  When installing Node.js, the default options are appropriate.

- [Python 3.5.0 - https://www.python.org/ftp/python/3.5.0/python-3.5.0.exe](https://www.python.org/ftp/python/3.5.0/python-3.5.0.exe)

  When installing Python:

  - Choose 'Customize Installation'
  - On 'Optional Features':

    Check 'pip' and 'for all users (requires elevation)'.

    Uncheck 'Documentation', 'tcl/tk and IDLE', 'Python test suite', 'py launcher'.

  - On 'Advanced Options':
 
    Uncheck all options.
  
    Set the installation path to `c:\Python35`.

- [Ruby 2.2.3 - https://dl.bintray.com/oneclick/rubyinstaller/rubyinstaller-2.2.3.exe](https://dl.bintray.com/oneclick/rubyinstaller/rubyinstaller-2.2.3.exe)

  When installing Ruby:

  - On 'Installation Destination and Optional Tasks':
 
    Set the installation path to `c:\Ruby223`.
  
    Check 'Add Ruby executables to your PATH'.

- [Ruby DevKit - https://dl.bintray.com/oneclick/rubyinstaller/DevKit-mingw64-32-4.7.2-20130224-1151-sfx.exe](https://dl.bintray.com/oneclick/rubyinstaller/DevKit-mingw64-32-4.7.2-20130224-1151-sfx.exe)

  When installing the Ruby DevKit:

  - Extract to `c:\RubyDevKit`.

  - Install the DevKit into our Ruby installation:
  
    ~~~
    cd c:\RubyDevKit
    ruby dk.rb init
    ruby dk.rb install
    ~~~

## Creating a Virtual Environment and Installing Dependencies

All Python work should be done within a virtual environment, to avoid dependency conflicts.
Node.js and Ruby have their own dependency management (i.e., npm shrinkwrap and bundler).
Our Python automation scripts will employ those tools, but we first need to configure Python.

Create the virtual environment. From the working directory of our project (e.g., `c:\devel\{{ page.working_directory }}\`):

    c:\Python35\python.exe -m venv env35    

This will create a directory for the virtual environment (e.g., `c:\devel\{{ page.working_directory }}\env35\`).

Next activate that virtual environment and install our Python dependencies: 

    env35\Scripts\activate.bat
    pip install -r requirements3.txt

Next use Python's invoke automation to get the rest of our dependencies:

    invoke update_dependencies

## Building and Serving the Site

Invoke automation is provided for building the site.  

If it is not already active, you need to re-activate the virtual environment.
From the working directory of our project (e.g., `c:\devel\{{ page.working_directory }}\`):

    env35\Scripts\activate.bat

To build the site:
    
    invoke build_test

To build and serve the site on `localhost:4000`, continuously updating based on changes:

    invoke serve_test

## Submitting Changes via Pull Request

This course website lives on GitHub:

<https://github.com/utah-cs5540-au16/web-cs5540-au16> 

We recommend the GitHub Desktop client:

<https://desktop.github.com/>

You can submit pull requests, and should be certain you submit them via feature branches:

<https://guides.github.com/introduction/flow/>

<https://www.atlassian.com/git/tutorials/comparing-workflows>

<https://spring.io/blog/2010/12/21/social-coding-in-spring-projects>

<http://codeinthehole.com/writing/pull-requests-and-other-good-practices-for-teams-using-github/>
