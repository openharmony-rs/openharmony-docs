# pthread_attr.h

## Overview

Provides the attr about TA multi-thread.

**Library**: NA

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Related module**: [TeeTrusted](capi-teetrusted.md)

## Summary

### Macro

| Name | Description |
| -- | -- |
| TEESMP_THREAD_ATTR_CA_WILDCARD 0 | Defines that the thread attribute of ca is not explicitly set (wildcard/default state).<br>**Since**: 20 |
| TEESMP_THREAD_ATTR_CA_INHERIT (-1U) | Defines that the thread attribute of ca inherit from the parent thread.<br>**Since**: 20 |
| TEESMP_THREAD_ATTR_TASK_ID_INHERIT (-1U) | Defines that the task ID attribute inherit from the parent task/thread.<br>**Since**: 20 |
| TEESMP_THREAD_ATTR_HAS_SHADOW 0x1 | Defines that the thread attribute has a shadow.<br>**Since**: 20 |
| TEESMP_THREAD_ATTR_NO_SHADOW 0x0 | Defines that the thread attribute does not have a shadow.<br>**Since**: 20 |

### Function

| Name | Description |
| -- | -- |
| [int pthread_attr_settee(pthread_attr_t *a, int ca, int task_id, int shadow)](#pthread_attr_settee) | Sets thread attributes for CA, task ID, and shadow settings. |

## Function description

### pthread_attr_settee()

```c
int pthread_attr_settee(pthread_attr_t *a, int ca, int task_id, int shadow)
```

**Description**

Sets thread attributes for CA, task ID, and shadow settings.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| pthread_attr_t *a | Pointer to the thread attribute object to be modified. |
| int ca | Specifies the CA attribute value (e.g., TEESMP_THREAD_ATTR_CA_INHERIT for inheritance). |
| int task_id | Specifies the task ID attribute value (e.g., TEESMP_THREAD_ATTR_TASK_ID_INHERIT for inheritance). |
| int shadow | Indicates whether to enable shadow settings (TEESMP_THREAD_ATTR_NO_SHADOW 0x0 for no shadow, TEESMP_THREAD_ATTR_HAS_SHADOW 0x1 for has shadow). |

**Returns**:

| Type | Description |
| -- | -- |
| int | always return 0. |


