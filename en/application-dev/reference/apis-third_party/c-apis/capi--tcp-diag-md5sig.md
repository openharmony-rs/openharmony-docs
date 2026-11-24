# tcp_diag_md5sig

## Overview

<!--Device-struct tcp_diag_md5sig {...}--><!--Device-struct tcp_diag_md5sig {...}-End-->

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint8_t tcpm_family | <!--Device-uint8_t tcpm_family--><!--Device-uint8_t tcpm_family-End--> |
| uint8_t tcpm_prefixlen | <!--Device-uint8_t tcpm_prefixlen--><!--Device-uint8_t tcpm_prefixlen-End--> |
| uint16_t tcpm_keylen | <!--Device-uint16_t tcpm_keylen--><!--Device-uint16_t tcpm_keylen-End--> |
| uint32_t tcpm_addr[4] | <!--Device-uint32_t tcpm_addr[4]--><!--Device-uint32_t tcpm_addr[4]-End--> |
| uint8_t tcpm_key[TCP_MD5SIG_MAXKEYLEN] | <!--Device-uint8_t tcpm_key[TCP_MD5SIG_MAXKEYLEN]--><!--Device-uint8_t tcpm_key[TCP_MD5SIG_MAXKEYLEN]-End--> |


