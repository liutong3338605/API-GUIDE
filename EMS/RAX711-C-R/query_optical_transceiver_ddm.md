# Query Optical Transceiver Digital Diagnostics

## API Information
Query digital diagnostics monitoring (DDM) parameters for optical transceivers on an RAX711-C-R network element, including temperature, bias current, TX/RX optical power, and voltage with alarm thresholds.

## API Path
`http://XX.XX.XX.XX/tiap_ems_basic_mgt/tiap_ems_basic_mgt/v20/optical_transceiver_ddm`

## Request Protocol
HTTP

## Request Method
GET

## Query Parameters
| Parameter Name | Description | Required | Type | Restriction | Example |
| --- | --- | --- | --- | --- | --- |
| `neId` | Network element ID | Yes | `number` | | 220 |
| `page` | Page number for pagination | No | `number` | | 1 |
| `start` | Starting record offset | No | `number` | | 0 |
| `limit` | Maximum number of records per page | No | `number` | | 25 |

### Request Example
```
http://172.16.1.248/tiap_ems_basic_mgt/tiap_ems_basic_mgt/v20/optical_transceiver_ddm?neId=220&page=1&start=0&limit=25
```

## Response Content
### Return Result
> Success (200)
Json array

| Parameter Name | Description | Required | Type | Data Dictionary | Restriction | Example |
| --- | --- | --- | --- | --- | --- | --- |
| `[0]` | DDM parameter item | Yes | `object` | | | See example below |
| `[0]>>ifIndex` | Interface index | Yes | `string` | | | "272908344" |
| `[0]>>instance` | DDM parameter instance identifier (format: `ifIndex.sequence`) | Yes | `string` | | | "272908344.1" |
| `[0]>>neId` | Network element ID | Yes | `number` | | | 220 |
| `[0]>>opticalTransceiverDDM15MinValidIntervals` | Valid 15-minute DDM sampling intervals | Yes | `string` | | | "0" |
| `[0]>>opticalTransceiverDDM24HrValidIntervals` | Valid 24-hour DDM sampling intervals | Yes | `string` | | | "0" |
| `[0]>>opticalTransceiverParamAlarmLastChange` | Time since last alarm state change | Yes | `string` | | | "0 hours, 0 minutes, 0 seconds" |
| `[0]>>opticalTransceiverParamAlarmLastValue` | Last alarm parameter value | Yes | `string` | | | "N/A" |
| `[0]>>opticalTransceiverParamAlarmStatus` | Parameter alarm status | Yes | `string` | 1 = Normal<br>2 = Warning<br>3 = Alarm | | "1" |
| `[0]>>opticalTransceiverParamHighAlarmThresh` | High alarm threshold | Yes | `string` | | | "75.0℃" |
| `[0]>>opticalTransceiverParamHighWarningThresh` | High warning threshold | Yes | `string` | | | "70.0℃" |
| `[0]>>opticalTransceiverParamLowAlarmThresh` | Low alarm threshold | Yes | `string` | | | "-5.0℃" |
| `[0]>>opticalTransceiverParamLowWarningThresh` | Low warning threshold | Yes | `string` | | | "0.0℃" |
| `[0]>>opticalTransceiverParameterType` | DDM parameter type | Yes | `number` | 1 = Temperature<br>2 = Bias Current<br>3 = TX Optical Power<br>4 = RX Optical Power<br>5 = Voltage | | 1 |
| `[0]>>opticalTransceiverParameterValue` | Current parameter value (with unit) | Yes | `string` | | | "37.7℃" |
| `[0]>>portName` | Port name | Yes | `string` | | | "gigaethernet1/2/8" |

### Success Example
```json
[
  {
    "ifIndex": "272908344",
    "instance": "272908344.1",
    "neId": 220,
    "opticalTransceiverDDM15MinValidIntervals": "0",
    "opticalTransceiverDDM24HrValidIntervals": "0",
    "opticalTransceiverParamAlarmLastChange": "0 hours, 0 minutes, 0 seconds",
    "opticalTransceiverParamAlarmLastValue": "N/A",
    "opticalTransceiverParamAlarmStatus": "1",
    "opticalTransceiverParamHighAlarmThresh": "75.0℃",
    "opticalTransceiverParamHighWarningThresh": "70.0℃",
    "opticalTransceiverParamLowAlarmThresh": "-5.0℃",
    "opticalTransceiverParamLowWarningThresh": "0.0℃",
    "opticalTransceiverParameterType": 1,
    "opticalTransceiverParameterValue": "37.7℃",
    "portName": "gigaethernet1/2/8"
  },
  {
    "ifIndex": "272908344",
    "instance": "272908344.2",
    "neId": 220,
    "opticalTransceiverDDM15MinValidIntervals": "0",
    "opticalTransceiverDDM24HrValidIntervals": "0",
    "opticalTransceiverParamAlarmLastChange": "0 hours, 0 minutes, 0 seconds",
    "opticalTransceiverParamAlarmLastValue": "N/A",
    "opticalTransceiverParamAlarmStatus": "1",
    "opticalTransceiverParamHighAlarmThresh": "100.00mA",
    "opticalTransceiverParamHighWarningThresh": "80.00mA",
    "opticalTransceiverParamLowAlarmThresh": "0.00mA",
    "opticalTransceiverParamLowWarningThresh": "0.00mA",
    "opticalTransceiverParameterType": 2,
    "opticalTransceiverParameterValue": "17.23mA",
    "portName": "gigaethernet1/2/8"
  },
  {
    "ifIndex": "272908344",
    "instance": "272908344.3",
    "neId": 220,
    "opticalTransceiverDDM15MinValidIntervals": "0",
    "opticalTransceiverDDM24HrValidIntervals": "0",
    "opticalTransceiverParamAlarmLastChange": "0 hours, 0 minutes, 0 seconds",
    "opticalTransceiverParamAlarmLastValue": "N/A",
    "opticalTransceiverParamAlarmStatus": "1",
    "opticalTransceiverParamHighAlarmThresh": "-2.5dBm",
    "opticalTransceiverParamHighWarningThresh": "-3.0dBm",
    "opticalTransceiverParamLowAlarmThresh": "-11.0dBm",
    "opticalTransceiverParamLowWarningThresh": "-10.5dBm",
    "opticalTransceiverParameterType": 3,
    "opticalTransceiverParameterValue": "-6.2dBm",
    "portName": "gigaethernet1/2/8"
  },
  {
    "ifIndex": "272908344",
    "instance": "272908344.4",
    "neId": 220,
    "opticalTransceiverDDM15MinValidIntervals": "0",
    "opticalTransceiverDDM24HrValidIntervals": "0",
    "opticalTransceiverParamAlarmLastChange": "0 hours, 0 minutes, 0 seconds",
    "opticalTransceiverParamAlarmLastValue": "N/A",
    "opticalTransceiverParamAlarmStatus": "1",
    "opticalTransceiverParamHighAlarmThresh": "-2.0dBm",
    "opticalTransceiverParamHighWarningThresh": "-3.0dBm",
    "opticalTransceiverParamLowAlarmThresh": "-21.9dBm",
    "opticalTransceiverParamLowWarningThresh": "-21.0dBm",
    "opticalTransceiverParameterType": 4,
    "opticalTransceiverParameterValue": "-4.9dBm",
    "portName": "gigaethernet1/2/8"
  },
  {
    "ifIndex": "272908344",
    "instance": "272908344.5",
    "neId": 220,
    "opticalTransceiverDDM15MinValidIntervals": "0",
    "opticalTransceiverDDM24HrValidIntervals": "0",
    "opticalTransceiverParamAlarmLastChange": "0 hours, 0 minutes, 0 seconds",
    "opticalTransceiverParamAlarmLastValue": "N/A",
    "opticalTransceiverParamAlarmStatus": "1",
    "opticalTransceiverParamHighAlarmThresh": "3.6V",
    "opticalTransceiverParamHighWarningThresh": "3.5V",
    "opticalTransceiverParamLowAlarmThresh": "3.0V",
    "opticalTransceiverParamLowWarningThresh": "3.1V",
    "opticalTransceiverParameterType": 5,
    "opticalTransceiverParameterValue": "3.3V",
    "portName": "gigaethernet1/2/8"
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

## Key Monitoring Parameters

### Temperature (Type 1)
| Field | Description | Example |
| --- | --- | --- |
| `opticalTransceiverParameterValue` | Current module temperature | "37.7℃" |
| `opticalTransceiverParamHighWarningThresh` | High warning threshold | "70.0℃" |
| `opticalTransceiverParamHighAlarmThresh` | High alarm threshold | "75.0℃" |
| `opticalTransceiverParamLowWarningThresh` | Low warning threshold | "0.0℃" |
| `opticalTransceiverParamLowAlarmThresh` | Low alarm threshold | "-5.0℃" |

### Bias Current (Type 2)
| Field | Description | Example |
| --- | --- | --- |
| `opticalTransceiverParameterValue` | Current bias current | "17.23mA" |
| `opticalTransceiverParamHighWarningThresh` | High warning threshold | "80.00mA" |
| `opticalTransceiverParamHighAlarmThresh` | High alarm threshold | "100.00mA" |
| `opticalTransceiverParamLowWarningThresh` | Low warning threshold | "0.00mA" |
| `opticalTransceiverParamLowAlarmThresh` | Low alarm threshold | "0.00mA" |

### TX Optical Power (Type 3)
| Field | Description | Example |
| --- | --- | --- |
| `opticalTransceiverParameterValue` | Current TX optical power | "-6.2dBm" |
| `opticalTransceiverParamHighWarningThresh` | High warning threshold | "-3.0dBm" |
| `opticalTransceiverParamHighAlarmThresh` | High alarm threshold | "-2.5dBm" |
| `opticalTransceiverParamLowWarningThresh` | Low warning threshold | "-10.5dBm" |
| `opticalTransceiverParamLowAlarmThresh` | Low alarm threshold | "-11.0dBm" |

### RX Optical Power (Type 4)
| Field | Description | Example |
| --- | --- | --- |
| `opticalTransceiverParameterValue` | Current RX optical power | "-4.9dBm" |
| `opticalTransceiverParamHighWarningThresh` | High warning threshold | "-3.0dBm" |
| `opticalTransceiverParamHighAlarmThresh` | High alarm threshold | "-2.0dBm" |
| `opticalTransceiverParamLowWarningThresh` | Low warning threshold | "-21.0dBm" |
| `opticalTransceiverParamLowAlarmThresh` | Low alarm threshold | "-21.9dBm" |

### Voltage (Type 5)
| Field | Description | Example |
| --- | --- | --- |
| `opticalTransceiverParameterValue` | Current voltage | "3.3V" |
| `opticalTransceiverParamHighWarningThresh` | High warning threshold | "3.5V" |
| `opticalTransceiverParamHighAlarmThresh` | High alarm threshold | "3.6V" |
| `opticalTransceiverParamLowWarningThresh` | Low warning threshold | "3.1V" |
| `opticalTransceiverParamLowAlarmThresh` | Low alarm threshold | "3.0V" |

## Usage Notes
1. Each DDM parameter type returns as a separate array item identified by `opticalTransceiverParameterType`
2. The `instance` field uses the format `{ifIndex}.{sequence}` (e.g., "272908344.1") to uniquely identify each DDM parameter
3. RAX711-C-R uses `opticalTransceiverParameterType = 5` for voltage, whereas iTN167 uses `7`
4. Threshold values include the measurement unit (e.g., "75.0℃", "100.00mA", "-2.5dBm")
5. `opticalTransceiverDDM15MinValidIntervals` and `opticalTransceiverDDM24HrValidIntervals` of `"0"` indicate sampling intervals are being initialized
6. When no alarm has occurred, `opticalTransceiverParamAlarmLastValue` returns "N/A"

## Related Documentation
- [Query Optical Transceiver Information](query_optical_transceiver_info.md) - Query optical transceiver static configuration and status for RAX711-C-R
- [Query Optical Transceiver Current Status](query_optical_transceiver_current_status.md) - Query current operating status for RAX711-C-R
- [Query Optical Transceiver Digital Diagnostics (iTN167)](../167/query_optical_transceiver_ddm.md) - Equivalent endpoint for iTN167 devices
