[Shells](Shells.md#shells) | [Development Environments](PackageManagers.md#development-environments) |  [Git](Git.md#git) | [Virtural Environments](Environments.md#environments) | [Markdown and Editors](MarkdownEditors.md#markdown) | [Programming Languages](Programming.md#programming) | [Task Management](OnlineTools.md#online-tools) | [Specialized Tools](SpecializedTools.md#specialized-tools) 

# Computing Environments

Creating computing and development environments will be an essential skill for software engineering. Unfortunately, consistently getting software installed on a your computer and correctly setting up the environments can take away weeks of your productive time.

Virtual machines/containers can provide a useful solution for automating the creation and management of your computing environment and development workflow. Unfortunately, when developers think about virtual machines, a common idea that comes to mind is a dedicated heavy-weight virtualized system with a full graphics Desktop. Alternatively, you may think of dual-booted systems. While these types of systems can be useful, the goal of this workshop is to introduce you to a different concept for software development.

## A philosophy: Be able to throw away your machine and still code

> Code that only runs on your machine is useful to no one else

With computing environments, we are able to automate the specification of our our environment for running our code, which makes it easier for us to recreate and share our computing environments with others on a new machine.

To use a computing environment, you can use your host operating system to write code, interact with the running program, and visualize its executions. But you avoid execution code on your own machine itself---that all happens inside the computing environment.

> Computing environments are for running code, not writing code.

To accomplish this, we use a set of tools to enable you to map files and program between your host environment and computing environment. 

## Creating a Virtual Machine

[VirtualBox](https://www.virtualbox.org/wiki/Downloads) is a lightweight virtualization provider. It is very effective for creating *headless* virtual machines that run without any GUI/Desktop interface.

Install VirtualBox.

Windows: If you're running Hyper-V and VirtualBox, and you're experiencing crashes when you try to start a VM, you may need to [turn off Hyper-V](https://superuser.com/questions/540055/convenient-way-to-enable-disable-hyper-v-in-windows-8) (which exclusively locks use of CPU for virtualization).

#### Manual creation

While it is possible to use the VirtualBox GUI to manually install a virtual machine (and run through the OS installation script); this is not an effective automation approach!

#### Baker

With [Baker](https://getbaker.io), you can create a virtual machine with a simple configuration file.

For example, we could create a new `baker.yml` file, with the following contents:

```
name: baker-example
vm:
  memory: "1024"
```

By running `baker bake`, you can create this virtual machine in VirtualBox and interact with it through it `baker ssh`. Your current directly on your computer will be accessible inside the virtual machine through a shared folder. This allows you to edit/code directly on your computer while still being able to run commands/services in a Baker environment.

## Using Baker

Cool. But how do I get tools or programming languages installed in a Baker environment? _Bakelets_ are modules that can be added to a baker environment. There are many modules available, and you can even add your own custom modules.

Here is an example Baker environment with the python bakelet.

``` yml
name: baker-example
vm:
  memory: "1024"
lang:
  - python2
```

But can we do more?

## Baker Commands

Imagine your project is using a tool, such as mkdocs, to manage your documentation for your site. You want a way to easy run commands in the Baker environment without having to directly ssh into the environment. With Baker *commands*, you can add a set of actions that can be performed inside the Baker environment. By default, baker commands will run with the shared project folder as the current working directory.

``` yml
name: baker-docs
vm: 
  ip: 192.168.22.30
lang:
  - python2
commands:
  build: mkdocs build
  serve: mkdocs serve -a 0.0.0.0:8000
  gh-deploy: mkdocs gh-deploy
```

For example, by running `baker run serve`, you will be able to local edit and preview your live documentation site by visiting 192.168.22.30:8000 in your browser.

Note: Baker is beta software, an alternative (but more difficult) tool to consider is [vagrant](https://www.vagrantup.com/).

## Optional: Creating environment for CoffeeMaker

Clone this repository:
https://github.com/ottomatica/baker-examples/

CoffeeMaker is a simple web-based Java application that serves up coffee ingredients and receipes. Inside the directory `baker/examples/headless-chrome-selenium/` there is a lightweight version of the program, called "CoffeeMaker-Lite". In this version of CoffeeMaker, the DB and other functionality has been removed in order to keep this application simple.

This codebase has several requirements: It needs Java 1.8 JDK installed, maven, and a headless version of chrome running. A set of selenium tests will use the ChromeDriver to verify the _limited_ functionality of the web app.

### Baker environment

The following baker.yml sets up Java 8, maven, and Google Chrome automatically.

``` yaml
name: headless-selenium
vm:
  ip: 192.168.9.11
lang:
  - java8
tools:
  - maven
packages:
  - apt:
    - google-chrome-stable:
        deb: https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
commands:
  unit-test: cd CoffeeMaker-Lite/; mvn test
  web-test: cd Selenium-Tests/; mvn test
  serve: cd CoffeeMaker-Lite/; mvn spring-boot:run
```

### Try it out

Create the vm.

``` bash
baker bake
```

Start up the web app.

``` bash
baker run serve
```

Visiting the site at http://192.168.9.11:8080, will allow you to interact with the web app.

Now, run the selenium tests, which will use chrome.

``` bash
baker run web-test
```

You should see the following results.

```
Results :

Tests run: 2, Failures: 0, Errors: 0, Skipped: 0

[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time: 6.512 s
[INFO] Finished at: 2018-08-11T00:32:30+00:00
[INFO] Final Memory: 13M/32M
[INFO] ------------------------------------------------------------------------
```

