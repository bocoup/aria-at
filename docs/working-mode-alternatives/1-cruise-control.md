## About this page

The ARIA-AT working mode describes roles, responsibilities, and process for the primary community group deliverables -- assistive technology (AT) interoperability reports. It does not cover every aspect of community group operations.

The development of this revision  of the working mode was discussed in [issue 375](https://github.com/w3c/aria-at/issues/375). Please raise a new issue to provide feedback or discuss further revision.
 
## Roles

Role | Responsibility
-----|---------------
Test developer | Research assistive technology behavior, propose [assertions](Glossary#assertion), propose tests, and formulate [draft test plans](Glossary#draft-test-plan). Note: Test developers are Community Group members.
ARIA-AT Community Group | Review draft test plans to develop consensus on tests, assertions, and assertion priorities, moving draft test plans to [candidate status](Glossary#candidate-test-plan).
Tester | Run tests to generate report data. Note: Testers are Community Group members who participate in the test review process.
AT developer | Review candidate test plans, raise test plan issues, review assertion failures, utilize failure data to resolve AT bugs.
ARIA-AT Community Group Chair | Manage  working mode process and resolve conflicts.
Test admin | Manage reporting database access,  support test plan review and consensus process. Note: Test admins are Community Group members who can represent the Community Group in negotiations  with AT developers.
APG Task Force | Resolve issues in test cases based on examples in the WAI-ARIA Authoring Practices Guide.
ARIA Working Group | Follow up on issues with the ARIA specification, browser implementations, or OS-level accessibility API implementations.
At large web developers and interested parties | Utilize report data to identify  root causes of unexpected AT behaviors in web experiences. If a discrepancy indicates a potential error in ARIA-AT reports, raise an  issue against the appropriate  report.

## Process

### Summary

The   working mode process describes how the ARIA-AT community group works with stakeholders to define expectations for assistive technologies.
The ultimate goal of the process is to achieve stakeholder consensus for  expectations so assistive technologies that meet the expectations are interoperable.
The project's primary deliverables are interoperability reports about which expectations are met by each assistive technology.

The expectations are defined in [[test plans|Glossary#test-plan]].
The following sections describe the steps the community group follows to develop and report on expectations for each test plan.
In practice, at any given time, there are multiple test plans moving through the process that could all be at different steps; many test plans are  developed and executed in parallel.

AT a high level, the process is broken into the following phases:
1. **Test Plan Research and Development:** The scope of assistive technology expectations for a specific set of assistive technologies and a specific accessibility semantic or design pattern implementation is defined, relevant  existing behaviors are documented, and a set of tests for the in-scope assistive technologies is proposed in a draft test plan.
1. **Draft Test Plan Review:** The community group vets the quality and potential efficacy of the plan by running the draft tests to generate  results for each in-scope assistive technology. When the community group believes  a draft plan is ready for review by assistive technology developers and other relevant stakeholders, the plan and   test results are published in a  candidate test plan report.
1. **Candidate Test Plan Review:** Developers of the in-scope assistive technologies have 120 days to begin providing feedback on candidate test plan reports. After 180 days in the candidate phase, as long as all feedback from  assistive technology developers has been resolved, the candidate test plan and its report are promoted to the recommended test plan status.
1. **Recommended Test Plan Reporting:** Recommended test plans generate reports of actual  interoperability levels based on consensus expectations.
   Recommended test plans are repeatedly  executed as in-scope assistive technology and browser versions change.
   AT developers use recommended test reports to make changes that improve interoperability.
   Regressions cause an issue to be raised against the  report. Anyone who reads a report and believes they have discovered an error may also raise an issue against the report.
1. **Issue Triage for Recommended Test Reports:** The community group has 30 days to identify a resolution plan for each issue raised   against a recommended test report. Resolution plans for valid issues that require changes to assertions or commands may return the test plan to either the draft or candidate phases, depending on the severity and scope of the issue. Corrections that do not alter assertions or commands can be made  without changing the status of the test plan. All changes are publicly logged.

### Test Plan Research and Development

1. (Community Group) Populate the backlog in the [Test Plan Workflow Github Project](https://github.com/w3c/aria-at/projects/1)
   with GitHub issues specifying [[test cases|Glossary#test-case]]   for which a [[test plan|Glossary#test-plan]] is needed. 
   The community group is responsible for setting the current scope of the backlog, such that it covers the accessibility semantics and assistive technologies being prioritized by the community group.
1. (Test Developer) Select a GitHub issue specifying a test case for which a test plan is needed from the backlog in the [Test Plan Workflow Github Project](https://github.com/w3c/aria-at/projects/1).
   All documentation of the test plan development will be recorded in the GitHub issue for that test case.
1. (Test Developer) Read the relevant parts of the [ARIA specification](https://w3c.github.io/aria/) and the [APG](https://w3c.github.io/aria-practices/) to understand the intent of the accessibility semantics and features present in the test case. Document understanding and provide links in the GitHub issue.
1. (Test Developer) If there are native OS components with similar accessibility semantics, study how AT behaves when using those components. Document relevant findings in the GitHub issue.
1. (Test Developer) Research any special AT configuration requirements. If some relevant accessibility semantics are not supported using the default AT configuration, explore and document the AT configuration changes needed to convey the semantics. Document relevant findings in the GitHub issue.
1. (Test Developer) Create a draft pull request in the aria-at repo containing a [draft test plan](How-to-contribute-tests)  proposing instructions, commands, assertions, assertion priorities, and expected user settings that:
   *   Are aligned with the intent of the ARIA specification and APG documentation.
   *   Are aligned with what ATs already do or what the test developer believes the AT developers are willing to implement.
1. (Test Admin) When a test developer indicates a draft test plan is ready for community group review, merge the pull request into the main branch of the aria-at repo, and create a draft test plan in the [ARIA-AT Test Queue](https://aria-at.w3.org/test-queue).

### Draft Test Plan Review

1. (Tester) Review and run the tests in the draft test plan, optionally using the automated testing tool.
1. (Tester) If  the plan is missing a test, raise an issue against the plan.
1. (Tester) Raise an issue for any test in the plan that is incomplete, inaccurate, overly restrictive, excessively  prescriptive, does not satisfy editorial conventions, contains scripting bugs, or otherwise does not meet community group standards for tests.
1. (Test Developer) Resolve issues raised against draft test plan. If an issue is due to a problem with the ARIA specification, the APG, a browser, or an OS-level accessibility API, then:
   * File an issue for the ARIA Working Group or APG Task Force as appropriate.
   * Raise an issue in the aria-at repo for each [[blocked accessibility semantic|Glossary#blocked-accessibility-semantic]]. Label the issue "blocked accessibility semantic".
   * In each blocked semantic issue, reference the appropriate specification and the issue raised against that specification.
   * Remove assertions effected by the blocked semantic.
   * Catalog each assertion that was removed in the test plan development issue and reference the appropriate blocked semantic issue.
1. (Test Admin) Ensure each test plan run is fully executed by at least two testers.
1. (Test Admin) For any test plan run where results from different testers conflict with one another, review conflicts to assess root cause.
   * If the root cause is an error in the test, raise an issue against the test.
   * If the root cause is tester interpretation, facilitate conversation to determine which tester's results should be modified.
1. (Test Admin) For each test plan run where there are no conflicts and where some tests fail, facilitate Community Group conversation about the failures  to ensure Community Group consensus that the test is appropriate and that the failure indicates the presence of a browser, accessibility API, or AT bug.


### Candidate Test Plan Review


1. (Test Admin) When all the following conditions are met, promote draft test plan to [[candidate test plan|Glossary#candidate-test-plan]]:
   * All review issues are closed.
   * [[Equivalent test run results|Glossary#equivalent-test-results]] have been generated by at least 2 testers in at least one browser.
1. (Test Admin) Notify developers of the in-scope assistive technologies that  the candidate test report is available for their review and of the due date for initial feedback.
1. (AT developer) Within 120 days, if the plan is not satisfactory, raise issues in the aria-at repo.
1. (Test Admin, Test Developer, and AT Developer) Collaborate to resolve test plan issues within 60 days. After the plan has been in the candidate phase for 180 days, if any issues remain open, do one or more of  the following:
   * Agree to extend candidate phase for a specific time period.
   * Agree the  [[assertion priority|Glossary#assertion-priority]] of a disputed assertion can be changed from required to optional.
   * Agree that a disputed assertion is unnecessary and remove it from the plan.
   * Agree that an [[accessibility semantic is blocked|Glossary#blocked-accessibility-semantic]] by an upstream issue, and assertions that test it should be removed.  
1. (Test Developer) If closing a test plan issue required agreement that an accessibility semantic is blocked by a problem with the ARIA specification, the APG, a browser, or an OS-level accessibility API, then:
   * File an issue for the ARIA Working Group or APG Task Force as appropriate.
   * Raise an issue in the aria-at repo for each [[blocked accessibility semantic|Glossary#blocked-accessibility-semantic]]. Label the issue "blocked accessibility semantic".
   * In each blocked semantic issue, reference the appropriate specification and the issue raised against that specification.
   * Remove assertions effected by the blocked semantic.
   * Catalog each assertion that was removed in the test plan development issue and reference the appropriate blocked semantic issue.

### Recommended Test Plan Reporting

1. (Test Admin) Promote candidate test plan to [[recommended test plan|Glossary#recommended-test-plan]] when all the following conditions are met:
   * The test plan has been in candidate phase for at least 120 days.
   * There are no open test plan issues.
1. (Test Admin) If a recommended test plan does not have a report for all in-scope AT and browser combinations, add the missing test plan runs to the test queue.
1. (Tester) Execute  all test plan runs in the test queue for the recommended test plan, optionally using the automated testing tool.
1. (Test Admin) Publish the reports for any [[test plan runs|Glossary#test-plan-run]] where there are [[equivalent test results|Glossary#equivalent-test-results]] from at least two testers using a [[comparable AT/Browser combination|Glossary#comparable-product-versions]].
1. (Test Admin or AT Developer) For all commands where test results indicate an assertion is either not supported or incorrectly supported, file an interoperability bug against the AT.
1. (AT developer) Resolve interoperability bugs; optionally integrate the aria-at test into AT build process.
1. (Test Admin) When a new version of an in-scope AT or browser is released:
   * Update lists of product versions for which  testing is required.
   * Update test queue to show that the  AT/Browser combination is missing test results for current versions.
1. (Tester) For any recommended test plan that does not have a published report for a current assistive  technology and browser combination, execute a [[test plan run|Glossary#test-plan-run]] for that combination.
1. (Tester) If a report for a new AT or browser version generates regressions, i.e., the assertions passed with the prior version and fail with the new version, raise an issue against the recommended test report.
1. (At Large Web Developer or Interested Party) If testing a different but valid implementation of an accessibility semantic generates results that differ from the recommended test report, raise an issue against the report.

### Issue Triage for Recommended Test Reports

1. (Test Admin) When an issue is raised against a recommended test report, within 30 days, complete one of the following:
   * If the issue is a regression and the root cause is a  change in AT output that appears to still satisfy assertions, validate this conclusion with community group and revise the report accordingly, i.e., the newly failing assertion becomes a passing assertion.
   * If root cause is a new AT bug, file an AT interoperability bug with the AT developer.
   * If root cause is a browser or an OS-level accessibility API bug, raise a bug with the owner of that product.
   * If root cause is a problem with the test or test infrastructure, discuss corrective action options with community group and disposition report accordingly, e.g., revert the plan to candidate status and follow the candidate phase process.

## Conflict resolution

If agreement regarding (1) what is being asserted in a test or (2) the assertion’s priority, or (3) the assertion’s expected user setting cannot be reached, it can be resolved as follows:
*   The test developer should evaluate the feedback and make a decision on whether to modify the test or respond and keep the test as-is.
*   If the involved AT developers agree with each other but disagree with the test author, then:
   *   The test developer should edit the test plan and the test to reflect AT developer consensus, or escalate to the chairs.

In any case, if agreement still cannot be made, either party can escalate to the chairs.

## Escalation to chairs

Escalate by sending an email to the Chairs, or at-mentioning the Chairs in the relevant GitHub issue.

The Chairs attempt to resolve the conflict. If this is not possible, the Chairs can opt for one of the following, as they deem appropriate:
*   Find a solution that is mutually acceptable.
*   Choose one behavior based on merit or based on majority implemented behavior in AT.
*   Raise the issue with the ARIA WG.
*   Remove the test.


## GitHub management

Anyone in the community group can and is encouraged to review PRs.

@mfairchild365 and @zcorpan are able to merge reviewed PRs to protected branches.

These labels exist for issues and PRs:

*   `test`
*   `process`
*   `documentation`
*   `test-runner`
*   `test-report`
*   `feedback`
*   `prototype-test-runner`
*   `revisit later`
*   `Agenda+` for adding something to the teleconference agenda
*   `Agenda+` F2F for adding something to the next face-to-face meeting agenda
*   `AT: <product>` for different AT products

The workflow for test plans is managed in [this project board](https://github.com/w3c/aria-at/projects/1), where the “steps” in the columns refer to the process defined in this document for tests.
