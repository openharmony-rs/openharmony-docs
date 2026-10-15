# sigaction

## Overview

## Summary

### Member variables

| Name | Description |
| -- | -- |
| sigset_t sa_mask |  |
| int sa_flags |  |


### Member functions

| Name | Complete quotation | Description |
| -- | -- | -- |
| [void (\*sa_handler)(int)](#sa_handler) | \_\_sa_handler->sa_handler() |  |
| [void (\*sa_sigaction)(int, siginfo_t *, void *)](#sa_sigaction) | \_\_sa_handler->sa_sigaction() |  |
| [void (\*sa_restorer)(void)](#sa_restorer) | sa_restorer() |  |

## Member function description

### sa_handler()

```c
void (*sa_handler)(int)
```

**Description**

### sa_sigaction()

```c
void (*sa_sigaction)(int, siginfo_t *, void *)
```

**Description**

### sa_restorer()

```c
void (*sa_restorer)(void)
```

**Description**


