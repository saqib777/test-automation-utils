```
TEST DATA GENERATOR — AUTOMATION UTILITIES LIBRARY (CODE)

import random
import string
import uuid


def generate_random_string(length=8):
    """
    Generates a random lowercase alphabetic string.
    """
    return ''.join(random.choice(string.ascii_lowercase) for _ in range(length))


def generate_random_email():
    """
    Generates a random email address.
    """
    username = generate_random_string(6)
    domain = generate_random_string(5)
    return f"{username}@{domain}.com"


def generate_random_phone_number():
    """
    Generates a random 10-digit phone number as a string.
    """
    return ''.join(random.choice(string.digits) for _ in range(10))


def generate_random_user():
    """
    Generates a dictionary representing a user object.
    """
    return {
        "id": str(uuid.uuid4()),
        "first_name": generate_random_string(6).capitalize(),
        "last_name": generate_random_string(6).capitalize(),
        "email": generate_random_email(),
        "phone": generate_random_phone_number()
    }


def generate_boundary_numbers():
    """
    Returns common boundary values for numeric testing.
    """
    return {
        "min": 0,
        "max": 100,
        "just_below_min": -1,
        "just_above_max": 101
    }


def generate_invalid_emails():
    """
    Returns a list of invalid email formats for negative testing.
    """
    return [
        "plainaddress",
        "@missingusername.com",
        "missingdomain@.com",
        "missingat.com",
        "user@domain"
    ]


```
