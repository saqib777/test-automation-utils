
RETRY LOGIC — AUTOMATION UTILITIES LIBRARY (CODE)

import time


def retry(operation, retries=3, delay=2, retry_exceptions=(Exception,)):
    """
    Retries a given operation if it raises a specified exception.

    Parameters:
    operation          : A callable (function or lambda) to execute
    retries            : Number of retry attempts
    delay              : Delay in seconds between retries
    retry_exceptions   : Tuple of exception types that trigger a retry

    Returns:
    Result of the operation if successful

    Raises:
    The last encountered exception after all retries fail
    """
    last_exception = None

    for attempt in range(1, retries + 1):
        try:
            return operation()
        except retry_exceptions as exception:
            last_exception = exception
            print(
                f"Retry attempt {attempt} failed with error: {exception}"
            )

            if attempt < retries:
                time.sleep(delay)

    raise last_exception


def retry_with_condition(operation, condition, retries=3, delay=2):
    """
    Retries an operation until a condition is satisfied.

    Parameters:
    operation : A callable that returns a result
    condition : A callable that evaluates the result
    retries   : Number of retry attempts
    delay     : Delay in seconds between retries

    Returns:
    Result that satisfies the condition

    Raises:
    Exception if condition is not met after all retries
    """
    for attempt in range(1, retries + 1):
        result = operation()

        if condition(result):
            return result

        print(
            f"Condition not met on attempt {attempt}. Retrying..."
        )

        if attempt < retries:
            time.sleep(delay)

    raise Exception("Condition not met after maximum retry attempts")
