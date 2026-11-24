# signalfd_siginfo

## Overview

<!--Device-struct signalfd_siginfo {...}--><!--Device-struct signalfd_siginfo {...}-End-->

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t ssi_signo | <!--Device-uint32_t ssi_signo--><!--Device-uint32_t ssi_signo-End--> |
| int32_t ssi_errno | <!--Device-int32_t ssi_errno--><!--Device-int32_t ssi_errno-End--> |
| int32_t ssi_code | <!--Device-int32_t ssi_code--><!--Device-int32_t ssi_code-End--> |
| uint32_t ssi_pid | <!--Device-uint32_t ssi_pid--><!--Device-uint32_t ssi_pid-End--> |
| uint32_t ssi_uid | <!--Device-uint32_t ssi_uid--><!--Device-uint32_t ssi_uid-End--> |
| int32_t ssi_fd | <!--Device-int32_t ssi_fd--><!--Device-int32_t ssi_fd-End--> |
| uint32_t ssi_tid | <!--Device-uint32_t ssi_tid--><!--Device-uint32_t ssi_tid-End--> |
| uint32_t ssi_band | <!--Device-uint32_t ssi_band--><!--Device-uint32_t ssi_band-End--> |
| uint32_t ssi_overrun | <!--Device-uint32_t ssi_overrun--><!--Device-uint32_t ssi_overrun-End--> |
| uint32_t ssi_trapno | <!--Device-uint32_t ssi_trapno--><!--Device-uint32_t ssi_trapno-End--> |
| int32_t ssi_status | <!--Device-int32_t ssi_status--><!--Device-int32_t ssi_status-End--> |
| int32_t ssi_int | <!--Device-int32_t ssi_int--><!--Device-int32_t ssi_int-End--> |
| uint64_t ssi_ptr | <!--Device-uint64_t ssi_ptr--><!--Device-uint64_t ssi_ptr-End--> |
| uint64_t ssi_utime | <!--Device-uint64_t ssi_utime--><!--Device-uint64_t ssi_utime-End--> |
| uint64_t ssi_stime | <!--Device-uint64_t ssi_stime--><!--Device-uint64_t ssi_stime-End--> |
| uint64_t ssi_addr | <!--Device-uint64_t ssi_addr--><!--Device-uint64_t ssi_addr-End--> |
| uint16_t ssi_addr_lsb | <!--Device-uint16_t ssi_addr_lsb--><!--Device-uint16_t ssi_addr_lsb-End--> |
| uint16_t \_\_pad2 | <!--Device-uint16_t \_\_pad2--><!--Device-uint16_t \_\_pad2-End--> |
| int32_t ssi_syscall | <!--Device-int32_t ssi_syscall--><!--Device-int32_t ssi_syscall-End--> |
| uint64_t ssi_call_addr | <!--Device-uint64_t ssi_call_addr--><!--Device-uint64_t ssi_call_addr-End--> |
| uint32_t ssi_arch | <!--Device-uint32_t ssi_arch--><!--Device-uint32_t ssi_arch-End--> |
| uint8_t \_\_pad[128-14*4-5*8-2*2] | <!--Device-uint8_t \_\_pad[128-14*4-5*8-2*2]--><!--Device-uint8_t \_\_pad[128-14*4-5*8-2*2]-End--> |


