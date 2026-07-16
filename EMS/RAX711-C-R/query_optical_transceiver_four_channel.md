# Query Optical Transceiver Four-Channel Information

## API Information
Query the four-channel monitoring parameters of optical transceivers on an RAX711-C-R network element, returning per-channel temperature, voltage, bias current, TX optical power, and RX optical power in a flat tabular structure.

## API Path
`http://XX.XX.XX.XX/tiap_ems_north/tiap_ems_basic_mgt/v20/optical_transceiver_ddm/four`

## Request Protocol
HTTP

## Request Method
GET

## Query Parameters
| Parameter Name | Description | Required | Type | Restriction | Example |
| --- | --- | --- | --- | --- | --- |
| `neId` | Network element ID | Yes | `number` | | 220 |
| `portIndex` | Port interface index | Yes | `number` | | 272908344 |
| `page` | Page number for pagination | No | `number` | | 1 |
| `start` | Starting record offset | No | `number` | | 0 |
| `limit` | Maximum number of records per page | No | `number` | | 25 |

### Request Example
```
http://172.16.1.248/tiap_ems_north/tiap_ems_basic_mgt/v20/optical_transceiver_ddm/four?neId=220&portIndex=272908344&page=1&start=0&limit=25
```

## Response Content
### Return Result
> Success (200)
Json object (wrapped)

| Parameter Name | Description | Required | Type | Data Dictionary | Restriction | Example |
| --- | --- | --- | --- | --- | --- | --- |
| `data` | Array of four-channel DDM records | Yes | `array` | | | See example below |
| `data>>[0]` | Single channel record | Yes | `object` | | | |
| `data>>[0]>>portName` | Port name | Yes | `string` | | | "gigaethernet1/2/8" |
| `data>>[0]>>channelId` | Channel number | Yes | `number` | | 1 - 4 | 1 |
| `data>>[0]>>moduleTemperature` | Module temperature (with unit) | Yes | `string` | | | "37.7℃" |
| `data>>[0]>>supportVoltage` | Power supply voltage (with unit) | Yes | `string` | | | "3.3V" |
| `data>>[0]>>biasCurrent` | Bias current (with unit) | Yes | `string` | | | "17.23mA" |
| `data>>[0]>>txOpticalPower` | TX optical power (with unit) | Yes | `string` | | | "-6.2dBm" |
| `data>>[0]>>rxOpticalPower` | RX optical power (with unit) | Yes | `string` | | | "-4.9dBm" |
| `total` | Total number of records | Yes | `number` | | | 4 |

### Success Example
```json
{
  "data": [
    {
      "portName": "gigaethernet1/2/8",
      "channelId": 1,
      "moduleTemperature": "37.7℃",
      "supportVoltage": "3.3V",
      "biasCurrent": "17.23mA",
      "txOpticalPower": "-6.2dBm",
      "rxOpticalPower": "-4.9dBm"
    },
    {
      "portName": "gigaethernet1/2/8",
      "channelId": 2,
      "moduleTemperature": "37.7℃",
      "supportVoltage": "3.3V",
      "biasCurrent": "16.85mA",
      "txOpticalPower": "-6.5dBm",
      "rxOpticalPower": "-5.1dBm"
    },
    {
      "portName": "gigaethernet1/2/8",
      "channelId": 3,
      "moduleTemperature": "37.7℃",
      "supportVoltage": "3.3V",
      "biasCurrent": "17.10mA",
      "txOpticalPower": "-6.0dBm",
      "rxOpticalPower": "-4.8dBm"
    },
    {
      "portName": "gigaethernet1/2/8",
      "channelId": 4,
      "moduleTemperature": "37.7℃",
      "supportVoltage": "3.3V",
      "biasCurrent": "16.92mA",
      "txOpticalPower": "-6.4dBm",
      "rxOpticalPower": "-5.2dBm"
    }
  ],
  "total": 4
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
| `supportVoltage` | Supply voltage | 3.0V ~ 3.6V (normal) |
| `biasCurrent` | Bias current | 0mA ~ 100mA |
| `txOpticalPower` | TX optical power | -11dBm ~ -2.5dBm |
| `rxOpticalPower` | RX optical power | -22dBm ~ -2dBm |

## Usage Notes
1. This endpoint uses a **flat per-channel structure** unlike `/optical_transceiver_ddm` which uses key-value pairs with parameter types
2. Each channel (1-4) returns as a separate record with its own measured values
3. The `portIndex` parameter is required and identifies the specific optical port interface
4. Response is wrapped in `{data: [...], total: N}` format for ExtJS grid store compatibility
5. Unlike the standard DDM endpoint, this endpoint does **not** return alarm thresholds or alarm status — it provides raw measured values only
6. All parameter values include measurement units in the string (e.g., "37.7℃", "3.3V")

## Related Documentation
- [Query Optical Transceiver Digital Diagnostics](query_optical_transceiver_ddm.md) - Standard DDM parameters with alarm thresholds for RAX711-C-R
- [Query Optical Transceiver Information](query_optical_transceiver_info.md) - Optical transceiver static configuration for RAX711-C-R
