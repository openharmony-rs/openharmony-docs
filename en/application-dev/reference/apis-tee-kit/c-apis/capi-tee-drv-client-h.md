# tee_drv_client.h

## Overview

Declare tee driver client API.

**Library**: NA

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Related module**: [TeeTrusted](capi-teetrusted.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [int64_t tee_drv_open(const char *drv_name, const void *param, uint32_t param_len)](#tee_drv_open) | Open the specified driver in the TEE. |
| [int64_t tee_drv_ioctl(int64_t fd, uint32_t cmd_id, const void *param, uint32_t param_len)](#tee_drv_ioctl) | Cancels an operation. |
| [int64_t tee_drv_close(int64_t fd)](#tee_drv_close) | Open the specified driver in the TEE. |

## Function description

### tee_drv_open()

```c
int64_t tee_drv_open(const char *drv_name, const void *param, uint32_t param_len)
```

**Description**

Open the specified driver in the TEE.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *drv_name | [IN] The driver name. |
| const void *param | [IN] The parameter information. |
| uint32_t param_len | [IN] The length of the parameter. |

**Returns**:

| Type | Description |
| -- | -- |
| int64_t | Returns greater than 0, which means the fd of the corresponding driver.          Returns less than or equal to 0, which means falied to open the driver. |

### tee_drv_ioctl()

```c
int64_t tee_drv_ioctl(int64_t fd, uint32_t cmd_id, const void *param, uint32_t param_len)
```

**Description**

Cancels an operation.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| int64_t fd | [IN] The file descriptor of the driver. |
| uint32_t cmd_id | [IN] The command id. |
| const void *param | [IN] The parameter information. |
| uint32_t param_len | [IN] The length of the parameter. |

**Returns**:

| Type | Description |
| -- | -- |
| int64_t | Returns <b>0</b> if the operation is successful.          Returns <b>-1</b> if the operation is failed. |

### tee_drv_close()

```c
int64_t tee_drv_close(int64_t fd)
```

**Description**

Open the specified driver in the TEE.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| int64_t fd | [IN] The file descriptor of the driver. |

**Returns**:

| Type | Description |
| -- | -- |
| int64_t | Returns <b>0</b> if the operation is successful.          Returns <b>-1</b> if the operation is failed. |


