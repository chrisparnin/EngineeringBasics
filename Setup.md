[Setup](Setup.md#setup) | [Shells](Shells.md#shells) |  [Git](Git.md#git) | [Markdown and IDEs](MarkdownEditors.md#markdown) |  [Virtual Environments](Environments.md#environments) | [Task Management](OnlineTools.md#online-tools)

# Setup

To successfully build software, you need a properly configured environment with a variety of tools. To help us get started, we will we install some tools, package managers, that make it a little easier to configure systems. 

Whether you're a Mac, Windows, or Linux user---you should be able to find a way to be productive with the tools from this workshop. However, there may be specific tweaks, issues, and accomodatations you may have to make based on your platform.

## An installation philosophy

> *Avoid manual installation, automate with package managers!*

When possible, using a package manager can allow you to automate and streamline the installation of tools. Instead of hunting down the right website, finding the right version and dowload link, then clicking through an installation wizard---you let the package manager take care of all those manual steps for you! 

Tip: Later on, the ability to automate the installation of software environments becomes important in later stages of software development, such as continuous integration, or deployment.

### Package Managers

*Package managers* are tools for installing libraries and tools, which help manage dependencies and configuration of files and environment variables. 

There are generally two flavors of package managers. *Binary* package managers typically install platform specific dependencies, whereas, *source* package managers typically install libraries you can use in your code.

* **Binary**: brew, choco, apt-get  
* **Source**: npm, pip, maven

### Installing Package Managers

If you're using Linux, you typically already have `yum` or `apt-get`. You can skip this step.

##### Installing HomeBrew on Mac OS X

Homebrew is a popular package manager for MacOS. To install, open a terminal window and run the install command shown on [http://brew.sh/](http://brew.sh/).

Here is an example of how to install the utility `wget`.
```bash
brew install wget
```

##### Installing Chocolatey on Windows

Chocolatey is a package manager for Windows. 

Follow the instructions on the [Chocolatey website](https://chocolatey.org/install) to install. 
Once Chocolatey is installed, you can use it to install other tools on your system using `choco install <package-name>`.  Look for the package name on the Chocolatey website.

Here are some example commands
```
choco install wget
```

## Practice: Installing useful software

See if you can find the packages for these tools with your package manager and install them.

* git
* Java 1.8 (JDK 8)
* nodejs
* python2

Tip: If you install Git on Windows, make sure to add git util bins to your PATH. This provide will access to many GNU commands in Windows.

## Optional: Make Windows Just as Awesome

If you have **Windows 10**, you can use the [Windows Subsystem for Linux](https://docs.microsoft.com/en-us/windows/wsl/about)!  Follow the [Windows 10 Installation Guide](https://docs.microsoft.com/en-us/windows/wsl/install-win10).

You can also get many of the same commands available in your windows shell environment by installing git and ensuring they exist on your path.

* Update your System Environment Variables Path to include: `C:\Program Files\Git\usr\bin`. 
* Restart your shell and many unix commands will work in windows too!

You can install even more unix utilities:
* Install gnuwin basic utils for windows: `choco install gnuwin32-coreutils.install`
* Update your System Environment Variables Path: `C:\Program Files (x86)\GnuWin32\bin`

![Windows-EnvironmentVariables](resources/imgs/win-env.jpg)
