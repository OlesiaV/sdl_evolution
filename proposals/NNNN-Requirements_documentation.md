# SDL requirements repository 

* Proposal: [SDL-NNNN](NNNN-filename.md)
* Author: [Olesia Vasylieva](https://github.com/smartdevicelink)
* Status: **Awaiting review**
* Impacted Platforms: []

## Introduction

Creation of requirements repository in GitHub will allow to document SDL requirements with clear scenarios which will improve software development and testing processes.

## Motivation

Currently system requirements are not publicly available and are not represented in the form of user stories which causes difficulties in understanding of feature purposes and proper system behavior for OEM manufacturers.

## Proposed solution

Proposed to create Requirements repository which will allow to keep requirements in the form of user stories with detailed feature descriptions, use cases and diagrams.

The requirements will be presented in the form according to template provided below:

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

N/A

## Impact on existing code

N/A

## Alternatives considered

N/A
