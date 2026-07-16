# Query Optical Transceiver Four-Channel Information

## API Information
Query the four-channel monitoring parameters of optical transceivers on an RAX721 network element. Note that RAX721 10G SFP+ transceivers are single-channel devices, so this endpoint returns empty data for RAX721; the response structure below documents the expected format when data is present (e.g., for multi-channel transceivers).

## API Path
`http://XX.XX.XX.XX/tiap_ems_basic_mgt/tiap_ems_basic_mgt/v20/optical_transceiver_ddm/four`

## Request Protocol
HTTP

## Request Method
GET

## Query Parameters
| Parameter Name | Description | Required | Type | Restriction | Example |
| --- | --- | --- | --- | --- | --- |
| `neId` | Network element ID | Yes | `number` | | 127 |
| `portIndex` | Port interface index | Yes | `number` | | 272900112 |
| `page` | Page number for pagination | No | `number` | | 1 |
| `start` | Starting record offset | No | `number` | | 0 |
| `limit` | Maximum number of records per page | No | `number` | | 25 |

### Request Example
```
http://172.16.1.248/tiap_ems_basic_mgt/tiap_ems_basic_mgt/v20/optical_transceiver_ddm/four?neId=127&portIndex=272900112&page=1&start=0&limit=25
```

## Response Content
### Return Result
> Success (200)
Json object (wrapped)

| Parameter Name | Description | Required | Type | Data Dictionary | Restriction | Example |
| --- | --- | --- | --- | --- | --- | --- |
| `code` | Response status code (0 = success) | Yes | `number` | | | 0 |
| `data` | Array of four-channel DDM records | Yes | `array` | | | See example below |
| `data>>[0]` | Single channel record | Yes | `object` | | | |
| `data>>[0]>>portName` | Port name | Yes | `string` | | | "tengigabitethernet1/1/3" |
| `data>>[0]>>channelId` | Channel number | Yes | `number` | | 1 - 4 | 1 |
| `data>>[0]>>moduleTemperature` | Module temperature (with unit) | Yes | `string` | | | "33.1℃" |
| `data>>[0]>>supportVoltage` | Power supply voltage (with unit) | Yes | `string` | | | "3.3V" |
| `data>>[0]>>biasCurrent` | Bias current (with unit) | Yes | `string` | | | "33.11mA" |
| `data>>[0]>>txOpticalPower` | TX optical power (with unit) | Yes | `string` | | | "-3.4dBm" |
| `data>>[0]>>rxOpticalPower` | RX optical power (with unit) | Yes | `string` | | | "-37.0dBm" |
| `total` | Total number of records | Yes | `number` | | | 0 |

### Success Example (with data — for reference)
```json
{
  "code": 0,
  "data": [
    {
      "portName": "tengigabitethernet1/1/3",
      "channelId": 1,
      "moduleTemperature": "33.1℃",
      "supportVoltage": "3.3V",
      "biasCurrent": "33.11mA",
      "txOpticalPower": "-3.4dBm",
      "rxOpticalPower": "-37.0dBm"
    },
    {
      "portName": "tengigabitethernet1/1/3",
      "channelId": 2,
      "moduleTemperature": "33.1℃",
      "supportVoltage": "3.3V",
      "biasCurrent": "N/A",
      "txOpticalPower": "N/A",
      "rxOpticalPower": "N/A"
    },
    {
      "portName": "tengigabitethernet1/1/3",
      "channelId": 3,
      "moduleTemperature": "33.1℃",
      "supportVoltage": "3.3V",
      "biasCurrent": "N/A",
      "txOpticalPower": "N/A",
      "rxOpticalPower": "N/A"
    },
    {
      "portName": "tengigabitethernet1/1/3",
      "channelId": 4,
      "moduleTemperature": "33.1℃",
      "supportVoltage": "3.3V",
      "biasCurrent": "N/A",
      "txOpticalPower": "N/A",
      "rxOpticalPower": "N/A"
    }
  ],
  "total": 4
}
```

### Actual Response (RAX721)
```json
{
  "total": 0,
  "data": [],
  "code": 0
}
```

## Data Dictionary

### Measured Parameters (per Channel)
| Field | Description | Unit |
| --- | --- | --- |
| `moduleTemperature` | Module operating temperature | ℃ |
| `supportVoltage` | Power supply voltage | V |
| `biasCurrent` | Transmitter bias current | mA |
| `txOpticalPower` | Transmitted optical power | dBm |
| `rxOpticalPower` | Received optical power | dBm |

## Key Monitoring Parameters

### Per Channel Metrics
| Parameter Name | Description | Typical Range |
| --- | --- | --- |
| `moduleTemperature` | Module temperature | 0℃ ~ 70℃ (normal) |
| `supportVoltage` | Supply voltage | 3.0V ~ 3.7V (normal) |
| `biasCurrent` | Bias current | 0mA ~ 100mA |
| `txOpticalPower` | TX optical power | -11dBm ~ 3dBm |
| `rxOpticalPower` | RX optical power | -22dBm ~ 2.5dBm |

## Usage Notes
1. This endpoint uses a **flat per-channel structure** unlike `/optical_transceiver_ddm` which uses key-value pairs with parameter types
2. Each channel (1-4) returns as a separate record with its own measured values
3. The `portIndex` parameter is required and identifies the specific optical port interface
4. Response is wrapped in `{code: N, data: [...], total: N}` format for ExtJS grid store compatibility
5. Unlike the standard DDM endpoint, this endpoint does **not** return alarm thresholds or alarm status — it provides raw measured values only
6. All parameter values include measurement units in the string (e.g., "33.1℃", "3.3V")
7. **RAX721-specific**: RAX721 uses 10G SFP+ single-channel transceivers (USFP+-192/S1), so this endpoint returns `{"total":0,"data":[],"code":0}` — the four-channel mode is not applicable to RAX721 devices
8. For single-channel DDM data on RAX721, use the [Query Optical Transceiver Digital Diagnostics](query_optical_transceiver_ddm.md) endpoint instead
9. The `portIndex` value is the `ifIndex` from the optical transceiver info response (e.g., `272900112` for `tengigabitethernet1/1/3`)

## Related Documentation
- [Query Optical Transceiver Digital Diagnostics (RAX721)](query_optical_transceiver_ddm.md) - Standard DDM parameters with alarm thresholds for RAX721
- [Query Optical Transceiver Information (RAX721)](query_optical_transceiver_info.md) - Optical transceiver static configuration for RAX721
- [Query Optical Transceiver Current Status (RAX721)](query_optical_transceiver_current_status.md) - Current operating status for RAX721
- [Query Optical Transceiver Four-Channel Information (RAX711-C-R)](../RAX711-C-R/query_optical_transceiver_four_channel.md) - Equivalent endpoint with active data for RAX711-C-R devices
