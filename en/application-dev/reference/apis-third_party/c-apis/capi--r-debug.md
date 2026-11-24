# r_debug

## Overview

<!--Device-struct r_debug {...}--><!--Device-struct r_debug {...}-End-->

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int r_version | <!--Device-int r_version--><!--Device-int r_version-End--> |
| [struct link_map](capi--link-map.md) *r_map | <!--Device-struct link_map *r_map--><!--Device-struct link_map *r_map-End--> |
| ElfW(Addr) r_brk | <!--Device-ElfW(Addr) r_brk--><!--Device-ElfW(Addr) r_brk-End--> |
| r_state.RT_CONSISTENT, | <!--Device-r_state.RT_CONSISTENT,--><!--Device-r_state.RT_CONSISTENT,-End--> |
| r_state.RT_ADD, | <!--Device-r_state.RT_ADD,--><!--Device-r_state.RT_ADD,-End--> |
| r_state.RT_DELETE | <!--Device-r_state.RT_DELETE--><!--Device-r_state.RT_DELETE-End--> |
| ElfW(Addr) r_ldbase | <!--Device-ElfW(Addr) r_ldbase--><!--Device-ElfW(Addr) r_ldbase-End--> |


