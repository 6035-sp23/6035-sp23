# Setting up the class tools

Choose a language and its corresponding skeleton repo. Though the choice of language is up to you and your group, we encourage you to default to Java:

- [Java](https://github.com/6035-sp23/java-skeleton)
- [Scala](https://github.com/6035-sp23/scala-skeleton)
- [Go](https://github.com/6035-sp23/go-skeleton)
- Get in touch with the TAs if you want to use Haskell or any other language.

Create and navigate to a directory where you'd like your project files to be stored (`~/Documents/6.035-compiler-phase1` or `~/Desktop/6.035-compiler-phase1` is a good choice) and run the following commands.

```bash
git init

git remote add skeleton git@github.com:6035-sp23/<LANGUAGE>-skeleton.git
git pull skeleton main

git remote add origin git@github.com:6035-sp23/<YOUR KERB>.git
git push -u origin main
```

This should initialize your phase 1 project directory with the skeleton code for your chosen language. If you get `Permission denied (publickey)`, make sure you have set up an SSH key with GitHub (see the [Git handout](git.md)).

Make sure that your environment is set up correctly by running `./build.sh` and `./run.sh`. You should also check out the [documentation on testing your compiler](testing.md).

While you are encouraged to use this infrastructure, you may also choose to modify it however you like, or even ignore it and design your own infrastructure from scratch. If you choose to do so, you will still need to replicate all command line options and the functionality required for the scripts that build and execute the compiler, as detailed in the [project specification][project info].

# Provided infrastructure

## Java/Scala

The Java and Scala skeletons rely on Apache Ant for build automation. Ant is configured by the `build.xml` file, which we mainly use to recursively select Java files for compilation. You are encouraged to read and understand the provided `build.xml`.

The Java skeleton has the following structure:

```
.
|-- build.sh
|-- run.sh
|-- build.xml
`-- src
    `-- edu
        `-- mit
            `-- compilers
                |-- Main.java
                `-- grammar
                    |-- parser.cup
                    |-- scanner.flex
                `-- tools
                    |-- CLI.java
    `-- decaf
        `-- Parallel
            |-- Analyze.java
```

The program entry point is located in `Main.java`. `CLI.java` implements the command-line interface described in the [project specification][project info]; you can modify it to add new command-line flags as needed. There are some dummy parser and scanner defined in the `grammar` folder (which get compiled into Java classes in the `autogen` folder once you build). `Analyze.java` will only be used in phase 5; more information about it will be provided when phase 5 is released.

The Scala skeleton is similar, but with the source files in different locations. Specifically, `CLI.java` is located in `src/util/`, dummy parser files are located in `edu/mit/compilers/parser/`, and the equivalent of `Main.java` is `src/compile/Compiler.scala`. Also, we have included a sample unit test for convenience in the `unittests` directory, which may be run with `ant test`.

## Go

The files that you will actually be creating and modifying live in `workspace/compiler`. In the source file directory, `main.go` contains the program entry point, and `cli.go` implements the command-line interface described in the [project specification][project info]. Feel free to modify `cli.go` to add more command-line flags as needed. `grammar` contains dummy files related to scanning and parsing: `ast.go`, `golex.go`, `parser.go`, `parser.y`. When you run `./build.sh`, `parser.y` will be compiled to a file `y.go`.

# Running your compiler

All skeleton projects come with a `build.sh` and `run.sh` in the project root. Use these to build and run your compiler respectively. They will also be used for grading, so if you make any changes to the build or run process, make sure to modify these files to reflect them. In general, these two files are the only restriction we impose on the structure of your projects. If you decide to change the repository structure, or even use a langiage for which we have no template, you just need to modify `build.sh` and `run.sh` to correctly build and run your system.

Arguments passed to `run.sh` are passed straight to your compiler. Read the [project specification][project info] for more information about the command-line arguments that your compiler should accept.

[project info]: project-overview.pdf
