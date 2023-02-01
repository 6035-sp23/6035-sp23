# Setting up a programming environment

You will need an x86-64 Unix environment to run the class tools and ensure that we can build your compiler on the grading server.

If you're not already on a Unix environment (e.g., Linux, MacOS, WSL, MinGW), you can [set up a virtual machine](vm.md). Alternatively, you can use [the Athena environment](https://ist.mit.edu/athena).[^1]

Since you'll be doing a lot of coding in your chosen environment, it's worth investing effort into customizing it to be comfortable and productive for you. This might include installing your favorite text editor, tweaking your VM settings, or figuring out how to make your favorite IDE work with the class tools. A common solution is to develop on your local machine and run the compiler on the Unix environment (synchronyzing code with a [shared folder](https://docs.vmware.com/en/VMware-Workstation-Pro/17/com.vmware.ws.using.doc/GUID-D6D9A5FD-7F5F-4C95-AFAB-EDE9335F5562.html), `scp`, `rsync`, `sshfs`, or git).

A note: when developing across multiple environments, it is very easy to lose your code (including overwriting local git history). **Push your code early and often.** Take advantage of git branches to develop code without breaking your partners' builds.

Please see the [Grading Environment handout](../materials/handouts/grading.md) for details on the grading environment.

## ARM Environments

If you have an ARM environment, you will likely not be able to install an x86-64 Linux VM with VMware/VirtualBox. If you are using a recent (M1/M2) Mac, [Rosetta 2](https://support.apple.com/en-us/HT211861) should allow you to run x86-64 programs. If you are using another ARM environment without the ability to emulate x86-64 programs, you can develop on Athena. In either case, you may be able to use QEMU or equivalent to run an x86-64 Linux.

It is your responsibility to ensure that your compiler is entirely compatible with the x86 grading environment -- you can test this on Athena. If you are having issues, please contact the TAs.

## Ubuntu
Subsequent instructions assume that you're on a default Ubuntu installation. If you're completely new to Linux, read [Using the Ubuntu Terminal](cmd.md). You will need to use the terminal at least to run the test scripts.

We will be using Git to distribute test scripts and handle code submission. You should also use Git to collaborate with your teammates. If you're not familiar with basic Git usage like resolving merge conflicts, read [Using Git](git.md). That also includes instructions for setting up Git.

Finally, set up the environment for your chosen language. If you're using Java or Scala, install the JDK and Apache Ant:

```
sudo apt install -y openjdk-17-jdk ant
```

If you're using Scala, also install Scala:

```
sudo apt install -y scala
```

Make sure the environment variable `SCALA_HOME` is set to "/usr/share/scala", and that `scala -version` reports that you have Scala 2.11.

If you're using Go, follow [the installation instructions on Go's website](https://golang.org/doc/install).

## MacOS
If you are on Mac, the equivalent commands would look like this:

```
brew install --cask adoptopenjdk17
```
If you run into trouble because you have multiple openjdk versions installed, see this [article](https://medium.com/@devkosal/switching-java-jdk-versions-on-macos-80bc868e686a) about switching between the different versions of java on MacOS.

```
brew install ant
```

```
brew install scala@2.11
```
Make sure the environment variable `SCALA_HOME` is set to "/usr/local/opt/scala@2.11"

**Important note:** Ant support has been removed from the latest version of Scala. Make sure that you're using at most Scala 2.11. If you'd like to use the latest Scala, feel free to update the build scripts to support it. With your permission, we might even be able to use them in later class offerings!

If you're using Go, follow [the installation instructions on Go's website](https://golang.org/doc/install).

[^1]: While the class was traditionally run on Athena, we recommend against using Athena this semester. The dialup can be slow and isn't suited for computationally intensive work like optimizing programs.
