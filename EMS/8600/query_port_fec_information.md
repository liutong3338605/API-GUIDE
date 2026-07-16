# Query Port FEC Information

## API Information
Query FEC-related information for a specific port, including FEC mode, before/after FEC error thresholds, and error rates.

## API Path
`http://XX.XX.XX.XX/tiap_ems_north/tiap_ems_basic_mgt/v1/interface`

## Request Protocol
HTTP

## Request Method
GET

## Query Parameters
| Parameter Name | Description | Required | Type | Restriction | Example |
| --- | --- | --- | --- | --- | --- |
| `neId` | Network element ID | Yes | `number` | | 176 |
| `cardId` | Card identifier path | Yes | `string` | | /ne=176/shelf=1/slot=1/card=1.1 |
| `portId` | Port identifier path | Yes | `string` | | /ne=176/shelf=1/slot=1/card=1.1/port=1#portType=262/outerIndex=1 |
| `layerType` | Layer type filter | Yes | `string` | | LR_FEC_MODE |

### Request Example
```
http://172.16.1.248/tiap_ems_north/tiap_ems_basic_mgt/v1/interface?neId=176&cardId=/ne=176/shelf=1/slot=1/card=1.1&portId=/ne=176/shelf=1/slot=1/card=1.1/port=1%23portType=262/outerIndex=1&layerType=LR_FEC_MODE
```

> **Note:** The `portId` parameter contains the `#` character which must be URL-encoded as `%23`.

## Response Content
### Return Result
> Success (200)
Json object

| Parameter Name | Description | Required | Type | Data Dictionary | Restriction | Example |
| --- | --- | --- | --- | --- | --- | --- |
| `code` | Response status code | Yes | `number` | | | 0 |
| `total` | Total count of returned records | Yes | `number` | | | 1 |
| `data` | FEC configuration data object | Yes | `object` | | | See example below |
| `data>>fecMode` | FEC mode | Yes | `string` | See Data Dictionary | | "2" |
| `data>>befcEcThreshold` | Before FEC error threshold | Yes | `string` | See Data Dictionary | | "6" |
| `data>>aefcEcThreshold` | After FEC error threshold | Yes | `string` | See Data Dictionary | | "6" |
| `data>>befcEcRate` | Before FEC error rate | Yes | `string` | See Data Dictionary | | "0" |
| `data>>aefcEcRate` | After FEC error rate | Yes | `string` | See Data Dictionary | | "0" |
| `data>>layerRate` | Layer rate type | Yes | `string` | | | "LR_FEC_MODE" |

### Success Example
```json
{
    "total": 1,
    "data": {
        "aefcEcRate": "0",
        "aefcEcThreshold": "6",
        "befcEcRate": "0",
        "befcEcThreshold": "6",
        "fecMode": "2",
        "layerRate": "LR_FEC_MODE"
    },
    "code": 0
}
```

## Data Dictionary

### fecMode (FEC Mode)

| Value | Description |
| --- | --- |
| 1 | NO FEC |
| 2 | GFEC |
| 3 | FEC I.4 |
| 4 | FEC I.7 |
| 5 | SD-FEC Mode 1 |
| 6 | SD-FEC Mode 2 |
| 7 | SD-FEC Mode 3 |
| 8 | OFEC |

### befcEcThreshold / aefcEcThreshold (FEC Error Threshold)

| Value | Description |
| --- | --- |
| 3 | 1.0E-3 |
| 4 | 1.0E-4 |
| 5 | 1.0E-5 |
| 6 | 1.0E-6 |
| 7 | 1.0E-7 |
| 8 | 1.0E-8 |
| 9 | 1.0E-9 |

### befcEcRate / aefcEcRate (FEC Error Rate)

| Value | Description |
| --- | --- |
| 0 | 0 |
| Other values | 1.0E-{value} (value is the exponent of scientific notation) |

## Related Documentation
- [Query Port Information](query_port_information.md) - Query port link status and working speed
- [Query Optical Transceiver DDM](query_optical_transceiver_ddm.md) - Query optical transceiver digital diagnostic monitoring
- [Query Optical Transceiver](query_optical_transceiver.md) - Query detailed optical transceiver information
