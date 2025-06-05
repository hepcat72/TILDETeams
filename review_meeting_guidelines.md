# Document Review Meeting Guidelines
- Version 2.0
- Prepared by: Robert Leach

## PURPOSE

**Understanding Review Issues**: The primary purpose of the document review meeting is to ensure that the document author understands the defects found by reviewers, pertaining to the reviewed document(s).

**Understanding the documents**: A secondary purpose of the document review meeting is to ensure that the reviewer understands the document content enough to be able to identify defects in the document.

**Generally**: The general purpose of the review meeting is not to determine *how* to resolve an issue, but rather to define *what* an issue is.

## GOAL

**Address the Issue**: The primary reason for having a document review meeting is to facilitate the document review process toward the goal of merging document changes that fully address an approved issue/change-request.

**Teamwork**: A document review process in general, is intended to establish roles, set expectations, and thereby mitigate or prevent contention by everyone understanding what their role is and what is expected of them.

A document review meeting is useful when the review process has stalled.

**Generally**: The overarching goal is software quality assurance.

## SCOPE

A document review meeting entails the following topics.

- The understanding of perceived defects in the document(s).
- The understanding of suggested defect fixes (if any).
- The understanding of the content of the document(s).

The following are outside the scope of a document review meeting.

- Underlying requirements and design.^1
- Over-arching project-level topics.^2
- Debates over whether a perceived defect is a true defect.
- Discussions over how to solve a defect.

Resolutions of review issues are handled after a meeting on an individual basis using the review and re-review iterative process.

## ROLES & RESPONSIBILITIES

### CM LEADER (CONFIGURATION MANAGEMENT LEADER)

#### CM LEADER RESPONSIBILITIES

- Ensures reviews are performed in a timely fashion.
- Ensure the author has sufficient time to review issues before the meeting.
- Ensure timely implementations of approved issues/change requests.
- Manages the scope and pace of document review meetings.

#### CM LEADER LIMITATIONS

None

#### CM LEADER ACTIONS

- The CM Leader calls, schedules, and runs the meeting.
- The CM Leader manages the scope and pace of a document review meeting using the following actions:
  - Declare a topic/discussion _Beyond Meeting Scope_^3
  - Declare a topic/discussion _Beyond Document Scope_^4
  - Change or table discussion topics in the interests of _Time_^5
- Decides on review issue resolution when the author and reviewer encounter an impasse or when resolution is deemed to be taking too long.
- Can assign reviewers to a pull request.
- The CM Leader ends the meeting once all major and higher severity issues have been communicated and understood.

### REVIEWER

#### REVIEWER RESPONSIBILITIES

The reviewer is the bulwark of quality assurance.  It is the reviewer's overall responsibility to see that the issue/approved change request is implemented and merged with as few defects as possible.  The reviewer and author are thus working toward a common goal.

The reviewer's responsibility in the context of a document review meeting is as it pertains to identifying, reporting, and explaining defects.  The reviewer's meeting responsibilities are to:

- Before a document review meeting
  - Request time extensions if a review cannot be completed in a timely fashion.
  - Find defects in the reviewed documents.
    See the DEFECT section under DEFINITIONS for how to identify a defect.
- During a document review meeting
  - Communicate defects to the author.
  - Ensure the author fully understands every reported defect.
  - Ensure they understand the document content.
- After a document review meeting
  - Respond to the author's attempts to resolve reported defects in a timely fashion.
  - Work with the author toward a resolution satisfying the closing of the issue the document(s) were intended to implement.
  - Request time extensions if a re-review cannot be completed in a timely fashion.
  - If a defect is outside the scope of the issue for which the work was done, it is the reviewer's responsibility to create new issues to refactor any work merged from the current issue.  Any such issue is subject to the change request approval process.

#### REVIEWER LIMITATIONS

It is not the reviewer's responsibility to reject an issue/change request or prevent the completion of the work on an issue.  However, the reviewer is not expected to:

- Perform work on the documents in question to resolve defects in the author's code.
- Create new change requests to resolve defects in the author's code.

Both are solely the author's responsibility.

#### REVIEWER ACTIONS

1. Prior to meeting, the reviewer completes a review of the document(s).  See the REVIEW ISSUE section in the DEFINITIONS section to see what goes in a review issue.
2. In the meeting, a reviewer has the following responsibilities:
   - Describe each defect they found in the documents.
   - Ensure the author understands the defect.
   - Ask for clarifications of document content, when unclear.
3. After the meeting, the reviewer has the following responsibilities:
   1. Resolve any defects previously raised if what you learned in the meeting served to prove that the reported defect was invalid or outside the document scope.
   2. Wait for the author to request a re-review.
   3. Complete a re-review
      - If the answers to any of your questions in the meeting resulted in any new perception of unreported defects, create new review issues to report them.
      - Evaluate the author's proposed resolution to every previously reported defect you raised.  If the developer:
        - Implemented changes to resolve the defect
          - If the defect no longer exists, resolve the review issue.
          - If the defect still exists, respond with an explanation as to why the issue is not resolved.
          - If the change introduces new defects, create a new review issue as described in step 1.
        - Commented on the review issue with a claim that the defect reported is invalid, re-evaluate and either resolve the review issue or work with the author to come to a resolution that resolves the underlying approved issue.  Seek help from the CM Leader, if a judgement must be made.
        - Created a new issue to resolve the review item at a later date, evaluate the issue and either resolve the review item or respond with an explanation of why handling it in a later issue is an inadequate resolution.

### AUTHOR

#### AUTHOR RESPONSIBILITIES

The author is the owner of the implementation changes and is the only one who is allowed to modify those changes relating to the taken issue.  The author's responsibility is as it pertains to addressing defects reported by reviewers.  The author's responsibilities are to:

- Before requesting review
  - Implement the issue design to satisfy all issue and general requirements, adhering to all project guidelines as they existed when the work began.  Implementation includes documentation and tests.
  - Follow the design in the issue as much as possible.  The implementation may deviate from the design as long as the work satisfies the requirements in the issue.
  - Adhere to all general project requirements, including coding conventions.
- During a document review meeting
  - Understand all defects reported by reviewers.
  - Ensure the reviewer understands the content of the document(s).
- After a document review meeting
  - Address and respond to every defect reported by reviewers.
  - Work with the reviewer toward a resolution satisfying the closing of the issue.
  - Request re-review after addressing all reported defects.
  - Merge the documents into the repository, once all defects have been resolved to the reviewer's satisfaction.

#### AUTHOR LIMITATIONS

The author is not expected to:

- Implement changes to satisfy new or changed requirements outside the scope of the issue and project requirements that were in place when it was taken.  Such work should be an entirely separate issue, to be applied after the work implementing the current issue is merged.
- Solicit timely responses from reviewers.  This responsibility lies with the CM Leader.  If a reviewer does not respond to good faith attempts to address a reported defect, the defect will be default-ruled as invalid.

The CM Leader reserves the right to step in on the resolution of any reported defect.

#### AUTHOR ACTIONS

1. Before the meeting, the author takes the following actions:
   - Take an approved issue.
   - Implement the issue.
   - Run tests.
   - Request review.
2. In the meeting, the author takes the following actions:
   - Answer reviewer questions about the content of the document(s).
   - Ask for clarifications about reported defects, if unclear.
3. After the meeting, the author takes the following actions:
   1. Address reported defects in one of the following 4 ways.
      - Flag a reported defect as invalid.
        - Respond to the reviewer's defect report to explain why the reported defect is not a defect.
        - Optionally, implement a test to demonstrate that the defect does not exist.
      - Implement changes to eliminate the reported defect.
      - Create an issue to address the defect after merge.
        - Respond to the reviewer's defect report to ask the reviewer to inspect the issue and see if it is an acceptable resolution to the defect.
      - Report the issue as tolerable, given the issue severity and time constraints.
        - Ask the reviewer if they would like an issue to be created or if they agree that the defect is tolerable.
   2. After addressing all defects, request a re-review, and wait for the reviewer to re-review the document(s).
   3. Repeat this process to resolve the existing and any new defects reported by the reviewer until all reach a mutual resolution.  Seek help from the CM Leader, if a judgement to resolve a reported defect must be made.

## DEFINITIONS

### DEFECT (A.K.A. BUG OR FAULT)

There are 2 general types of defects in the context of a document review process: those that result in the creation of a document review issue and those that result in the creation of a change request (a new "issue" that is subject to a separate approval process) that is outside the scope of the document review process.

A defect that should result is a document review issue can be any issue involving:

- An unsatisfied
  - Issue requirement
  - General requirement
- Coding conventions
- Missing tests
- Missing documentation
- Readability
- Performance
- Scalability
- Maintainability, such as
  - Unnecessary overhead tasks
  - Dependence on deprecated, private, or unsupported language features
  - Elevated likelihood of frequent lengthy debug efforts
- Robustness

A defect that is outside the scope of a document review and should result in the creation of a new change request can be any issue involving:

- A difference of opinion or preference that is not codified in the project.
- A problem in any portion of the issue planning the implementation.
  This can be problems with requirements, design, assumptions, limitations, or any other portion of an issue.
  Examples of such problems may include, but are not limited to:
  - An omission in the issue requirements.
  - A logic flaw in the design that excludes an edge case.

### ISSUE (A.K.A. CHANGE REQUEST)

Not to be confused with a "review issue", an "issue" / "change request" is a request to make a change to the repository or to any documented project component.  It can describe a bug or feature pertaining to code, documentation, process, plan, or any other project component.

An issue describes:

- Reasoning behind the change request that can either be:
  - A problem/bug
  - A description of the inspiration behind a feature request
- Support for the change, e.g.
  - How to reproduce the problem
  - How to observe the inspirational element
- A suggested implementation to fix the problem or implement the feature

An issue is subject to approval for design work through a change request procedure.  Once approved for design, the issue is taken by an author and the issue owner section is fleshed with:

- Requirements
- Limitations
- Assumptions
- Affected Components
- Interface change description (from a user perspective)
- Design (free-form pseudocode)
- Tests

Once filled in, the issue owner section is subject to review, to be approved for implementation.

### REVIEW ISSUE

A report of a defect in a reviewed document by a reviewer.  See the DEFECT section under DEFINITIONS for details on how to identify a defect.

A review issue must meet the following requirements:

- Must identify a defect related to a specific reviewed document or documents.  As such, each defect must include:
  - Location and name of the document relating to the defect.
  - Document line numbers (line numbers may only be omitted when the defect regards file presence, location, or name)
- Must have a severity (Blocking/Non-blocking/Question)
- May optionally include a suggested fix

### MERGE REQUEST (A.K.A. PULL REQUEST)

A merge request is a request to incorporate new or changed documents into the repository.  A merge request comes about after an issue has been accepted for work and undergone successful design review.  A merge request is followed by a review request once the changes pass continuous integration tests.

## FOOTNOTES

1. _Unless the document(s) being reviewed are requirements or design documents, all planning leading up to the implementation of a document are beyond the scope of a document review.  If any such defect arises during a document review meeting, the parties broaching the issue will be directed by the CM leader to create an issue to be addressed as a change request._
2. _Defects involving project-level topics such as project planning, principles, conventions, general requirements, etc. are beyond the scope of a document review meeting._
3. _If interactions between meeting members strays beyond the reviewer conveying defects found during their review, or a clarification of document content, the CM Leader may declare the topic "beyond meeting scope" and either direct the reviewer to advance to the next issue or re-orient the discussion back toward the identification of the reviewer's interpretation of defects and ensure that the defect pointed out is understood by the developer._
4. _If the CM Leader determines that the discussion of an issue has gone beyond the scope of the document, the CM Leader may declare the topic "beyond document scope" and either direct the reviewer to advance to the next issue or re-orient the discussion back toward the identification of the reviewer's interpretation of defects and ensure that the defect pointed out is understood by the developer._
5. _If the CM Leader determines that a discussion, while productive, may be more effectively/efficiently addressed outside of the meeting, he/she may suggest that the topic be discussed after the meeting and direct the reviewer to advance to the next issue._

## REFERENCES

1. `document_review_form.txt` version 1.3 _from the TreeView3 project_
2. `review_meeting_guidelines.txt` version 1.3 _from the TreeView3 project_
3. `SCMP_TreeView3.doc` 8/14/2015 _from the TreeView3 project_
