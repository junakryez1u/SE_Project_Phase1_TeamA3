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

![table1](


