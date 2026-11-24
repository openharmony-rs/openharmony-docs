# sg_io_hdr

## Overview

<!--Device-struct sg_io_hdr {...}--><!--Device-struct sg_io_hdr {...}-End-->

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int interface_id | <!--Device-int interface_id--><!--Device-int interface_id-End--> |
| int dxfer_direction | <!--Device-int dxfer_direction--><!--Device-int dxfer_direction-End--> |
| unsigned char cmd_len | <!--Device-unsigned char cmd_len--><!--Device-unsigned char cmd_len-End--> |
| unsigned char mx_sb_len | <!--Device-unsigned char mx_sb_len--><!--Device-unsigned char mx_sb_len-End--> |
| unsigned short iovec_count | <!--Device-unsigned short iovec_count--><!--Device-unsigned short iovec_count-End--> |
| unsigned dxfer_len | <!--Device-unsigned dxfer_len--><!--Device-unsigned dxfer_len-End--> |
| void *dxferp | <!--Device-void *dxferp--><!--Device-void *dxferp-End--> |
| unsigned char *cmdp | <!--Device-unsigned char *cmdp--><!--Device-unsigned char *cmdp-End--> |
| unsigned char *sbp | <!--Device-unsigned char *sbp--><!--Device-unsigned char *sbp-End--> |
| unsigned timeout | <!--Device-unsigned timeout--><!--Device-unsigned timeout-End--> |
| unsigned flags | <!--Device-unsigned flags--><!--Device-unsigned flags-End--> |
| int pack_id | <!--Device-int pack_id--><!--Device-int pack_id-End--> |
| void *usr_ptr | <!--Device-void *usr_ptr--><!--Device-void *usr_ptr-End--> |
| unsigned char status | <!--Device-unsigned char status--><!--Device-unsigned char status-End--> |
| unsigned char masked_status | <!--Device-unsigned char masked_status--><!--Device-unsigned char masked_status-End--> |
| unsigned char msg_status | <!--Device-unsigned char msg_status--><!--Device-unsigned char msg_status-End--> |
| unsigned char sb_len_wr | <!--Device-unsigned char sb_len_wr--><!--Device-unsigned char sb_len_wr-End--> |
| unsigned short host_status | <!--Device-unsigned short host_status--><!--Device-unsigned short host_status-End--> |
| unsigned short driver_status | <!--Device-unsigned short driver_status--><!--Device-unsigned short driver_status-End--> |
| int resid | <!--Device-int resid--><!--Device-int resid-End--> |
| unsigned int duration | <!--Device-unsigned int duration--><!--Device-unsigned int duration-End--> |
| unsigned int info | <!--Device-unsigned int info--><!--Device-unsigned int info-End--> |


