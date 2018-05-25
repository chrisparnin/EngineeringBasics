[Shells](Shells.md#shells) | [Development Environments](PackageManagers.md#development-environments) |  [Git](Git.md#git) | [Virtural Environments](Environments.md#environments) | [Markdown and Editors](MarkdownEditors.md#markdown) | [Programming Languages](Programming.md#programming) | [Task Management](OnlineTools.md#online-tools) | [Specialized Tools](SpecializedTools.md#specialized-tools) 

# Specialized Tools

Data analysis requires additional tools beyond those for development and scripting.  To prepare for the rest of Bootcamp, install the following tools:

## MySQL

MySQL is a database system.  Storing data in a database for querying can be useful for data analysis.  You can automate data analysis by writing a program to do the work for you.

Install [MySQL Community Server](https://dev.mysql.com/downloads/mysql/).  If you are running Windows, use the MySQL Installer.  Ensure that you install the MySQL Workbench too.  If you are running another OS, install the [MySQL Workbench]. 

More detailed [MySQL install instructions for CSC326](https://pages.github.ncsu.edu/engr-csc326-staff/326-course-page/install/#phase-4-mysql) are available [requires NCSU login id].

### Installing from the Command Line

Run the following on the appropriate shell for your OS.

**Mac**

```bash
brew install mysql
# enable services and start local server
brew tap homebrew/services
brew services start mysql
# Install workbench
brew tap caskroom/cask
brew install brew-cask
brew cask install mysqlworkbench
```

**Windows** (you may need to run your shell in Administrator mode)

```bash
# install mysql
choco install mysql

# Or, Use my custom mysql installer :)
git clone https://github.com/CSC-326/AutoInstall
cd AutoInstall/choco/mysql/
choco install .\mysql.nuspec -y

choco install mysql.workbench -y
```

## R & RStudio

[R](https://www.r-project.org/) is a program for statistical computing.  [RStudio](https://www.rstudio.com/) is a development environment for R.  

Follow [these directions](https://www.ics.uci.edu/~jutts/110/InstallingRandRStudio.pdf) to install R and RStudio.