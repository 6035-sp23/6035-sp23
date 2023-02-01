# Grading Environment

The grading environment is used to build and run your submissions.

## Software configuration

The grading server is running Ubuntu 22.04, with the following software:
- JDK: openjdk 17.0.5
- Scala: 2.11.12
- Go: 1.19.5
- Ant: 1.10.7
- Python: 3.10.6
- bash: 5.0.17

Please make sure your submission is compatible with these versions, and that all other dependencies are self-contained in the project. If you need a dependency not listed where which is not feasible to package with your project, please contact the course staff.

## Hardware configuration

The grading server is an 8-core Intel Xeon E5-2630 machine with 16GB RAM.

# Autograding

When you push to the `phaseN-submission` branch (with `N` replaced by the phase 1 through 5; `git push origin phaseN-submission`), the autograder will download the latest code you pushed, build your compiler, run test cases, and report the results in a comment on the last commit push. Your grade will be determined by the highest scoring submission you make before the deadline.

The autograder is shared (round-robin) between all students, and we expect that it will be busy around the deadline. You should validate that your submission works on the autograder well before the deadline.
