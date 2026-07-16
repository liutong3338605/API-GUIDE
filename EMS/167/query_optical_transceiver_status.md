# Query Optical Transceiver Status

## API Information
Query optical transceiver status information for a specific network element, including vendor details, optical parameters, monitoring data, and configuration status.

## API Path
`http://XX.XX.XX.XX/tiap_ems_basic_mgt/tiap_ems_basic_mgt/v20/optical_transceiver`

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
http://172.16.1.248/tiap_ems_basic_mgt/tiap_ems_basic_mgt/v20/optical_transceiver?neId=283&page=1&start=0&limit=25
```

## Response Content
### Return Result
> Success (200)
Json array

| Parameter Name | Description | Required | Type | Data Dictionary | Restriction | Example |
| --- | --- | --- | --- | --- | --- | --- |
| `[0]` | Optical transceiver item | Yes | `object` | | | See example below |
| `[0]>>biasCurrent` | Bias current | Yes | `string` | | | "2" |
| `[0]>>ifIndex` | Interface index | Yes | `number` | | | 1 |
| `[0]>>moduleTemperature` | Module temperature | Yes | `string` | | | "1" |
| `[0]>>neId` | Network element ID | Yes | `number` | | | 283 |
| `[0]>>opticalTransceiverBRMax` | Maximum bit rate | Yes | `number` | | | 1300 |
| `[0]>>opticalTransceiverBRMin` | Minimum bit rate | Yes | `number` | | | 1300 |
| `[0]>>opticalTransceiverCDR` | Clock data recovery support | Yes | `number` | | | 2 |
| `[0]>>opticalTransceiverCMU` | Clock multiplier unit support | Yes | `number` | | | 2 |
| `[0]>>opticalTransceiverCalibrationType` | Calibration type | Yes | `number` | | | 2 |
| `[0]>>opticalTransceiverCompatibility` | Compatibility standard | Yes | `string` | | | "1000_BASE_LX" |
| `[0]>>opticalTransceiverConnectorType` | Connector type | Yes | `number` | | | 8 |
| `[0]>>opticalTransceiverCooled` | Cooling status | Yes | `number` | | | 2 |
| `[0]>>opticalTransceiverDDM` | Digital diagnostics monitoring support | Yes | `number` | | | 1 |
| `[0]>>opticalTransceiverDetectorType` | Detector type | Yes | `number` | | | 1 |
| `[0]>>opticalTransceiverFEC` | Forward error correction support | Yes | `number` | | | 2 |
| `[0]>>opticalTransceiverInVpsLowPower` | Input VPS low power status | Yes | `number` | | | 1 |
| `[0]>>opticalTransceiverLineLoopBack` | Line loopback status | Yes | `number` | | | 2 |
| `[0]>>opticalTransceiverMediaType` | Media type | Yes | `number` | | | 6 |
| `[0]>>opticalTransceiverOutVpsLowPower` | Output VPS low power status | Yes | `number` | | | 2 |
| `[0]>>opticalTransceiverPowerDissipation` | Power dissipation | Yes | `number` | | | 0 |
| `[0]>>opticalTransceiverRSSI` | RSSI monitoring support | Yes | `number` | | | 2 |
| `[0]>>opticalTransceiverRefClock` | Reference clock support | Yes | `number` | | | 2 |
| `[0]>>opticalTransceiverStandby` | Standby status | Yes | `number` | | | 1 |
| `[0]>>opticalTransceiverTransmissionDistance` | Transmission distance (m) | Yes | `string` | | | "15000" |
| `[0]>>opticalTransceiverTransmitterType` | Transmitter type | Yes | `number` | | | 2 |
| `[0]>>opticalTransceiverTunalbe` | Tunable laser support | Yes | `number` | | | 2 |
| `[0]>>opticalTransceiverTxDis` | Transmitter disable status | Yes | `number` | | | 2 |
| `[0]>>opticalTransceiverType` | Transceiver type | Yes | `number` | | | 4 |
| `[0]>>opticalTransceiverVendorName` | Vendor name | Yes | `string` | | | "Raisecom" |
| `[0]>>opticalTransceiverVendorPN` | Vendor part number | Yes | `string` | | | "USFP-Gb/S1-D-03R" |
| `[0]>>opticalTransceiverVendorRev` | Vendor revision | Yes | `string` | | | "1.0" |
| `[0]>>opticalTransceiverVendorSN` | Vendor serial number | Yes | `string` | | | "B1811700965" |
| `[0]>>opticalTransceiverVps` | VPS status | Yes | `number` | | | 1 |
| `[0]>>opticalTransceiverWaveTolerance` | Wavelength tolerance | Yes | `string` | | | "0" |
| `[0]>>opticalTransceiverWavelength` | Wavelength (nm) | Yes | `string` | | | "1310" |
| `[0]>>opticalTransceiverWavelengthContrl` | Wavelength control support | Yes | `number` | | | 2 |
| `[0]>>opticalTransceiverXFILoopBack` | XFI loopback status | Yes | `number` | | | 2 |
| `[0]>>portName` | Port name | Yes | `string` | | | "NNI 1" |
| `[0]>>powerSupplyVoltage` | Power supply voltage | Yes | `string` | | | "2" |
| `[0]>>rxOpticalPower` | Received optical power | Yes | `string` | | | "2" |
| `[0]>>txOpticalPower` | Transmitted optical power | Yes | `string` | | | "2" |

### Success Example
```json
[
  {
    "biasCurrent": "2",
    "ifIndex": 1,
    "moduleTemperature": "1",
    "neId": 283,
    "opticalTransceiverBRMax": 1300,
    "opticalTransceiverBRMin": 1300,
    "opticalTransceiverCDR": 2,
    "opticalTransceiverCMU": 2,
    "opticalTransceiverCalibrationType": 2,
    "opticalTransceiverCompatibility": "1000_BASE_LX",
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
    "opticalTransceiverTransmissionDistance": "15000",
    "opticalTransceiverTransmitterType": 2,
    "opticalTransceiverTunalbe": 2,
    "opticalTransceiverTxDis": 2,
    "opticalTransceiverType": 4,
    "opticalTransceiverVendorName": "Raisecom        ",
    "opticalTransceiverVendorPN": "USFP-Gb/S1-D-03R",
    "opticalTransceiverVendorRev": "1.0 ",
    "opticalTransceiverVendorSN": "B1811700965     ",
    "opticalTransceiverVps": 1,
    "opticalTransceiverWaveTolerance": "0",
    "opticalTransceiverWavelength": "1310",
    "opticalTransceiverWavelengthContrl": 2,
    "opticalTransceiverXFILoopBack": 2,
    "portName": "NNI 1",
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
| `opticalTransceiverVendorPN` | Vendor part number | `string` | "USFP-Gb/S1-D-03R" |
| `opticalTransceiverVendorSN` | Vendor serial number | `string` | "B1811700965" |
| `opticalTransceiverVendorRev` | Vendor revision | `string` | "1.0" |
| `opticalTransceiverCompatibility` | Compatibility standard | `string` | "1000_BASE_LX" |
| `opticalTransceiverWavelength` | Wavelength (nm) | `string` | "1310" |
| `opticalTransceiverTransmissionDistance` | Transmission distance (m) | `string` | "15000" |

## Related Documentation
- [Query Card Temperature](query_card_temperature.md) - Query card temperature information
