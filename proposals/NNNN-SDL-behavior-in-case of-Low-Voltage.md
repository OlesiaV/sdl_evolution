# Feature name

* Proposal: [SDL-NNNN](NNNN-filename.md)
* Author: [SDL Developer](https://github.com/smartdevicelink)
* Status: **Awaiting review**
* Impacted Platforms: [Core / iOS / Android / Web / RPC / Protocol]

## Introduction

A short description of what the feature is. Try to keep it to a single-paragraph "elevator pitch" so the reader understands what problem this proposal is addressing.

## Motivation

Describe the problems that this proposal seeks to address. If the problem is that some common pattern is currently hard to express, show how one can currently get a similar effect and describe its drawbacks. If it's completely new functionality that cannot be emulated, motivate why this new functionality would help SDL mobile developers or OEMs provide users with useful functionality.

## Proposed solution

When battery voltage hits below 7v
Extend enum "ApplicationsCloseReason" with "LOW_VOLTAGE" element. By getting this value, SDL stops any read/write activities:
- SDL ignores all incoming requests from mobile applications
- SDL ignores all responses and messages from HMI except OnAwakeSDL
- SDL discards all notifications and responses received from HMi that needed to be transferred to mobile app
- SDL stops audio/video streaming
- During LOW_VOLTAGE all transports are unavailable for SDL
SDL persists resumption related data stored before receiving OnExitAllApplications(LOW_VOLTAGE)
If SDL receives OnExitAllApplications(LOW_VOLTAGE) during Policy Table Update the update sequence must be stopped. Policy table remains with flag UPDATE_NEEDED
SDL resumes its regular work after receiving OnAwakeSDL

Use case 1
SDL receives OnExitAllApplications (LOW_VOLTAGE)
SDL sets 10 seconds timer 
SDL ignores all messages from HMI except OnAwakeSDL or OnExitAllApplications(IGNITION_OFF)
Timer expires and no OnAwakeSDL from HMI
SDL shuts down

Timer is not expired and HMI sent OnAwakeSDL
SDL resumes 


## Potential downsides

Describe any potential downsides or known objections to the course of action presented in this proposal, then provide counter-arguments to these objections. You should anticipate possible objections that may come up in review and provide an initial response here. Explain why the positives of the proposal outweigh the downsides, or why the downside under discussion is not a large enough issue to prevent the proposal from being accepted.

## Impact on existing code

Describe the impact that this change will have on existing code. Will some SDL integrations stop compiling due to this change? Will applications still compile but produce different behavior than they used to? Is it possible to migrate existing SDL code to use a new feature or API automatically?

## Alternatives considered

Describe alternative approaches to addressing the same problem, and why you chose this approach instead.
