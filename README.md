# plan-automation-framework

Automation Framework:
Tech Stack:
Playwright ----------------	Web browser automation
Testng --------------------	Powerful testing frameworks for structuring, organizing, and executing test cases
Maven ---------------------	Build automation tools for managing project dependencies, compiling code, running tests, and packaging the automation framework
Allure --------------------	Feature-rich reporting tools that provide visually appealing and detailed test execution reports, including screenshots, logs, and step-by-step execution details
Git -----------------------	Essential for managing source code, collaborating with team members.
Jackson -------------------	Jackson provides annotations to map the POJO fields to JSON.
Lombok --------------------	Provides annotations to reduce boilerplate code
Page Object Model (POM) ---	A design pattern that improves test maintainability and reusability by separating page elements and interactions from test logic.
Data-Driven Testing -------	Designing tests to execute with multiple sets of data, enhancing test coverage and efficiency.
Error Handling & Retries --	Implementing mechanisms to handle unexpected errors and retry failed test steps or scenarios to improve test stability.
Parallel Execution --------	Configuring the framework to run tests concurrently across multiple threads or machines to reduce execution time.
Clear & Concise Reporting - Providing comprehensive and easily understandable reports to quickly identify issues and track progress.





Static and dynamic test data
Retries
Mailable Reports

creating a framework with playwright (java), allure reports (include Steps), Data driven, Page object model, test case retries, use jackson and lombok for json test data, static and dynamic test data, host allure reports to show past reports



Playwright (Java) – for browser automation.
Allure Reports – with step annotations and screenshot attachments.
Jackson + Lombok – for structured and easy JSON test data handling.
Page Object Model (POM) – for reusability and clean structure.
Test Retries – to re-run flaky tests.
Data-driven Testing – from .json and .properties files.
Static + Dynamic Test Data
Allure Report Hosting – store and serve historical reports.

src/
 ├── main/
 │    ├── java/
 │    │    ├── base/            # BaseTest, Playwright setup
 │    │    ├── pages/           # Page Objects
 │    │    ├── utils/           # JSON reader, DB utils, config
 │    │    ├── data/            # POJOs with Lombok for test data
 │    └── resources/
 │         └── testdata/        # JSON files
 │         └── config.properties
 ├── test/
 │    └── java/
 │         └── tests/           # Test classes
 └── testng.xml


 1. Playwright Setup (BaseTest.java)
Initializes browser

Loads properties

Can preload test data from JSON

2. Allure Integration
Use @Step, @Attachment annotations from io.qameta.allure.

Add screenshot in teardown on failure.

Configure via allure.properties.

3. JSON Data with Jackson + Lombok
POJO annotated with @Data, @JsonProperty

Utility method using Jackson’s ObjectMapper to load

4. Test Retry Mechanism
Create RetryAnalyzer.java implementing IRetryAnalyzer.

5. Page Object Model
Each page class holds locators + page methods.

Methods should return this or next PageObject for fluent chaining.

6. Test Data Handling
Static: JSON preloaded to POJO.

Dynamic: Generated in test or before methods.

7. Allure Hosting
Generate HTML via allure generate --clean

Store on server, S3, or in Jenkins workspace.

Version them to view historical reports.

🚀 Optional Add-ons
Docker support for headless runs

CI/CD Integration with GitHub Actions, Jenkins, or GitLab

Oracle DB Utility for test setup/teardown

