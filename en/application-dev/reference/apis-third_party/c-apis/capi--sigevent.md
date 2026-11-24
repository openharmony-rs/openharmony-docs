# sigevent

## Overview

<!--Device-struct sigevent {...}--><!--Device-struct sigevent {...}-End-->

## Summary

### Member variables

| Name | Description |
| -- | -- |
| union [sigval](capi--sigval.md) sigev_value | <!--Device-union sigval sigev_value--><!--Device-union sigval sigev_value-End--> |
| int sigev_signo | <!--Device-int sigev_signo--><!--Device-int sigev_signo-End--> |
| int sigev_notify | <!--Device-int sigev_notify--><!--Device-int sigev_notify-End--> |
| pthread_attr_t *sigev_notify_attributes | <!--Device-pthread_attr_t *sigev_notify_attributes--><!--Device-pthread_attr_t *sigev_notify_attributes-End--> |
| char \_\_pad[56-3*sizeof(long)] | <!--Device-char \_\_pad[56-3*sizeof(long)]--><!--Device-char \_\_pad[56-3*sizeof(long)]-End--> |


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


