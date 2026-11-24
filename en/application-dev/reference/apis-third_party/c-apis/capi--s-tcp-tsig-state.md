# s_tcp_tsig_state

## Overview

<!--Device-struct s_tcp_tsig_state {...}--><!--Device-struct s_tcp_tsig_state {...}-End-->

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int counter | <!--Device-int counter--><!--Device-int counter-End--> |
| struct dst_key *key | <!--Device-struct dst_key *key--><!--Device-struct dst_key *key-End--> |
| void *ctx | <!--Device-void *ctx--><!--Device-void *ctx-End--> |
| unsigned char sig[NS_PACKETSZ] | <!--Device-unsigned char sig[NS_PACKETSZ]--><!--Device-unsigned char sig[NS_PACKETSZ]-End--> |
| int siglen | <!--Device-int siglen--><!--Device-int siglen-End--> |


