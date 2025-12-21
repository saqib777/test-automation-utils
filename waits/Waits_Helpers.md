```
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
from selenium.common.exceptions import TimeoutException

DEFAULT_TIMEOUT = 10


def wait_for_element_present(driver, locator, timeout=DEFAULT_TIMEOUT):
    """
    Waits until the element is present in the DOM.
    This does not guarantee that the element is visible.
    """
    try:
        return WebDriverWait(driver, timeout).until(
            EC.presence_of_element_located(locator)
        )
    except TimeoutException:
        raise TimeoutException(
            f"Element with locator {locator} was not present after {timeout} seconds"
        )


def wait_for_element_visible(driver, locator, timeout=DEFAULT_TIMEOUT):
    """
    Waits until the element is present and visible on the screen.
    """
    try:
        return WebDriverWait(driver, timeout).until(
            EC.visibility_of_element_located(locator)
        )
    except TimeoutException:
        raise TimeoutException(
            f"Element with locator {locator} was not visible after {timeout} seconds"
        )


def wait_for_element_clickable(driver, locator, timeout=DEFAULT_TIMEOUT):
    """
    Waits until the element is clickable.
    """
    try:
        return WebDriverWait(driver, timeout).until(
            EC.element_to_be_clickable(locator)
        )
    except TimeoutException:
        raise TimeoutException(
            f"Element with locator {locator} was not clickable after {timeout} seconds"
        )


def wait_for_text_to_be_present(driver, locator, text, timeout=DEFAULT_TIMEOUT):
    """
    Waits until specific text appears inside an element.
    """
    try:
        return WebDriverWait(driver, timeout).until(
            EC.text_to_be_present_in_element(locator, text)
        )
    except TimeoutException:
        raise TimeoutException(
            f'Text "{text}" was not present in element {locator} after {timeout} seconds'
        )


def wait_for_url_contains(driver, partial_url, timeout=DEFAULT_TIMEOUT):
    """
    Waits until the current URL contains the given partial value.
    Useful for navigation validation.
    """
    try:
        return WebDriverWait(driver, timeout).until(
            EC.url_contains(partial_url)
        )
    except TimeoutException:
        raise TimeoutException(
            f'URL did not contain "{partial_url}" after {timeout} seconds'
        )

```
