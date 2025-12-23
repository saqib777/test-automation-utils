
```

SCREENSHOT HELPER — AUTOMATION UTILITIES LIBRARY (CODE)

import os
from datetime import datetime


def take_screenshot(driver, name="screenshot", base_dir="screenshots"):
    """
    Takes a screenshot and saves it with a timestamp.

    Parameters:
    driver    : Selenium WebDriver instance
    name      : Base name for the screenshot file
    base_dir  : Directory where screenshots will be stored

    Returns:
    Full path of the saved screenshot
    """
    if not os.path.exists(base_dir):
        os.makedirs(base_dir)

    timestamp = datetime.now().strftime("%Y%m%d_%H%M%S")
    file_name = f"{name}_{timestamp}.png"
    file_path = os.path.join(base_dir, file_name)

    driver.save_screenshot(file_path)
    return file_path


def take_screenshot_on_failure(driver, test_name):
    """
    Convenience method for capturing screenshots during failures.

    Parameters:
    driver     : Selenium WebDriver instance
    test_name  : Name of the failing test

    Returns:
    Full path of the saved screenshot
    """
    return take_screenshot(driver, name=f"FAIL_{test_name}")


```
