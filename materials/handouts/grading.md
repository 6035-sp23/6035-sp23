# Grading Environment

The grading environment is used to build and run your submissions.

## Software configuration

The grading server is running Ubuntu 22.04, with the following software:
- JDK: openjdk 17.0.5
- Scala: 2.11.12
- Scala: 3.2.2 (with binaries `scala3`, `scala3-compiler`)
- sbt: 1.8.2
- Go: 1.19.5
- Ant: 1.10.7
- Rust: 1.6.7
  - rustc 1.67.1
  - cargo 1.67.1
  - rustup 1.25.2
- gcc/g++:  11.3.0
- Bison: 3.8.2
- flex: 2.6.4
- Python: 3.10.6
- bash: 5.0.17

Please make sure your submission is compatible with these versions, and that all other dependencies are self-contained in the project. If you need a dependency not listed where which is not feasible to package with your project, please contact the course staff.

The grading server does not have network access when running tests. Ensure that `./build.sh` downloads all necessary dependencies, and that `./run.sh` does not require internet access (e.g., `cargo run` will not work in `./run.sh`).

## Hardware configuration

The grading server appears as an 2-core Intel Xeon E5-2630 machine with 4GB RAM.

# Autograding

When you push to the `phaseN-submission` branch (with `N` replaced by the phase 1 through 5; `git push origin phaseN-submission`), the autograder will download the latest code you pushed, build your compiler, run test cases, and report the results in a comment on the last commit push. Your grade will be determined by the highest scoring submission you make before the deadline.

The autograder is shared (round-robin) between all students, and we expect that it will be busy around the deadline. You should validate that your submission works on the autograder well before the deadline.

**DO NOT FORCE PUSH TO THE phaseN-submission BRANCH.** In the case that there is an issue with the grading server, we will re-run pushes that were previously graded. Force pushing will remove these commits. Broadly, it is considered a violation of academic integrity to tamper with the git history. If there is a technical reason that you must force push, please contact the TAs.

# Changes to private test cases

- 2/12/23 3:00PM: fixed a bug in one private scanner test
