# elf_prpsinfo

## Overview

<!--Device-struct elf_prpsinfo {...}--><!--Device-struct elf_prpsinfo {...}-End-->

## Summary

### Member variables

| Name | Description |
| -- | -- |
| char pr_state | <!--Device-char pr_state--><!--Device-char pr_state-End--> |
| char pr_sname | <!--Device-char pr_sname--><!--Device-char pr_sname-End--> |
| char pr_zomb | <!--Device-char pr_zomb--><!--Device-char pr_zomb-End--> |
| char pr_nice | <!--Device-char pr_nice--><!--Device-char pr_nice-End--> |
| unsigned long int pr_flag | <!--Device-unsigned long int pr_flag--><!--Device-unsigned long int pr_flag-End--> |
| unsigned short int pr_uid | <!--Device-unsigned short int pr_uid--><!--Device-unsigned short int pr_uid-End--> |
| unsigned short int pr_gid | <!--Device-unsigned short int pr_gid--><!--Device-unsigned short int pr_gid-End--> |
| int pr_pid, pr_ppid, pr_pgrp, pr_sid | <!--Device-int pr_pid, pr_ppid, pr_pgrp, pr_sid--><!--Device-int pr_pid, pr_ppid, pr_pgrp, pr_sid-End--> |
| char pr_fname[16] | <!--Device-char pr_fname[16]--><!--Device-char pr_fname[16]-End--> |
| char pr_psargs[ELF_PRARGSZ] | <!--Device-char pr_psargs[ELF_PRARGSZ]--><!--Device-char pr_psargs[ELF_PRARGSZ]-End--> |


