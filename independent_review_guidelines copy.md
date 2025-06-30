# Document Review Process Guidelines

- Version 2.0
- Prepared by: Robert Leach

## GOALS

**Quality Assurance**: The primary purpose of the document review process is quality assurance: assuring that all changes to the repository are as free from defects as possible.

**Requirements Satisfaction**: The document review process is not meant to determine *how* to resolve a change request, but rather that the proposed changes *meet the requirements of the change request*.

**Implement the Change Request**: The document review process is meant to facilitate updates to the document(s) to ensure that the change request is implemented.

**Teamwork**: A document review process is intended to establish roles, set expectations, and thereby mitigate or prevent contention by making sure that everyone understands what their role is and what is expected of them.

**Controlling Change**: The document review process is a component of curtailing uncontrolled change.  Uncontrolled change leads to defects and unpredictability.

## SCOPE

This document lays out a Quality Assurance change control process applied to merge requests to a project's repository.  It applies to all members of a development team involved in the project.  It does not apply to merge/pull requests originating outside the development team.

The document review process entails the following topics.

- The identification and resolution of defects.
- The identification and resolution of unsatisfied specific requirements in the issue and general requirements.
- The limitation of changes to those described in the change request.

The following are outside the scope of the document review process.

- Underlying requirements and design (unless reviewing requirements and design).^1
- Over-arching project-level topics.^2
- Debates over differing interpretations of documented general requirements (or best practices).
- Undocumented requirements (specific or general).

If review issues about general requirements lead to an impasse over a review issue, it should result in a change request to clarify the general requirements.

NOTE: Every issue from a review is generally valid.  Whether it is within the scope of the document review process is just a question of what alternate process may be better applied to that issue, such as a change request/approval or design review.

## ROLES & RESPONSIBILITIES

### CM LEADER (CONFIGURATION MANAGEMENT LEADER)

The CM Leader is the guardian of the repository and controls and oversees the processes governing all changes to it.

#### CM LEADER RESPONSIBILITIES

- Creates the SCMP (Configuration Management Plan) that describes the processes of change control.
- Ensures reviews are performed in a timely fashion.
- Ensure the author has sufficient time to review issues before the meeting.
- Ensure timely implementations of approved issues/change requests.
- Manages the scope and pace of document review meetings.

#### CM LEADER LIMITATIONS

None

#### CM LEADER ACTIONS

- The CM Leader calls, schedules, and runs document review meetings.
  - The CM Leader manages the scope and pace of a document review meeting using the following actions:
    - Declare a topic/discussion _Beyond Meeting Scope_^3
    - Declare a topic/discussion _Beyond Document Scope_^4
    - Change or table discussion topics in the interests of _Time_^5
  - The CM Leader ends a document review meeting once all major and higher severity issues have been communicated and understood.
- Decides on review issue resolution when the author and reviewer encounter an impasse or when resolution is deemed to be taking too long.
- Can assign reviewers to a pull request.

### REVIEWER

The reviewer is the bulwark of quality assurance.  They own the review issues they create and decide whether the author's work meets the requirements without defects.

#### REVIEWER RESPONSIBILITIES

It is the reviewer's overall responsibility to work with the author are toward the common goal of satisfying the requirements of merging the implementation of approved change requests with as few defects as possible.

The reviewer's responsibility in the context of a document review meeting is as it pertains to identifying, reporting, and explaining defects.  The reviewer's meeting responsibilities are to:

- During a document review meeting
  - Communicate defects to the author.
  - Ensure the author fully understands every reported defect.
- During an independent document review
  - Complete reviews and respond to the author's attempts to resolve reported defects in a timely fashion (or request more time).
  - Make a good faith effort to understand the document content being reviewed.
  - Find defects in reviewed documents.
    See the DEFECT section under DEFINITIONS for how to identify a defect.
  - Describe defects to the author to a degree that enables the author to address them.
  - Work with the author toward resolving review issues and the common goal of satisfying the approved change request.
  - If a defect is outside the scope of the issue for which the work was done, it is the reviewer's responsibility to create new issues to refactor any work merged from the current issue.  Any such issue is subject to the change request approval process.

#### REVIEWER LIMITATIONS

It is not the reviewer's responsibility to reject a change request or prevent the completion of the work on an issue.  However, the reviewer is not expected to:

- Perform work on the documents in question to resolve defects in the author's code.
- Create new change requests to resolve defects in the author's code (unless the change is unrelated to the requirements).

Both are solely the author's responsibility.

#### REVIEWER ACTIONS

1. Completes an independent review (or re-review) of document(s) in a merge request, upon review request.  See the REVIEW ISSUES section for details.
   1. Resolve any review issues previously raised if the authors actions adequately address the issue.
   2. Respond to unresolved issues to work toward a mutual resolution.
      - If the answers to any of your questions result in any new perception of unreported defects, create new review issues to report them.
      - Evaluate the author's proposed resolution to every previously reported defect you raised.  If the developer:
        - Implemented changes to resolve the defect
          - If the defect no longer exists, resolve the review issue.
          - If the defect still exists, respond with an explanation as to why the issue is not resolved.
          - If the change introduces new defects, create a new review issue as described in step 1.
        - Commented on the review issue with a claim that the defect reported is invalid, re-evaluate and either resolve the review issue or work with the author to come to a resolution that resolves the underlying approved issue.  Seek help from the CM Leader, if a judgement must be made.
        - Created a new issue to resolve the review item at a later date, evaluate the issue and either resolve the review item or respond with an explanation of why handling it in a later issue is an inadequate resolution.
   3. After submitting a review, wait for the author to request a re-review.
2. Requests time extensions from the CM Leader if they cannot complete a review before the due date in the PR description.
3. In a document review meeting meeting, a reviewer takes the following actions:
   - Describe each defect they found in the documents.
   - Explain review issues that the author asks about.
   - Ask for clarifications of document content, when unclear.

### AUTHOR

The author is the owner of the implementation/changes and is the only one who is allowed to modify those changes relating to the taken issue.  The author is the only one who can decide how to address a review issue.

#### AUTHOR RESPONSIBILITIES

The author's responsibility is as it pertains to addressing defects reported by reviewers.  The author's responsibilities are to:

- Before requesting review
  - Implement the issue design to satisfy all issue and general requirements, adhering to all project guidelines as they existed when the work began.  Implementation includes documentation and tests.
  - Follow the design in the issue as much as possible.  The implementation may deviate from the design as long as the work satisfies the requirements in the issue.
  - Adhere to all general project requirements, including coding conventions.
- During the independent review process
  - Address every defect reported by reviewers.
  - Work with the reviewer toward a resolution satisfying the closing of the issue.
  - Request re-review after addressing all reported defects.
  - Merge the documents into the repository, once all defects have been resolved to the reviewer's satisfaction.
- During a document review meeting
  - Understand all defects reported by reviewers.
  - Ensure the reviewer understands the content of the document(s).

#### AUTHOR LIMITATIONS

The author is not expected to:

- Implement changes to satisfy new or changed requirements outside the scope of the issue and project requirements that were in place when it was taken.  Such work should be an entirely separate change request, subject to the change request approval process, and to be implemented after the work implementing the current issue is merged.
- Solicit timely responses from reviewers.  This responsibility lies with the CM Leader.  If a reviewer does not respond to good faith attempts to address a reported defect, the defect can be overruled by the CM Leader.

The CM Leader reserves the right to step in on the resolution of any reported defect.

#### AUTHOR ACTIONS

1. Take an approved issue.
2. Work up a design for the issue.
3. Implement the issue.
4. Run tests.
5. Request review.
6. Respond to review issues (See the RESPONDING TO A REVIEW ISSUE section).
7. Go back to step 5 untill all review issues are resolved or request the CM to schedule a document review meeting.
8. During a document review meeting, the author takes the following actions:
   - Answer reviewer questions about the content of the document(s).
   - Ask for clarifications about reported defects, if unclear.
9. After a document review meeting, the author takes the following actions:
   1. Address reported defects.  See the RESPONDING TO A REVIEW ISSUE section.
   2. After addressing all defects, request a re-review, and wait for the reviewer to re-review the document(s).
   3. Repeat this process to resolve the existing and any new defects reported by the reviewer until all reach a mutual resolution.  Seek help from the CM Leader, if a judgement to resolve a reported defect must be made.

## PROCESS

The following describes the general overall context surrounding a code review to contextualize the point when a document review meeting occurs.

### SOFTWARE ENGINEERING PHASES

1. Planning
   - Software Project Management Plan (SPMP)
   - Software Configuration Management Plan (SCMP)  **WE ARE HERE**
   - Software Quality Assurance Plan (SQAP)
   - Software Testing Plan (STP)
2. Requirements
3. Design
4. Implementation
5. Testing
6. Maintenance

### CHANGE CONTROL PROCESS

Each step described here is dependent on the steps before it.  The process for each step should be described in the SCMP, e.g. the process by which a change request is approved.  This document does not describe the processes outside the scope of document review.

This process starts with a "Change Request" / "Issue".  Each change request is a potential mini-project in and of itself, going through every phase described in SOFTWARE ENGINEERING PHASES above from Requirements through Testing.  The steps pertaining to document review are in bold.

1. Change request submitted
2. Change request review process
3. Change request approved^6 (if rejected, stop here)
4. Change request taken by an author (a.k.a. "developer")
5. Author works on the document design^7
6. Author requests design review
7. Design review process
8. Design approved (if rejected, return to step 5)
9. **Author works on the document ("Implementation")**
10. **Author requests document review**
11. **Independent document review process**  (See the INDEPENDENT DOCUMENT REVIEW PROCESS section)
12. **Document approved (if rejected, return to step 9)**
13. Document merged into the repository

### INDEPENDENT DOCUMENT REVIEW PROCESS

A document review is a line-by-line review of changes to be merged into the project.  At this point, the change request and document design have been approved and the purpose of the document review is to suss out defects in the implementation and adherence to the requirements.  The document implementation does **not** have to follow the design or follow the suggestions in the issue owner section, but it does have to meet the specific requirements in the issue and general requirements in the SPMP.

1. Author requests document (re-)review
2. Independent review period.^8  The reviewer:
   1. Searches for defects in previously unreviewed document changes
   2. Evaluates the author's responses to any of the reviewer's previously created review issues and either:
      - Marks the review issue as resolved
      - Responds to the author's comment or changes to explain why the review issue is still not resolved
   3. Submits completed review to the author
3. All requested independent reviews are completed
4. If there are unresolved review issues
   1. Author works to address^9 every review issue
   2. If a reviewer and author cannot come to a mutual resolution of any issue, the author may request that the CM schedule a document review meeting
   3. Return to step 1
5. Document approved

### DOCUMENT REVIEW MEETING

A document review _meeting_ is only necessary if 1 or more reviewers do not fully understand the document changes, if the author does not fully understand an issue raised by a reviewer, or if the CM deems it necessary.

#### DOCUMENT REVIEW MEETING GOALS

**Understanding Review Issues**: The primary goal of the document review meeting is to ensure that the document author understands the defects found by reviewers, pertaining to the reviewed document(s).

**Understanding the documents**: A secondary goal of the document review meeting is to ensure that the reviewer understands the document content enough to be able to identify defects in the document.

**Generally**: The general goal of the review meeting is not to determine *how* to resolve an issue, but rather to define *what* an issue is.

A document review meeting is useful when the review process has stalled.

#### DOCUMENT REVIEW MEETING SCOPE

A document review meeting entails the following topics.

- The understanding of perceived defects in the document(s).
- The understanding of suggested defect fixes (if any).
- The understanding of the content of the document(s).

The following are outside the scope of a document review.

- Underlying requirements and design.^1
- Over-arching project-level topics.^2
- Debates over whether a perceived defect is a true defect.
- Discussions over how to solve a defect.

#### DOCUMENT REVIEW MEETING PROCESS

An author or reviewer can request the CM to schedule a document review meeting if they are unclear or confused about a review issue or a document being reviewed and believe that the pull request interface is inadequate to the task of communicating the details.  The CM leader may schedule a document review meeting at their discretion.  When that meeting takes place, it will proceed with the following process.

1. The CM leader starts the document review and designated each reviewer, one by one to go through their unresolved issues.
2. For each reviewer issue:
   1. The reviewer:
      - Describes a review issue issue or
      - Asks a question to clear up confusion they have about a document
      - Responds to any question the author posed about confusion they have about the issue
   2. The author:
      - May indicate that they understand the issue
      - May ask a question to clear up confusion about the review issue
      - Responds to any question the reviewer posed about confusion they have about the document
   3. The CM leader may interject at any point to:
      - Declare a topic/discussion _Beyond Meeting Scope_^3
      - Declare a topic/discussion _Beyond Document Scope_^4
      - Change or table discussion topics in the interests of _Time_^5
      - End the meeting
3. Once all review issues have been covered, the CM ends the meeting

After the meeting, the review/re-review process continues, but the CM may take action to resolve any review issue.

## REVIEW ISSUES

### CREATING A REVIEW ISSUE

Review issues are created by reviewers during the independent review period.  There are 3 types of review issues:

- **Defect** (See DEFECT in the DEFINITIONS section.)
  - A _defect_ review issue must be related to a specific reviewed document.
  - Reviewers work with the author to agree on a resolution to the review issues.
  - Blocking review issues can only be resolved by the reviewer.
- **Unrelated**
  - An _unrelated_ review issue is when changes in the document are unrelated to the issue requirements.
    - I.e. The indicated changes are "feature creep".
    - The change request does not mention them.
    - Feature creep is a source of uncontrolled change.  All changes should go through the change request approval process.
  - Note that this excludes any business rules such as applying newly changed coding convention constraints to pre-existing document content, e.g. updating docstring formats of code unrelated to the issue, but note that such buisness rules should be documented.
  - Trivial/minor changes, or ancillary unrelated changes should be a judgement call.
- **Question**
  - A _question_ review issue should be asked when a reviewer needs information to be able to find defects (in a subsequent re-review), e.g. "What is the return type of this method call?"

Every review issue must include:

- Document name and line numbers (line numbers may only be omitted when the defect regards file presence, location, or name)
- Severity (Blocking/Non-blocking/Question)
- May optionally include a suggested fix

### RESPONDING TO A REVIEW ISSUE

The author and reviewer work together on each issue to successfully agree on a resolution.  The author and reviewer go back and forth to resolve each review issue.  The author addresses/responds-to all unresolved review issues after all reviewers have submitted their independent reviews (to prevent outstanding review work from reviewing stale code) and the reviewer responds once re-review has been requested.  Both the author and reviewer must respond to every unresolved review issue before re-requesting or submitting a review.  It is a conversation working toward a mutually agreeable resolution.

The author is the owner of the changes and is the only one who can make changes.

The reviewer is the owner of the review issues they create and is the only one that can resolve (blocking) issues.

There are 5 types of proposed responses to review issues:

- **Fixed**
  - The author has accepted the review issue as valid.
  - The author implements changes to the document to fix it.
  - The author's changes are subject to re-review by the reviewer upon subsequent re-review request.
  - The reviewer is responsible for resolving the review issue if they agree the changes fix the issue.
  - The reviewer is responsible for explain why a review issue is still not fixed, if they disagree that the author's changes do not fix the issue.
- **Deferred**
  - The author
    - has accepted the review issue as valid.
    - may elect to create a change request(/issue) to implement a fix, and resolve a non-blocking review issue.
    - may elect to create a change request(/issue) to implement a fix to a blocking review issue, but must convince the reviewer why doing so is worthwhile.
  - The reviewer:
    - is responsible to determine whether a deferral is an acceptable resolution and either resolve the review issue or explain why deferral is an insufficient resolution.
  - If a change request was created, it should be linked in a review issue response before resolving.
- **Invalid**
  - Marking a review issue as _invalid_ is a _suggestion_ by the author that a review issue is _not_ an issue and if it is blocking, only the reviewer (or CM) can resolve the issue.
  - Examples of an acceptable reason for marking a review issue as "invalid":
    - The defect is not a defect.  This may be due to a misunderstanding of the document, the issue, or of the requirements (specific or general).
    - The defect is an opinion or preference.  E.g. The document meets or doesn't meet the requirements, based on interpretation.^10
    - The review issue is based on an unspecified requirement.^10
  - The author:
    - is obliged to understand the review issue.
    - is responsible to make the case to the reviewer that the review issue they raised is not an issue.
    - cannot resolve a blocking invalid issue.
    - may cite any related requirement and explain how the document satisfies it.
  - The reviewer:
    - may agree and resolve the issue or disagree and further explain.  (The CM can also resolve a blocking invalid issue.)
    - is obliged to help the author understand the issue.
    - may cite any related requirement and explain how the document does not satisfy it.
- **Wontfix**
  - The author
    - has accepted the review issue as valid.
    - may mark any review issue as "wontfix", but must make a case to the reviewer if the review issue is blocking.
    - may mark the review issue as resolved if it is non-blocking.
  - The reviewer
    - may resolve a _wontfix_ review issue if they have been convinced.
    - may reject an _invalid_ review issue marking, but must make a case to the author as to why the case they made is insufficient to resolve the review issue.
- **Answer**
  - E.g. The author attempts to answer a reviewer's question.

## DEFINITIONS

### DEFECT (A.K.A. BUG OR FAULT)

There are 2 general types of defects in the context of a document review process:

- Defects that result in the creation of a document review issue
- Defects that result in the creation of a change request (a new "issue" that is subject to a separate approval process) that is outside the scope of the document review process

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

A defect that is outside the scope of a document review and should result in the creation of a new change request can be any issue involving:

- A difference of opinion or preference that is not codified in the project.
- A problem in any portion of the issue planning the implementation.
  This can be problems with requirements, design, assumptions, limitations, or any other portion of an issue.
  Examples of such problems may include, but are not limited to:
  - An omission in the issue requirements.
  - A logic flaw in the design that excludes an edge case.

### CHANGE REQUEST (A.K.A. A GITHUB "ISSUE")

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

### MERGE REQUEST (A.K.A. A GITHUB "PULL REQUEST")

A merge request is a request to incorporate added, removed, or changed documents into the repository.  A merge request comes about after an issue has been accepted for work and undergone successful design review.  A merge request is followed by a review request once the changes pass continuous integration tests.

## FOOTNOTES

1. _Unless the document(s) being reviewed are requirements or design documents, all planning leading up to the implementation of a document are beyond the scope of a document review.  If any such defect arises during a document review meeting, the parties broaching the issue will be directed by the CM leader to create an issue to be addressed as a change request._
2. _Defects involving project-level topics such as project planning, principles, conventions, general requirements, etc. are beyond the scope of a document review meeting._
3. _If interactions between meeting members strays beyond the reviewer conveying defects found during their review, or a clarification of document content, the CM Leader may declare the topic "beyond meeting scope" and either direct the reviewer to advance to the next issue or re-orient the discussion back toward the identification of the reviewer's interpretation of defects and ensure that the defect pointed out is understood by the developer._
4. _If the CM Leader determines that the discussion of an issue has gone beyond the scope of the document, the CM Leader may declare the topic "beyond document scope" and either direct the reviewer to advance to the next issue or re-orient the discussion back toward the identification of the reviewer's interpretation of defects and ensure that the defect pointed out is understood by the developer._
5. _If the CM Leader determines that a discussion, while productive, may be more effectively/efficiently addressed outside of the meeting, he/she may suggest that the topic be discussed after the meeting and direct the reviewer to advance to the next issue._
6. _The change request approval process should involve prioritization and estimation of cost that govern when an issue is available to be taken up by a developer._
7. _For the purposes of succinctness, "design" encompasses requirements, limitations, assumptions, affected components, etc.  I.e. everything in the "Issue Owner" section of the Issue template._
8. _Reviewers complete an independent review to ensure that the document changes are free of defects.  Defects can include typos, logic errors, failures to satisfy: specific requirements from the change request or general requirements in the SPMP, etc.  See the DEFECT heading in the DEFINITIONS section._
9. _Addressing an issue can involve document changes, responding to reviewer questions, suggesting an issue as invalid (with an explanation), or creating a separate change request to implement a fix._
10. _If a review issue pertains to: requirements that are subjective or open to interpretation, subjective opinion, or are regarding unspecified requirements, a document review is not the right forum to hash out such an issue.  The review process should proceed without delay.  The reviewer's recourse is to create a change request to address such an issue by changing the general requirements or change the documents with new requirements specified._

## REFERENCES

1. `document_review_form.txt` version 1.3 _from the TreeView3 project_
2. `review_meeting_guidelines.txt` version 1.3 _from the TreeView3 project_
3. `SCMP_TreeView3.doc` 8/14/2015 _from the TreeView3 project_
