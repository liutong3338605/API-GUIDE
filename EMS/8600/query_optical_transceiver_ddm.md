# Query Optical Transceiver Digital Diagnostic Information

## API Information
Query optical transceiver digital diagnostic monitoring (DDM) information for a specific port, including temperature, bias current, transmit/receive power, supply voltage, and their alarm/warning thresholds.

## API Path
`http://XX.XX.XX.XX/tiap_ems_north/tiap_ems_basic_mgt/v20/optical_transceiver_ddm`

## Request Protocol
HTTP

## Request Method
GET

## Query Parameters
| Parameter Name | Description | Required | Type | Restriction | Example |
| --- | --- | --- | --- | --- | --- |
| `neId` | Network Element ID | Yes | `number` | | 30 |
| `portId` | Port identifier path | Yes | `string` | Format: /ne={neId}/shelf={shelf}/slot={slot}/card={card}/port={port}#portType={type} | /ne=176/shelf=1/slot=1/card=1.1/port=1#portType=262/outerIndex=1 |
| `indexInMib` | MIB index path | Yes | `string` | Format: /ne={neId}/shelf={shelf}/slot={slot}/card={card}/port={port}#portType={type} | /ne=176/shelf=1/slot=1/card=1.1/port=0#portType=27 |
| `protocolVersion` | Protocol version | Yes | `string` | | 3 |
| `moduleType` | Module type identifier | Yes | `string` | | 18 |
| `page` | Page number | No | `number` | | 1 |
| `start` | Starting row number | No | `number` | | 0 |
| `limit` | Maximum number of rows returned | No | `number` | | 15 |

### Request Example
```
https://172.16.1.248/tiap_ems_north/tiap_ems_basic_mgt/v20/optical_transceiver_ddm?neId=30&portId=/ne=176/shelf=1/slot=1/card=1.1/port=1#portType=262/outerIndex=1&indexInMib=/ne=176/shelf=1/slot=1/card=1.1/port=0#portType=27&protocolVersion=3&moduleType=18&page=1&start=0&limit=15
```

> **Note:** The `portId` and `indexInMib` parameters contain special characters (`#`, `/`, `=`) and must be URL-encoded.

## Response Content
### Return Result
> Success (200)
Json array

| Parameter Name | Description | Required | Type | Data Dictionary | Restriction | Example |
| --- | --- | --- | --- | --- | --- | --- |
| `[0]` | DDM parameter item | Yes | `object` | | | See example below |
| `[0]>>channelId` | Channel ID | Yes | `string` | | | "--" |
| `[0]>>effectiveStatus` | Effective status | Yes | `string` | 1 = Available<br>2 = Unavailable | | "1" |
| `[0]>>neId` | Network Element ID | Yes | `number` | | | 176 |
| `[0]>>opticalTransceiverParamAlarmStatus` | Alarm status of the monitoring parameter | Yes | `string` | 1 = Normal<br>2 = High alarm<br>3 = High warning<br>4 = Low alarm<br>5 = Low warning | | "1" |
| `[0]>>opticalTransceiverParamHighAlarmThresh` | High alarm threshold | Yes | `string` | | | "90.0°C" |
| `[0]>>opticalTransceiverParamHighWarningThresh` | High warning threshold | Yes | `string` | | | "80.0°C" |
| `[0]>>opticalTransceiverParamLowAlarmThresh` | Low alarm threshold | Yes | `string` | | | "-40.0°C" |
| `[0]>>opticalTransceiverParamLowWarningThresh` | Low warning threshold | Yes | `string` | | | "-20.0°C" |
| `[0]>>opticalTransceiverParameterType` | Optical transceiver monitoring parameter type | Yes | `number` | | | 1 |
| `[0]>>opticalTransceiverParameterValue` | Optical transceiver monitoring parameter value | Yes | `string` | | | "42.738°C" |
| `[0]>>portId` | Port identifier | Yes | `string` | | | "" |
| `[0]>>unit` | Unit of measurement | Yes | `string` | | | "°C" |

### Success Example
```json
[
    {
        "channelId": "--",
        "effectiveStatus": "1",
        "neId": 176,
        "opticalTransceiverParamAlarmStatus": "1",
        "opticalTransceiverParamHighAlarmThresh": "90.0°C",
        "opticalTransceiverParamHighWarningThresh": "80.0°C",
        "opticalTransceiverParamLowAlarmThresh": "-40.0°C",
        "opticalTransceiverParamLowWarningThresh": "-20.0°C",
        "opticalTransceiverParameterType": 1,
        "opticalTransceiverParameterValue": "42.738°C",
        "portId": "",
        "unit": "°C"
    },
    {
        "channelId": "--",
        "effectiveStatus": "1",
        "neId": 176,
        "opticalTransceiverParamAlarmStatus": "1",
        "opticalTransceiverParamHighAlarmThresh": "80.0mA",
        "opticalTransceiverParamHighWarningThresh": "55.0mA",
        "opticalTransceiverParamLowAlarmThresh": "5.0mA",
        "opticalTransceiverParamLowWarningThresh": "10.0mA",
        "opticalTransceiverParameterType": 2,
        "opticalTransceiverParameterValue": "22.014mA",
        "portId": "",
        "unit": "mA"
    },
    {
        "channelId": "--",
        "effectiveStatus": "1",
        "neId": 176,
        "opticalTransceiverParamAlarmStatus": "1",
        "opticalTransceiverParamHighAlarmThresh": "0.0dBm",
        "opticalTransceiverParamHighWarningThresh": "-3.0dBm",
        "opticalTransceiverParamLowAlarmThresh": "-12.006dBm",
        "opticalTransceiverParamLowWarningThresh": "-9.003dBm",
        "opticalTransceiverParameterType": 3,
        "opticalTransceiverParameterValue": "-5.984dBm",
        "portId": "",
        "unit": "dBm"
    },
    {
        "channelId": "--",
        "effectiveStatus": "1",
        "neId": 176,
        "opticalTransceiverParamAlarmStatus": "4",
        "opticalTransceiverParamHighAlarmThresh": "0.0dBm",
        "opticalTransceiverParamHighWarningThresh": "-3.0dBm",
        "opticalTransceiverParamLowAlarmThresh": "-28.239dBm",
        "opticalTransceiverParamLowWarningThresh": "-25.086dBm",
        "opticalTransceiverParameterType": 4,
        "opticalTransceiverParameterValue": "-60.0dBm",
        "portId": "",
        "unit": "dBm"
    },
    {
        "channelId": "--",
        "effectiveStatus": "1",
        "neId": 176,
        "opticalTransceiverParamAlarmStatus": "1",
        "opticalTransceiverParamHighAlarmThresh": "3.8v",
        "opticalTransceiverParamHighWarningThresh": "3.5v",
        "opticalTransceiverParamLowAlarmThresh": "2.9v",
        "opticalTransceiverParamLowWarningThresh": "3.1v",
        "opticalTransceiverParameterType": 7,
        "opticalTransceiverParameterValue": "3.327v",
        "portId": "",
        "unit": "v"
    }
]
```

## Key Monitoring Parameters

### Alarm Status
| Parameter Name | Data Dictionary |
| --- | --- |
| `opticalTransceiverParamAlarmStatus` | 1 = Normal<br>2 = High alarm<br>3 = High warning<br>4 = Low alarm<br>5 = Low warning |

### Effective Status
| Parameter Name | Data Dictionary |
| --- | --- |
| `effectiveStatus` | 1 = Available<br>2 = Unavailable |

## Data Dictionary

### opticalTransceiverParamAlarmStatus
| Value | Meaning |
| --- | --- |
| 1 | Normal |
| 2 | High alarm |
| 3 | High warning |
| 4 | Low alarm |
| 5 | Low warning |

### effectiveStatus
| Value | Meaning |
| --- | --- |
| 1 | Available |
| 2 | Unavailable |

## Usage Notes
1. The `portId` and `indexInMib` parameters contain special characters (`#`, `/`, `=`) and must be URL-encoded when passed as query parameters.
2. Each array item represents one DDM parameter type (temperature, bias current, TX power, RX power, supply voltage, etc.). The `opticalTransceiverParameterType` field identifies which parameter is being reported.
3. The `unit` field indicates the unit of measurement for the current parameter value and thresholds.
4. Threshold values include the unit suffix (e.g., `"90.0°C"`, `"80.0mA"`, `"0.0dBm"`) — parsing should account for the unit suffix.

## Related Documentation
- [Query Optical Transceiver Information](query_optical_transceiver_information.md) - Query optical module basic information
- [Query Port Information](query_port_information.md) - Query port link status and working speed
