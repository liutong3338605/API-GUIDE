# Query Optical Transceiver Digital Diagnostics

## API Information
Query digital diagnostics monitoring (DDM) parameters for optical transceivers on a specific network element, including temperature, bias current, TX/RX optical power, and power supply voltage with alarm thresholds.

## API Path
`http://XX.XX.XX.XX/tiap_ems_north/tiap_ems_basic_mgt/v20/optical_transceiver_ddm`

## Request Protocol
HTTP

## Request Method
GET

## Query Parameters
| Parameter Name | Description | Required | Type | Restriction | Example |
| --- | --- | --- | --- | --- | --- |
| `neId` | Network element ID | Yes | `number` | | 283 |
| `page` | Page number for pagination | No | `number` | | 1 |
| `start` | Starting record offset | No | `number` | | 0 |
| `limit` | Maximum number of records per page | No | `number` | | 25 |

### Request Example
```
http://172.16.1.248/tiap_ems_north/tiap_ems_basic_mgt/v20/optical_transceiver_ddm?neId=283&page=1&start=0&limit=25
```

## Response Content
### Return Result
> Success (200)
Json array

| Parameter Name | Description | Required | Type | Data Dictionary | Restriction | Example |
| --- | --- | --- | --- | --- | --- | --- |
| `[0]` | DDM parameter item | Yes | `object` | | | See example below |
| `[0]>>ifIndex` | Interface index | Yes | `string` | | | "1" |
| `[0]>>instance` | DDM parameter instance identifier | Yes | `string` | | | "1.1" |
| `[0]>>neId` | Network element ID | Yes | `number` | | | 283 |
| `[0]>>opticalTransceiverDDM15MinValidIntervals` | Valid 15-minute DDM sampling intervals | Yes | `string` | | | "4" |
| `[0]>>opticalTransceiverDDM24HrValidIntervals` | Valid 24-hour DDM sampling intervals | Yes | `string` | | | "1" |
| `[0]>>opticalTransceiverParamAlarmLastChange` | Time since last alarm state change | Yes | `string` | | | "0 hours, 0 minutes, 0 seconds" |
| `[0]>>opticalTransceiverParamAlarmLastValue` | Last alarm parameter value | Yes | `string` | | | "N/A" |
| `[0]>>opticalTransceiverParamAlarmStatus` | Parameter alarm status | Yes | `string` | 1 = Normal<br>2 = Warning<br>3 = Alarm | | "1" |
| `[0]>>opticalTransceiverParamHighAlarmThresh` | High alarm threshold | Yes | `string` | | | "80.0℃" |
| `[0]>>opticalTransceiverParamHighWarningThresh` | High warning threshold | Yes | `string` | | | "75.0℃" |
| `[0]>>opticalTransceiverParamLowAlarmThresh` | Low alarm threshold | Yes | `string` | | | "-5.0℃" |
| `[0]>>opticalTransceiverParamLowWarningThresh` | Low warning threshold | Yes | `string` | | | "0.0℃" |
| `[0]>>opticalTransceiverParameterType` | DDM parameter type | Yes | `number` | 1 = Temperature<br>2 = Bias Current<br>3 = TX Optical Power<br>4 = RX Optical Power<br>7 = Power Supply Voltage | | 1 |
| `[0]>>opticalTransceiverParameterValue` | Current parameter value (with unit) | Yes | `string` | | | "46.3℃" |
| `[0]>>portName` | Port name | Yes | `string` | | | "NNI 1" |

### Success Example
```json
[
  {
    "ifIndex": "1",
    "instance": "1.1",
    "neId": 283,
    "opticalTransceiverDDM15MinValidIntervals": "4",
    "opticalTransceiverDDM24HrValidIntervals": "1",
    "opticalTransceiverParamAlarmLastChange": "0 hours, 0 minutes, 0 seconds",
    "opticalTransceiverParamAlarmLastValue": "N/A",
    "opticalTransceiverParamAlarmStatus": "1",
    "opticalTransceiverParamHighAlarmThresh": "80.0℃",
    "opticalTransceiverParamHighWarningThresh": "75.0℃",
    "opticalTransceiverParamLowAlarmThresh": "-5.0℃",
    "opticalTransceiverParamLowWarningThresh": "0.0℃",
    "opticalTransceiverParameterType": 1,
    "opticalTransceiverParameterValue": "46.3℃",
    "portName": "NNI 1"
  },
  {
    "ifIndex": "1",
    "instance": "1.2",
    "neId": 283,
    "opticalTransceiverDDM15MinValidIntervals": "4",
    "opticalTransceiverDDM24HrValidIntervals": "1",
    "opticalTransceiverParamAlarmLastChange": "0 hours, 0 minutes, 0 seconds",
    "opticalTransceiverParamAlarmLastValue": "N/A",
    "opticalTransceiverParamAlarmStatus": "1",
    "opticalTransceiverParamHighAlarmThresh": "100.00mA",
    "opticalTransceiverParamHighWarningThresh": "80.00mA",
    "opticalTransceiverParamLowAlarmThresh": "0.00mA",
    "opticalTransceiverParamLowWarningThresh": "0.00mA",
    "opticalTransceiverParameterType": 2,
    "opticalTransceiverParameterValue": "9.86mA",
    "portName": "NNI 1"
  },
  {
    "ifIndex": "1",
    "instance": "1.3",
    "neId": 283,
    "opticalTransceiverDDM15MinValidIntervals": "4",
    "opticalTransceiverDDM24HrValidIntervals": "1",
    "opticalTransceiverParamAlarmLastChange": "0 hours, 0 minutes, 0 seconds",
    "opticalTransceiverParamAlarmLastValue": "N/A",
    "opticalTransceiverParamAlarmStatus": "1",
    "opticalTransceiverParamHighAlarmThresh": "-2.5dBm",
    "opticalTransceiverParamHighWarningThresh": "-3.0dBm",
    "opticalTransceiverParamLowAlarmThresh": "-11.0dBm",
    "opticalTransceiverParamLowWarningThresh": "-10.5dBm",
    "opticalTransceiverParameterType": 3,
    "opticalTransceiverParameterValue": "-6.0dBm",
    "portName": "NNI 1"
  },
  {
    "ifIndex": "1",
    "instance": "1.4",
    "neId": 283,
    "opticalTransceiverDDM15MinValidIntervals": "4",
    "opticalTransceiverDDM24HrValidIntervals": "1",
    "opticalTransceiverParamAlarmLastChange": "3 hours, 34 minutes, 47 seconds",
    "opticalTransceiverParamAlarmLastValue": "-40.0dBm",
    "opticalTransceiverParamAlarmStatus": "1",
    "opticalTransceiverParamHighAlarmThresh": "-2.0dBm",
    "opticalTransceiverParamHighWarningThresh": "-3.0dBm",
    "opticalTransceiverParamLowAlarmThresh": "-22.9dBm",
    "opticalTransceiverParamLowWarningThresh": "-21.9dBm",
    "opticalTransceiverParameterType": 4,
    "opticalTransceiverParameterValue": "-3.9dBm",
    "portName": "NNI 1"
  },
  {
    "ifIndex": "1",
    "instance": "1.7",
    "neId": 283,
    "opticalTransceiverDDM15MinValidIntervals": "4",
    "opticalTransceiverDDM24HrValidIntervals": "1",
    "opticalTransceiverParamAlarmLastChange": "0 hours, 0 minutes, 0 seconds",
    "opticalTransceiverParamAlarmLastValue": "N/A",
    "opticalTransceiverParamAlarmStatus": "1",
    "opticalTransceiverParamHighAlarmThresh": "3.600V",
    "opticalTransceiverParamHighWarningThresh": "3.500V",
    "opticalTransceiverParamLowAlarmThresh": "3.000V",
    "opticalTransceiverParamLowWarningThresh": "3.100V",
    "opticalTransceiverParameterType": 7,
    "opticalTransceiverParameterValue": "3.294V",
    "portName": "NNI 1"
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
| 7 | Power Supply Voltage | V |

### opticalTransceiverParamAlarmStatus
| Value | Description |
| --- | --- |
| 1 | Normal |
| 2 | Warning |
| 3 | Alarm |

## Key Monitoring Parameters

### Temperature (Type 1)
| Field | Description |
| --- | --- |
| `opticalTransceiverParameterValue` | Current module temperature |
| `opticalTransceiverParamHighWarningThresh` | High warning threshold |
| `opticalTransceiverParamHighAlarmThresh` | High alarm threshold |
| `opticalTransceiverParamLowWarningThresh` | Low warning threshold |
| `opticalTransceiverParamLowAlarmThresh` | Low alarm threshold |

### Bias Current (Type 2)
| Field | Description |
| --- | --- |
| `opticalTransceiverParameterValue` | Current bias current |
| `opticalTransceiverParamHighWarningThresh` | High warning threshold |
| `opticalTransceiverParamHighAlarmThresh` | High alarm threshold |
| `opticalTransceiverParamLowWarningThresh` | Low warning threshold |
| `opticalTransceiverParamLowAlarmThresh` | Low alarm threshold |

### TX Optical Power (Type 3) / RX Optical Power (Type 4)
| Field | Description |
| --- | --- |
| `opticalTransceiverParameterValue` | Current optical power |
| `opticalTransceiverParamHighWarningThresh` | High warning threshold |
| `opticalTransceiverParamHighAlarmThresh` | High alarm threshold |
| `opticalTransceiverParamLowWarningThresh` | Low warning threshold |
| `opticalTransceiverParamLowAlarmThresh` | Low alarm threshold |

### Power Supply Voltage (Type 7)
| Field | Description |
| --- | --- |
| `opticalTransceiverParameterValue` | Current supply voltage |
| `opticalTransceiverParamHighWarningThresh` | High warning threshold |
| `opticalTransceiverParamHighAlarmThresh` | High alarm threshold |
| `opticalTransceiverParamLowWarningThresh` | Low warning threshold |
| `opticalTransceiverParamLowAlarmThresh` | Low alarm threshold |

## Usage Notes
1. Each DDM parameter type returns as a separate array item identified by `opticalTransceiverParameterType`
2. The `instance` field uniquely identifies each DDM parameter instance (e.g., "1.1" for temperature, "1.2" for bias current)
3. Threshold values include the measurement unit (e.g., "80.0℃", "100.00mA", "-2.5dBm")
4. `opticalTransceiverParamAlarmStatus` value of "1" indicates the parameter is within normal range
5. When no alarm has occurred, `opticalTransceiverParamAlarmLastValue` returns "N/A" and `opticalTransceiverParamAlarmLastChange` returns "0 hours, 0 minutes, 0 seconds"
6. `opticalTransceiverDDM15MinValidIntervals` and `opticalTransceiverDDM24HrValidIntervals` indicate the number of valid sampling intervals collected

## Related Documentation
- [Query Optical Transceiver Status](query_optical_transceiver_status.md) - Query optical transceiver static configuration and status information
