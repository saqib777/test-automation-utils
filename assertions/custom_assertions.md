```
CUSTOM ASSERTIONS — AUTOMATION UTILITIES LIBRARY (CODE)

def assert_equal(actual, expected, message=None):
    """
    Asserts that two values are equal.
    """
    if actual != expected:
        default_message = (
            f"Assertion failed: expected '{expected}', but got '{actual}'"
        )
        raise AssertionError(message or default_message)


def assert_not_equal(actual, expected, message=None):
    """
    Asserts that two values are not equal.
    """
    if actual == expected:
        default_message = (
            f"Assertion failed: value '{actual}' was not expected"
        )
        raise AssertionError(message or default_message)


def assert_true(condition, message=None):
    """
    Asserts that a condition is True.
    """
    if not condition:
        default_message = "Assertion failed: condition evaluated to False"
        raise AssertionError(message or default_message)


def assert_false(condition, message=None):
    """
    Asserts that a condition is False.
    """
    if condition:
        default_message = "Assertion failed: condition evaluated to True"
        raise AssertionError(message or default_message)


def assert_not_empty(collection, message=None):
    """
    Asserts that a collection is not empty.
    """
    if not collection:
        default_message = "Assertion failed: collection is empty"
        raise AssertionError(message or default_message)


def assert_contains(container, item, message=None):
    """
    Asserts that an item exists inside a container.
    """
    if item not in container:
        default_message = (
            f"Assertion failed: '{item}' not found in '{container}'"
        )
        raise AssertionError(message or default_message)

```
