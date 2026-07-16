# Query Port Information

## API Information
Query port link status and working speed

## API Path
`http://XX.XX.XX.XX/tiap_ems_north/tiap_ems_basic_mgt/v1/interface`

## Request Protocol
HTTP

## Request Method
GET

## Query Parameters
| Parameter Name | Description | Required | Type | Restriction | Example |
| --- | --- | --- | --- | --- | --- |
| `neId` | Network Element ID | Yes | `number` | | 30 |
| `cardId` | Card identifier path | Yes | `string` | | /ne=30/shelf=1/slot=3/card=1.1 |
| `portId` | Port identifier path | Yes | `string` | | /ne=170/shelf=1/slot=3/card=1.1/port=1#portType=270 |
| `layerType` | Layer rate type | Yes | `string` | | LR_Ethernet |

### Request Example
```
http://172.16.1.248/tiap_ems_north/tiap_ems_basic_mgt/v1/interface?neId=30&cardId=/ne=30/shelf=1/slot=3/card=1.1&portId=/ne=170/shelf=1/slot=3/card=1.1/port=1#portType=270&layerType=LR_Ethernet
```

## Response Content
### Return Result
> Success (200)
Json object

| Parameter Name | Description | Required | Type | Data Dictionary | Restriction | Example |
| --- | --- | --- | --- | --- | --- | --- |
| `total` | Total count of returned records | Yes | `number` | | | 1 |
| `data` | Port information data object | Yes | `object` | | | See example below |
| `data>>portInsulate` | Port isolation | Yes | `string` | | | "2" |
| `data>>ethLinkStatus` | Link status | Yes | `string` | 1 = Link up<br>2 = Link down | | "2" |
| `data>>txFlowControlSwitch` | Transmit flow control switch | Yes | `string` | | | "2" |
| `data>>phyLoopback` | Physical loopback status | Yes | `string` | | | "1" |
| `data>>portSpeed` | Port speed | Yes | `string` | auto = auto<br>100M = 100M<br>1000M = 1000M | | "10G" |
| `data>>layerRate` | Layer rate type | Yes | `string` | | | "LR_Ethernet" |
| `data>>alsEnable` | ALS (Automatic Laser Shutdown) enable status | Yes | `string` | | | "2" |
| `data>>rxFlowControlSwitch` | Receive flow control switch | Yes | `string` | | | "2" |
| `data>>duplexStatus` | Duplex mode | Yes | `string` | 1 = Auto-negotiation<br>2 = Half duplex<br>3 = Full duplex | | "3" |
| `data>>isEnable` | Port enable status | Yes | `string` | | | "2" |
| `code` | Operation result code | Yes | `number` | | | 0 |

### Success Example
```json
{
    "total": 1,
    "data": {
        "portInsulate": "2",
        "ethLinkStatus": "2",
        "txFlowControlSwitch": "2",
        "phyLoopback": "1",
        "portSpeed": "10G",
        "layerRate": "LR_Ethernet",
        "alsEnable": "2",
        "rxFlowControlSwitch": "2",
        "duplexStatus": "3",
        "isEnable": "2"
    },
    "code": 0
}
```

## Key Monitoring Parameters

| Parameter | Description | Type | Example | Notes |
| --- | --- | --- | --- | --- |
| `ethLinkStatus` | Link status | `string` | "2" | 1 = Link up, 2 = Link down |
| `portSpeed` | Port speed | `string` | "10G" | Supports auto, 100M, 1000M, 10G |
| `duplexStatus` | Duplex mode | `string` | "3" | 1 = Auto-negotiation, 2 = Half duplex, 3 = Full duplex |
| `txFlowControlSwitch` | Transmit flow control | `string` | "2" | |
| `rxFlowControlSwitch` | Receive flow control | `string` | "2" | |
| `phyLoopback` | Physical loopback | `string` | "1" | |
| `isEnable` | Port enable status | `string` | "2" | |

## Data Dictionary

### ethLinkStatus
| Value | Description |
|-------|-------------|
| 1 | Link up |
| 2 | Link down |

### portSpeed
| Value | Description |
|-------|-------------|
| auto | Auto-negotiation |
| 100M | 100 Mbps |
| 1000M | 1000 Mbps (1 Gbps) |

### duplexStatus
| Value | Description |
|-------|-------------|
| 1 | Auto-negotiation |
| 2 | Half duplex |
| 3 | Full duplex |

## Related Documentation
- [Query Optical Transceiver Information](query_optical_transceiver_information.md) - Query optical module information for specific cards
