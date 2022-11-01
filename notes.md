# Notes to pytest Quick Start Guide

# Chapter 1. Introducing pytest

- Testing programs manually is natural; writing automated tests is not.
- A test suite ensure that new functionality is working, that a bug has been squashed forever, and that fixing a bug or introducing a new feature does not break another part of the system.
- A test suite is code that tests your code.
    - Create one or more necessary resources
    - Call the application code under test
    - Assert that the results are as expected
    - Run the tests continuously, such as every hour or every commit, by using an automated system such as Jenkins
- Adding tests for a piece of code means that from now on it will be tested again and again as features are added and bugs are fixed.
- Having a well-written and in-depth test suite will allow you to make changes, big or small, with confidence.

## Why pytest?

- It is a mature and full-featured testing framework, from small tests to large-scale functional tests for applications and librairies alike.
- It is simple to get started with.

        # filename test_fibo.py
        from fibo import fibonacci

        def test_fibo():
            assert fibonacci(4) == 3

        pytest test_fibo.py -q

- You use plain assert statements to write  your checks, with detailed reporting.
- It has automatic test discovery.
- It has fixtures to manage test resources.
- It has plug-ins to expand its built-in capabilities and test frameworks and applications.

# Chapter 2. Writing and running tests

## Writing and running tests

- Determine the installed version of pytest.

        pytest --version

- There is no need to create classes; just write simple functions and plain `assert` statements.

        def test_abc():
            ...

        def test_def():
            ...
## Running tests

- You can start by executing the `pytest` command.

        pytest

- This will find all of the `test_*.py` and `_test.py` modules in the current directory and below and will run all of the tests found in those files.
- You can reduce the search to specific directories (my preference):

        cd tests  # a directory within datasense/
        pytest

- You can execute a specific test file.

        pytest test_abc.py

- You can execute a specific test within a specific file.

        pytest test_abc.py::test_one

- There are many other possibilities. The above two will be my choices.
- pytest will show a more verbose output with the `-v` flag.

        pytest -v

- pytest will show which tests exist, without running them, using the `--collect-only` flag.

        pytest --collect-only

## Powerful asserts

- `pytest` makes use of the built-in `assert` statement to check assumptions during testing. You do not need to remember various `self.assert*` or `self.expect*` functions.
- pytest shows the line of the failure, as well as the variables and expressions involved in the failure, and provides specialized explanations of failures involving other data types.

## Test separate from your code

- I have organized my tests in a separate directory from the main package.

        datasense/
            datasense/
                control_charts.py
                graphs.py
                html.py
                __init__.py
                msa.py
                munging.py
                pyxl.py
                sequel.py
                stats.py
            tests/
                test_control_charts.py
                test_graphs.py
                test_html.py
                test_msa.py
                test_munging.py
                test_pyxl.py
                test_sequel.py
                test_stats.py
            setup.py

- It keeps library code and testing code separate.
- The testing code is not included in the source package.

## Usefull command-line options

- Keyword expressions

        " runs def test*() that contain "file" in the `item id`, that is, in the def test*() name
        pytest -v -k "file"
        " provides a summary of the N longest running tets, or zero to see all tests
        pytest --durations=N

# Chapter 3. Markers and parametrization

- Marks allow us to selectively run tests based on applied and built-in marks, and to attache general data to test functions
- Test parametrization allows us to easily apply the same test function to a set of input values. This avoids duplicating test code and makes it easy to add new test cases that may appear as our code evolves.

## Mark basics

- pytest allows you to mark functions and classes with metadata.
- These metadata can be used to selectively run tests and are also available for figures and plugins, to perform different tasks.

    from pytest import mark
    @mark.timeout(10, method="thread")  # the test should take < 10 s

- Then from the command line:

        pytest -m timeout  # run all tests with the timeout mark

- Marks can be applied to classes. This will apply that same mark to all tests methods in that class, avoiding having to copy and paste the mark code over all test methods. All subclasses will inherit the mark.

# Chapter 4. Fixtures

# Chapter 5. Plugins

# Chapter 6. Converting unittest suites to pytest

# Chapter 7. Wrapping up
