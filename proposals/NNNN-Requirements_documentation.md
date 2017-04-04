# SDL requirements repository 

* Proposal: [SDL-NNNN](NNNN-filename.md)
* Author: [Olesia Vasylieva](https://github.com/smartdevicelink)
* Status: **Awaiting review**
* Impacted Platforms: [Documentation]

## Introduction

Creation of Requirements repository in GitHub (sdl_requirements) will allow to document SDL requirements with clear scenarios which will improve software development and testing processes.

## Motivation

Currently system requirements are not publicly accessible and are not represented in the form of user stories which causes difficulties in understanding of feature purposes and proper system behavior for OEM manufacturers and mobile applications developers.

## Proposed solution

Proposed to create Requirements repository (sdl_requirements) which will allow to keep requirements in the form of user stories with detailed feature descriptions, use cases and diagrams. GitHub Requirements repository will improve the collaboration with contributors clarifying system behavior and capabilities. 

Clear feature representation gives more options for mobile applications developers and can become a helpful tool for integration preparations on OEM platforms.

There are [sdl_hmi_integration_guidelines](https://github.com/smartdevicelink/sdl_hmi_integration_guidelines) and [sdl_core_guides](https://github.com/smartdevicelink/sdl_core_guides) in free access for community but none of these documents provide clarifications on SDL system behavior and do not give full description of available features.

**Creation of Requirements repository will allow to minimize or eliminate the following difficulties:**

- A lot of requests on Slack regarding SDL feature description since currently the list of SDL features is not clear for community
- Placement of existing SDL requirements is not freely available
- Inaccessibility of requiremetns makes feature review and defects analysis complex
- Complexity of integration maintenance

Requirements repository also requires defined Requirements management process which includes but not limitted to:

- documenting of new requirements
- updating existing requirements based on changes proposed through Evolution process
- tracing requirements lifecycle from proposal to every change made to the requirement
- prevent duplicates or contradictions in requirements

SDL Development Lifecycle includes creation and usage of a list of artifacts that are located in different repositories. In the confines of SDL Development Lifecycle generic artifacts are:

- Requirement
- Tasks
- Defetcs

Next picture shows relations between different arifacts in SDL.

![tasks_relations](https://github.com/OlesiaV/sdl_evolution/blob/requirements-documentation-proposal/proposals/assets/sdl_requirements_repository/tasks_relations.png)<br>

Requirements form basis of acceptance criteria for future contribution. Such issues are high level description of expected outcome. Proposed to create the requirements according to [requirement_template](https://github.com/OlesiaV/sdl_evolution/blob/requirements-documentation-proposal/proposals/assets/sdl_requirements_repository/requirement_template.md). 

The Requirement will be linked to the document with all detailed technical information, Use Cases and Diagrams which can be revised in case of any changes, see the template to [detailed_info](https://github.com/OlesiaV/sdl_evolution/blob/requirements-documentation-proposal/proposals/assets/sdl_requirements_repository/detailed_info.md).

Technical Task contains information describing changes to Requirements , proposed to be created according to the [technical_task_template](https://github.com/OlesiaV/sdl_evolution/blob/requirements-documentation-proposal/proposals/assets/sdl_requirements_repository/technical_task_template.md).



## Potential downsides

Additional efforts in Requirements management which includes tracking of any changes and updates on GitHub.

## Impact on existing code

Proposed process has no impact on existing code but it evolves Requirements management process.

## Alternatives considered

- Not to implement any Requirements repository on GitHub and leave SDL requirement inaccessible for community
- Consider having another shared resource for Requirements management
