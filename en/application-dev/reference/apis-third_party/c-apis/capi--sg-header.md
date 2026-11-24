# sg_header

## Overview

<!--Device-struct sg_header {...}--><!--Device-struct sg_header {...}-End-->

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int pack_len | <!--Device-int pack_len--><!--Device-int pack_len-End--> |
| int reply_len | <!--Device-int reply_len--><!--Device-int reply_len-End--> |
| int pack_id | <!--Device-int pack_id--><!--Device-int pack_id-End--> |
| int result | <!--Device-int result--><!--Device-int result-End--> |
| unsigned twelve_byte:1 | <!--Device-unsigned twelve_byte:1--><!--Device-unsigned twelve_byte:1-End--> |
| unsigned target_status:5 | <!--Device-unsigned target_status:5--><!--Device-unsigned target_status:5-End--> |
| unsigned host_status:8 | <!--Device-unsigned host_status:8--><!--Device-unsigned host_status:8-End--> |
| unsigned driver_status:8 | <!--Device-unsigned driver_status:8--><!--Device-unsigned driver_status:8-End--> |
| unsigned other_flags:10 | <!--Device-unsigned other_flags:10--><!--Device-unsigned other_flags:10-End--> |
| unsigned char sense_buffer[SG_MAX_SENSE] | <!--Device-unsigned char sense_buffer[SG_MAX_SENSE]--><!--Device-unsigned char sense_buffer[SG_MAX_SENSE]-End--> |


