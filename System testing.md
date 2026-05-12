1. Introduction to Testing
Software testing is the process of evaluating a software application to identify defects, bugs, or unexpected behaviour. It involves executing components under controlled conditions and comparing the actual results with expected results.
Testing is a critical part of software development because it improves the reliability, correctness, and maintainability of the system. Without proper testing, defects may reach end users, causing poor experiences or security vulnerabilities. For the Lost and Found System, testing ensures that item submissions are recorded correctly and that business registrations are validated properly before an account is created.

2. Purpose of Testing
The purpose of testing in this project is to:
•Identify defects early before the system is deployed or used by real users.
•Verify that each component behaves as intended under both expected and unexpected conditions.
•Ensure that form validation correctly rejects invalid or incomplete inputs.
•Confirm that successful inputs are processed and stored as expected.

3. Focus on Testing — Chosen Components
Two critical components were selected for testing from the Lost and Found System codebase:

Component 1: Item Submission Form 
The item submission form is the core feature of the system. It is triggered when a user clicks 'Submit Lost Item' or 'Submit Found Item' on the homepage. The openForm() function opens a modal where the user must provide: an item name, a location (from a dropdown of 12 venues), a category, a date, and the type (lost or found).
This component is critical because it is the primary way data enters the system. If the form does not validate correctly, incomplete or invalid reports could be saved, making it impossible for items to be matched with their owners. It was selected for testing because it handles multiple input fields, each with their own validation requirements.

Component 2: Business Registration Form 
The business registration form allows businesses such as hotels, airports, and restaurants to create an account in the system. The registerModal form collects the business's full name, email address, business type, and password.
This component is important because it controls who can access the business dashboard and manage inventory. If registration validation fails, invalid accounts could be created, or genuine businesses could be locked out. It was selected because it tests multiple required fields, email format validation, and duplicate email detection.

Test Cases — Component 2: Business Registration Form

![table1](https://github.com/junakryez1u/SE_Project_Phase1_TeamA3/raw/main/Screenshot%202026-05-12%20191932.png)


5. Writing Test Code
The system is built in HTML and JavaScript with no backend framework. To write executable tests, the core validation logic from java.js and business.js was simulated in Python, following the same conditional structure present in the original code. Each test function uses assert statements to verify that the function returns the correct result for a given input.

Test Code — Component 1: Item Submission Form


# Simulated logic from  — Item Submission Form

def submit_item(item_name, location, category, date, item_type):
    if not item_name or not item_name.strip():
        return 'Validation error: item name required'
    if not location:
        return 'Validation error: location required'
    if not category:
        return 'Validation error: category required'
    if not date:
        return 'Validation error: date required'
    if item_type not in ['lost', 'found']:
        return 'Validation error: item type required'
    return 'Item report saved successfully'

def test_valid_lost_submission():
    result = submit_item('Blue Backpack', 'Airport', 'Luggage', '2026-05-01', 'lost')
    assert result == 'Item report saved successfully'

def test_valid_found_submission():
    result = submit_item('Black Wallet', 'Hotel', 'Accessories', '2026-05-10', 'found')
    assert result == 'Item report saved successfully'

def test_empty_item_name():
    result = submit_item('', 'Airport', 'Luggage', '2026-05-01', 'lost')
    assert result == 'Validation error: item name required'

def test_no_location():
    result = submit_item('Phone', '', 'Electronics', '2026-05-01', 'lost')
    assert result == 'Validation error: location required'

def test_no_category():
    result = submit_item('Keys', 'Taxi', '', '2026-05-01', 'lost')
    assert result == 'Validation error: category required'

def test_no_date():
    result = submit_item('Laptop', 'College', 'Electronics', '', 'lost')
    assert result == 'Validation error: date required'

def test_all_fields_empty():
    result = submit_item('', '', '', '', '')
    assert result == 'Validation error: item name required'

def test_spaces_only_name():
    result = submit_item('   ', 'Airport', 'Luggage', '2026-05-01', 'lost')
    assert result == 'Validation error: item name required'

    4. Preparing Test Cases
Test cases were designed to cover three types of scenarios for each component:
•Normal/valid inputs — confirming the happy path works correctly.
•Invalid inputs — checking that bad data is rejected with a clear error.
•Edge/boundary cases — testing empty strings, whitespace-only values, special characters, and duplicate entries.

Test Cases — Component 1: Item Submission Form

![table2](https://github.com/junakryez1u/SE_Project_Phase1_TeamA3/raw/main/Screenshot%202026-05-12%20192434.png)



Test Code — Component 2: Business Registration Form

# Simulated logic from  — Business Registration

registered_emails = []

def register_business(name, email, business_type, password):
    if not name or not name.strip():
        return 'Validation error: name required'
    if not email or '@' not in email:
        return 'Validation error: valid email required'
    if not business_type or not business_type.strip():
        return 'Validation error: business type required'
    if not password or not password.strip():
        return 'Validation error: password required'
    if email in registered_emails:
        return 'Error: email already registered'
    registered_emails.append(email)
    return 'Account created, success message shown'

def test_valid_registration():
    registered_emails.clear()
    result = register_business('Juna Kryeziu', 'juna@business.com', 'Hotel', 'Secure123')
    assert result == 'Account created, success message shown'

def test_empty_name():
    result = register_business('', 'juna@business.com', 'Hotel', 'Secure123')
    assert result == 'Validation error: name required'

def test_invalid_email():
    result = register_business('Juna', 'not-an-email', 'Hotel', 'Secure123')
    assert result == 'Validation error: valid email required'

def test_empty_email():
    result = register_business('Juna', '', 'Hotel', 'Secure123')
    assert result == 'Validation error: valid email required'

def test_empty_business_type():
    result = register_business('Juna', 'juna@b.com', '', 'Secure123')
    assert result == 'Validation error: business type required'

def test_empty_password():
    result = register_business('Juna', 'juna@b.com', 'Hotel', '')
    assert result == 'Validation error: password required'

def test_duplicate_email():
    registered_emails.clear()
    register_business('Juna', 'juna@business.com', 'Hotel', 'Secure123')
    result = register_business('Juna', 'juna@business.com', 'Hotel', 'Secure123')
    assert result == 'Error: email already registered'


    Test Code — Component 2: Business Registration Form

# Simulated logic from business.js — Business Registration

registered_emails = []

def register_business(name, email, business_type, password):
    if not name or not name.strip():
        return 'Validation error: name required'
    if not email or '@' not in email:
        return 'Validation error: valid email required'
    if not business_type or not business_type.strip():
        return 'Validation error: business type required'
    if not password or not password.strip():
        return 'Validation error: password required'
    if email in registered_emails:
        return 'Error: email already registered'
    registered_emails.append(email)
    return 'Account created, success message shown'

def test_valid_registration():
    registered_emails.clear()
    result = register_business('Juna Kryeziu', 'juna@business.com', 'Hotel', 'Secure123')
    assert result == 'Account created, success message shown'

def test_empty_name():
    result = register_business('', 'juna@business.com', 'Hotel', 'Secure123')
    assert result == 'Validation error: name required'

def test_invalid_email():
    result = register_business('Juna', 'not-an-email', 'Hotel', 'Secure123')
    assert result == 'Validation error: valid email required'

def test_empty_email():
    result = register_business('Juna', '', 'Hotel', 'Secure123')
    assert result == 'Validation error: valid email required'

def test_empty_business_type():
    result = register_business('Juna', 'juna@b.com', '', 'Secure123')
    assert result == 'Validation error: business type required'

def test_empty_password():
    result = register_business('Juna', 'juna@b.com', 'Hotel', '')
    assert result == 'Validation error: password required'

def test_duplicate_email():
    registered_emails.clear()
    register_business('Juna', 'juna@business.com', 'Hotel', 'Secure123')
    result = register_business('Juna', 'juna@business.com', 'Hotel', 'Secure123')
    assert result == 'Error: email already registered'

def test_spaces_only_password():
    result = register_business('Juna', 'juna@b.com', 'Hotel', '   ')
    assert result == 'Validation error: password required'

6. Running Tests
The tests were executed using Python 3 in the terminal. All test functions were placed in a single file named test_lost_found.py and run with the following command:

python -m pytest test_lost_found.py -v

Test results are interpreted as follows:
•PASSED — The function returned the expected result for the given input. The assert statement did not raise an error.
•FAILED — The function returned an unexpected result. The assert statement raised an AssertionError, showing the actual vs. expected output.
•ERROR — The test could not run due to a syntax or runtime error in the code.

![screenshot1](https://github.com/junakryez1u/SE_Project_Phase1_TeamA3/raw/main/WhatsApp%20Image%202026-05-12%20at%207.13.51%20PM.jpeg)


![screenshot2](


![screenshot3](


![screenshot4](


7. Test Coverage and Reflection
Test coverage refers to how thoroughly the tests exercise the code paths, conditions, and possible failure modes of a component.

For the Item Submission Form, the tests cover:
•All required fields individually (name, location, category, date, type).
•All fields empty at once.
•Whitespace-only inputs which should be treated as empty.
•Very long inputs and special characters including script injection.

For the Business Registration Form, the tests cover:
•All four required fields individually (name, email, type, password).
•Invalid email format (missing @ symbol).
•All fields empty at once.
•Whitespace-only password.
•Duplicate email registration to prevent multiple accounts with the same email.

What could still be improved:
•Integration tests that test the full form-to-database flow in the browser environment.
•Testing the modal open/close behaviour (openForm and closeForm functions) with a browser automation tool such as Selenium or Playwright.
•Testing that the correct industry page loads when a user selects a venue from the dropdown.
•Performance testing to verify behaviour when a large number of items are submitted simultaneously.





