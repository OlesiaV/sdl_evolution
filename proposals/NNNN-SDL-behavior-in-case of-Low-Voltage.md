# Feature name

* Proposal: [SDL-NNNN](NNNN-filename.md)
* Author: [SDL Developer](https://github.com/smartdevicelink)
* Status: **Awaiting review**
* Impacted Platforms: [Core / iOS / Android / Web / RPC / Protocol]

## Introduction

This proposal defines SDL behavior in case of low voltage event.
Low voltage scenario is triggered when the battery voltage hits below 7v. In case of such event emmc is turned off and all read/write operations are unavailable. After the voltage level is restored all oprations are resumed.

## Motivation

Implement logic that will allow SDL to resume after battery charge is restored or to start up correctly in the next ingnition cycle if SDL was shut down due to LOW VOLTAGE event. 

## Proposed solution

When battery voltage hits below 7v
Extend enum "ApplicationsCloseReason" with "LOW_VOLTAGE" element. By getting this value, SDL stops any read/write activities:
- SDL ignores all requests from mobile applications
- SDL ignores all responses and messages from HMI except OnAwakeSDL or OnExitAllApplications (IGNITION_OFF)
- SDL stops audio/video streaming
- During LOW_VOLTAGE all transports are unavailable for SDL
SDL persists resumption related data stored before receiving OnExitAllApplications(LOW_VOLTAGE)
If SDL receives OnExitAllApplications(LOW_VOLTAGE) during Policy Table Update the update sequence must be stopped. Policy table remains with flag UPDATE_NEEDED
SDL resumes its regular work after receiving OnAwakeSDL
It is expected that after 10 seconds voltage level won't be resumed HMI will send OnExitAllApplications (IGNITION_OFF)


## Potential downsides

Describe any potential downsides or known objections to the course of action presented in this proposal, then provide counter-arguments to these objections. You should anticipate possible objections that may come up in review and provide an initial response here. Explain why the positives of the proposal outweigh the downsides, or why the downside under discussion is not a large enough issue to prevent the proposal from being accepted.

## Impact on existing code

Describe the impact that this change will have on existing code. Will some SDL integrations stop compiling due to this change? Will applications still compile but produce different behavior than they used to? Is it possible to migrate existing SDL code to use a new feature or API automatically?

## Alternatives considered

Describe alternative approaches to addressing the same problem, and why you chose this approach instead.
