# SDL requirements repository 

* Proposal: [SDL-NNNN](NNNN-filename.md)
* Author: [Olesia Vasylieva](https://github.com/smartdevicelink)
* Status: **Awaiting review**
* Impacted Platforms: [Core / iOS / Android / Web / RPC / Protocol]

## Introduction

Creation of requirements repository will allow to document SDL requirements with clear scenarios which will improve software development and testing processes.

## Motivation

Currently system requirements are not publicly available and are not represented in the form of user stories which causes difficulties in understanding of feature purposes and proper system behavior.

## Proposed solution

Proposed to create Requirements repository which will allow to keep requirements in the form of user stories with detailed feature descriptions and use cases. 

The requirements will be presented in the form according to template provided below:

>_The Requirement must be set with the following labels:_
>
> **Requirement**
>
>**Priority:** _High, Medium or Low_
>
> ## Description
>
> User story or the high-level idea of described feature
>
> ## Detailed description
>
> Link to GitHub with detailed document in MD format
>
> **Use Case 1:** The name of Use Case
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
> Describes alternative flow to Main flow described above.
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



## Potential downsides

Describe any potential downsides or known objections to the course of action presented in this proposal, then provide counter-arguments to these objections. You should anticipate possible objections that may come up in review and provide an initial response here. Explain why the positives of the proposal outweigh the downsides, or why the downside under discussion is not a large enough issue to prevent the proposal from being accepted.

## Impact on existing code

Describe the impact that this change will have on existing code. Will some SDL integrations stop compiling due to this change? Will applications still compile but produce different behavior than they used to? Is it possible to migrate existing SDL code to use a new feature or API automatically?

## Alternatives considered

Describe alternative approaches to addressing the same problem, and why you chose this approach instead.
