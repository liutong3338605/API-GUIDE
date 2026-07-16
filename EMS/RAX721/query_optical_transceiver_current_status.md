# Query Optical Transceiver Current Status

## API Information
Query the current operating status of optical transceivers on a specific RAX721 network element, including hardware information, port configuration, DDM enable state, and loopback status.

## API Path
`http://XX.XX.XX.XX/tiap_ems_basic_mgt/tiap_ems_basic_mgt/v20/optical_transceiver_current_status`

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
http://172.16.1.248/tiap_ems_basic_mgt/tiap_ems_basic_mgt/v20/optical_transceiver_current_status?neId=127&page=1&start=0&limit=25
```

## Response Content
### Return Result
> Success (200)
Json array

| Parameter Name | Description | Required | Type | Data Dictionary | Restriction | Example |
| --- | --- | --- | --- | --- | --- | --- |
| `[0]` | Current status item | Yes | `object` | | | See example below |
| `[0]>>ifIndex` | Interface index | Yes | `number` | | | 272900096 |
| `[0]>>neId` | Network element ID | Yes | `number` | | | 127 |
| `[0]>>opticalTransceiverFecAppType` | FEC application type | Yes | `number` | | | 0 |
| `[0]>>opticalTransceiverFrequnecyGrid` | Frequency grid | Yes | `number` | | | 0 |
| `[0]>>opticalTransceiverHwInfoAbsStatus` | Hardware absent/removed status | Yes | `number` | 1 = Present<br>2 = Absent | | 2 |
| `[0]>>opticalTransceiverHwInfoLaser` | Laser hardware status | Yes | `number` | 1 = Normal<br>2 = Failure<br>-1 = N/A | | 1 |
| `[0]>>opticalTransceiverHwInfoNRStatus` | Hardware not-ready status | Yes | `number` | 1 = Ready<br>2 = Not Ready<br>-1 = N/A | | -1 |
| `[0]>>opticalTransceiverHwInfoRxLosStatus` | RX loss of signal status | Yes | `number` | 1 = Normal<br>2 = LOS | | 1 |
| `[0]>>opticalTransceiverHwInfoStandby` | Hardware standby status | Yes | `number` | 1 = Active<br>2 = Standby<br>-1 = N/A | | -1 |
| `[0]>>opticalTransceiverPortCheckPwdEnable` | Port password check enable status | Yes | `number` | 1 = Enabled<br>2 = Disabled | | 1 |
| `[0]>>opticalTransceiverPortDDMEnable` | Port DDM enable status | Yes | `number` | 1 = Enabled<br>2 = Disabled | | 1 |
| `[0]>>opticalTransceiverPortNotifyEnable` | Port notification enable status | Yes | `number` | 1 = Enabled<br>2 = Disabled | | 1 |
| `[0]>>opticalTransceiverUserLineLoopBack` | User line loopback status | Yes | `number` | 1 = Active<br>2 = Inactive<br>-1 = N/A | | -1 |
| `[0]>>opticalTransceiverUserXFILoopBack` | User XFI loopback status | Yes | `number` | 1 = Active<br>2 = Inactive<br>-1 = N/A | | -1 |
| `[0]>>portName` | Port name | Yes | `string` | | | "tengigabitethernet1/1/1" |

### Success Example
```json
[
  {
    "ifIndex": 272900096,
    "neId": 127,
    "opticalTransceiverFecAppType": 0,
    "opticalTransceiverFrequnecyGrid": 0,
    "opticalTransceiverHwInfoAbsStatus": 2,
    "opticalTransceiverHwInfoLaser": 1,
    "opticalTransceiverHwInfoNRStatus": -1,
    "opticalTransceiverHwInfoRxLosStatus": 1,
    "opticalTransceiverHwInfoStandby": -1,
    "opticalTransceiverPortCheckPwdEnable": 1,
    "opticalTransceiverPortDDMEnable": 1,
    "opticalTransceiverPortNotifyEnable": 1,
    "opticalTransceiverUserLineLoopBack": -1,
    "opticalTransceiverUserXFILoopBack": -1,
    "portName": "tengigabitethernet1/1/1"
  },
  {
    "ifIndex": 272900112,
    "neId": 127,
    "opticalTransceiverFecAppType": 0,
    "opticalTransceiverFrequnecyGrid": 0,
    "opticalTransceiverHwInfoAbsStatus": 2,
    "opticalTransceiverHwInfoLaser": 1,
    "opticalTransceiverHwInfoNRStatus": -1,
    "opticalTransceiverHwInfoRxLosStatus": 2,
    "opticalTransceiverHwInfoStandby": -1,
    "opticalTransceiverPortCheckPwdEnable": 1,
    "opticalTransceiverPortDDMEnable": 1,
    "opticalTransceiverPortNotifyEnable": 1,
    "opticalTransceiverUserLineLoopBack": -1,
    "opticalTransceiverUserXFILoopBack": -1,
    "portName": "tengigabitethernet1/1/3"
  }
]
```

## Data Dictionary

### Status / Enable Fields
| Value | Meaning |
| --- | --- |
| 1 | Enabled / Normal / Active / Present |
| 2 | Disabled / Failure / Inactive / Absent |
| -1 | Not Applicable / Not Supported |

### Hardware Status Fields
| Field | 1 | 2 | -1 |
| --- | --- | --- | --- |
| `opticalTransceiverHwInfoAbsStatus` | Present | Absent | — |
| `opticalTransceiverHwInfoLaser` | Normal | Failure | N/A |
| `opticalTransceiverHwInfoNRStatus` | Ready | Not Ready | N/A |
| `opticalTransceiverHwInfoRxLosStatus` | Normal | LOS | — |
| `opticalTransceiverHwInfoStandby` | Active | Standby | N/A |

### Loopback Status
| Value | Meaning |
| --- | --- |
| 1 | Active |
| 2 | Inactive |
| -1 | Not Applicable |

## Key Monitoring Parameters

### Hardware Health
| Parameter Name | Description | Example |
| --- | --- | --- |
| `opticalTransceiverHwInfoRxLosStatus` | RX loss of signal status | 1 |
| `opticalTransceiverHwInfoLaser` | Laser status | 1 |
| `opticalTransceiverHwInfoAbsStatus` | Module presence status | 2 |
| `opticalTransceiverHwInfoNRStatus` | Module ready status | -1 |
| `opticalTransceiverHwInfoStandby` | Standby status | -1 |

### Port Configuration
| Parameter Name | Description | Example |
| --- | --- | --- |
| `opticalTransceiverPortDDMEnable` | DDM monitoring enabled | 1 |
| `opticalTransceiverPortCheckPwdEnable` | Password check enabled | 1 |
| `opticalTransceiverPortNotifyEnable` | Port notification enabled | 1 |

### Loopback
| Parameter Name | Description | Example |
| --- | --- | --- |
| `opticalTransceiverUserLineLoopBack` | Line loopback status | -1 |
| `opticalTransceiverUserXFILoopBack` | XFI loopback status | -1 |

## Usage Notes
1. Unlike iTN167, the RAX721 does not expose CRC check status fields in this endpoint
2. `opticalTransceiverPortCheckPwdEnable` controls optical transceiver password verification on RAX721 devices
3. `opticalTransceiverHwInfoLaser = 1` indicates the laser hardware is in normal operating condition
4. `opticalTransceiverHwInfoRxLosStatus = 2` on `tengigabitethernet1/1/3` indicates loss of signal (LOS) on the RX path, consistent with the RX optical power Critical Alarm (-37.0dBm) observed in DDM data for this port
5. `opticalTransceiverHwInfoAbsStatus = 2` (Absent) despite the transceiver being operational — this may indicate the module is not physically reported as present in the hardware inventory but is functionally active
6. A value of `-1` indicates the feature is not applicable or not supported for this transceiver type
7. Port names follow the format `tengigabitethernet{slot}/{subslot}/{port}`

## Related Documentation
- [Query Optical Transceiver Information (RAX721)](query_optical_transceiver_info.md) - Query optical transceiver static configuration and status for RAX721
- [Query Optical Transceiver Digital Diagnostics (RAX721)](query_optical_transceiver_ddm.md) - DDM parameters with alarm thresholds for RAX721
- [Query Optical Transceiver Current Status (RAX711-C-R)](../RAX711-C-R/query_optical_transceiver_current_status.md) - Equivalent endpoint for RAX711-C-R devices
