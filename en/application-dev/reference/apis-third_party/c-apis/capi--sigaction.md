# sigaction

## Overview

<!--Device-struct sigaction {...}--><!--Device-struct sigaction {...}-End-->

## Summary

### Member variables

| Name | Description |
| -- | -- |
| \_\_sa_handler |  |
| sigset_t sa_mask |  |
| int sa_flags |  |


### Member functions

| Name | Complete quotation | Description |
| -- | -- | -- |
| [void (\*sa_handler)(int)](#sa_handler) | \_\_sa_handler->sa_handler |  |
| [void (\*sa_sigaction)(int, siginfo_t *, void *)](#sa_sigaction) | \_\_sa_handler->sa_sigaction |  |
| [void (\*sa_restorer)(void)](#sa_restorer) | sa_restorer |  |

## Member function description

### sa_handler()

```c
void (*sa_handler)(int)
```

**Description**

<!--Device-void (*sa_handler)(int)--><!--Device-void (*sa_handler)(int)-End-->

### sa_sigaction()

```c
void (*sa_sigaction)(int, siginfo_t *, void *)
```

**Description**

<!--Device-void (*sa_sigaction)(int, siginfo_t *, void *)--><!--Device-void (*sa_sigaction)(int, siginfo_t *, void *)-End-->

### sa_restorer()

```c
void (*sa_restorer)(void)
```

**Description**

<!--Device-void (*sa_restorer)(void)--><!--Device-void (*sa_restorer)(void)-End-->


