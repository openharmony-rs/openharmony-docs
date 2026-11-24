# dl_phdr_info

## Overview

<!--Device-struct dl_phdr_info {...}--><!--Device-struct dl_phdr_info {...}-End-->

## Summary

### Member variables

| Name | Description |
| -- | -- |
| ElfW(Addr) dlpi_addr | <!--Device-ElfW(Addr) dlpi_addr--><!--Device-ElfW(Addr) dlpi_addr-End--> |
| const char *dlpi_name | <!--Device-const char *dlpi_name--><!--Device-const char *dlpi_name-End--> |
| const ElfW(Phdr) *dlpi_phdr | <!--Device-const ElfW(Phdr) *dlpi_phdr--><!--Device-const ElfW(Phdr) *dlpi_phdr-End--> |
| ElfW(Half) dlpi_phnum | <!--Device-ElfW(Half) dlpi_phnum--><!--Device-ElfW(Half) dlpi_phnum-End--> |
| unsigned long long int dlpi_adds | <!--Device-unsigned long long int dlpi_adds--><!--Device-unsigned long long int dlpi_adds-End--> |
| unsigned long long int dlpi_subs | <!--Device-unsigned long long int dlpi_subs--><!--Device-unsigned long long int dlpi_subs-End--> |
| size_t dlpi_tls_modid | <!--Device-size_t dlpi_tls_modid--><!--Device-size_t dlpi_tls_modid-End--> |
| void *dlpi_tls_data | <!--Device-void *dlpi_tls_data--><!--Device-void *dlpi_tls_data-End--> |


