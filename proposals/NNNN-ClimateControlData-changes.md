# "ClimateControlData" structure changes in Mobile and HMI APIs

* Proposal: [SDL-NNNN](NNNN-filename.md)
* Author: [Olesia Vasylieva](https://github.com/smartdevicelink)
* Status: **Awaiting review**
* Impacted Platforms: [Core / iOS / Android / Web / RPC]

## Introduction

"ClimateControlData" structure defines the available control options of the "CLIMATE" vehicle module for remote-control mobile application.

## Motivation

Proposed to optimize temperature settings in Climate Control with defined minimal and maximal temperature settings for different temperature units (Celsius or Farenheit).
New parameters will also allow user to set ventialtion mode of the vehicle and receive information if the AC is on the maximum level.


## Proposed solution

Proposed to modify the existing parameters of  the "ClimateControlData" structure

1. To move "TemperatureUnit" from "ClimateControlData" structure to "Temperature" structure.
"currentTemp" and "desiredTemp" must be specified by "Temperature" structure.

2. To add new parameters "acMaxEnable" and "ventilationMode" to "ClimateControlData" structure

 | Parameter name |Value | Description |
 | ------------ | ------------ |------------ |
 

##### HMI and Mobile APIs changes

```
<struct name="ClimateControlData">
    <param name="fanSpeed" type="Integer" minvalue="0" maxvalue="100" mandatory="false">
    </param>
  <param name="currentTemp" type="Temperature" mandatory="false">
    </param>
    <param name="desiredTemp" type="Temperature" mandatory="false">
    </param>
    <param name="acEnable" type="Boolean" mandatory="false">
    </param>
    <param name="acMaxEnable" type="Boolean" mandatory="false">
    </param>
    <param name="circulateAirEnable" type="Boolean" mandatory="false">
    </param>
    <param name="autoModeEnable" type="Boolean" mandatory="false">
    </param>
    <param name="defrostZone" type="DefrostZone" mandatory="false">
    </param>
    <param name="dualModeEnable" type="Boolean" mandatory="false">
    </param>
     <param name="ventilationMode" type="VentilationMode" mandatory="false">
    </param>
  </struct>
   <enum name="VentilationMode">
    <element name="UPPER"/>
    <element name="LOWER"/>
    <element name="BOTH"/>
  </enum>
  <struct name="Temperature">
      <param name="unit" type="TemperatureUnit">
         <description>Temperature Unit</description>
      </param>
      <param name="valueC" type="Float" minvalue="14.0" maxvalue="30" mandatory=”false”>
         <description>Temperature Value in Celsius</description>
      </param>
      <param name="valueF" type="Float" minvalue="60" maxvalue="90" mandatory=”false”>
         <description>Temperature Value in Farenheit</description>
      </param>
   </struct>
   <enum name="TemperatureUnit">
      <element name="FAHRENHEIT" />
      <element name="CELSIUS" />
   </enum>
```

## Potential downsides

N/A

## Impact on existing code

Describe the impact that this change will have on existing code. Will some SDL integrations stop compiling due to this change? Will applications still compile but produce different behavior than they used to? Is it possible to migrate existing SDL code to use a new feature or API automatically?

## Alternatives considered

N/A
