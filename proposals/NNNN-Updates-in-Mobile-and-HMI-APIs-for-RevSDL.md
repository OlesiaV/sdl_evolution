# Seats HMI Settings and Audio controls updates

* Proposal: [SDL-NNNN](NNNN-filename.md)
* Author: [SDL Developer](https://github.com/smartdevicelink)
* Status: **Awaiting review**
* Impacted Platforms: [Core / iOS / Android / Web / RPC / Protocol]

## Introduction

To extend Revers_SDL functinality "SEATS", "HMI_SETTINGS" and "AUDIO" are proposed to be added to "ModuleType" in HMI and Mobile APIs

## Motivation

Proposed changes will allow user to obtain SEAT, HMI_SETTINGS and AUDIO control functions of the vehicle using mobile application.
Previously only CLIMATE and RADIO control functions were enabled for mobile remote control.

## Proposed solution

#### For SEATS control the following functions will be enabled for mobile application:

- READ and SET parameters

| Control Item | Value range | Description |
| ------------ | ------------ |------------ |
| Cooled Seat level | 0-100 | Level of the seat cooling |
| Seat Horizontal Positon | 0-100 | Adjust Seat Forward |
| Seat Vertical Position | 0-100 | Height (up or down) |
| Seat Angle Position | 0-100 | Seat pitch |
| Back Tilt Position | 0-100 | Backrest recline |
| Back Lumbar position | Struct {TOP, MIDDLE, BOTTOM} | Lumbar position |
| Massage Seat | Start, Stop | Starting or stopping massage |
| Massage Seat Zone | Struct{LUMBAR, BOTTOM} | Choosing massage zone |
| Massage Seat Level | Struct{ HIGH, LOW} | Massage intensity |

- READ only parameters

| Control Item | Value range | Description |
| ------------ | ------------ |------------ |
| Cooled Seats | ON, OFF | Display if seats cooling is enabled |
| Heated Seat | ON, OFF | Display if seats heating is enabled |
| Massage Enabled | ON, OFF | Display if seats massage is enabled |

#### For "HMI Settings" mobile application will be able to READ and SET 

| Control Item | Value range | Description |
| ------------ | ------------ |------------ |
| Display Mode | DAY, NIGHT, AUTO | To display or set one of the available display modes |
| Distance Unit | Miles, Kilometers | To display or set one of the available distance units |
| Temperature Unit | Temperature Unit | To display or set one of the available temperature units |

#### For "AUDIO" mobile application will be able to READ and SET:

| Control Item | Value range | Description |
| ------------ | ------------ |------------ |
| Audio Source | CD, TUNER, BLUETOOTH| Show the current one or set one of the available audio sources |
| Audio volume | 0-100| Volume level |
| Equilizer Settings | CStruct {Channel Name as string, Channel setting as 0-100} | Defines the list of supported channels (band) and their current/desired settings on HU |

#### The following updates need to be implemented in HMI and Mobile APIs:

1. "ModuleType" enum must be extenede with "AUDIO", "SEATS", "HMI_SETTINGS" values
 ```
 <enum name="ModuleType">
        <element name="CLIMATE"/>
        <element name="RADIO"/>
        <element name="AUDIO"/>
        <element name="SEATS"/>
        <element name="HMI_SETTINGS"/>
    </enum>
```

2. "ModuleData" structure must be extenede with "seatsControlData", "hmiControlData", "audioControlData" parameters:

```
<struct name="ModuleData">
        <description>The moduleType indicates which type of data should be changed and identifies which data object exists in this struct. For example, if the moduleType is CLIMATE then a "climateControlData" should exist</description>
        <param name="moduleType" type="ModuleType"></param>
        <param name="moduleZone" type="InteriorZone"></param>
        <param name="radioControlData" type="RadioControlData" mandatory="false"></param>
        <param name="climateControlData" type="ClimateControlData" mandatory="false"></param>
        <param name="seatsControlData" type="SeatsControlData" mandatory="false"></param>
        <param name="hmiControlData" type="HMIControlData" mandatory="false"></param>
        <param name="audioControlData" type="AudioControlData" mandatory="false"></param>
    </struct>
```

3. The following structures and enums must be added:

```
<struct name="SeatsControlData">
	  <description>Corresponds to "SEATS" ModuleType</description>
        <param name="cooledSeats" type="Boolean" mandatory="false"></param>
        <param name="cooledSeatLevel" type="Integer" minvalue="0" maxvalue="100" mandatory="false"></param>
        <param name="heatedSeat" type="Boolean" mandatory="false"></param>
        <param name="seatHorizontalPosition" type="Integer" minvalue="0" maxvalue="100" mandatory="false"></param>
        <param name="seatVerticalPosition" type="Integer" minvalue="0" maxvalue="100" mandatory="false"></param>
        <param name="seatAnglePosition" type="Integer" minvalue="0" maxvalue="100" mandatory="false"></param>
        <param name="backTiltPosition" type="Integer" minvalue="0" maxvalue="100" mandatory="false"></param>
        <param name="backLumbarPosition" type="LumbarPosition" mandatory="false"></param>
        <param name="massageSeat" type="MassageSeatAction" mandatory="false"></param>
        <param name="massageSeatZone" type="MassageSeatZone" mandatory="false"></param>
        <param name="massageSeatLevel" type="MassageSeatLevel" mandatory="false"></param>
        <param name="massageEnabled" type="Boolean" mandatory="false"></param>
    </struct>
    <enum name="LumbarPosition">
        <element name="TOP"/>
        <element name="MIDDLE"/>
        <element name="BOTTOM"/>
    </enum>
    <enum name="MassageSeatAction">
        <element name="START"/>
        <element name="STOP"/>
    </enum>
    <enum name="MassageSeatZone">
        <element name="LUMBAR"/>
        <element name="BOTTOM"/>
    </enum>
    <enum name="MassageSeatLevel">
        <element name="HIGH"/>
        <element name="LOW"/>
    </enum>
    <struct name="HMIControlData">
	  <description>Corresponds to "HMI_SETTINGS" ModuleType</description>
        <param name="displayMode" type="DisplayMode" mandatory="false"></param>
        <param name="temperatureUnit" type="TemperatureUnit" mandatory="false"></param>
        <param name="distanceUnit" type="DistanceUnit" mandatory="false"></param>
    </struct>
     <enum name="DisplayMode">
        <element name="DAY"/>
        <element name="NIGHT"/>
        <element name="AUTO"/>
    </enum>
    <enum name="DistanceUnit">
        <element name="MILES"/>
        <element name="KILOMETERS"/>
    </enum>
     <struct name="AudioControlData">
	  <description>Corresponds to "AUDIO" ModuleType</description>
        <param name="source" type="AudioSource" mandatory="false"></param>
        <param name="audioVolume" type="Integer" minvalue="0" maxvalue="100" mandatory="false"></param>
        <param name="equalizerSettings" type="EqualizerSettings" minsize="1" maxsize="10" mandatory="false" array ="true">
            <description>Defines the list of supported channels (band) and their current/desired settings on HU</description>
        </param>
    </struct>
     <enum name="AudioSource">
        <element name="CD"/>
        <element name="BLUETOOTH"/>
        <element name="TUNER"/>
    </enum>
    <struct name="EqualizerSettings">
        <description>Defines the each Equalizer chanel setting to be obtained via OnInteriorVehicleData or to be set-up via SetInteriorVehicleData on HU.</description>
        <param name="channel" type="String" mandatory="true">
            <description>Frequency name (e.i. "Treble" or "125 Hz")</description>
        </param>
        <param name="channelSettings" type="Integer" minvalue="0" maxvalue="100" mandatory="true"></param>
    </struct>
```


## Potential downsides

Describe any potential downsides or known objections to the course of action presented in this proposal, then provide counter-arguments to these objections. You should anticipate possible objections that may come up in review and provide an initial response here. Explain why the positives of the proposal outweigh the downsides, or why the downside under discussion is not a large enough issue to prevent the proposal from being accepted.

## Impact on existing code

Describe the impact that this change will have on existing code. Will some SDL integrations stop compiling due to this change? Will applications still compile but produce different behavior than they used to? Is it possible to migrate existing SDL code to use a new feature or API automatically?

## Alternatives considered

N/A

