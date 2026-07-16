# Query Optical Transceiver Information

## API Information
Query optical transceiver information for a specific network element of RAX721 device, including vendor details, optical parameters, monitoring data, and configuration status.

## API Path
`http://XX.XX.XX.XX/tiap_ems_north/tiap_ems_basic_mgt/v20/optical_transceiver`

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
http://172.16.1.248/tiap_ems_north/tiap_ems_basic_mgt/v20/optical_transceiver?neId=127&page=1&start=0&limit=25
```

## Response Content
### Return Result
> Success (200)
Json array

| Parameter Name | Description | Required | Type | Data Dictionary | Restriction | Example |
| --- | --- | --- | --- | --- | --- | --- |
| `[0]` | Optical transceiver item | Yes | `object` | | | See example below |
| `[0]>>biasCurrent` | Bias current | Yes | `string` | | | "2" |
| `[0]>>ifIndex` | Interface index | Yes | `number` | | | 272900096 |
| `[0]>>moduleTemperature` | Module temperature | Yes | `string` | | | "1" |
| `[0]>>neId` | Network element ID | Yes | `number` | | | 127 |
| `[0]>>opticalTransceiverAbility` | Transceiver capability bitmap | Yes | `string` | | | "491552" |
| `[0]>>opticalTransceiverBR` | Bit rate type | Yes | `number` | | | 103 |
| `[0]>>opticalTransceiverBRMax` | Maximum bit rate | Yes | `number` | | | 10300 |
| `[0]>>opticalTransceiverBRMin` | Minimum bit rate | Yes | `number` | | | 10300 |
| `[0]>>opticalTransceiverCDR` | Clock data recovery support | Yes | `number` | 1 = Supported<br>2 = Not Supported | | 2 |
| `[0]>>opticalTransceiverCMU` | Clock multiplier unit support | Yes | `number` | 1 = Supported<br>2 = Not Supported | | 2 |
| `[0]>>opticalTransceiverCalibrationType` | Calibration type | Yes | `number` | | | 2 |
| `[0]>>opticalTransceiverCompatibility` | Compatibility standard | Yes | `string` | | | "10G_BASE_LR" |
| `[0]>>opticalTransceiverConnectorType` | Connector type | Yes | `number` | 8 = LC | | 8 |
| `[0]>>opticalTransceiverCooled` | Cooling status | Yes | `number` | 1 = Cooled<br>2 = Uncooled | | 2 |
| `[0]>>opticalTransceiverDDM` | Digital diagnostics monitoring support | Yes | `number` | 1 = Supported<br>2 = Not Supported | | 1 |
| `[0]>>opticalTransceiverDetectorType` | Detector type | Yes | `number` | 1 = PIN | | 1 |
| `[0]>>opticalTransceiverFEC` | Forward error correction support | Yes | `number` | 1 = Supported<br>2 = Not Supported | | 2 |
| `[0]>>opticalTransceiverInVpsLowPower` | Input VPS low power status | Yes | `number` | 1 = Low Power<br>2 = Normal | | 1 |
| `[0]>>opticalTransceiverLineLoopBack` | Line loopback status | Yes | `number` | 1 = Active<br>2 = Inactive | | 2 |
| `[0]>>opticalTransceiverMediaType` | Media type | Yes | `number` | 6 = Single Mode Fiber | | 6 |
| `[0]>>opticalTransceiverOutVpsLowPower` | Output VPS low power status | Yes | `number` | 1 = Low Power<br>2 = Normal | | 2 |
| `[0]>>opticalTransceiverPowerDissipation` | Power dissipation | Yes | `number` | | | 0 |
| `[0]>>opticalTransceiverRSSI` | RSSI monitoring support | Yes | `number` | 1 = Supported<br>2 = Not Supported | | 2 |
| `[0]>>opticalTransceiverRefClock` | Reference clock support | Yes | `number` | 1 = Supported<br>2 = Not Supported | | 2 |
| `[0]>>opticalTransceiverStandby` | Standby status | Yes | `number` | 1 = Active<br>2 = Standby | | 1 |
| `[0]>>opticalTransceiverTransmissionDistance` | Transmission distance (m) | Yes | `string` | | | "10000" |
| `[0]>>opticalTransceiverTransmitterType` | Transmitter type | Yes | `number` | 1 = FP Laser | | 1 |
| `[0]>>opticalTransceiverTunalbe` | Tunable laser support | Yes | `number` | 1 = Tunable<br>2 = Fixed | | 2 |
| `[0]>>opticalTransceiverTxDis` | Transmitter disable status | Yes | `number` | 1 = Disabled<br>2 = Normal | | 2 |
| `[0]>>opticalTransceiverType` | Transceiver type | Yes | `number` | 4 = SFP+ | | 4 |
| `[0]>>opticalTransceiverVendorName` | Vendor name | Yes | `string` | | | "Raisecom" |
| `[0]>>opticalTransceiverVendorPN` | Vendor part number | Yes | `string` | | | "USFP+-192/S1" |
| `[0]>>opticalTransceiverVendorRev` | Vendor revision | Yes | `string` | | | "1.0" |
| `[0]>>opticalTransceiverVendorSN` | Vendor serial number | Yes | `string` | | | "30401200700210" |
| `[0]>>opticalTransceiverVps` | VPS status | Yes | `number` | | | 1 |
| `[0]>>opticalTransceiverWaveTolerance` | Wavelength tolerance | Yes | `string` | | | "1310" |
| `[0]>>opticalTransceiverWavelength` | Wavelength (nm) | Yes | `string` | | | "1310" |
| `[0]>>opticalTransceiverWavelengthContrl` | Wavelength control support | Yes | `number` | 1 = Supported<br>2 = Not Supported | | 2 |
| `[0]>>opticalTransceiverXFILoopBack` | XFI loopback status | Yes | `number` | 1 = Active<br>2 = Inactive | | 2 |
| `[0]>>portName` | Port name | Yes | `string` | | | "tengigabitethernet1/1/1" |
| `[0]>>powerSupplyVoltage` | Power supply voltage | Yes | `string` | | | "2" |
| `[0]>>rxOpticalPower` | Received optical power | Yes | `string` | | | "2" |
| `[0]>>txOpticalPower` | Transmitted optical power | Yes | `string` | | | "2" |

### Success Example
```json
[
  {
    "biasCurrent": "2",
    "ifIndex": 272900096,
    "moduleTemperature": "1",
    "neId": 127,
    "opticalTransceiverAbility": "491552",
    "opticalTransceiverBR": 103,
    "opticalTransceiverBRMax": 10300,
    "opticalTransceiverBRMin": 10300,
    "opticalTransceiverCDR": 2,
    "opticalTransceiverCMU": 2,
    "opticalTransceiverCalibrationType": 2,
    "opticalTransceiverCompatibility": "10G_BASE_LR",
    "opticalTransceiverConnectorType": 8,
    "opticalTransceiverCooled": 2,
    "opticalTransceiverDDM": 1,
    "opticalTransceiverDetectorType": 1,
    "opticalTransceiverFEC": 2,
    "opticalTransceiverInVpsLowPower": 1,
    "opticalTransceiverLineLoopBack": 2,
    "opticalTransceiverMediaType": 6,
    "opticalTransceiverOutVpsLowPower": 2,
    "opticalTransceiverPowerDissipation": 0,
    "opticalTransceiverRSSI": 2,
    "opticalTransceiverRefClock": 2,
    "opticalTransceiverStandby": 1,
    "opticalTransceiverTransmissionDistance": "10000",
    "opticalTransceiverTransmitterType": 1,
    "opticalTransceiverTunalbe": 2,
    "opticalTransceiverTxDis": 2,
    "opticalTransceiverType": 4,
    "opticalTransceiverVendorName": "Raisecom        ",
    "opticalTransceiverVendorPN": "USFP+-192/S1    ",
    "opticalTransceiverVendorRev": "1.0 ",
    "opticalTransceiverVendorSN": "30401200700210  ",
    "opticalTransceiverVps": 1,
    "opticalTransceiverWaveTolerance": "1310",
    "opticalTransceiverWavelength": "1310",
    "opticalTransceiverWavelengthContrl": 2,
    "opticalTransceiverXFILoopBack": 2,
    "portName": "tengigabitethernet1/1/1",
    "powerSupplyVoltage": "2",
    "rxOpticalPower": "2",
    "txOpticalPower": "2"
  },
  {
    "biasCurrent": "2",
    "ifIndex": 272900112,
    "moduleTemperature": "1",
    "neId": 127,
    "opticalTransceiverAbility": "491552",
    "opticalTransceiverBR": 103,
    "opticalTransceiverBRMax": 10300,
    "opticalTransceiverBRMin": 10300,
    "opticalTransceiverCDR": 2,
    "opticalTransceiverCMU": 2,
    "opticalTransceiverCalibrationType": 2,
    "opticalTransceiverCompatibility": "10G_BASE_LR",
    "opticalTransceiverConnectorType": 8,
    "opticalTransceiverCooled": 2,
    "opticalTransceiverDDM": 1,
    "opticalTransceiverDetectorType": 1,
    "opticalTransceiverFEC": 2,
    "opticalTransceiverInVpsLowPower": 1,
    "opticalTransceiverLineLoopBack": 2,
    "opticalTransceiverMediaType": 6,
    "opticalTransceiverOutVpsLowPower": 2,
    "opticalTransceiverPowerDissipation": 0,
    "opticalTransceiverRSSI": 2,
    "opticalTransceiverRefClock": 2,
    "opticalTransceiverStandby": 1,
    "opticalTransceiverTransmissionDistance": "10000",
    "opticalTransceiverTransmitterType": 1,
    "opticalTransceiverTunalbe": 2,
    "opticalTransceiverTxDis": 2,
    "opticalTransceiverType": 4,
    "opticalTransceiverVendorName": "Raisecom        ",
    "opticalTransceiverVendorPN": "USFP+-192/S1    ",
    "opticalTransceiverVendorRev": "1.0 ",
    "opticalTransceiverVendorSN": "30401200700302  ",
    "opticalTransceiverVps": 1,
    "opticalTransceiverWaveTolerance": "1310",
    "opticalTransceiverWavelength": "1310",
    "opticalTransceiverWavelengthContrl": 2,
    "opticalTransceiverXFILoopBack": 2,
    "portName": "tengigabitethernet1/1/3",
    "powerSupplyVoltage": "2",
    "rxOpticalPower": "2",
    "txOpticalPower": "2"
  }
]
```

## Key Monitoring Parameters

### Optical Performance
| Parameter Name | Description | Type | Example |
| --- | --- | --- | --- |
| `txOpticalPower` | Transmitted optical power | `string` | "2" |
| `rxOpticalPower` | Received optical power | `string` | "2" |
| `biasCurrent` | Bias current | `string` | "2" |
| `moduleTemperature` | Module temperature | `string` | "1" |
| `powerSupplyVoltage` | Power supply voltage | `string` | "2" |

### Physical Information
| Parameter Name | Description | Type | Example |
| --- | --- | --- | --- |
| `opticalTransceiverVendorName` | Vendor name | `string` | "Raisecom" |
| `opticalTransceiverVendorPN` | Vendor part number | `string` | "USFP+-192/S1" |
| `opticalTransceiverVendorSN` | Vendor serial number | `string` | "30401200700210" |
| `opticalTransceiverVendorRev` | Vendor revision | `string` | "1.0" |
| `opticalTransceiverCompatibility` | Compatibility standard | `string` | "10G_BASE_LR" |
| `opticalTransceiverWavelength` | Wavelength (nm) | `string` | "1310" |
| `opticalTransceiverTransmissionDistance` | Transmission distance (m) | `string` | "10000" |

### Capability Information
| Parameter Name | Description | Type | Example |
| --- | --- | --- | --- |
| `opticalTransceiverAbility` | Transceiver capability bitmap | `string` | "491552" |
| `opticalTransceiverBR` | Bit rate type | `number` | 103 |
| `opticalTransceiverBRMax` | Maximum bit rate | `number` | 10300 |
| `opticalTransceiverBRMin` | Minimum bit rate | `number` | 10300 |

## Data Dictionary

### Support / Enable Fields
| Value | Meaning |
| --- | --- |
| 1 | Supported / Enabled / Active |
| 2 | Not Supported / Disabled / Inactive |

## Usage Notes
1. The `opticalTransceiverAbility` field is a bitmap encoding the transceiver's supported capabilities
2. The interface index (`ifIndex`) for RAX721 uses full numeric encoding (e.g., `272900096`) rather than string paths
3. Port names follow the format `tengigabitethernet{slot}/{subslot}/{port}`
4. RAX721 uses 10G SFP+ transceivers (`opticalTransceiverCompatibility` = "10G_BASE_LR", `opticalTransceiverType` = 4) with vendor PN "USFP+-192/S1"
5. RAX721 transceivers operate in Active mode (`opticalTransceiverStandby` = 1), unlike RAX711-C-R which defaults to Standby mode
6. `opticalTransceiverInVpsLowPower` = 1 indicates input VPS is in low power state
7. `opticalTransceiverPowerDissipation` value of `0` may indicate the parameter is not supported by this transceiver model
8. Vendor name fields contain trailing whitespace in the raw response; trimming is recommended when displaying

## Related Documentation
- [Query Optical Transceiver Digital Diagnostics (RAX721)](query_optical_transceiver_ddm.md) - DDM parameters for RAX721 devices
- [Query Optical Transceiver Information (RAX711-C-R)](../RAX711-C-R/query_optical_transceiver_info.md) - Equivalent endpoint for RAX711-C-R devices
- [Query Optical Transceiver Status (iTN167)](../167/query_optical_transceiver_status.md) - Equivalent endpoint for iTN167 devices
