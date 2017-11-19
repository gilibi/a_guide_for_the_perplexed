# Unit Testing

## “It Is” and “It Is Not” :
First , just to make sure there is no confusion around this term - unit testing means that a developer is writing a piece of code to test 
a small component or a unit of his software (_independently from other parts_). Because the scope is very limited , there is no way to test it without writing a code.
**It is not** a manual testing the developer is doing before handover the code to QA for further testing.



## what do you need to know :
There are many frameworks you can use to write unit tests :
*	in java you can use JUnit
*	in python you can use PyUnit, unittest, pytest
*	additional javaScript test frameworks : Jasmine, Mocha and QUnit 

Just pick up one and start coding …


## why – I am not convinced yet :
- When something gets wrong, you can just rerun your unit tests and find the source of the bug instead of look in the entire software .
-	You are writing code that will make users happy (or customers 😊) , hopefully, you will add new functionality and upgrades . The unit tests can be a great help to
ensure you didn’t break anything.
-	The ultimate way for continuous integration and continuous delivery.

 “
Best way to convince... find a bug, write a unit test for it, fix the bug.
That particular bug is unlikely to ever appear again, and you can prove it with your test.
If you do this enough, others will catch on quickly.”


## 100% Code coverage  - really ?
Well, there are certain tools to measure code coverage i.e what percentage of the code written for the product is tested by a unit test. Many software development managers believe that 100% code coverage is necessary to ensure that the code is tested adequately. 
Writing many unit tests on every piece of code, will take time and money . A developer can only write ~N lines of code a week and you need to figure out what percentage of that code should be unit test code vs production code so here are a few principles for better unit testing :

- Isolation - avoid dependencies such as environment settings, or databases. A single test should not depend on running other tests before it, nor should it be affected by the order of execution of other tests
- A test should either pass all the time or fail until fixed. Having a unit test that passes some of the time is equivalent to not having a test at all.
- Naming convention - the test method name is very important. When a well-named test fails, it is easier to understand what was tested and why it failed.
- It should be easy . If it is too complicated , probably you need to refactor the code you are writing .
- For work balance and knowledge sharing, consider involving an additional team member to take part in this effort.





