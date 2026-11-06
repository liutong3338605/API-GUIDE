# API Information
This API is used to get the list of TopoLink

## API Path
`https://172.16.61.51/north_topo/rest/topo/topo_link/link_info`

## Request Protocol
HTTP

## Request Method
GET
## Request Header

The header must contain user and Authentication-Token, where the value of user must be the same user who requested the token.

## Query Parameters
| Parameter Name | Description | Required | Type | Restriction | Example |
| --- | --- | --- | --- | --- | --- |
| `page` | Not used by the server (pagination is controlled by `start` / `limit` only) | No | `number` | Ignored by the server | 1 |
| `start` | The starting index (OFFSET of the SQL `LIMIT start, limit` clause) | No | `number` | Non-negative integer, default `0` | 0 |
| `limit` | The maximum number of items per page | No | `number` | Positive integer, default `50` | 25 |
| `param` | Fuzzy search keyword. Matches any of: link_symbol_id, link_name1, remark, A/Z node name, A/Z port userlabel. If the keyword contains "uni"/"bi", the link `direction` is also filtered (1 = Unidirection, 2 = Bidirection) | No | `string` | SQL LIKE pattern, `%keyword%` is applied automatically | 1111 |
| `diffSrcAndSink` | If present, excludes self-loop links where source node equals destination node (`src_symbol_id != dest_symbol_id`) | No | `string` | Any non-empty value enables the filter | 1 |

## Request Body
None

## Response Content
### Return Result
> Success (200)
Json object

The response is a JSON object with three top-level members:

| Parameter Name | Description | Type | Example |
| --- | --- | --- | --- |
| `success` | Whether the request succeeded | `boolean` | true |
| `data` | Array of topo link records (fields described below) | `array` | - |
| `total` | Total number of links matching the query (before pagination) | `number` | 1 |

Fields of each object in `data`:

| Parameter Name | Description | Required | Type | Data Dictionary | Restriction | Example |
| --- | --- | --- | --- | --- | --- | --- |
| `link_symbol_id` | Unique link symbol ID (primary key of table `topo_link_symbol`) | Yes | `number` | - | Positive integer only | 3 |
| `link_name1` | Link name | Yes | `string` | - | - | "1111" |
| `remark` | Remark / description of the link | Yes | `string` | - | - | "" |
| `direction` | Link direction | Yes | `number` | 1 = Unidirection, 2 = Bidirection | Enumerated values: 1, 2 | 2 |
| `src_symbol_id` | Symbol ID of the A-side (source) node in the topology | Yes | `number` | - | Positive integer only | 9 |
| `dest_symbol_id` | Symbol ID of the Z-side (destination) node in the topology | Yes | `number` | - | Positive integer only | 12 |
| `src_port_id` | Resource ID (DN) of the A-side port | Yes | `string` | - | `res_port.port_id` DN format | "/ne=10/shelf=1/slot=3/card=1.1/port=1#portType=1" |
| `des_port_id` | Resource ID (DN) of the Z-side port | Yes | `string` | - | `res_port.port_id` DN format | "/ne=13/shelf=1/slot=5/card=1.1/port=8#portType=4996/subPort=4094#subPortType=351" |
| `topo_type_id` | Link type ID | Yes | `string` | - | Positive integer string (varchar column) | "16" |
| `minAlarmLevel` | Lowest alarm severity propagated on this link (used for link coloring on the topo view) | Yes | `number` | 10 = no alarm level configured | Non-negative integer | 10 |
| `topo_type_name` | Display name of the link type (from `topo_node_type.display_name`) | Yes | `string` | - | - | "Common link" |
| `anode_name` | Name of the A-side node (from `topo_symbol.symbol_name1` of `src_symbol_id`) | Yes | `string` | - | - | "neon" |
| `znode_name` | Name of the Z-side node (from `topo_symbol.symbol_name1` of `dest_symbol_id`) | Yes | `string` | - | - | "10.200.199.170" |
| `anode_port` | User label of the A-side port (from `res_port.userlabel` of `src_port_id`) | No | `null/string` | - | Empty/null if the port is not bound or not found | "tdm1/3/1" |
| `znode_port` | User label of the Z-side port (from `res_port.userlabel` of `des_port_id`) | No | `null/string` | - | Empty/null if the port is not bound or not found | "gigaethernet1/5/8.4094" |
| `src_map_hierarchy` | Topology hierarchy path of the A-side node | Yes | `string` | - | Comma-enclosed symbol ID path, from root to the node | ",0,11,9," |
| `des_map_hierarchy` | Topology hierarchy path of the Z-side node | Yes | `string` | - | Comma-enclosed symbol ID path, from root to the node | ",0,14,12," |

### Success Example
```json
{
    "success": true,
    "data": [
        {
            "link_symbol_id": 3,
            "link_name1": "1111",
            "remark": "",
            "direction": 2,
            "src_symbol_id": 9,
            "dest_symbol_id": 12,
            "src_port_id": "/ne=10/shelf=1/slot=3/card=1.1/port=1#portType=1",
            "des_port_id": "/ne=13/shelf=1/slot=5/card=1.1/port=8#portType=4996/subPort=4094#subPortType=351",
            "topo_type_id": "16",
            "minAlarmLevel": 10,
            "topo_type_name": "Common link",
            "anode_name": "neon",
            "znode_name": "10.200.199.170",
            "anode_port": "tdm1/3/1",
            "znode_port": "gigaethernet1/5/8.4094",
            "src_map_hierarchy": ",0,11,9,",
            "des_map_hierarchy": ",0,14,12,"
        }
    ],
    "total": 1
}
```
