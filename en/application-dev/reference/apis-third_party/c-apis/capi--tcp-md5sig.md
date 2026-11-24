# tcp_md5sig

## Overview

<!--Device-struct tcp_md5sig {...}--><!--Device-struct tcp_md5sig {...}-End-->

## Summary

### Member variables

| Name | Description |
| -- | -- |
| struct sockaddr_storage tcpm_addr | <!--Device-struct sockaddr_storage tcpm_addr--><!--Device-struct sockaddr_storage tcpm_addr-End--> |
| uint8_t tcpm_flags | <!--Device-uint8_t tcpm_flags--><!--Device-uint8_t tcpm_flags-End--> |
| uint8_t tcpm_prefixlen | <!--Device-uint8_t tcpm_prefixlen--><!--Device-uint8_t tcpm_prefixlen-End--> |
| uint16_t tcpm_keylen | <!--Device-uint16_t tcpm_keylen--><!--Device-uint16_t tcpm_keylen-End--> |
| uint32_t \_\_tcpm_pad | <!--Device-uint32_t \_\_tcpm_pad--><!--Device-uint32_t \_\_tcpm_pad-End--> |
| uint8_t tcpm_key[TCP_MD5SIG_MAXKEYLEN] | <!--Device-uint8_t tcpm_key[TCP_MD5SIG_MAXKEYLEN]--><!--Device-uint8_t tcpm_key[TCP_MD5SIG_MAXKEYLEN]-End--> |


