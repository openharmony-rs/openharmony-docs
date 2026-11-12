# sigevent

## Overview

<!--Device-struct sigevent {...}--><!--Device-struct sigevent {...}-End-->

## Summary

### Member variables

| Name | Description |
| -- | -- |
| union [sigval](capi--sigval.md) sigev_value |  |
| int sigev_signo |  |
| int sigev_notify |  |
| pthread_attr_t *sigev_notify_attributes |  |
| char \_\_pad |  |


### Member functions

| Name | Complete quotation | Description |
| -- | -- | -- |
| [void (\*sigev_notify_function)(union sigval)](#sigev_notify_function) | sigev_notify_function |  |

## Member function description

### sigev_notify_function()

```c
void (*sigev_notify_function)(union sigval)
```

**Description**

<!--Device-void (*sigev_notify_function)(union sigval)--><!--Device-void (*sigev_notify_function)(union sigval)-End-->


