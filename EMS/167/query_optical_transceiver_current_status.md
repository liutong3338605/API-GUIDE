# Query Optical Transceiver Current Status

## API Information
Query the current operating status of optical transceivers on a specific network element, including CRC check status, DDM enable state, hardware information, loopback status, and port notification configuration.

## API Path
`http://XX.XX.XX.XX/tiap_ems_north/tiap_ems_basic_mgt/v20/optical_transceiver_current_status`

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
http://172.16.1.248/tiap_ems_north/tiap_ems_basic_mgt/v20/optical_transceiver_current_status?neId=283&page=1&start=0&limit=25
```

## Response Content
### Return Result
> Success (200)
Json array

| Parameter Name | Description | Required | Type | Data Dictionary | Restriction | Example |
| --- | --- | --- | --- | --- | --- | --- |
| `[0]` | Current status item | Yes | `object` | | | See example below |
| `[0]>>ifIndex` | Interface index | Yes | `number` | | | 1 |
| `[0]>>neId` | Network element ID | Yes | `number` | | | 283 |
| `[0]>>opticalTransceiverBaseCRCCheckStatus` | Base CRC check status | Yes | `number` | 1 = Normal<br>2 = Failure | | 1 |
| `[0]>>opticalTransceiverDynamicDdmCRCCheckStatus` | Dynamic DDM CRC check status | Yes | `number` | 1 = Normal<br>2 = Failure | | 1 |
| `[0]>>opticalTransceiverFecAppType` | FEC application type | Yes | `number` | | | 0 |
| `[0]>>opticalTransceiverFrequnecyGrid` | Frequency grid | Yes | `number` | | | 0 |
| `[0]>>opticalTransceiverHwInfoAbsStatus` | Hardware absent/removed status | Yes | `number` | 1 = Present<br>2 = Absent | | 2 |
| `[0]>>opticalTransceiverHwInfoLaser` | Laser hardware status | Yes | `number` | 1 = Normal<br>2 = Failure<br>-1 = N/A | | -1 |
| `[0]>>opticalTransceiverHwInfoNRStatus` | Hardware not-ready status | Yes | `number` | 1 = Ready<br>2 = Not Ready<br>-1 = N/A | | -1 |
| `[0]>>opticalTransceiverHwInfoRxLosStatus` | RX loss of signal status | Yes | `number` | 1 = Normal<br>2 = LOS | | 1 |
| `[0]>>opticalTransceiverHwInfoStandby` | Hardware standby status | Yes | `number` | 1 = Active<br>2 = Standby<br>-1 = N/A | | -1 |
| `[0]>>opticalTransceiverPortCRCCheckEnable` | Port CRC check enable status | Yes | `number` | 1 = Enabled<br>2 = Disabled | | 1 |
| `[0]>>opticalTransceiverPortDDMEnable` | Port DDM enable status | Yes | `number` | 1 = Enabled<br>2 = Disabled | | 1 |
| `[0]>>opticalTransceiverPortNotifyEnable` | Port notification enable status | Yes | `number` | 1 = Enabled<br>2 = Disabled | | 1 |
| `[0]>>opticalTransceiverStaticDdmCRCCheckStatus` | Static DDM CRC check status | Yes | `number` | 1 = Normal<br>2 = Failure | | 1 |
| `[0]>>opticalTransceiverUserLineLoopBack` | User line loopback status | Yes | `number` | 1 = Active<br>2 = Inactive<br>-1 = N/A | | -1 |
| `[0]>>opticalTransceiverUserXFILoopBack` | User XFI loopback status | Yes | `number` | 1 = Active<br>2 = Inactive<br>-1 = N/A | | -1 |
| `[0]>>portName` | Port name | Yes | `string` | | | "NNI 1" |

### Success Example
```json
[
  {
    "ifIndex": 1,
    "neId": 283,
    "opticalTransceiverBaseCRCCheckStatus": 1,
    "opticalTransceiverDynamicDdmCRCCheckStatus": 1,
    "opticalTransceiverFecAppType": 0,
    "opticalTransceiverFrequnecyGrid": 0,
    "opticalTransceiverHwInfoAbsStatus": 2,
    "opticalTransceiverHwInfoLaser": -1,
    "opticalTransceiverHwInfoNRStatus": -1,
    "opticalTransceiverHwInfoRxLosStatus": 1,
    "opticalTransceiverHwInfoStandby": -1,
    "opticalTransceiverPortCRCCheckEnable": 1,
    "opticalTransceiverPortDDMEnable": 1,
    "opticalTransceiverPortNotifyEnable": 1,
    "opticalTransceiverStaticDdmCRCCheckStatus": 1,
    "opticalTransceiverUserLineLoopBack": -1,
    "opticalTransceiverUserXFILoopBack": -1,
    "portName": "NNI 1"
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

### CRC Check Status
| Value | Meaning |
| --- | --- |
| 1 | Normal (Pass) |
| 2 | Failure |

### Loopback Status
| Value | Meaning |
| --- | --- |
| 1 | Active |
| 2 | Inactive |
| -1 | Not Applicable |

## Key Monitoring Parameters

### CRC Check & Health
| Parameter Name | Description | Example |
| --- | --- | --- |
| `opticalTransceiverBaseCRCCheckStatus` | Base firmware CRC integrity | 1 |
| `opticalTransceiverStaticDdmCRCCheckStatus` | Static DDM data CRC integrity | 1 |
| `opticalTransceiverDynamicDdmCRCCheckStatus` | Dynamic DDM data CRC integrity | 1 |

### Hardware Status
| Parameter Name | Description | Example |
| --- | --- | --- |
| `opticalTransceiverHwInfoRxLosStatus` | RX loss of signal status | 1 |
| `opticalTransceiverHwInfoAbsStatus` | Module presence status | 2 |
| `opticalTransceiverHwInfoLaser` | Laser status | -1 |
| `opticalTransceiverHwInfoNRStatus` | Module ready status | -1 |
| `opticalTransceiverHwInfoStandby` | Standby status | -1 |

### Port Configuration
| Parameter Name | Description | Example |
| --- | --- | --- |
| `opticalTransceiverPortDDMEnable` | DDM monitoring enabled | 1 |
| `opticalTransceiverPortCRCCheckEnable` | CRC check enabled | 1 |
| `opticalTransceiverPortNotifyEnable` | Port notification enabled | 1 |

## Usage Notes
1. A value of `-1` indicates the feature is not applicable or not supported for this transceiver type
2. CRC check status fields should all return `1` for a normally operating transceiver
3. `opticalTransceiverHwInfoAbsStatus = 2` does not necessarily mean a fault; verify with the physical device
4. Loopback fields returning `-1` indicate the transceiver does not support loopback functionality

## Related Documentation
- [Query Optical Transceiver Status](query_optical_transceiver_status.md) - Query optical transceiver static configuration and status
- [Query Optical Transceiver Digital Diagnostics](query_optical_transceiver_ddm.md) - Query DDM monitoring parameters with alarm thresholds
