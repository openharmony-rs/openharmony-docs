# elf_prstatus

## Overview

<!--Device-struct elf_prstatus {...}--><!--Device-struct elf_prstatus {...}-End-->

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [struct elf_siginfo](capi--elf-siginfo.md) pr_info | <!--Device-struct elf_siginfo pr_info--><!--Device-struct elf_siginfo pr_info-End--> |
| short int pr_cursig | <!--Device-short int pr_cursig--><!--Device-short int pr_cursig-End--> |
| unsigned long int pr_sigpend | <!--Device-unsigned long int pr_sigpend--><!--Device-unsigned long int pr_sigpend-End--> |
| unsigned long int pr_sighold | <!--Device-unsigned long int pr_sighold--><!--Device-unsigned long int pr_sighold-End--> |
| pid_t pr_pid | <!--Device-pid_t pr_pid--><!--Device-pid_t pr_pid-End--> |
| pid_t pr_ppid | <!--Device-pid_t pr_ppid--><!--Device-pid_t pr_ppid-End--> |
| pid_t pr_pgrp | <!--Device-pid_t pr_pgrp--><!--Device-pid_t pr_pgrp-End--> |
| pid_t pr_sid | <!--Device-pid_t pr_sid--><!--Device-pid_t pr_sid-End--> |
| pr_utime.tv_usec | <!--Device-pr_utime.tv_usec--><!--Device-pr_utime.tv_usec-End--> |
| elf_gregset_t pr_reg | <!--Device-elf_gregset_t pr_reg--><!--Device-elf_gregset_t pr_reg-End--> |
| int pr_fpvalid | <!--Device-int pr_fpvalid--><!--Device-int pr_fpvalid-End--> |


