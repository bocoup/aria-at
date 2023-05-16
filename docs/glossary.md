# Glossary

## About this page

This page provides definitions for terms with special meaning in the ARIA-AT project.

Terms are organized into categories under level 2 headings. Each term is a level 3 heading. The organization is not strictly alphabetical so that someone who wishes to learn ARIA-AT lingo can read the page and gain some understanding without a lot of jumping around.

To reference terms from other pages in this wiki, use markdown syntax:

~~~
[[TermYouWantToReference|Glossary#TermInLowerCaseWithSpacesReplacedWithHyphen]]
~~~

Example:

~~~
This sentence includes a reference to [[test plan|Glossary#test-plan]].
~~~


## ARIA-AT Testing Model Terms

### Assertion

Statement of an expected behavior for an assistive technology.

An assertion specifies an assistive technology behavior that is expected when a user performs a specific task in a given context where a given accessibility semantic is present. For example, specifies how a screen reader is expected to behave when a user performs  a reading command that accesses an element with the `checkbox` role. In this example:
* The test specifies the user task of  "Read a checkbox".
* The given context is the test case, which is an implementation of a checkbox.
* The given  accessibility semantic is the ARIA role `checkbox`.
* The assertion could be, "The screen reader conveys the role `checkbox` to the user."

### Assertion Priority

Specifies whether an assertion is “Required” or “optional”.

The ARIA--AT project attempts to define  assistive technology behaviors necessary for an accessibility semantic to provide the perceivability, operability, or understandability intended for that semantic by the ARIA specification. Assertions that describe necessary behaviors are given a priority of "Required." The ARIA-AT community group seeks consensus on required assertions from all effected assistive technology  developers as well as community group members.

In addition, the project intends to promote assistive technology support for additional behaviors  that the community recognizes as very helpful ways of improving perceivability, understandability, oroperability when a specific accessibility semantic is present in the context defined by a specific test case. Assertions that describe behaviors that may be helpful but may not be recognized as necessary by all assistive technology developers are given a priority of "Optional."

### Expected User Setting

Specifies a non-default user setting that needs to be set in an assistive technology  in order to perform a test, i.e., to perform a given user task. The default assumption for all assertions is that the assertion should be met when the assistive technology is configured with its defaults. If a test requires a deviation from the default configuration, the expected user setting must be specified.

### Test

Defines a user task for a test case, the commands that are used to perform the task, and the assertions that need to be satisfied for successful completion of the task. A test defines the specific commands used for each assistive technology that will be tested using the test.

Each assertion specified in a test has a priority and optionally an expected user setting.

That is, given an implementation of an ARIA design pattern (a test case), the test specifies a task for a tester to complete and the assertions that need to be tested after completing the task. For example, given a checkbox, read the checkbox and then test that it's role, name, and state are correctly conveyed. Note that a screen reader may provide multiple commands that read a checkbox. So, a test includes a list of commands for the tester to test.

### Test Case

An implementation of one or more accessibility semantics.

Test cases provide the context for a test. For example, to test the assistive technology behaviors for the accessibility semantics associated with the `checkbox` role, we need an implementation of a checkbox that uses the `checkbox` role.

The initial suite of test cases for the ARIA-AT project  are the implementation examples provided by the [WAI-ARIA Authoring Practices Guide](http://w3c.github.io/aria-practices/). A primary goal of the ARIA-AT project is to provide the data necessary for each APG example to include an assistive technology support table to help web authors understand whether or not the pattern illustrated by that example is [accessibility supported](https://www.w3.org/TR/UNDERSTANDING-WCAG20/conformance.html#accessibility-supporteddef).

### Test Plan

The set of tests that apply to a test case. A test plan covers all tests necessary for the test case widget to be fully supported by a certain kind of assistive technology, e.g., screen readers.

A test plan includes all tests for a particular implementation of an ARIA design pattern. A plan covers all AT currently supported by the project, e.g., all tests for all AT for the grouped checkbox example.


### Test Plan Run

Execution of all tests in a test plan with a specific assistive technology at a specific version using a specific browser at a specific version, e.g., run all tests in the checkbox test plan with JAWS X and Chrome Y. X and Y include minor version numbers.

### Equivalent Test Results

Some steps in ARIA-AT processes  require comparing results from two different executions of a given test **T** to determine if they are equivalent (agree with one another) or are conflicting (disagree with one another). For example, the process mitigates the likelihood of human error by having two people run the same test.

Results **R1** and **R2** from test **T** are equivalent if:
1. **R1** and **R2** contain identical assertion support for every command in T:
   * Each assertion designated  as supported for a given command in **R1** is also designated as supported for that command in **R2**.
   * Each assertion designated  as not supported for a given command in **R1** is also designated as not supported for that command in **R2**.
   * Each assertion designated  as incorrectly supported for a given command in **R1** is also designated as incorrectly supported for that command in **R2**.
2. **R1** and **R2** contain identical output for every command in test **T**, including unexpected excess output.


## Working Mode Process Terms

### Draft Test Plan

A test plan containing tests that are in the process of being developed by a tes developer and the community group.
It is not yet ready for review by assistive technology developers or the broader accessibility community.

### Candidate Test Plan

A test plan that has been reviewed for accuracy and completeness by community group members, and it is deemed by the community group to be ready for review by assistive technology developers and the wider accessibility community.

### Recommended Test Plan

A test plan that has been reviewed by assistive technology developers, and they have agreed that it can be used to generate public reports.

### Blocked Test Plan
 
A test plan that has unresolved issues with upstream dependency on an open issue related to the ARIA Authoring Practices Guide, the ARIA specification, a browser, or OS-level accessibility API.

### Blocked Accessibility Semantic

An ARIA attribute, HTML element, or HTML attribute that cannot be tested due to unresolved issues with upstream dependency on an open issue related to the ARIA Authoring Practices Guide, the ARIA specification, a browser, or OS-level accessibility API.

### Comparable Product Versions

Version **X** and version **Y** of a given AT/browser combination are comparable for a test if they yield [equivalent test results](#equivalent-test-results).

**X** and **Y** refer to different versions of the same AT and browser. For instance, if **X** refers to JAWS version **j1** and Chrome version **c1**, then **Y** must refer to a different pairing of JAWS and Chrom versions, e.g., JAWS **J2** and Chrome **c1**.
Version comparability does not refer to comparison of a given AT when used with  two different browsers or a given browser when used with two different assistive technologies.

