
```

LOGGING HELPER — AUTOMATION UTILITIES LIBRARY (CODE)

import logging
import os


def get_logger(name="automation_logger", log_level=logging.INFO, log_dir="logs"):
    """
    Creates and returns a configured logger instance.

    Parameters:
    name       : Name of the logger
    log_level  : Logging level (INFO, WARNING, ERROR)
    log_dir    : Directory where log files will be stored

    Returns:
    Configured logger instance
    """
    if not os.path.exists(log_dir):
        os.makedirs(log_dir)

    logger = logging.getLogger(name)

    if logger.handlers:
        return logger

    logger.setLevel(log_level)

    formatter = logging.Formatter(
        "%(asctime)s - %(levelname)s - %(message)s"
    )

    file_handler = logging.FileHandler(
        os.path.join(log_dir, f"{name}.log")
    )
    file_handler.setFormatter(formatter)

    console_handler = logging.StreamHandler()
    console_handler.setFormatter(formatter)

    logger.addHandler(file_handler)
    logger.addHandler(console_handler)

    return logger



```
