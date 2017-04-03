# SDL requirements repository 

* Proposal: [SDL-NNNN](NNNN-filename.md)
* Author: [Olesia Vasylieva](https://github.com/smartdevicelink)
* Status: **Awaiting review**
* Impacted Platforms: [Documentation]

## Introduction

Creation of Requirements repository in GitHub (sdl_requirements) will allow to document SDL requirements with clear scenarios which will improve software development and testing processes.

## Motivation

Currently system requirements are not publicly accessible and are not represented in the form of user stories which causes difficulties in understanding of feature purposes and proper system behavior for OEM manufacturers.

## Proposed solution

Proposed to create Requirements repository (sdl_requirements) which will allow to keep requirements in the form of user stories with detailed feature descriptions, use cases and diagrams. GitHub Requirements repository will improve the collaboration with contributors clarifying system behavior and capabilities. 

Clear feature representation gives more options for mobile developers and can become a helpful tool for integration preparations on OEM platform.

Implementing requirements management may also reduce complexity in integration maintenance

**Creation of Requirements repository will allow to minimize or eliminate the following difficulties:**

- A lot of requests on Slack regarding SDL feature description since currently the list of SDL features is not clear for community
- Placement of existing SDL requirements is not freely available
- Inaccessibility of requiremetns makes feature review and defects analysis complex

The Requirements will be presented according to template provided below:

>_The Requirement must have the following labels:_
>
> **Requirement**
>
> **Priority:** _High, Medium or Low_
>
> ## The name of the feature
>
> ## Description
>
> User story or the high-level idea of described feature
>
> ## Detailed description
>
> Link to GitHub with detailed document in MD format
>
> **Use Case 1:** Name of the Use Case
>
> **Main Flow:**
>
> _Pre-conditions:_
>
> Text of related pre-condition
>
> Note: there could be more than one pre-condition
>
> _Steps:_
>
> Description of steps for user OR sequence
>
> Note: there could be more than one Step
>
> _Expected:_
>
> Description of expected SDL behavior after Steps above
>
> **Alternative flow 1**
>
> Alternative flow for one of the steps above + expected SDL behavior in this flow
>
> _Describes alternative flow to Main flow described above._
>
> **Alternative flow 2**
>
> Step N.N. Alternative flow for one of the steps above + expected SDL behavior in this flow
>
> ## Related Diagrams
>
> Diagrams (for example activity diagram) describing this feature must be attached
>
> ## Links
>
> **Proposal:** GitHub issue Number + summary
>
> **Parent requirement:** Link to parent requirement issue + summary **OR empty**
>
> **Related Technical Tasks**

## Potential downsides

Additional efforts in Requirements management which includes tracking of any changes and updates

## Impact on existing code

Proposed process has no impact on existing code but it evolves requirements management process

## Alternatives considered

- Not to implement any Requirements repository on GitHub and leave SDL requirement inaccessible for community
- Consider having another shared resource for Requirements management
