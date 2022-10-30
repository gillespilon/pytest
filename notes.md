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

# Chapter 3. Markers and parametrization

# Chapter 4. Fixtures

# Chapter 5. Plugins

# Chapter 6. Converting unittest suites to pytest

# Chapter 7. Wrapping up
