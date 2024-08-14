C. Late 2020, Early 2021 - Technical Writing Sample - Jerel Nelson Starks

---
# QA Automation Workflow

---
# Discovery + Preparation
#### Observe + Understand
Discovery and Ideation steps usually occur concurrently.
- Meet with QA Managers and Product Managers to review necessary needs in regards to QA automation.
- Create a test plan based on business requirements and engineering needs.
- Update [QA Automation Schedule]() to include new assignments.

### Ideation Meeting Agenda
Discover a segment or module of the product that requires automation testing based on a data-driven approach and qualitative impact.
* Establish the scope of testing.
* Establish what type of testing type is best for the specific instance.
* Interpret client interviews and business requirements information from the meeting.
* Devise test logistics:
  * Who will be performing test designing and writing? Find the QA team member who has the most experience in that specific facet of the application.
  * How will this affect the schedule and business needs?
---
# Ideation + Test Planning
#### Define Test Objectives and Criteria
- Create a Jira Epic to sort and group Jira tasks for the specific facet of the application stipulated in the last step.
Automated test cases are based on user stories and are contextual to a journey map.
### Test Case (Jira Issue) Criteria
* Tests are single purpose and only test one thing or feature.
  * Multiple assertions are acceptable when there are multiple expected results.
* The initial test state should be static with minimal preconditions.
### Test Case Focus
Automated test case creation should focus on user stories and test cases that are:
* Susceptible to human error; and,
* Require immense repetition; and,
* Include a large amount of data; and,
* Use a lot of frequently used functions and modules.
### Test Case (Jira Issue) Creation
* Create a Jira task for each test case. Within each Jira task, create two sub-tasks.
  * The first sub-task is for writing the TestRail test case.
  * The second sub-task is for implementing the test automation.

There are instances where test case writing tasks are handled in a test plan or within the parent epic. In these instances, a single automation task should be created in Jira for each TestRail test case without creating additional sub-tasks or writing tasks.
* Meet with QA Managers and Product Managers to review Jira epic, tasks, and sub-tasks. If the Jira issues reach approval, move on to the next step.
* Update [QA Automation Schedule]() to include automation tasks.
---
# Prototype + Test
#### Create Test Data for Automation
There are two or more individuals involved in this step, the **test designer**(s) and **test reviewer**(s).
* The **test designer** creates and writes TestRail test cases from Jira tasks (user stories).
* The **test reviewer** reviews and approve or disapprove a TestRail test case.
## Test Designer
Write automation test cases in TestRail based on Jira tasks created in the previous step. Set respective Jira sub-task from **Open** to **In Progress** when writing a test case.
### TestRail Case Creation Procedure
* Write test case(s) in TestRail with **Preconditions**, **Steps**, and **Expected Result**(s). Reference the TestRails case to a respective Jira task.
* Keep in mind [Cypress Best Practices and Procedures]() when creating a test case.
* Within the TestRail case meta-data:
  * Set the Assignee to the test designer and the Reviewer to the test reviewer.
  * Set the Test Case Status from **None** to **Unreviewed**.
  * Set the Automation Status to **None**.
<details>
<summary>Here is an example of a test case.</summary>
Test case image goes here
</details>

### Jira Task Creation Procedure
* Once TestRail cases are written and complete, set the respective Jira sub-task(s) from **In Progress** to **Testable**.
### Step Completion
* If necessary, review TestRail cases with the QA team or an assigned **test reviewer** for approval. Once the review is complete, the **test reviewer** must set the respective Jira sub-task to **Closed (Passed Testing)**.
## Test Reviewer
* Review TestRail cases when the respective Jira task has a status of **Testable**.
### TestRail Case and Jira Review Procedure
* Once a Jira task for test writing has the status Testable, begin the review process:
  * Set the Jira task to status to **Being Tested**.
  * Set the TestRail Test Case Status to **In Progress**.

The test case must validate and fulfill all items listed in the **Expected Results** section of the TestRail case.
* If the TestRail test case is valid:

  * Set the respective Jira task to **Closed (TestRail)**.
  * Set the TestRail Test Case Status to **Reviewed**.
  
#### Changes Requested
* If the TestRail test cases need changes, set the respective Jira task to **Reopen** with test notes and recommendations that solves the conflicts with the test case. 
  
### Step Completion
* If necessary, review TestRail cases with the test designer. Once the review is complete and passed, set the respective Jira task status to **Closed (TestRail)** and the TestRail Test Case Status to **Reviewed**.
---
# Implementation
### Write and Execute Automation Tests
Please **DO NOT** write any test specs or test case implementation without having completed and reviewed TestRail cases for them.
* There are two or more individuals involved in this step, the **test engineer**(s) and **test reviewer**(s).
  * The **test engineer** writes code that implements the test case(s) mentioned in the previous step.
  * The **test reviewer** reviews and approves or disapproves of an automated test case implementation.
## Test Engineer
* Write automation test specs in Cypress based on created TestRail cases in the previous step.
* While performing implementation of a test spec:
  * Set the respective Jira task from **Open** to **In Progress**.
  * Set the respective TestRail case automation status from **None** to **In Progress**.
### GitHub and Jira Procedure
Review [Git Version Control]() documentation.
1. Create a **Branch** referencing either the Jira Epic (for small automation groups) or per Jira task. E.g., `QA-13/Amortization-Custom-Curve-Test`
   Make sure to reference the respective Jira issue in the branch name to ensure they are linked. E.g., `QA-45/<Branch Name>`
2. Write test specs as per [Cypress Best Practices and Procedures]() following **Preconditions, Steps, and Expected Result(s)** stated in the respective TestRail case.
3. Once initial test spec implementation is complete:
   1. Open a **Pull Request** on GitHub.
      1. Assign relevant QA team member(s) as a **Reviewer**.
      2. Assign yourself as the **Assignee**.
      3. Set the **Label** to automation.
      4. Set the **Milestone** to the current or relevant release date.
   2. Set the respective Jira task(s) status from **In Progress** to **Testable**.
   3. Set the TestRail Automation Status to **Unreviewed**.
4. Once the test case(s) implementation review is completed and passed, the **test reviewer** should merge and close the Pull Request.
   The **test engineer** should never close and merge their Pull Request
   
<details>

<summary>Here's a simple git workflow example:</summary>

Get the most recent code and create a local branch.
```shell
git fetch
git checkout main
git pull
git checkout -b <new branch name>
npm i
npx cypress open
```
Add code changes to staging after they have been saved.
```shell
git add .
git commit -m "<commit message>"
```
Push local/staging code to the remote repository
```shell
  git push --set-upstream origin <the branch name>  
```

Subsequent pushes after the initial push can be simply performed with a git push.
</details>

* Once the branch is ready for code review and merging, open a pull request on the GitHub web app. This is because there are specific data points mentioned above that need to be inputted.
#### Changes Requested
* If the **test reviewer** has requested changes, please review their comments & test notes and resolve these conflicts as necessary.
#### TestRail Procedure
* Set the respective TestRail case assignee to yourself and set the reviewer to the **test reviewer**.
* Once the test spec implementation is ready for testing and validation (e.g., a Pull Request is open and the respective Jira task is Testable), set the respective TestRail case Automation Status to Unreviewed.

### Step Completion
* Once the review is reviewed and approved, the **test reviewer** should:
  * Set the respective Jira task(s) from **Testable** to **Closed (Passed Testing)**.
  * Set the respective TestRail case Automation Status to **Cypress**.
## Test Reviewer
* Review a test implementation when the respective Jira task has the status of **Testable**.
#### Jira and TestRail Procedures
* Once a Jira task for test implementation has the status **Testable**, begin the review process:
  * Set the Jira task status to **Being Tested**. Make sure you are assigned as the QA Tester and the **test engineer** is assigned as the **Assignee**.

#### GitHub Procedure
On the respective GitHub branch, assign yourself as a Reviewer (if not done already) and checkout the branch.
Re-evaluate the [Git Version Control]() documentation if you need to refresher on how to checkout a branch.
<details>

<summary>Here's a simple git workflow example:</summary>

Get the most recent code and run the test through the GUI:
```shell
git fetch
git checkout <name of the test implementations branch>
npm i
npx cypress open
```
Run the test through the command line headless-ly:
```shell
git fetch
git checkout <name of the test implementation's branch>
npm i
npx cypress run <path to test spec>
```
</details>

### Test Implementation Validation Procedure and Criteria
* On your local machine or cloud service, run the new or updated test specs for _validity_.
  * Validity: Does the test spec successfully fulfill the task’s acceptance criteria and the TestRail case’s expected results?
* The test should be able to be run headless-ly and headed, without and with the GUI, respectively.
  * Re-evaluate the [Cypress Setup]() documentation if you need a refresher on how to run a specific test spec or to run the test with specific options.
* If the test is designed to run on a specific environment (e.g., prod) or div, make sure to run the test spec at the respective location.
#### Changes Requested
* If the test spec needs changes, set the respective Jira sub-task to Reopen with test notes and recommendations that resolves the conflicts
* Within the review functionality on GitHub, add in-line comments and test notes that help resolve the conflicts. Submit the review with the Request changes option.
#### Valid Tests
* If the test spec is considered valid, complete the review on GitHub and merge the pull request with the Close & Merge the Pull Request option.
  * If there are open proposed changes, make sure to resolve these with the **test engineer** before closing and merging a pull request.

If necessary, review test implementations with **test engineer**(s).
### Step Completion
* Once the test implementation review is complete and passed:
  * Set the respective Jira sub-task to **Closed (Passed Testing)**.
  * Set TestRail case Automation Status to **Cypress**.

The **test engineer** should never close and merge their Pull Request, this is only performed by **Reviewers** assigned within the GitHub Pull Request.

---
# Test Deliverables + Maintenance
#### Test Artifacts, Reporting, and Upkeep
## Issue Closure
* Meet with QA Managers and Product Managers to review test automation and test plan/suites/cases, if approval of automation is complete, close respective Jira issues (epic and tasks).
* Update [QA Automation Schedule]() to reflect the status of assigned epics and tasks.
### Reporting
Test result reporting populates in three locations:
* The [Cypress Dashboard]()
* Slack
* [TestRail]()
### Maintenance
Test specs should be updated whenever a change to the front-end code of codename1 and codename2 breaks the test or makes the test no longer necessary.
## Test Maintenance Process
If a test no longer functions and requires updating, these actions should be performed:
### Jira
* A new [Jira Automation task]() should be created with a reference to the original automation task to repair the test.
### TestRail
* The respective TestRail case should have the Automation Status changed from **Cypress** to **Maintenance**.
---
If you have any suggestions or have questions about this process, please contact @Jerel Nelson Starks.

