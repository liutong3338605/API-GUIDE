# API Information
This API is used to get the list of NE


## API Path
`https://172.16.1.248/nortn_inventory/rest/inventory/res_ne/select/page_suffix`

## Request Protocol
HTTP

## Request Method
GET

## Query Parameters
| Parameter Name | Description | Required | Type | Restriction | Example |
| --- | --- | --- | --- | --- | --- |
| `page` | The page number | Yes | `number` |  | 1 |
| `start` | The starting index | Yes | `number` |  | 0 |
| `limit` | The maximum number of items per page | Yes | `number` |  | 25 |

## Request Body
None

## Response Content
### Return Result
> Success (200)
Json object

| Parameter Name | Description | Required | Type | Data Dictionary | Restriction | Example |
| --- | --- | --- | --- | --- | --- | --- |
| `uuid` | Unique device identification ID | Yes | `string` | - | 36-bit UUID standard format | "a60d3f70-db2e-11f0-b89f-61b6ad1f2900" |
| `neid` | Network element ID of the device | Yes | `number` | - | Positive integer only | 6 |
| `softbaseversion` | Device basic software version | Yes | `string` | - | - | "P200R002C53" |
| `vendor` | Device manufacturer name | Yes | `string` | - | - | "Raisecom" |
| `location` | Physical location of the device | Yes | `string` | - | - | "" |
| `userlabel` | Custom label/name of the device | Yes | `string` | - | - | "172.16.67.48" |
| `nativeemsname` | Native EMS name | No | `null/string` | - | - | null |
| `aliasnamelist` | Device alias name list | No | `null/array` | - | - | null |
| `resourcestate` | Device Online status | Yes | `number` | 1 = Online 0: Offline |  | 1 |
| `longitude` | Device longitude coordinate | No | `null/number` | - | Complies with geographic coordinate specifications | null |
| `latitude` | Device latitude coordinate | No | `null/number` | - | Complies with geographic coordinate specifications | null |
| `south_protocol` | Southbound access protocol type | Yes | `number` | 0 = Unknown, 1 = SNMP | Enumerated values: 0, 1 | 1 |
| `proto_param` | Southbound protocol configuration parameters | Yes | `string` | - | Standard JSON format string | "{\"port\":161,\"retries\":2,\"timeout\":5,\"version\":2,\"hostname\":\"172.16.67.48\",\"community_read\":\"d0e713448981713b4fc17fbeb0854331\",\"community_write\":\"4bbf67cb9c38e861129378c654936b78\"}" |
| `netypeid` | Network element type ID | Yes | `number` | - | Positive integer only | 2001 |
| `ipaddress` | Device management IP address | Yes | `string` | - | Standard IPv4 format | "172.16.67.48" |
| `master_ipaddress` | Master device IP address | Yes | `string` | - | Standard IPv4 format | "172.16.67.48" |
| `slave_ipaddress` | Slave device IP address | No | `null/string` | - | Standard IPv4 format | null |
| `macaddress` | Device MAC address | Yes | `string` | - | Standard MAC address format | "a8:6d:5f:34:f7:cf" |
| `hostname` | Device host name | Yes | `string` | - | - | "Raisecom" |
| `telnet_port` | Telnet service port number | Yes | `number` | - | 1-65535 | 23 |
| `software_ver` | Device software version | Yes | `string` | - | - | "5.6.22_20251215" |
| `software_ver_disp` | Display version of software | No | `null/string` | - | - | null |
| `hardware_ver` | Device hardware version | Yes | `string` | - | - | "E.10" |
| `web_url` | Device web management URL | Yes | `string` | - | - | "" |
| `tenant` | Tenant ID | Yes | `number` | - | Non-negative integer | 0 |
| `managedomain` | Management domain | No | `null/string` | - | - | null |
| `create_time` | Device creation time | Yes | `string` | - | UTC ISO 8601 format | "2025-12-17T09:56:24.000Z" |
| `poll_enabled` | Polling switch status | Yes | `number` | 0 = Disabled, 1 = Enabled | Enumerated values: 0, 1 | 1 |
| `poll_interval` | Polling interval (seconds) | Yes | `number` | - | Positive integer | 1800 |
| `last_res_sync_begin_time` | Last resource sync start time | No | `null/number` | - | Unix timestamp (ms) | 1765965385700 |
| `last_res_sync_end_time` | Last resource sync end time | No | `null/number` | - | Unix timestamp (ms) | 1765965420004 |
| `last_sync_status` | Last sync overall status | Yes | `number` | 1 = Idle, 3 = Success | Enumerated values: 1,3 | 3 |
| `last_res_sync_consistency` | Last resource sync consistency | Yes | `number` | 1 = Consistent | Enumerated value:1 | 1 |
| `last_res_sync_remark` | Last resource sync remark | Yes | `string` | - | - | "Synchronization successful" |
| `port` | SNMP service port | Yes | `number` | - | 1-65535 | 161 |
| `managed_url` | Device managed access URL | Yes | `string` | - | - | "" |
| `uplink_port` | Uplink port name | Yes | `string` | - | - | "" |
| `reverse_pattern` | Reverse connection pattern | No | `null/string` | - | - | null |
| `is_support_reverse` | Reverse connection support status | Yes | `number` | 0 = Not supported, 1 = Supported | Enumerated values:0,1 | 0 |
| `last_alarm_sync_begin_time` | Last alarm sync start time | No | `null/number` | - | Unix timestamp (ms) | null |
| `last_alarm_sync_end_time` | Last alarm sync end time | No | `null/number` | - | Unix timestamp (ms) | null |
| `last_alarm_sync_status` | Last alarm sync status | Yes | `number` | 1 = Idle | Enumerated value:1 | 1 |
| `last_alarm_sync_triggermode` | Last alarm sync trigger mode | No | `null/string` | - | - | null |
| `last_alarm_sync_remark` | Last alarm sync remark | No | `null/string` | - | - | null |
| `ssh_port` | SSH service port number | Yes | `number` | - | 1-65535 | 22 |
| `poll_protocol` | Polling protocol type | Yes | `number` | 1 = SNMP | Enumerated value:1 | 1 |
| `islocal` | Local device flag | Yes | `number` | 0 = Remote, 1 = Local | Enumerated values:0,1 | 1 |
| `project_status` | Project deployment status | Yes | `number` | 1 = Normal | Enumerated value:1 | 1 |
| `row_key` | Data table row key | Yes | `string` | - | - | "" |
| `index_in_mib` | Index in MIB library | No | `null/number` | - | - | null |
| `managed_mode` | Device management mode | Yes | `number` | 1 = Managed | Enumerated value:1 | 1 |
| `pm_ver` | Performance monitoring version | Yes | `number` | - | Non-negative integer | 0 |
| `lldp` | LLDP MAC address | Yes | `string` | - | Standard MAC address format | "a8:6d:5f:34:f7:cf" |
| `chassis_mac` | Chassis MAC address | No | `null/string` | - | Standard MAC address format | null |
| `uplink_ne` | Uplink network element ID | No | `null/number` | - | - | null |
| `business` | Business affiliation | No | `null/string` | - | - | null |
| `serial_no` | Device serial number | Yes | `string` | - | - | "103002033201S22119S0740P" |
| `loid` | Logical optical ID | No | `null/string` | - | - | null |
| `south_feature_key` | Southbound feature key | No | `null/string` | - | - | null |
| `omc_id` | OMC management ID | No | `null/string` | - | - | null |
| `fixed_netype_id` | Fixed network element type ID | Yes | `number` | - | Positive integer | 2001 |
| `netype_userlabel` | Custom label of NE type | Yes | `string` | - | - | "iTN167-4GC(B)" |
| `nemodel_name` | NE model name | Yes | `string` | - | - | "iTN167-4GC(B)" |
| `fixed_nemodel_name` | Fixed NE model name | Yes | `string` | - | - | "iTN167-4GC(B)" |
| `nemodel_userlabel` | Custom label of NE model | Yes | `string` | - | - | "iTN167-4GC(B)" |
| `cot_location` | COT physical location | No | `null/string` | - | - | null |
| `create_user` | Creator username | Yes | `string` | - | - | "administrator" |
| `update_time` | Last update time | Yes | `string` | - | UTC ISO 8601 format | "2025-12-26T09:20:50.000Z" |
| `ne_desc` | Device description | No | `null/string` | - | - | null |
| `map_hierarchy` | Hierarchy in topology map | Yes | `string` | - | - | ",0,3," |
| `area1_id` | Level 1 area ID | Yes | `number` | - | Positive integer | 3 |
| `area2_id` | Level 2 area ID | No | `null/number` | - | Positive integer | null |
| `area3_id` | Level 3 area ID | No | `null/number` | - | Positive integer | null |
| `area4_id` | Level 4 area ID | No | `null/number` | - | Positive integer | null |
| `area5_id` | Level 5 area ID | No | `null/number` | - | Positive integer | null |
| `is_support_resourcesyn` | Resource sync support status | Yes | `number` | 0 = Not supported,1 = Supported | Enumerated values:0,1 | 1 |
| `virtual_port_count` | Virtual port total count | Yes | `number` | - | Positive integer | 20 |
| `virtual_max_pon_count` | Max virtual PON port count | Yes | `number` | - | Positive integer | 8 |
| `virtual_lsr_id` | Virtual LSR ID | Yes | `string` | - | - | "" |
| `engine_id` | SNMP engine ID | Yes | `string` | - | Standard SNMP engine ID format | "80:00:22:b6:03:a8:6d:5f:34:f7:cf" |
| `is_polling` | Real-time polling status | Yes | `number` | 0 = Stopped,1 = Running | Enumerated values:0,1 | 1 |
| `net_work_level` | Network hierarchy level | Yes | `number` | - | Non-negative integer | 0 |
| `is_support_pm` | Performance monitoring support status | Yes | `number` | 0 = Not supported,1 = Supported | Enumerated values:0,1 | 0 |
| `last_rebuildlr_begin_time` | Last LR rebuild start time | Yes | `number` | - | Unix timestamp (ms) | 1766736726724 |
| `last_rebuildlr_end_time` | Last LR rebuild end time | Yes | `number` | - | Unix timestamp (ms) | 1766736726816 |
| `last_rebuildlr_status` | Last LR rebuild status | Yes | `number` | 1 = Success,2 = Failed | Enumerated values:1,2 | 2 |
| `trap_target_address` | SNMP trap target address | No | `null/string` | - | Standard IPv4 format | null |
| `trap_source_address` | SNMP trap source address | No | `null/string` | - | Standard IPv4 format | null |
| `is_support_replace` | Device replace support status | Yes | `number` | 0 = Not supported,1 = Supported | Enumerated values:0,1 | 0 |
| `rackid` | Rack ID | No | `null/number` | - | Positive integer | null |
| `rack_userlabel` | Custom rack label | No | `null/string` | - | - | null |
| `netypename` | Network element type name | Yes | `string` | - | - | "iTN167-4GC(B)" |
| `subnet_id` | Subnet ID | Yes | `number` | - | Non-negative integer | 0 |
| `subnet_name` | Subnet name | Yes | `string` | - | - | "Root Subnet" |
| `retry` | SNMP retry count | Yes | `string` | - | Positive integer string | "2" |
| `readcom` | SNMP read community | Yes | `string` | - | - | "d0e713448981713b4fc17fbeb0854331" |
| `writecom` | SNMP write community | Yes | `string` | - | - | "4bbf67cb9c38e861129378c654936b78" |
| `timeout` | SNMP timeout (seconds) | Yes | `number` | - | Positive integer | 5 |
| `software_dispver` | Software display version | Yes | `string` | - | - | "5.6.22_20251215" |
| `alarm_last_syn_time` | Last alarm sync time | No | `null/number` | - | Unix timestamp (ms) | null |
| `alarm_res_syn_begin_time` | Alarm resource sync start time | No | `null/number` | - | Unix timestamp (ms) | null |
| `alarm_syn_remark` | Alarm sync remark | No | `null/string` | - | - | null |
| `alarm_syn_status` | Alarm sync status | Yes | `number` | 1 = Idle | Enumerated value:1 | 1 |
| `res_syn_begin_time` | Resource sync start time | Yes | `number` | - | Unix timestamp (ms) | 1765965385700 |
| `res_syn_consistency` | Resource sync consistency | Yes | `number` | 1 = Consistent | Enumerated value:1 | 1 |
| `res_syn_remark` | Resource sync remark | Yes | `string` | - | - | "Synchronization successful" |
| `last_syn_time` | Last synchronization time | Yes | `number` | - | Unix timestamp (ms) | 1765965420004 |
| `syn_status` | Synchronization status | Yes | `number` | 3 = Success | Enumerated value:3 | 3 |
| `fix_ne_type_id` | Fixed NE type identifier | Yes | `string` | - | - | "iPN100" |
| `friendly_name` | Device friendly name | Yes | `string` | - | - | "172.16.67.48" |
| `ircnetnodeid` | IRC network node ID | Yes | `number` | - | Positive integer | 6 |
| `ircnetypeid` | IRC network element type ID | Yes | `string` | - | - | "iTN167-4GC(B)" |
| `is_local` | Local device identifier | Yes | `number` | 0 = Remote,1 = Local | Enumerated values:0,1 | 1 |
| `lsr_id` | LSR identifier | Yes | `string` | - | Standard IPv4 format | "0.0.0.0" |
| `mac` | Device MAC address (secondary) | No | `null/string` | - | Standard MAC address format | null |
| `ne_name` | Network element name | Yes | `string` | - | - | "Raisecom" |
| `serial` | Device serial number (secondary) | Yes | `string` | - | - | "103002033201S22119S0740P" |
| `is_syn` | Synchronization enable flag | Yes | `number` | 0 = Disabled,1 = Enabled | Enumerated values:0,1 | 0 |
| `retries` | SNMP retry count (numeric) | Yes | `number` | - | Positive integer | 2 |
| `version` | SNMP protocol version | Yes | `number` | 2 = SNMPv2c | Enumerated value:2 | 2 |
| `v3authKey` | SNMPv3 authentication key | Yes | `string` | - | - | "" |
| `v3privKey` | SNMPv3 privacy key | Yes | `string` | - | - | "" |
| `v3contextName` | SNMPv3 context name | Yes | `string` | - | - | "" |
| `community_read` | SNMP read community (duplicate) | Yes | `string` | - | - | "d0e713448981713b4fc17fbeb0854331" |
| `v3authProtocol` | SNMPv3 authentication protocol | Yes | `string` | - | - | "MD5" |
| `v3privProtocol` | SNMPv3 privacy protocol | Yes | `string` | - | - | "DES" |
| `v3securityName` | SNMPv3 security name | Yes | `string` | - | - | "" |
| `community_write` | SNMP write community (duplicate) | Yes | `string` | - | - | "4bbf67cb9c38e861129378c654936b78" |
| `v3securityLevel` | SNMPv3 security level | Yes | `string` | - | - | "noAuthNoPriv" |
| `full_subnet_name` | Full subnet name | Yes | `string` | - | - | "Root Subnet" |


### Success Example
```json
version": null,
            "vendor": null,
            "location": "",
            "userlabel": "host172161248",
            "nativeemsname": null,
            "aliasnamelist": null,
            "resourcestate": 1,
            "longitude": null,
            "latitude": null,
            "south_protocol": 0,
            "proto_param": null,
            "netypeid": 451,
            "ipaddress": "172.16.1.248",
            "master_ipaddress": "172.16.1.248",
            "slave_ipaddress": null,
            "macaddress": "",
            "hostname": "",
            "telnet_port": 23,
            "software_ver": "",
            "software_ver_disp": null,
            "hardware_ver": "",
            "web_url": "",
            "tenant": 0,
            "managedomain": null,
            "create_time": "2025-12-17T09:36:49.000Z",
            "poll_enabled": 0,
            "poll_interval": 1800,
            "last_res_sync_begin_time": null,
            "last_res_sync_end_time": null,
            "last_sync_status": 1,
            "last_res_sync_consistency": 1,
            "last_res_sync_remark": "",
            "port": 161,
            "managed_url": "",
            "uplink_port": "",
            "reverse_pattern": null,
            "is_support_reverse": 0,
            "last_alarm_sync_begin_time": null,
            "last_alarm_sync_end_time": null,
            "last_alarm_sync_status": 1,
            "last_alarm_sync_triggermode": null,
            "last_alarm_sync_remark": null,
            "ssh_port": 22,
            "poll_protocol": 1,
            "islocal": 1,
            "project_status": 1,
            "row_key": "",
            "index_in_mib": null,
            "managed_mode": 1,
            "pm_ver": 0,
            "lldp": null,
            "chassis_mac": null,
            "uplink_ne": null,
            "business": null,
            "serial_no": null,
            "loid": null,
            "south_feature_key": null,
            "omc_id": null,
            "fixed_netype_id": 451,
            "netype_userlabel": "NMS",
            "nemodel_name": "",
            "fixed_nemodel_name": "",
            "nemodel_userlabel": "",
            "cot_location": null,
            "create_user": "",
            "update_time": "2025-12-25T11:41:41.000Z",
            "ne_desc": null,
            "map_hierarchy": ",0,1,",
            "area1_id": 1,
            "area2_id": null,
            "area3_id": null,
            "area4_id": null,
            "area5_id": null,
            "is_support_resourcesyn": 1,
            "virtual_port_count": 20,
            "virtual_max_pon_count": 8,
            "virtual_lsr_id": "",
            "engine_id": null,
            "is_polling": 0,
            "net_work_level": 0,
            "is_support_pm": 0,
            "last_rebuildlr_begin_time": 1766662901315,
            "last_rebuildlr_end_time": 1766662901337,
            "last_rebuildlr_status": 1,
            "trap_target_address": null,
            "trap_source_address": null,
            "is_support_replace": 0,
            "rackid": null,
            "rack_userlabel": null,
            "netypename": "NMS",
            "subnet_id": 0,
            "subnet_name": "根子网",
            "retry": null,
            "readcom": "",
            "writecom": "",
            "timeout": null,
            "software_dispver": "",
            "alarm_last_syn_time": null,
            "alarm_res_syn_begin_time": null,
            "alarm_syn_remark": null,
            "alarm_syn_status": 1,
            "res_syn_begin_time": null,
            "res_syn_consistency": 1,
            "res_syn_remark": "",
            "last_syn_time": null,
            "syn_status": 1,
            "fix_ne_type_id": "Server",
            "friendly_name": "host172161248",
            "ircnetnodeid": 2,
            "ircnetypeid": "NMS",
            "is_local": 1,
            "lsr_id": "",
            "mac": null,
            "ne_name": "",
            "serial": null,
            "is_syn": 0,
            "full_subnet_name": "根子网"
        },
        {
            "uuid": "a60d3f70-db2e-11f0-b89f-61b6ad1f2900",
            "neid": 6,
            "softbaseversion": "P200R002C53",
            "vendor": "Raisecom",
            "location": "",
            "userlabel": "172.16.67.48",
            "nativeemsname": null,
            "aliasnamelist": null,
            "resourcestate": 1,
            "longitude": null,
            "latitude": null,
            "south_protocol": 1,
            "proto_param": "{\"port\":161,\"retries\":2,\"timeout\":5,\"version\":2,\"hostname\":\"172.16.67.48\",\"v3authKey\":\"\",\"v3privKey\":\"\",\"v3contextName\":\"\",\"community_read\":\"d0e713448981713b4fc17fbeb0854331\",\"v3authProtocol\":\"MD5\",\"v3privProtocol\":\"DES\",\"v3securityName\":\"\",\"community_write\":\"4bbf67cb9c38e861129378c654936b78\",\"v3securityLevel\":\"noAuthNoPriv\"}",
            "netypeid": 2001,
            "ipaddress": "172.16.67.48",
            "master_ipaddress": "172.16.67.48",
            "slave_ipaddress": null,
            "macaddress": "a8:6d:5f:34:f7:cf",
            "hostname": "Raisecom",
            "telnet_port": 23,
            "software_ver": "5.6.22_20251215",
            "software_ver_disp": null,
            "hardware_ver": "E.10",
            "web_url": "",
            "tenant": 0,
            "managedomain": null,
            "create_time": "2025-12-17T09:56:24.000Z",
            "poll_enabled": 1,
            "poll_interval": 1800,
            "last_res_sync_begin_time": 1765965385700,
            "last_res_sync_end_time": 1765965420004,
            "last_sync_status": 3,
            "last_res_sync_consistency": 1,
            "last_res_sync_remark": "同步成功",
            "port": 161,
            "managed_url": "",
            "uplink_port": "",
            "reverse_pattern": null,
            "is_support_reverse": 0,
            "last_alarm_sync_begin_time": null,
            "last_alarm_sync_end_time": null,
            "last_alarm_sync_status": 1,
            "last_alarm_sync_triggermode": null,
            "last_alarm_sync_remark": null,
            "ssh_port": 22,
            "poll_protocol": 1,
            "islocal": 1,
            "project_status": 1,
            "row_key": "",
            "index_in_mib": null,
            "managed_mode": 1,
            "pm_ver": 0,
            "lldp": "a8:6d:5f:34:f7:cf",
            "chassis_mac": null,
            "uplink_ne": null,
            "business": null,
            "serial_no": "103002033201S22119S0740P",
            "loid": null,
            "south_feature_key": null,
            "omc_id": null,
            "fixed_netype_id": 2001,
            "netype_userlabel": "iTN167-4GC(B)",
            "nemodel_name": "iTN167-4GC(B)",
            "fixed_nemodel_name": "iTN167-4GC(B)",
            "nemodel_userlabel": "iTN167-4GC(B)",
            "cot_location": null,
            "create_user": "administrator",
            "update_time": "2025-12-26T09:20:50.000Z",
            "ne_desc": null,
            "map_hierarchy": ",0,3,",
            "area1_id": 3,
            "area2_id": null,
            "area3_id": null,
            "area4_id": null,
            "area5_id": null,
            "is_support_resourcesyn": 1,
            "virtual_port_count": 20,
            "virtual_max_pon_count": 8,
            "virtual_lsr_id": "",
            "engine_id": "80:00:22:b6:03:a8:6d:5f:34:f7:cf",
            "is_polling": 1,
            "net_work_level": 0,
            "is_support_pm": 0,
            "last_rebuildlr_begin_time": 1766736726724,
            "last_rebuildlr_end_time": 1766736726816,
            "last_rebuildlr_status": 2,
            "trap_target_address": null,
            "trap_source_address": null,
            "is_support_replace": 0,
            "rackid": null,
            "rack_userlabel": null,
            "netypename": "iTN167-4GC(B)",
            "subnet_id": 0,
            "subnet_name": "根子网",
            "retry": "2",
            "readcom": "d0e713448981713b4fc17fbeb0854331",
            "writecom": "4bbf67cb9c38e861129378c654936b78",
            "timeout": 5,
            "software_dispver": "5.6.22_20251215",
            "alarm_last_syn_time": null,
            "alarm_res_syn_begin_time": null,
            "alarm_syn_remark": null,
            "alarm_syn_status": 1,
            "res_syn_begin_time": 1765965385700,
            "res_syn_consistency": 1,
            "res_syn_remark": "同步成功",
            "last_syn_time": 1765965420004,
            "syn_status": 3,
            "fix_ne_type_id": "iPN100",
            "friendly_name": "172.16.67.48",
            "ircnetnodeid": 6,
            "ircnetypeid": "iTN167-4GC(B)",
            "is_local": 1,
            "lsr_id": "0.0.0.0",
            "mac": null,
            "ne_name": "Raisecom",
            "serial": "103002033201S22119S0740P",
            "is_syn": 0,
            "retries": 2,
            "version": 2,
            "v3authKey": "",
            "v3privKey": "",
            "v3contextName": "",
            "community_read": "d0e713448981713b4fc17fbeb0854331",
            "v3authProtocol": "MD5",
            "v3privProtocol": "DES",
            "v3securityName": "",
            "community_write": "4bbf67cb9c38e861129378c654936b78",
            "v3securityLevel": "noAuthNoPriv",
            "full_subnet_name": "根子网"
        }
    ]
}
```
