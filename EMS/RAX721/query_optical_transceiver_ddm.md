# Query Optical Transceiver Digital Diagnostics

## API Information
Query digital diagnostics monitoring (DDM) parameters for optical transceivers on an RAX721 network element, including temperature, bias current, TX/RX optical power, and voltage with alarm thresholds.

## API Path
`http://XX.XX.XX.XX/tiap_ems_basic_mgt/tiap_ems_basic_mgt/v20/optical_transceiver_ddm`

## Request Protocol
HTTP

## Request Method
GET

## Query Parameters
| Parameter Name | Description | Required | Type | Restriction | Example |
| --- | --- | --- | --- | --- | --- |
| `neId` | Network element ID | Yes | `number` | | 127 |
| `page` | Page number for pagination | No | `number` | | 1 |
| `start` | Starting record offset | No | `number` | | 0 |
| `limit` | Maximum number of records per page | No | `number` | | 25 |

### Request Example
```
http://172.16.1.248/tiap_ems_basic_mgt/tiap_ems_basic_mgt/v20/optical_transceiver_ddm?neId=127&page=1&start=0&limit=25
```

## Response Content
### Return Result
> Success (200)
Json array

| Parameter Name | Description | Required | Type | Data Dictionary | Restriction | Example |
| --- | --- | --- | --- | --- | --- | --- |
| `[0]` | DDM parameter item | Yes | `object` | | | See example below |
| `[0]>>ifIndex` | Interface index | Yes | `string` | | | "272900096" |
| `[0]>>instance` | DDM parameter instance identifier (format: `ifIndex.sequence`) | Yes | `string` | | | "272900096.1" |
| `[0]>>neId` | Network element ID | Yes | `number` | | | 127 |
| `[0]>>opticalTransceiverDDM15MinValidIntervals` | Valid 15-minute DDM sampling intervals | Yes | `string` | | | "96" |
| `[0]>>opticalTransceiverDDM24HrValidIntervals` | Valid 24-hour DDM sampling intervals | Yes | `string` | | | "7" |
| `[0]>>opticalTransceiverParamAlarmLastChange` | Time since last alarm state change | Yes | `string` | | | "0 hours, 0 minutes, 0 seconds" |
| `[0]>>opticalTransceiverParamAlarmLastValue` | Last alarm parameter value | Yes | `string` | | | "N/A" |
| `[0]>>opticalTransceiverParamAlarmStatus` | Parameter alarm status | Yes | `string` | 1 = Normal<br>2 = Warning<br>3 = Alarm<br>4 = Critical Alarm | | "1" |
| `[0]>>opticalTransceiverParamHighAlarmThresh` | High alarm threshold | Yes | `string` | | | "90.0℃" |
| `[0]>>opticalTransceiverParamHighWarningThresh` | High warning threshold | Yes | `string` | | | "85.0℃" |
| `[0]>>opticalTransceiverParamLowAlarmThresh` | Low alarm threshold | Yes | `string` | | | "-5.0℃" |
| `[0]>>opticalTransceiverParamLowWarningThresh` | Low warning threshold | Yes | `string` | | | "0.0℃" |
| `[0]>>opticalTransceiverParameterType` | DDM parameter type | Yes | `number` | 1 = Temperature<br>2 = Bias Current<br>3 = TX Optical Power<br>4 = RX Optical Power<br>5 = Voltage | | 1 |
| `[0]>>opticalTransceiverParameterValue` | Current parameter value (with unit) | Yes | `string` | | | "35.5℃" |
| `[0]>>portName` | Port name | Yes | `string` | | | "tengigabitethernet1/1/1" |

### Success Example
```json
[
  {
    "ifIndex": "272900096",
    "instance": "272900096.1",
    "neId": 127,
    "opticalTransceiverDDM15MinValidIntervals": "96",
    "opticalTransceiverDDM24HrValidIntervals": "7",
    "opticalTransceiverParamAlarmLastChange": "0 hours, 0 minutes, 0 seconds",
    "opticalTransceiverParamAlarmLastValue": "N/A",
    "opticalTransceiverParamAlarmStatus": "1",
    "opticalTransceiverParamHighAlarmThresh": "90.0℃",
    "opticalTransceiverParamHighWarningThresh": "85.0℃",
    "opticalTransceiverParamLowAlarmThresh": "-5.0℃",
    "opticalTransceiverParamLowWarningThresh": "0.0℃",
    "opticalTransceiverParameterType": 1,
    "opticalTransceiverParameterValue": "35.5℃",
    "portName": "tengigabitethernet1/1/1"
  },
  {
    "ifIndex": "272900096",
    "instance": "272900096.2",
    "neId": 127,
    "opticalTransceiverDDM15MinValidIntervals": "96",
    "opticalTransceiverDDM24HrValidIntervals": "7",
    "opticalTransceiverParamAlarmLastChange": "0 hours, 0 minutes, 0 seconds",
    "opticalTransceiverParamAlarmLastValue": "N/A",
    "opticalTransceiverParamAlarmStatus": "1",
    "opticalTransceiverParamHighAlarmThresh": "95.00mA",
    "opticalTransceiverParamHighWarningThresh": "85.00mA",
    "opticalTransceiverParamLowAlarmThresh": "2.00mA",
    "opticalTransceiverParamLowWarningThresh": "3.00mA",
    "opticalTransceiverParameterType": 2,
    "opticalTransceiverParameterValue": "36.54mA",
    "portName": "tengigabitethernet1/1/1"
  },
  {
    "ifIndex": "272900096",
    "instance": "272900096.3",
    "neId": 127,
    "opticalTransceiverDDM15MinValidIntervals": "96",
    "opticalTransceiverDDM24HrValidIntervals": "7",
    "opticalTransceiverParamAlarmLastChange": "0 hours, 0 minutes, 0 seconds",
    "opticalTransceiverParamAlarmLastValue": "N/A",
    "opticalTransceiverParamAlarmStatus": "1",
    "opticalTransceiverParamHighAlarmThresh": "3.0dBm",
    "opticalTransceiverParamHighWarningThresh": "2.0dBm",
    "opticalTransceiverParamLowAlarmThresh": "-10.2dBm",
    "opticalTransceiverParamLowWarningThresh": "-9.2dBm",
    "opticalTransceiverParameterType": 3,
    "opticalTransceiverParameterValue": "-3.1dBm",
    "portName": "tengigabitethernet1/1/1"
  },
  {
    "ifIndex": "272900096",
    "instance": "272900096.4",
    "neId": 127,
    "opticalTransceiverDDM15MinValidIntervals": "96",
    "opticalTransceiverDDM24HrValidIntervals": "7",
    "opticalTransceiverParamAlarmLastChange": "0 hours, 0 minutes, 0 seconds",
    "opticalTransceiverParamAlarmLastValue": "N/A",
    "opticalTransceiverParamAlarmStatus": "1",
    "opticalTransceiverParamHighAlarmThresh": "2.5dBm",
    "opticalTransceiverParamHighWarningThresh": "2.0dBm",
    "opticalTransceiverParamLowAlarmThresh": "-15.0dBm",
    "opticalTransceiverParamLowWarningThresh": "-14.5dBm",
    "opticalTransceiverParameterType": 4,
    "opticalTransceiverParameterValue": "-0.5dBm",
    "portName": "tengigabitethernet1/1/1"
  },
  {
    "ifIndex": "272900096",
    "instance": "272900096.5",
    "neId": 127,
    "opticalTransceiverDDM15MinValidIntervals": "96",
    "opticalTransceiverDDM24HrValidIntervals": "7",
    "opticalTransceiverParamAlarmLastChange": "0 hours, 0 minutes, 0 seconds",
    "opticalTransceiverParamAlarmLastValue": "N/A",
    "opticalTransceiverParamAlarmStatus": "1",
    "opticalTransceiverParamHighAlarmThresh": "3.7V",
    "opticalTransceiverParamHighWarningThresh": "3.6V",
    "opticalTransceiverParamLowAlarmThresh": "2.9V",
    "opticalTransceiverParamLowWarningThresh": "3.0V",
    "opticalTransceiverParameterType": 5,
    "opticalTransceiverParameterValue": "3.4V",
    "portName": "tengigabitethernet1/1/1"
  },
  {
    "ifIndex": "272900112",
    "instance": "272900112.1",
    "neId": 127,
    "opticalTransceiverDDM15MinValidIntervals": "96",
    "opticalTransceiverDDM24HrValidIntervals": "7",
    "opticalTransceiverParamAlarmLastChange": "0 hours, 0 minutes, 0 seconds",
    "opticalTransceiverParamAlarmLastValue": "N/A",
    "opticalTransceiverParamAlarmStatus": "1",
    "opticalTransceiverParamHighAlarmThresh": "90.0℃",
    "opticalTransceiverParamHighWarningThresh": "85.0℃",
    "opticalTransceiverParamLowAlarmThresh": "-5.0℃",
    "opticalTransceiverParamLowWarningThresh": "0.0℃",
    "opticalTransceiverParameterType": 1,
    "opticalTransceiverParameterValue": "33.1℃",
    "portName": "tengigabitethernet1/1/3"
  },
  {
    "ifIndex": "272900112",
    "instance": "272900112.2",
    "neId": 127,
    "opticalTransceiverDDM15MinValidIntervals": "96",
    "opticalTransceiverDDM24HrValidIntervals": "7",
    "opticalTransceiverParamAlarmLastChange": "0 hours, 0 minutes, 0 seconds",
    "opticalTransceiverParamAlarmLastValue": "N/A",
    "opticalTransceiverParamAlarmStatus": "1",
    "opticalTransceiverParamHighAlarmThresh": "95.00mA",
    "opticalTransceiverParamHighWarningThresh": "85.00mA",
    "opticalTransceiverParamLowAlarmThresh": "2.00mA",
    "opticalTransceiverParamLowWarningThresh": "3.00mA",
    "opticalTransceiverParameterType": 2,
    "opticalTransceiverParameterValue": "33.11mA",
    "portName": "tengigabitethernet1/1/3"
  },
  {
    "ifIndex": "272900112",
    "instance": "272900112.3",
    "neId": 127,
    "opticalTransceiverDDM15MinValidIntervals": "96",
    "opticalTransceiverDDM24HrValidIntervals": "7",
    "opticalTransceiverParamAlarmLastChange": "0 hours, 0 minutes, 0 seconds",
    "opticalTransceiverParamAlarmLastValue": "N/A",
    "opticalTransceiverParamAlarmStatus": "1",
    "opticalTransceiverParamHighAlarmThresh": "3.0dBm",
    "opticalTransceiverParamHighWarningThresh": "2.0dBm",
    "opticalTransceiverParamLowAlarmThresh": "-10.2dBm",
    "opticalTransceiverParamLowWarningThresh": "-9.2dBm",
    "opticalTransceiverParameterType": 3,
    "opticalTransceiverParameterValue": "-3.4dBm",
    "portName": "tengigabitethernet1/1/3"
  },
  {
    "ifIndex": "272900112",
    "instance": "272900112.4",
    "neId": 127,
    "opticalTransceiverDDM15MinValidIntervals": "96",
    "opticalTransceiverDDM24HrValidIntervals": "7",
    "opticalTransceiverParamAlarmLastChange": "220 days, 7 hours, 49 minutes, 52 seconds",
    "opticalTransceiverParamAlarmLastValue": "-37.0dBm",
    "opticalTransceiverParamAlarmStatus": "4",
    "opticalTransceiverParamHighAlarmThresh": "2.5dBm",
    "opticalTransceiverParamHighWarningThresh": "2.0dBm",
    "opticalTransceiverParamLowAlarmThresh": "-15.0dBm",
    "opticalTransceiverParamLowWarningThresh": "-14.5dBm",
    "opticalTransceiverParameterType": 4,
    "opticalTransceiverParameterValue": "-37.0dBm",
    "portName": "tengigabitethernet1/1/3"
  },
  {
    "ifIndex": "272900112",
    "instance": "272900112.5",
    "neId": 127,
    "opticalTransceiverDDM15MinValidIntervals": "96",
    "opticalTransceiverDDM24HrValidIntervals": "7",
    "opticalTransceiverParamAlarmLastChange": "0 hours, 0 minutes, 0 seconds",
    "opticalTransceiverParamAlarmLastValue": "N/A",
    "opticalTransceiverParamAlarmStatus": "1",
    "opticalTransceiverParamHighAlarmThresh": "3.7V",
    "opticalTransceiverParamHighWarningThresh": "3.6V",
    "opticalTransceiverParamLowAlarmThresh": "2.9V",
    "opticalTransceiverParamLowWarningThresh": "3.0V",
    "opticalTransceiverParameterType": 5,
    "opticalTransceiverParameterValue": "3.3V",
    "portName": "tengigabitethernet1/1/3"
  }
]
```

## Data Dictionary

### opticalTransceiverParameterType
| Value | Description | Unit |
| --- | --- | --- |
| 1 | Module Temperature | ℃ |
| 2 | Bias Current | mA |
| 3 | TX Optical Power | dBm |
| 4 | RX Optical Power | dBm |
| 5 | Voltage | V |

### opticalTransceiverParamAlarmStatus
| Value | Description |
| --- | --- |
| 1 | Normal |
| 2 | Warning |
| 3 | Alarm |
| 4 | Critical Alarm |

## Key Monitoring Parameters

### Temperature (Type 1)
| Field | Description | Example |
| --- | --- | --- |
| `opticalTransceiverParameterValue` | Current module temperature | "35.5℃" |
| `opticalTransceiverParamHighWarningThresh` | High warning threshold | "85.0℃" |
| `opticalTransceiverParamHighAlarmThresh` | High alarm threshold | "90.0℃" |
| `opticalTransceiverParamLowWarningThresh` | Low warning threshold | "0.0℃" |
| `opticalTransceiverParamLowAlarmThresh` | Low alarm threshold | "-5.0℃" |

### Bias Current (Type 2)
| Field | Description | Example |
| --- | --- | --- |
| `opticalTransceiverParameterValue` | Current bias current | "36.54mA" |
| `opticalTransceiverParamHighWarningThresh` | High warning threshold | "85.00mA" |
| `opticalTransceiverParamHighAlarmThresh` | High alarm threshold | "95.00mA" |
| `opticalTransceiverParamLowWarningThresh` | Low warning threshold | "3.00mA" |
| `opticalTransceiverParamLowAlarmThresh` | Low alarm threshold | "2.00mA" |

### TX Optical Power (Type 3)
| Field | Description | Example |
| --- | --- | --- |
| `opticalTransceiverParameterValue` | Current TX optical power | "-3.1dBm" |
| `opticalTransceiverParamHighWarningThresh` | High warning threshold | "2.0dBm" |
| `opticalTransceiverParamHighAlarmThresh` | High alarm threshold | "3.0dBm" |
| `opticalTransceiverParamLowWarningThresh` | Low warning threshold | "-9.2dBm" |
| `opticalTransceiverParamLowAlarmThresh` | Low alarm threshold | "-10.2dBm" |

### RX Optical Power (Type 4)
| Field | Description | Example |
| --- | --- | --- |
| `opticalTransceiverParameterValue` | Current RX optical power | "-0.5dBm" |
| `opticalTransceiverParamHighWarningThresh` | High warning threshold | "2.0dBm" |
| `opticalTransceiverParamHighAlarmThresh` | High alarm threshold | "2.5dBm" |
| `opticalTransceiverParamLowWarningThresh` | Low warning threshold | "-14.5dBm" |
| `opticalTransceiverParamLowAlarmThresh` | Low alarm threshold | "-15.0dBm" |

### Voltage (Type 5)
| Field | Description | Example |
| --- | --- | --- |
| `opticalTransceiverParameterValue` | Current voltage | "3.4V" |
| `opticalTransceiverParamHighWarningThresh` | High warning threshold | "3.6V" |
| `opticalTransceiverParamHighAlarmThresh` | High alarm threshold | "3.7V" |
| `opticalTransceiverParamLowWarningThresh` | Low warning threshold | "3.0V" |
| `opticalTransceiverParamLowAlarmThresh` | Low alarm threshold | "2.9V" |

## Usage Notes
1. Each DDM parameter type returns as a separate array item identified by `opticalTransceiverParameterType`
2. The `instance` field uses the format `{ifIndex}.{sequence}` (e.g., "272900096.1") to uniquely identify each DDM parameter
3. RAX721 uses `opticalTransceiverParameterType = 5` for voltage, same as RAX711-C-R, whereas iTN167 uses `7`
4. RAX721 supports alarm status `4` (Critical Alarm), which is triggered when RX optical power drops below the low alarm threshold (e.g., "-37.0dBm" on port tengigabitethernet1/1/3)
5. Threshold values include the measurement unit (e.g., "90.0℃", "95.00mA", "3.0dBm")
6. RAX721 DDM sampling has active valid intervals: `opticalTransceiverDDM15MinValidIntervals` = "96" and `opticalTransceiverDDM24HrValidIntervals` = "7", indicating ongoing monitoring
7. When no alarm has occurred, `opticalTransceiverParamAlarmLastValue` returns "N/A"
8. This response includes DDM data from two ports: `tengigabitethernet1/1/1` (ifIndex=272900096) and `tengigabitethernet1/1/3` (ifIndex=272900112)

## Related Documentation
- [Query Optical Transceiver Digital Diagnostics (iTN167)](../167/query_optical_transceiver_ddm.md) - Equivalent endpoint for iTN167 devices
- [Query Optical Transceiver Digital Diagnostics (RAX711-C-R)](../RAX711-C-R/query_optical_transceiver_ddm.md) - Equivalent endpoint for RAX711-C-R devices
