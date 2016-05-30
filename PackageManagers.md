[Shells](https://github.com/REU-SOS/EngineeringBasics/blob/master/Shells.md#shells) | [Package Managers](https://github.com/REU-SOS/EngineeringBasics/blob/master/PackageManagers.md#configuration-management) |  [Git](https://github.com/REU-SOS/EngineeringBasics/blob/master/Git.md#git) | [Markdown and Editors](https://github.com/REU-SOS/EngineeringBasics/blob/master/MarkdownEditors.md#markdown) | [Programming with Python/Node](https://github.com/REU-SOS/EngineeringBasics/blob/master/Programming.md#programming) | [Task Management](https://github.com/REU-SOS/EngineeringBasics/blob/master/OnlineTools.md#online-tools)

# Configuration Management

To help us get started, we will we install some tools that make it a little easier to configure systems.

The advantage of having these tools is that it makes it easier to install large bundles of software, often automatically. These allows others to easily build software without worrying about missing a dependency.

### Package Managers

Package managers are tools for installing libraries and tools, which help manage dependencies and configuration of files and environment variables. 

There are generally two flavors of package managers. *Binary* package managers typically install platform specific dependencies, whereas, *source* package managers typically install libraries you can use in your code.

**Binary**: brew, choco, apt-get  
**Source**: npm, pip, maven

### Installing a Binary Package Manager

If you're using linux, you typically already have `yum` or `apt-get`. You can skip this step. Otherwise, for Windows and Mac OS X, let's install some tools.

#### Installing Chocolatey on Windows

Open a cmd line window run as Administrator and run install command shown on [https://chocolatey.org/install](https://chocolatey.org/install).

Let's install some useful tools:
```
# A source code repository tool
choco install git
# Install R statistical language
choco install r.project
```

#### Installing HomeBrew on Mac OS X

Open a terminal window and run the install command shown on [http://brew.sh/](http://brew.sh/).

Let's install some useful tools:

```bash
# A source code repository tool
brew install git
# Add a new distribution source ("science"). 
brew tap homebrew/science
# Install R statistical language
brew install R
```

## Practice 1: Install Basic Development Environments

We will install a basic node.js, Java, and python development environment. Let's practice our package management skills learned above.

Install the following using brew/choco:

* Node
* Python (version 2)
* Pip
* Java 1.8 (JDK)
* Maven

You may have to search the web to find the right package names!

### Some other things...

On Mac OS, this is a nice way to setup many c/c++ compilers and linkers, and build tools such as make.

```
xcode-select --install
```

For Windows, installing [Visual Studio 2015, Community](https://www.visualstudio.com/en-us/products/visual-studio-community-vs.aspx), will actually make it easier to get a similiar set of tools installed on your system.

Finally, you probably want to have the latest version of Eclipse if you haven't already.  There is a nice auto-installer you can use (see banner on top of page).

https://eclipse.org/downloads/

## Practice 2: Testing your build environment

Let's put your development environment to the test. See if you can build the following project. It requires python, node, and c++ to be properly installed on a system.

```bash
git clone https://github.com/alt-code/TaskLights
cd TaskLights/src
npm install
```
