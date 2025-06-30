# INDEPENDENT REVIEW GUIDELINES

- Version 2.0
- Prepared by: Robert Leach

## PURPOSE

**Quality Assurance**: A primary purpose of the independent review process is to find and fix *defects* among the proposed changes.

**Requirements Completeness**: A primary purpose of the independent review process is to ensure that the proposed changes *meet the requirements* of the change request and the project's general requirements.

**Generally**: Independent reviews are not meant to determine *how* or *whether* to implement a change, but simply *whether* the proposed changes *satisfy the change request*.

## GOALS

**Facillitate Implementation**: The independent review process is meant to facilitate updates to the changed document(s) to ensure that an approved change request is implemented with as few defects as possible.

**Change Control**: The independent review process is a component of curtailing uncontrolled change.  Controlling change leads to a reduction of defects, increases reliability, and contributes to accurate estimates of project costs.

**Teamwork**: The independent review process is intended to establish roles, set expectations, and thereby mitigate or prevent contention by making sure that everyone understands what their role is and what is expected of them.

## SCOPE

These guidelines lay out a process applied to merge requests to a project's repository.  It applies to all members of a development team involved in an independent review.  It does not apply to merge requests originating from outside the development team.

There are 2 types of independent reviews:

- **Design Review**
- **Code Review**

NOTE: Every issue from a review is generally valid, but not every issue is within the scope of the independent review process.  Whether it is within scope is a question of what process is best suited to address it.

For context, this is a list of processes intended to handle the following example problems that could come up during an independent review:

- **Change Request Process**
  - Problems relating to the independent review process, should result in a change request made on the process document itself (e.g. this document).
  - Problems relating to general requirements should result in a change request to change the project's general requirements, such as:
    - An omission in the project's general requirements that changes should be required to adhere to.
    - Differing interpretations of an existing general requirement that lead to a review issue impasse.
    - Differing preferences in design strategy that lead to a review issue impasse.
  - Problems relating to the specific change request whose work is being reviewed should result in a new change request.
    - A reviewer believes that a pull request should not be merged.
    - A bug was found during a code review that was close to, but not a part of, the changes in the PR.
    - A reviewer would prefer the change to be implemented in a different way, even though the current changes meet the requirements.
    - A problem was found in the change request's approved requirements or design.
- **Independent Review Process**
  - A bug was found in the current PR's changes.
  - The changes in a PR don't satisfy a requirement in the change request.
  - A change in the PR is not a part of the requirements in the change request.

How a change is implemented, whether it is a design review or code review, is completely at the discretion of the author, as long as it meets the requirements.  A design *informs* the code implementation, but does not constrain it.  Designs (and design reviews) are worthwhile because the earlier in the process a defect is found, the cheaper it is to fix.  The scope of either review (design or code) is only as it pertains to the requirements of the change request.

The independent review process entails the following topics.

- The identification and description of defects.
- The identification unsatisfied specific and general requirements.
- The identification of changes unrelated to the change request.
- The evaluation of efforts by the author to address identified review issues, and the resolving of those issues.

The following are outside the scope of the independent review process.

- Whether a change request should be implemented.
- Underlying requirements and design (unless reviewing requirements and design).^1
- Over-arching project-level topics.^2
- Debates over differing interpretations of existing general requirements (or best practices).
- Undocumented requirements (specific or general).

If review issues about general requirements lead to an impasse over a review issue, it should result in a change request to clarify the general requirements.

## ROLES & RESPONSIBILITIES

### CM LEADER (CONFIGURATION MANAGEMENT LEADER)

The CM Leader is the guardian of the repository and controls and oversees the processes governing all changes to it.

#### CM LEADER RESPONSIBILITIES

- Creates the processes that manage independent reviews.
- Ensures independent reviews are performed in a timely fashion.

#### CM LEADER LIMITATIONS

None

#### CM LEADER ACTIONS

- Can assign reviewers to a pull request.
- Can resolve review issues when the author and reviewer encounter an impasse or when resolution is deemed to be taking too long.
- Sets independent review deadlines.

### REVIEWER

The reviewer is the bulwark of quality assurance.  They own the review issues they create and decide whether the author's work meets the requirements without defects.

#### REVIEWER RESPONSIBILITIES

It is the reviewer's overall responsibility to work with the author are toward the common goal of satisfying the requirements of merging the implementation of approved change requests with as few defects as possible.

The reviewer's independent review responsibilities are to:

- Complete independent reviews by the deadline set by the CM Leader (or request more time).
- Make a good faith effort to understand the changes being reviewed.
- Find defects in reviewed changes.
  See the DEFECT section under DEFINITIONS for how to identify a defect.
- Describe defects to the author to a degree that enables the author to address them.
- Upon re-review request, respond to the author's attempts to address reported review issues within the time period set by the CM Leader (or request more time).
- Work with the author toward resolving review issues and the common goal of satisfying the approved change request.
- If a defect is outside the scope of the issue for which the work was done, it is the reviewer's responsibility to create new issues to refactor any work merged from the current issue.  Any such issue is subject to the change request approval process.

#### REVIEWER LIMITATIONS

(Despite the GitHub Pull Request interface's Approve/reject mechanism, which applies to pull requests originating from non-team members who are not subject to the change control processes described in this document...) It is not the reviewer's responsibility to reject a change request or prevent the completion of the work on an issue.  The reviewer is not expected to:

- While it helps to understand the context of a change, it is not necessary for a reviewer to understand unchanged code surrounding the changes in a pull request in order to complete a review.  If knowledge about code not involved in the change request is necessary to find defects, the reviewer is expected to create a _question_ review issue.
- While it helps to find bugs, it is not necessary for a reviewer to run the code or run the tests, especially if continuous integration testing is a part of the pull request.
- Perform work on the changed documents in question to resolve defects in the author's code.
- Create new change requests to resolve defects in the author's code (unless the defect relates to different interpretations of existing requirements or undocumented requirements).
- Merge a pull request.

All are solely the author's responsibility.

#### REVIEWER ACTIONS

- Submit a completed independent review (or re-review) of changes, upon review request.
- Create review issues in comments on a pull request.  See the REVIEW ISSUES section for details on the requirements of a review issue.
- Respond to unresolved issues to work toward a mutual resolution.
  - If the answers to any review issue question results in any new perception of unreported defects, create new review issues to report them.
  - Evaluate the author's proposed resolution to every previously reported defect you raised.
    - If the author implemented changes to resolve the defect
      - If the defect no longer exists, resolve the review issue.
      - If the defect still exists, respond with an explanation as to why the issue is not resolved.
      - If the change introduces new defects, create a new review issue as described in step 1.
    - If the author commented on the review issue to suggest that a reported defect is not a defect, re-evaluate and either resolve the review issue or explain why the defect does exist and work with the author to come to a resolution that resolves the underlying approved change request.  Seek help from the CM Leader, if a judgement must be made.
    - If the author created a new change request to resolve the review item at a later date, evaluate the issue and either resolve the review item or respond with an explanation of why handling it in a later issue is an inadequate resolution.
- After submitting a review, wait for the author to request a re-review.
- Request time extensions from the CM Leader if unable to complete a review before the deadline set by the CM Leader.

### AUTHOR

The author is the owner of the implementation/changes and is the only one who is allowed to modify those changes relating to the taken issue.  The author is the only one who can decide *how* to address a review issue.

#### AUTHOR RESPONSIBILITIES

The author's responsibility is as it pertains to addressing defects reported by reviewers.  The author's responsibilities are to:

- Implement the (design or code) to satisfy all requirements in the change request
- Implement the (design or code) to satisfy all general requirements that existed in the project documentation when the work began.
- Implement documentation and tests.
- Follow the design in the issue as much as possible.  The implementation may deviate from the design as long as the work satisfies the requirements in the issue.
- Address every defect reported by reviewers.  (See the RESPONDING TO A REVIEW ISSUE section for details.)
- Work with the reviewer toward a resolution satisfying the completion of the approved change request.
- Request re-review after addressing all reported defects.
- Merge the changes into the repository, once all defects have been resolved to the reviewer's satisfaction.
- Understand all defects reported by reviewers.
- Ensure the reviewer understands the changes.

#### AUTHOR LIMITATIONS

The author is not expected to:

- Implement changes to satisfy new or changed requirements outside the scope of the issue and project requirements that were in place when it was taken.  Such work should be an entirely separate change request, subject to the change request approval process, and to be implemented after the work implementing the current issue is merged.
- Solicit timely responses from reviewers.  This responsibility lies with the CM Leader.  If a reviewer does not respond to good faith attempts to address a reported defect, the defect can be overruled by the CM Leader.

The CM Leader reserves the right to step in on the resolution of any reported defect.

#### AUTHOR ACTIONS

1. Take an approved change request.
2. Work up a design for the change request.
3. Implement code for the change request.
4. Run tests.
5. Request review.
6. Wait for all reviewers to submit their independent reviews.
7. Respond to and address every review issue (See the RESPONDING TO A REVIEW ISSUE section).
8. Go back to step 5 untill all review issues are resolved or request the CM to schedule a review meeting.
9. Request a review meeting to resolve an impasse with a reviewer.

## PROCESS

The following describes the general overall context surrounding the independent review process to contextualize the point when an independent review occurs.

### SOFTWARE ENGINEERING PHASES

1. Planning
   - Software Project Management Plan (SPMP)
   - Software Configuration Management Plan (SCMP)
   - Software Quality Assurance Plan (SQAP)
   - Software Testing Plan (STP)
2. Requirements
3. Design
4. Implementation
5. Testing
6. Quality Assurance  **WE ARE HERE**
7. Maintenance

### CHANGE CONTROL PROCESS (QUALITY ASSURANCE PHASE)

Each step described here is dependent on the steps before it.  The process for each step should be described in the SCMP, e.g. the process by which a change request is approved.  This document does not describe the processes outside the scope of an independent review.

This process starts with a "Change Request" / "Issue".  Each change request is a potential mini-project in and of itself, going through every phase described in SOFTWARE ENGINEERING PHASES above from Requirements through Testing.

1. Change request submitted
2. Change request review process
3. Change request approved^3 (if rejected, stop here)
4. Change request taken by an author (a.k.a. "developer")
5. Author works up a design^4
6. Author requests design review
7. Design review process
8. Design approved (if rejected, return to step 5)
9. Author works on the changes ("Implementation")
10. Author requests independent review
11. Independent review process  **WE ARE HERE**
12. Request a review meeting (if necessary)
13. Schedule a review meeting (if necessary)
14. Review meeting (if necessary)
15. Changes approved (if rejected, return to step 9)
16. Changes merged into the repository

### INDEPENDENT REVIEW PROCESS

An independent review is a line-by-line review of changes to be merged into the project.  At this point, the change request and design have been approved.  The purpose of the independent review is to suss out defects in the implementation and ensure adherence to the requirements.  An implementation does **not** have to follow the design in the change request or follow the suggestions of the reviewers, but the changes do have to meet the specific requirements in the change request and project's documented general requirements.

1. Author requests an independent review (or re-review)
2. Independent review period.^5  The reviewer:
   1. Searches for defects in previously unreviewed changes
   2. Evaluates the author's responses to any of the reviewer's previously created review issues and either:
      - Marks the review issue as resolved
      - Responds to the author's comment or changes to explain why the review issue is still not resolved
   3. Submits completed review to the author
3. Once all requested independent reviews are completed, the author works to address all review issues.
4. If there are unresolved review issues
   1. Author works to address^6 every review issue
   2. If a reviewer and author cannot come to a mutual resolution of any issue, the author may request that the CM schedule a review meeting
   3. Return to step 1
5. Changes approved

## REVIEW ISSUES

### CREATING A REVIEW ISSUE

Review issues are created by reviewers during the independent review period.  There are 3 types of review issues:

- **Defect** (See DEFECT in the DEFINITIONS section.)
  - A _defect_ must be related to a specific reviewed document.
  - A defect should be described to an extent that enables the author to fix it.
  - Reviewers work with the author to agree on a resolution to the review issues.
  - Blocking review issues can only be resolved by the reviewer.
- **Unrelated**
  - An _unrelated_ review issue is when changes are unrelated to the issue requirements, i.e. "feature creep".
    - The change request does not mention them.
    - Feature creep is a source of uncontrolled change.
    - All changes should go through the change request approval process.
  - Exceptions:
    - This excludes any business rules such as applying newly changed coding convention constraints to pre-existing content, e.g. updating docstring formats of code unrelated to the issue, but note that such buisness rules should be documented.
    - Trivial/minor changes, or ancillary unrelated changes should be a judgement call.
- **Question**
  - A _question_ review issue should be asked when a reviewer needs information to be able to find defects (in a subsequent re-review), e.g. "What is the return type of this method call?"

Every review issue must include:

- Document name and line numbers (line numbers may only be omitted when the defect regards file presence, location, or name)
- Severity (Blocking/Non-blocking/Question)
- May optionally include a suggested fix

### RESPONDING TO A REVIEW ISSUE

The author and reviewer work together on each issue to successfully agree on a resolution.  The author and reviewer go back and forth to resolve each review issue.

The author addresses/responds-to all unresolved review issues after all reviewers have submitted their independent reviews (to prevent outstanding review work from reviewing stale code) and the reviewer responds once re-review has been requested.  Both the author and reviewer must respond to every unresolved review issue before re-requesting or submitting a review.  It is a conversation working toward a mutually agreeable resolution.

The author is the owner of the changes and is the only one who can make changes.

The reviewer is the owner of the review issues they create and is the only one that can resolve (blocking) issues.

There are 5 types of proposed responses to review issues:

- **Fixed**
  - The author
    - has accepted the review issue as valid.
    - has implemented changes to fix it.
    - may resolve unblocking fixed issues.
  - The reviewer
    - resolves fixed review issues if they agree the changes fix the issue.
    - explains why a review issue is still not fixed, if they disagree that the author's changes do not fix the issue.
- **Deferred**
  - The author
    - has accepted the review issue as valid.
    - may elect to create a change request(/issue) to implement a fix, and resolve a non-blocking review issue.
    - may elect to create a change request(/issue) to implement a fix to a blocking review issue, but must convince the reviewer why doing so is worthwhile.
    - should comment with a link in a review issue response.
    - may resolve unblocking deffered issues.
  - The reviewer:
    - resolves deferred review issues if they are an acceptable resolution
    - explains why deferral is an insufficient resolution.
- **Invalid**
  - Marking a review issue as _invalid_ is a _suggestion_ by the author that a review issue is _not_ an issue
  - If a review issue marked as invalid is blocking, only the reviewer (or CM) can resolve the issue.
  - Examples of an acceptable reason for marking a review issue as "invalid":
    - The defect is not a defect.  This may be due to a misunderstanding of the changes, the change request, or of the requirements.
    - The defect is an opinion or preference.  E.g. The changes either meet or don't meet the requirements based on interpretation.^7
    - The review issue is based on an unspecified requirement.^7
  - The author:
    - is obliged to understand the review issue.
    - is responsible to make the case to the reviewer that the review issue they raised is not an issue.
    - cannot resolve a blocking invalid issue.
    - may cite any related requirement and explain how the changes satisfy it.
  - The reviewer:
    - may agree and resolve the issue.
    - may reject a suggestion that a review issue is _invalid_, but must make a case to the author as to why it is valid.
    - is obliged to help the author understand the issue.
    - may cite any related requirement and explain how the changes do not satisfy it.
- **Wontfix**
  - The author
    - has accepted the review issue as valid.
    - may mark any review issue as "wontfix", but must make a case to the reviewer if the review issue is blocking.
    - may mark the review issue as resolved if it is non-blocking.
  - The reviewer
    - may resolve a _wontfix_ review issue if they have been convinced that a fix is not worth the effort.
    - may reject a suggestion that a review issue should not be fixed, but must make a case to the author as to why it is a blocking issue.
- **Answer**
  - E.g. The author attempts to answer a reviewer's question.

## DEFINITIONS

### DEFECT (A.K.A. BUG OR FAULT)

There are 2 general types of defects in the context of the independent review process:

- Defects that result in a *review issue*
- Defects that result in a *change request*

A defect resulting in a change request is subject to a separate approval process.  It is outside the scope of the independent review process and involves project components that were not affected by the specific change request.

A defect that should result is a review issue can be any issue involving:

- An unsatisfied
  - Issue requirement (defined in the issue/change request)
  - General requirement (as defined in the SPMP)
- Logic error
- Coding conventions (as defined in the SPMP)
- Missing tests
- Missing documentation
- Performance
- Scalability
- Maintainability, such as
  - Readability
  - Overhead (e.g. added maintenance tasks)
  - Dependence on deprecated, private, or unsupported language features
  - Elevated likelihood of frequent lengthy debug efforts
- Robustness
- Re-usability (re-usability goals can be described in the SPMP's general requirements)

A defect that is outside the scope of an independent review and should result in the creation of a new change request can be any issue involving:

- A difference of opinion or preference that is not codified in the project.
- A problem in any portion of the issue planning the implementation.
  This can be problems with requirements, design, assumptions, limitations, or any other portion of an issue.
  Examples of such problems may include, but are not limited to:
  - An omission in the issue requirements.
  - A logic flaw in the design that excludes an edge case.

### CHANGE REQUEST (A.K.A. A GITHUB "ISSUE")

Not to be confused with a "review issue", a "change request" is a request to make a change to the repository or to any project component.  It can describe a bug or feature pertaining to code, documentation, process, plan, or any other project component.

An change request describes:

- Reasoning behind the change request that can either be:
  - A problem/bug
  - A description of the inspiration behind a feature request
- Support for the change, e.g.
  - How to reproduce the problem
  - How to observe the inspirational element
- A suggested implementation to fix the problem or implement the feature

A change request is subject to approval.  Once approved, it is available to be taken for design work, then coding/implementation.  A developer can take an approved change request and author a design.  A change request is a mini project in and of itself.  Authoring a "design" for a change request is shorthand for that mini project and includes:

- Requirements
- Limitations
- Assumptions
- Affected Components
- Interface change description (from a user perspective)
- Design (free-form pseudocode)
- Tests

Once the plans for each of these categories is filled in, the design is subject to review, to be approved for implementation.

### MERGE REQUEST (A.K.A. A GITHUB "PULL REQUEST")

A merge request is a request to incorporate added, removed, or changed documents into the repository.  A merge request comes about after an issue has been accepted for work and undergone successful design review.  A merge request is followed by a review request once the changes pass continuous integration tests.

## FOOTNOTES

1. _Unless the changes being reviewed are requirements or design, all planning leading up to the implementation of a change request are beyond the scope of an independent review.  If any such defect arises during an independent review, the parties broaching the issue will be directed by the CM leader to create an issue to be addressed as a change request._
2. _Defects involving project-level topics such as project planning, principles, conventions, general requirements, etc. are beyond the scope of an independent review._
3. _The change request approval process should involve prioritization and estimation of cost that govern when an issue is available to be taken up by a developer._
4. _For the purposes of succinctness, "design" encompasses requirements, limitations, assumptions, affected components, etc._
5. _Reviewers complete an independent review to ensure that the changes are free of defects.  Defects can include typos, logic errors, failures to satisfy: specific requirements from the change request or general project requirements.  See the DEFECT heading in the DEFINITIONS section._
6. _Addressing an issue can involve new changes, responding to reviewer questions, suggesting an issue is invalid (with an explanation), or creating a separate change request to implement a fix._
7. _If a review issue pertains to: requirements that are subjective or open to interpretation, subjective opinion, or are regarding unspecified requirements, an independent review is not the right forum to hash out such an issue.  The review process should proceed without delay.  The reviewer's recourse is to create a change request to address such an issue by changing the general requirements or any other component of the project._

## REFERENCES

1. `document_review_form.txt` version 1.3 _from the TreeView3 project_
2. `review_meeting_guidelines.txt` version 1.3 _from the TreeView3 project_
3. `SCMP_TreeView3.doc` 8/14/2015 _from the TreeView3 project_
