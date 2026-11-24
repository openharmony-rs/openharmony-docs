# __ptrace_syscall_info

## Overview

<!--Device-struct __ptrace_syscall_info {...}--><!--Device-struct __ptrace_syscall_info {...}-End-->

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint8_t op | <!--Device-uint8_t op--><!--Device-uint8_t op-End--> |
| uint8_t \_\_pad[3] | <!--Device-uint8_t \_\_pad[3]--><!--Device-uint8_t \_\_pad[3]-End--> |
| uint32_t arch | <!--Device-uint32_t arch--><!--Device-uint32_t arch-End--> |
| uint64_t instruction_pointer | <!--Device-uint64_t instruction_pointer--><!--Device-uint64_t instruction_pointer-End--> |
| uint64_t stack_pointer | <!--Device-uint64_t stack_pointer--><!--Device-uint64_t stack_pointer-End--> |
| entry.nr | <!--Device-entry.nr--><!--Device-entry.nr-End--> |
| entry.args | <!--Device-entry.args--><!--Device-entry.args-End--> |
| exit.rval | <!--Device-exit.rval--><!--Device-exit.rval-End--> |
| exit.is_error | <!--Device-exit.is_error--><!--Device-exit.is_error-End--> |
| seccomp.nr | <!--Device-seccomp.nr--><!--Device-seccomp.nr-End--> |
| seccomp.args | <!--Device-seccomp.args--><!--Device-seccomp.args-End--> |
| seccomp.ret_data | <!--Device-seccomp.ret_data--><!--Device-seccomp.ret_data-End--> |


