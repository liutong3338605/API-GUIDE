# Query Optical Transceiver Status

## API Information
Query optical transceiver current status for a specific port, including OSNR, FEC configuration, hardware control information, dispersion compensation, OCH power monitoring, and alarm/warning thresholds.

## API Path
`http://XX.XX.XX.XX/tiap_ems_north/tiap_ems_basic_mgt/v20/optical_transceiver_current_status`

## Request Protocol
HTTP

## Request Method
GET

## Query Parameters
| Parameter Name | Description | Required | Type | Restriction | Example |
| --- | --- | --- | --- | --- | --- |
| `neId` | Network element ID | Yes | `number` | | 176 |
| `portId` | Port identifier path | Yes | `string` | | /ne=176/shelf=1/slot=1/card=1.1/port=1#portType=262/outerIndex=1 |
| `indexInMib` | MIB index path | Yes | `string` | | /ne=176/shelf=1/slot=1/card=1.1/port=0#portType=27 |
| `protocolVersion` | Protocol version | Yes | `string` | | 3 |
| `moduleType` | Module type identifier | Yes | `string` | | 18 |
| `page` | Page number | No | `number` | | 1 |
| `start` | Record start index | No | `number` | | 0 |
| `limit` | Maximum records per page | No | `number` | | 15 |

### Request Example
```
http://172.16.1.248/tiap_ems_north/tiap_ems_basic_mgt/v20/optical_transceiver_current_status?neId=176&portId=/ne=176/shelf=1/slot=1/card=1.1/port=1%23portType=262/outerIndex=1&indexInMib=/ne=176/shelf=1/slot=1/card=1.1/port=0%23portType=27&protocolVersion=3&moduleType=18&page=1&start=0&limit=15
```

> **Note:** Parameters containing `#` characters (e.g., `portId`, `indexInMib`) must be URL-encoded as `%23`.

## Response Content
### Return Result
> Success (200)
Json array

| Parameter Name | Description | Required | Type | Data Dictionary | Restriction | Example |
| --- | --- | --- | --- | --- | --- | --- |
| **Basic Information** | | | | | | |
| `[0]>>neId` | Network element ID | Yes | `number` | | | 176 |
| `[0]>>portId` | Port identifier path | Yes | `string` | | | /ne=176/shelf=1/slot=1/card=1.1/port=1#portType=262/outerIndex=1 |
| **Hardware Controlling Info** | | | | | | |
| `[0]>>opticalTransceiverHwInfoAbsStatus` | Optical module hardware controlling info in-position status | Yes | `number` | 1=Absent, 2=In position | | 2 |
| `[0]>>opticalTransceiverHwInfoLaser` | Optical module hardware controlling info LASER status | Yes | `number` | 1=ON, 2=OFF | | 1 |
| `[0]>>opticalTransceiverHwInfoStandby` | Optical module standby mode | Yes | `number` | 1=Normal, 2=Standby | | 1 |
| `[0]>>laserShutdownRealStatus` | Laser real shutdown status | Yes | `number` | 1=ON, 2=OFF | | 1 |
| **Authorization & Parity** | | | | | | |
| `[0]>>authorizationCheckResult` | Authorization check result | Yes | `string` | 1=Success, 2=Failed, 3=Partial Success | | "" |
| `[0]>>parityEnable` | Parity enable status | Yes | `string` | 0=Disable, 1=Enable | | "" |
| **Speed & Rate** | | | | | | |
| `[0]>>speed` | Speed (Mbps) | Yes | `string` | | | "" |
| `[0]>>opticalTransceiverRate` | Optical transceiver rate | Yes | `string` | See Data Dictionary | | "" |
| **CFP Configuration** | | | | | | |
| `[0]>>cfpFormat` | Cfp format | Yes | `string` | See Data Dictionary | | "0" |
| `[0]>>cfpTunningMode` | Cfp tuning mode | Yes | `string` | See Data Dictionary | | "0" |
| `[0]>>tunningChannel` | Tuning channel | Yes | `string` | | | "" |
| **Loopback & Power Mode** | | | | | | |
| `[0]>>loopbackStatus` | Loopback status | Yes | `string` | See Data Dictionary | | "1" |
| `[0]>>lowPowerMode` | Low power mode | Yes | `string` | See Data Dictionary | | "2" |
| **Dispersion Compensation** | | | | | | |
| `[0]>>dispersionCompensation` | Dispersion compensation mode | Yes | `string` | See Data Dictionary | | "3" |
| `[0]>>dispersionCompensationMax` | Dispersion compensation max (ps/nm) | Yes | `string` | | | "-16000" |
| `[0]>>dispersionCompensationMin` | Dispersion compensation min (ps/nm) | Yes | `string` | | | "2000" |
| `[0]>>dispersionCompensationValue` | Dispersion compensation value (ps/nm) | Yes | `string` | | | "0" |
| `[0]>>dispersionCompensationMaxCeiling` | Dispersion compensation max ceiling (ps/nm) | Yes | `string` | | | "" |
| `[0]>>dispersionCompensationMaxFloor` | Dispersion compensation max floor (ps/nm) | Yes | `string` | | | "" |
| `[0]>>dispersionValue` | Dispersion value (ps/nm) | Yes | `string` | | | "" |
| **Frequency** | | | | | | |
| `[0]>>frequencyInterval` | Frequency interval | Yes | `string` | See Data Dictionary | | "" |
| `[0]>>txFrequency` | Send frequency (Thz) | Yes | `string` | | | "" |
| `[0]>>rxFrequency` | Receive frequency (Thz) | Yes | `string` | | | "" |
| **Tx Power & OSNR** | | | | | | |
| `[0]>>txPower` | Tx power (dBm) | Yes | `string` | | | "0.0" |
| `[0]>>osnr` | Optical signal-to-noise ratio (dB) | Yes | `string` | | | "6553.5" |
| **OCH Power Monitoring** | | | | | | |
| `[0]>>ochSendPower` | OCH send power (dBm) | Yes | `string` | | | "" |
| `[0]>>ochSendPowerCeiling` | OCH send power ceiling (dBm) | Yes | `string` | | | "" |
| `[0]>>ochSendPowerFloor` | OCH send power floor (dBm) | Yes | `string` | | | "" |
| **OCH Alarm Thresholds** | | | | | | |
| `[0]>>ochReceivedPowerHighAlarmThreshold` | OCH receive power high alarm threshold (dBm) | Yes | `string` | | | "" |
| `[0]>>ochReceivedPowerLowAlarmThreshold` | OCH receive power low alarm threshold (dBm) | Yes | `string` | | | "" |
| `[0]>>ochSendPowerHighAlarmThreshold` | OCH send power high alarm threshold (dBm) | Yes | `string` | | | "" |
| `[0]>>ochSendPowerLowAlarmThreshold` | OCH send power low alarm threshold (dBm) | Yes | `string` | | | "" |
| **OCH Warning Thresholds** | | | | | | |
| `[0]>>ochReceivedPowerHighWarningThreshold` | OCH receive power high warning threshold (dBm) | Yes | `string` | | | "" |
| `[0]>>ochReceivedPowerLowWarningThreshold` | OCH receive power low warning threshold (dBm) | Yes | `string` | | | "" |
| `[0]>>ochSendPowerHighWarningThreshold` | OCH send power high warning threshold (dBm) | Yes | `string` | | | "" |
| `[0]>>ochSendPowerLowWarningThreshold` | OCH send power low warning threshold (dBm) | Yes | `string` | | | "" |
| **TQ5D Status** | | | | | | |
| `[0]>>readyStatus` | Ready status | Yes | `string` | 1=Ready, 2=Not Ready | | "1" |
| `[0]>>receiveStatus` | Receive status | Yes | `string` | 1=Normal, 2=Loss | | "2" |
| `[0]>>lazerTxFail` | Laser Tx fail | Yes | `string` | 1=Normal, 2=Failure | | "1" |
| `[0]>>alsEnable` | ALS enable status | Yes | `string` | 1=Open, 2=Closed | | "" |

### Success Example
```json
[
    {
        "alsEnable": "",
        "authorizationCheckResult": "",
        "cfpFormat": "0",
        "cfpTunningMode": "0",
        "dispersionCompensation": "3",
        "dispersionCompensationMax": "-16000",
        "dispersionCompensationMaxCeiling": "",
        "dispersionCompensationMaxFloor": "",
        "dispersionCompensationMin": "2000",
        "dispersionCompensationValue": "0",
        "dispersionValue": "",
        "frequencyInterval": "",
        "laserShutdownRealStatus": 1,
        "lazerTxFail": "1",
        "loopbackStatus": "1",
        "lowPowerMode": "2",
        "neId": 176,
        "ochReceivedPowerHighAlarmThreshold": "",
        "ochReceivedPowerHighWarningThreshold": "",
        "ochReceivedPowerLowAlarmThreshold": "",
        "ochReceivedPowerLowWarningThreshold": "",
        "ochSendPower": "",
        "ochSendPowerCeiling": "",
        "ochSendPowerFloor": "",
        "ochSendPowerHighAlarmThreshold": "",
        "ochSendPowerHighWarningThreshold": "",
        "ochSendPowerLowAlarmThreshold": "",
        "ochSendPowerLowWarningThreshold": "",
        "opticalTransceiverHwInfoAbsStatus": 2,
        "opticalTransceiverHwInfoLaser": 1,
        "opticalTransceiverHwInfoStandby": 1,
        "opticalTransceiverRate": "",
        "osnr": "6553.5",
        "parityEnable": "",
        "portId": "/ne=176/shelf=1/slot=1/card=1.1/port=1#portType=262/outerIndex=1",
        "readyStatus": "1",
        "receiveStatus": "2",
        "rxFrequency": "",
        "speed": "",
        "tunningChannel": "",
        "txFrequency": "",
        "txPower": "0.0"
    }
]
```

## Data Dictionary

### loopbackStatus (Loopback Status)

| Value | Description |
| --- | --- |
| 1 | No Loopback Mode |
| 2 | Local External LoopBack |
| 3 | Local Inner LoopBack |

### dispersionCompensation (Dispersion Compensation Mode)

| Value | Description |
| --- | --- |
| 1 | Auto |
| 2 | -- |
| 3 | -- |

### lowPowerMode (Low Power Mode)

| Value | Description |
| --- | --- |
| 1 | ON |
| 2 | OFF |
| N/A | N/A |
| -1 | -- |

### cfpFormat (Cfp Format)

| Value | Description |
| --- | --- |
| 0 | Unknown |
| 1 | DP16QAM |
| 2 | DPQPSK |
| 3 | DP8QAM |

### cfpTunningMode (Cfp Tuning Mode)

| Value | Description |
| --- | --- |
| 0 | Unknown |
| 1 | DWDM40 |
| 2 | DWDM80 |
| 3 | DWDM48 |
| 4 | DWDM96 |
| 5 | DWDM64 |

### frequencyInterval (Frequency Interval)

| Value | Description |
| --- | --- |
| 1 | 50 GHZ |
| 2 | 75 GHZ |
| 3 | 100 GHZ |
| 4 | Invalid |
| 5 | 6.25 GHZ |
| 6 | 150 GHZ |
| Other | -- |

### opticalTransceiverRate (Optical Transceiver Rate)

| Value | Description |
| --- | --- |
| 1 | 100G |
| 2 | 200G |
| 3 | 400G |
| 4 | 800G |
| Other | -- |

## Usage Notes
1. Parameters containing `#` characters (e.g., `portId`, `indexInMib`) must be URL-encoded as `%23` when used in query strings.
2. Many fields may return empty strings (`""`) when the corresponding capability or configuration is not applicable to the specific port or module type.
3. OSNR values are reported in dB with one decimal place precision.
4. Dispersion compensation values are reported in ps/nm.

## Related Documentation
- [Query Port Information](query_port_information.md) - Query port link status and working speed
- [Query Optical Transceiver DDM](query_optical_transceiver_ddm.md) - Query optical transceiver digital diagnostic monitoring
- [Query Optical Transceiver](query_optical_transceiver.md) - Query detailed optical transceiver information
- [Query Port FEC Information](query_port_fec_information.md) - Query FEC-related information for a specific port
