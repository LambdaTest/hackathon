# hackathon

## Problem Statement
Create `test-runners`. Each test-runner should have the following 2 functionalities:
1. It should be able to identify and pick all test-cases for a given repository. In simple words, write a `testDiscovery` function that can extract all test-cases for a given repository and store it in a json file in a given format.
2. It should be able to run the underlying tests for given array (one or more; subset) of testObjects generated in #1. In simple words, write a `testExecution` function that can execute tests given their identifiers.

## Description
Test-runners are piece of software that enable users to run the tests that they have written. In practice, in almost all programming languages, there are frameworks defined for writing the test-cases. For example, in Javascript world, there are test frameworks like `ava`, `jasmine`, `jest`, `mocha` and many others. Test-runners are an extension (or wrappers) of these test frameworks such that they have more controls on the underlying framework's functions, and at the same time, they make working with the underlying framework more user-friendly.

## Rationale
With the help of test-runners, we aim to transform the test-cases (as well as test-suites) written by a user inside a codebase (i.e. raw-text written in some programming language) into an object that can be made sense of independently. Once these objects are generated, test-runners should provide the ability to run the corresponding test-case for the given object and record its status, stats, metrics and various insights that are useful. Once we have these objects, one can employ techniques to solve various pressing problems in the world of test-case management and left-shifting the test feedback loop, for example:
- selecting a subset of these objects and running them for a finite number of repetitions to test for their flakiness,
- selecting a subset of these objects based on certain algorithms for a commit and running only this smaller subset to give >90% confidence of stability yet saving time in running all test-cases,
- overall testing health of your codebase, etc

## Constraints
You're free to choose any framework of any target programming language and can write the test-runner in any programming language as long as it generates output in the given format. For example, you can choose to write a test-runner in python that can identify test-cases written using TestNG framework of a java repository. Preferred target languages: Python, Java, C#, GoLang


Discovery Output:
```
{
  "testCases": [
    {
      "id": "TestCaseID1",                                          // `id` can be simply an md5 hash of label but should be ensured that it is unique for all test-cases (for at least the testFile)
      "label": "Test Case Label 1",
      "file": "test/test1.py",
      "test-suites": [ "TestSuiteID11", "TestSuiteID12" ... ]
    },
    {
      "id": "TestCaseID2",
      "label": "Test Case Label 2",
      "file": "test/test2.py",
      "test-suites": [ "TestSuiteID21", "TestSuiteID22" ... ]
    },
    ...
  ],
  "testSuites": [
    {
      "id": "TestSuiteID11",
      "label": "Test Suite Label 11",
      "file": "test/test1.py"
    },
    {
      "id": "TestSuiteID12",
      "label": "Test Suite Label 12",
      "file": "test/test1.py"
    },
    ...
  ]
}
```

Execution Output:
```
{
  "testCases": [
    {
      "id": "TestCaseID1",
      "status": "passed",
      "duration": 3
    },
    {
      "id": "TestCaseID2",
      "status": "failed",
      "duration": 17,
      "failureMsg": "Expected 2 is not equal to 3"
    },
    ...
  ],
  "testSuites": [
    {
      "id": "TestSuiteID11",
      "status": "passed",
      "duration": 89,
      "numTests": 12
    },
    {
      "id": "TestSuiteID12",
      "status": "failed",
      "file": "test/test1.py",
      "failureMsg": "One or more test-cases failed",
      "numTests": 16
    },
    ...
  ]
}
```

## Prizes 🥳
- Top 10 teams who successfully complete the above challenge would be given gift vouchers of $200 each. 
- Top 3 team members would be eligible for a 2 month paid internship focused on Open Source tech at Lambdatest Inc.

