# iTN8600-A EMS APIs

## Overview
This directory contains REST API documentation for iTN8600-A EMS (Element Management System) operations.

## API List

| # | API Name | File | Description | Method |
|---|----------|------|-------------|--------|
| 1 | [Query Optical Transceiver Information](query_optical_transceiver_information.md) | `query_optical_transceiver_information.md` | Query optical module information for a specific card | GET |
| 2 | [Query Port Information](query_port_information.md) | `query_port_information.md` | Query port link status and working speed | GET |
| 3 | [Query Optical Transceiver Digital Diagnostic Information](query_optical_transceiver_ddm.md) | `query_optical_transceiver_ddm.md` | Query optical transceiver digital diagnostic monitoring (DDM) information | GET |
| 4 | [Query Optical Transceiver](query_optical_transceiver.md) | `query_optical_transceiver.md` | Query detailed optical transceiver information including properties, thresholds, and alarm statuses | GET |
| 5 | [Query Port FEC Information](query_port_fec_information.md) | `query_port_fec_information.md` | Query FEC-related information for a specific port | GET |
| 6 | [Query Optical Transceiver Status](query_optical_transceiver_status.md) | `query_optical_transceiver_status.md` | Query optical transceiver current status including OSNR and hardware control info | GET |

## Related Documentation
- [LLDP](../lldp.md) - LLDP neighbor information query
- [TWAMP APIs](../../TWAMP/README.md) - TWAMP SLA measurement
- [PM APIs](../../PM/README.md) - Performance management
