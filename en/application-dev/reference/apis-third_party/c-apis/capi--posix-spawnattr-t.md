# posix_spawnattr_t

## Overview

<!--Device-struct posix_spawnattr_t {...}--><!--Device-struct posix_spawnattr_t {...}-End-->

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int \_\_flags | <!--Device-int \_\_flags--><!--Device-int \_\_flags-End--> |
| pid_t \_\_pgrp | <!--Device-pid_t \_\_pgrp--><!--Device-pid_t \_\_pgrp-End--> |
| sigset_t \_\_def, \_\_mask | <!--Device-sigset_t \_\_def, \_\_mask--><!--Device-sigset_t \_\_def, \_\_mask-End--> |
| int \_\_prio, \_\_pol | <!--Device-int \_\_prio, \_\_pol--><!--Device-int \_\_prio, \_\_pol-End--> |
| void *\_\_fn | <!--Device-void *\_\_fn--><!--Device-void *\_\_fn-End--> |
| char \_\_pad[64-sizeof(void *)] | <!--Device-char \_\_pad[64-sizeof(void *)]--><!--Device-char \_\_pad[64-sizeof(void *)]-End--> |


