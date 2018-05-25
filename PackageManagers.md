[Shells](Shells.md#shells) | [Development Environments](PackageManagers.md#development-environments) |  [Git](Git.md#git) | [Virtural Environments](Environments.md#environments) | [Markdown and Editors](MarkdownEditors.md#markdown) | [Programming Languages](Programming.md#programming) | [Task Management](OnlineTools.md#online-tools) | [Specialized Tools](SpecializedTools.md#specialized-tools) 

# Development Environments

To successfully develop and do data analysis, you need a properly configured environment To help us get started, we will we install some tools, package managers, that make it a little easier to configure systems.  Additionally, we will install two integrated development environments (IDEs) that include libraries and other resources to support development.

The advantage of having package managers is that it makes it easier to install large bundles of software, often automatically. These allows others to easily build software without worrying about missing a dependency.

## Package Managers

Package managers are tools for installing libraries and tools, which help manage dependencies and configuration of files and environment variables. 

There are generally two flavors of package managers. *Binary* package managers typically install platform specific dependencies, whereas, *source* package managers typically install libraries you can use in your code.

**Binary**: brew, choco, apt-get  
**Source**: npm, pip, maven

## Installing a Binary Package Manager

If you're using linux, you typically already have `yum` or `apt-get`. You can skip this step. Otherwise, for Windows and Mac OS X, let's install some tools.

### Installing Chocolatey on Windows

Chocolatey is a package manager for Windows. 

Follow the instructions on the Chocolatey website to install. https://chocolatey.org/install](https://chocolatey.org/install)

Once Chocolatey is installed, you can use it to install other tools on your system using `choco install <package-name>`.  Look for the package name on the Chocolatey website.

Here are some example commands
```
# Install core Linux utilities
choco install gnuwin32-coreutils.install
# Install wget
choco install wget
```

### Installing HomeBrew on Mac OS X

Open a terminal window and run the install command shown on [http://brew.sh/](http://brew.sh/).

Let's install some useful tools:

```bash
# Add a new distribution source ("science"). 
brew tap homebrew/science
```

## Practice 1: Install Basic Development Environments

We will install a basic node.js, Java, and python development environment. Let's practice our package management skills learned above.

Install the following using brew/choco/apt-get/yum:

* Node
* Python (version 3) (The Python package manager `pip` should install with Python.  Windows users should install Python directly from the Python website: https://www.python.org/downloads/.)
* Java 1.8 (JDK)
* Maven

You may have to search the web to find the right package names!

After you install these, you may need to make sure that they are on your path.  Test running a version command for each.

## C/C++ Development

On Mac OS, this is a nice way to setup many c/c++ compilers and linkers, and build tools such as make.

```
xcode-select --install
```

For Windows, installing [Visual Studio 2017, Community](https://www.visualstudio.com/vs/community/), will actually make it easier to get a similar set of tools installed on your system. Alternatively, for a lighter weight way, install the [Visual C++ Build Tools](http://landinghub.visualstudio.com/visual-cpp-build-tools) and the [Managed Apps Build Tools](https://www.microsoft.com/en-us/download/details.aspx?id=48159).

## Java Development

Install the latest version of [Eclipse](http://www.eclipse.org/). Install the version for **Java Development**.

https://eclipse.org/downloads/

## Practice 2: Testing your build environment

Let's put your development environment to the test. See if you can build the following project. It requires python, node, and c++ to be properly installed on a system.

```bash
git clone https://github.com/alt-code/TaskLights
cd TaskLights/src
npm install
```
