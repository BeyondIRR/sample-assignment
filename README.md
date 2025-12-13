# BeyondIRR Hiring Assignment

## Assignment Instructions

1. **Work Authenticity:** Ensure that all code you submit is your original work. Plagiarism or using someone else's code is strictly prohibited and will result in disqualification.

2. **Task Completion:** The assignment consists of multiple tasks, ranging from basic to advanced. It is not necessary to complete all tasks; you will be evaluated based on the number of tasks you complete progressively, the quality of your code, and your approach towards problem-solving.

3. **Best Practices:** Follow standard code formatting guidelines for Python. Use meaningful variable names, write modular code, and ensure proper error handling. Code readability and maintainability are critical, so please comment your code where necessary.

4. **Project Setup:** Begin by setting up a new **Django** project. Create a virtual environment, install Django, and start a new project. Include this setup process in your README file with relevant `requirements.txt`, so it's clear how to reproduce your environment.

5. **Version Control:** Use Git to track changes of your code. Please keep in mind that your code submission should demonstrate regular and incremental commits with meaningful messages and strictly avoid to commit your entire codebase in one go. This is crucial for us to evaluate your progress and development approach.

6. **Deadline**: Please submit your assignment by **11:59 PM on December 15, 2025**. No commits made after this timestamp will be considered for the evaluation.


## Assignment Challenges

### Task 1: Protect API endpoint(s)

> **Objective:** Secure the APIs by implementing JWT authentication using RS256 algorithm.
- Integrate JWT authentication across all API endpoints in this assignment.
- Implement token generation and validation as per the RS256 algorithm.
- Implement a Login API that accepts `email` and `password` and returns a JWT token.


### Task 2: Custom User Model with Unique Fields

> **Objective:** Implement a new **Account** model that adheres to the following specifications:
- Email should be unique for each user.
- Add a new field `arn_number` and that should also be unique for any given user.
- No username field should be present in the table.

_**Note**: An ARN number is a unique numeric code given to individuals or companies who want to sell mutual funds to its customers. Asset Management Companies (AMC) must use this code while dealing with Fund Managers in the selling and marketing of Funds. For e.g. Axis Securities Limited has ARN number as **64610**._


### Task 3: ARN Validation Service

> **Objective:** Develop a signup API that validates the ARN number during the registration process.
- The API should accept the given fields: `email`, `password`, `first_name`, `last_name` (optional), and `arn_number`.
- The Association of Mutual Funds in India (AMFI) provides a service on its website to locate the ARN verified distributor. Therefore, the developer must ensure the validity of the ARN number by fetching the record from the [AMFI website](https://www.amfiindia.com/locate-your-nearest-mutual-fund-distributor-details). 
- The email extracted from the website should match with the user's email used for signup. 
- If any error is encountered during the process, the API should return a reasonable error message.
- The developer may choose to scrape the website or use any other method to fetch the data.


### Task 4: Better Error Logs

> **Objective:** Implement a decorator that captures request payloads and responses in the event of an exception/error.
- Create a decorator `log_request` to record all the exceptions/errors emitted by a django view. Use this decorator to log any errors encountered during the signup process by a user.
- The decorator should populate the log entries in the model `LogRequest` with appropriate fields such as `url`, `status_code`, `timestamp`, etc. 
- The decorator should accept an optional parameter `record_success`. When set to `True`, it should capture the success responses as well.
- **Bonus:** The decorator should support masking of sensitive data points in the payload and response.


### Task 5: Bulk Transaction Updates via Excel Upload

> **Objective:** Create an API endpoint that allows users to upload an excel file to update their transaction records.
- The API should accept an excel file that contains multiple transaction records and add/update the `Transaction` model. 
- The Transaction schema should be as follows:
    | Field       | Type        | Description                |
    |------------ |-------------|----------------------------|
    | user        | Foreign Key | Reference to Account model |
    | product     | Char        | Unique product identifier  |
    | asset_class | Choice      | Equity, Debt, or Alternate |
    | date        | Date        | Date of transaction        |
    | units       | Decimal     | Units purchased/sold       |
    | amount      | Decimal     | Transaction amount         |
- For each record in the file:
    - If a transaction for the specified product and date already exists for the user, the API should update that record.
    - If no matching record exists, a new transaction record should be created.
- Ensure that each product can only have one transaction per day for a given user.
- **Bonus:** Optimize the process to handle large excel files efficiently.

_**Note:** Please find the required excel workbook `template.xlsx` within this repository._


### Task 6: Yearly Transaction Summary by Asset Class

> **Objective:** Develop an endpoint `/summary` that aggregates transaction data across different asset classes for each financial year.
- The endpoint should calculate the net transactions for each asset class (Equity, Debt, Alternate) within a financial year (1st April to 31st March) for a given user associated with the corresponding `Transaction` model.
- If there are no transactions for a particular asset class in a financial year, the sum for that asset class should be 0.
- The response should be structured as follows:
    ```
    {
        "FY24-25": {
            "Equity": 1000,
            "Debt": 2000,
            "Alternate": 3000
        },
        "FY23-24": {
            "Equity": 1000,
            "Debt": 2000,
            "Alternate": 0
        },
        ...
    }
    ```


## Extra Credits
Regardless of your main challenge completion, feel free to attempt the following tasks for some extra brownie points :D

### Bonus Task: Comprehensive Test Suite

> **Objective:** Develop a test suite to ensure the reliability and correctness of your code.
- Write tests cases for all critical components, including models, views, serializers, utilities, etc. alongwith integration and end-to-end tests.
- Aim for high code coverage to ensure that most of your code is tested. Use tools like `pytest-cov` or `coverage.py` to measure and report code coverage.


### Bonus Task: Detailed Documentation

> **Objective:** Create thorough documentation that explains how to use and extend your project.
- Include inline comments or docstrings in your code to explain complex logics.
- Extend your README file to include:
    - Detailed instructions for setting up the development environment.
    - API documentation, including endpoints, request formats, example responses, etc.
    - Links as citation(s) to any article/code referred to or used in the application.


## Submission Guidelines
- Create a private GitHub repository on your account for this assignment.
- Add the the following GitHub accounts as collaborators:
    - [Avi-Sh](https://github.com/Avi-Sh) - avishrant.sharma@beyondirr.tech
    - [sagar-birr](https://github.com/sagar-birr) - sagar.agarwal@beyondirr.tech
    - [Dhruv-Sachdev1313](https://github.com/Dhruv-Sachdev1313) - dhruv.sachdev@beyondirr.tech
- Submit the link to your private GitHub repository via the specified submission form shared on your respective emails.
- **DEADLINE: 11:59 PM on December 15, 2025, positively.**

_**Note:** Ensure that your repository is accessible to the provided GitHub username and includes all code, tests, requirements, configurations or documentation, if any._

We are eager to review your submission and look forward how you approach these challenges! Good Luck!
