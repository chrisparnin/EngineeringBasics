[Setup](Setup.md#setup) | [Shells](Shells.md#shells) |  [Git](Git.md#git) | [Markdown and IDEs](MarkdownEditors.md#markdown) |  [Virtual Environments](Environments.md#environments) | [Task Management](OnlineTools.md#online-tools)

# Computing Environments

Creating computing and development environments will be an essential skill for software engineering. Unfortunately, consistently getting software installed on a your computer and correctly setting up the environments can take away weeks of your productive time.

Virtual machines/containers can provide a useful solution for automating the creation and management of your computing environment and development workflow. Unfortunately, when developers think about virtual machines, a common idea that comes to mind is a dedicated heavy-weight virtualized system with a full graphics Desktop. Alternatively, you may think of dual-booted systems. While these types of systems can be useful, the goal of this workshop is to introduce you to a different concept for software development.

## A philosophy: Be able to throw away your machine and still code

> Code that only runs on your machine is useful to no one else

With computing environments, we are able to automate the specification of our environment for running our code, which makes it easier for us to recreate and share our computing environments with others on a new machine.

To use a computing environment, you can use your host operating system to write code, interact with the running program, and visualize its executions. But you avoid execution code on your own machine itself---that all happens inside the computing environment.

> Computing environments are for running code, not writing code.

To accomplish this, we use a set of tools to enable you to map files and program between your host environment and computing environment. 

## Creating a Virtual Machine

[VirtualBox](https://www.virtualbox.org/wiki/Downloads) is a lightweight virtualization provider. It is very effective for creating *headless* virtual machines that run without any GUI/Desktop interface.

Install VirtualBox.

> Windows: If you're running Hyper-V and VirtualBox, and you're experiencing crashes when you try to start a VM, you may need to [turn off Hyper-V](https://superuser.com/questions/540055/convenient-way-to-enable-disable-hyper-v-in-windows-8) (which exclusively locks use of CPU for virtualization).

> Linux: If you run `vboxmanage list vms` command and you get `WARNING: The vboxdrv kernel module is not loaded...` error, see the dicussion [here](https://askubuntu.com/a/229908) for how to fix it.

### Ensure virtualization is enabled

To be able to run virtual machines, your machine needs to support virtualization. 
Ensure virtualization (Intel VT-x or AMD-V) is enabled on your system using the instructions for your operating system:  
- **Windows:** open Task Manager and go to Performance tab, and you should see virtualization is enabled.
  <img src="resources/imgs/win-taskmanager.jpg" data-canonical-src="resources/imgs/win-taskmanager.jpg" width="600" />

- **Mac:** run the command below to see the list of supported CPU flags. If you see **VMX**, your machine supports hardware virtualization:  
   ```
   sysctl -a | grep machdep.cpu.features | grep VMX
   ```
   <img src="resources/imgs/mac-cpu-flags.png" data-canonical-src="resources/imgs/mac-cpu-flags.png" width="600" />
   
- **Linux:** run the command below to see the list of supported CPU flags. If you see **VMX** or **SVM** flag, youre machine supports hardware virtualization:
   ```
   grep -E "vmx|svm" /proc/cpuinfo
   ```
   <img src="resources/imgs/linux-cpu-flags.png" data-canonical-src="resources/imgs/linux-cpu-flags.png" width="600" />

#### Manual creation

While it is possible to use the VirtualBox GUI to manually install a virtual machine (and run through the OS installation script); this is not an effective automation approach!

#### Baker

With [Baker](https://getbaker.io), you can create a virtual machine with a simple configuration file.

For example, we could create a new `baker.yml` file, with the following contents:

```
name: baker-example
vm:
  memory: 1024
  ip: 192.168.20.40
```

By running `baker bake`, you can create this virtual machine in VirtualBox and interact with it through it `baker ssh`. Your current directory on your computer will be accessible inside the virtual machine through a shared folder. This allows you to edit/code directly on your computer while still being able to run commands/services in a Baker environment.

## Using Baker

Cool. But how do I get tools or programming languages installed in a Baker environment? _Bakelets_ are modules that can be added to a baker environment. There are many modules available, and you can even add your own custom modules.

Here is an example Baker environment with the python bakelet.

``` yml
name: baker-example
vm:
  memory: 1024
  ip: 192.168.20.40
lang:
  - python2
```

But can we do more? Yes! See the [baker-examples](https://github.com/ottomatica/baker-examples#baker-examples) repo.
