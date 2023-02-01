# Testing your Compiler


## Cloning the public test suite

The test infrastructure is managed as a separate Git project. To clone the tests, run the following in the root of your repo:

```
git clone git@github.com:6035-sp23/public-tests.git tests
```

This will download the tests into the `tests` directory, which should already be `gitignore`'d  in the provided skeleton code.

Make sure that your environment is set up correctly by running the parser tests: `./tests/test.py parser`. Note that you need `gcc` installed to run the test script. You can install it with the following command:

```
sudo apt install -y build-essential
```

You will need to run `git pull` in the `tests` directory at the start of each phase as more tests are released throughout the semester.

## Running tests

The test infrastructure comes with a file `test.py` to help you (and the grading server) run tests easily.

Run `./tests/test.py -h` (from your project root) to see what arguments you can pass in. Here are some examples:

- `./tests/test.py scanner -l` lists the scanner tests.
- `./tests/test.py scanner -j4` runs all scanner tests using four threads.
- `./tests/test.py scanner -f id*` runs all scanner tests starting with `id`.
- `./tests/test.py scanner -f id1 -v` runs the `id1` scanner test, but also prints everything to console, including the input, compiler output and stderr, and expected output.

Note that `-v` without `-d` only prints your compiler output after it has finished running, so nothing will show if your compiler enters an infinite loop. For real-time output, you should include the `-d` flag (which also passes `--debug` into your compiler).

Most of the other flags are only used in phase 3 and onwards. We will release more information about them when they become relevant.

## Writing your own tests

## Why

The public test cases only test a small fraction of the expected behavior of the compiler; the private test cases used for grading test a much larger fraction. To pass the private test cases, you will likely have to write new test cases of your own.

Further, compiler bugs tend to be complex and idiosyncratic, and bugs in early phases of the project will compound in the later phases: even if the private tests do not catch errors, you will want to ensure broad coverage.

## What

As general guidance, good tests should cover both breadth and depth of the spec, and should include both common cases and edge cases. It is generally good practice to include at least one small test case per correct behavior that you expect and at least one small test case per incorrect behavior (testing as little as possible outside of that single behavior). It is also generally good practice to include large test cases that test a large amount of correct behavior.

Note: you may not include tests anyone else has written (from other groups or found online, though things like Decaf implementations of common programs are fine). Your test cases are considered part of your compiler.

 Below we discuss more advanced techniques for testing your compiler.

### Randomized testing

Another common strategy is to randomly generate programs and test that your compiler has the expected behavior on these randomly generated programs. This is often used in conjunction with the differential testing and test case reduction techniques listed below.

### Differential testing

[*Differential testing*](https://en.wikipedia.org/wiki/Differential_testing) is a common approach to testing compilers which assumes access to two different compilers of the same language, and compares their output on a given input. In later stages of the project, you may be able to use `gcc` to perform differential testing on your compiler.

### Test case reduction

*Test case reduction* is a general testing technique in which for a failing test case, you chop away pieces until you find the smallest failing test derived from the original test case. A popular implementation of this for C is [C-Reduce](https://embed.cs.utah.edu/creduce/), which you may be able to emulate (e.g., via randomly deleting lines) or implement for Decaf programs.

### More!

There are all sorts of other strategies for testing compilers, including idempotency checks (e.g., having your compiler parse a program, output that representation in Decaf, parse the output representation, and checking that they're the same), parallel implementation checks (e.g., implementing an interpreter for Decaf programs within your compiler such that you can test that the behavior of generated code matches the interpreted behavior of code), and more. Feel free to use any of these strategies or to come up with your own!

## How

The easiest way to write your own test cases is to copy `tests` to a new directory `our-tests`, track this in your git repository, then run it with `./our-tests/test.py`. Other options include using tools like [git-subrepo](https://github.com/ingydotnet/git-subrepo) to track the `tests` directory within your project while still being able to pull upstream pushes.
