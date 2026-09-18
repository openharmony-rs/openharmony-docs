# tee_agent.h

## Overview

Provides the API about TA agent.

**Library**: NA

**System capability**: SystemCapability.Tee.TeeClient

**Since**: 20

**Related module**: [TeeTrusted](capi-teetrusted.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [TEE_Result tee_agent_lock(uint32_t agent_id)](#tee_agent_lock) | The TA sends a message to the gtask to lock the agent. |
| [TEE_Result tee_agent_unlock(uint32_t agent_id)](#tee_agent_unlock) | Unlock the agent. |
| [TEE_Result tee_send_agent_cmd(uint32_t agent_id)](#tee_send_agent_cmd) | Send agent cmd to gtask. |
| [TEE_Result tee_get_agent_buffer(uint32_t agent_id, void **buffer, uint32_t *length)](#tee_get_agent_buffer) | Receive messgage in get agent buffer. |

## Function description

### tee_agent_lock()

```c
TEE_Result tee_agent_lock(uint32_t agent_id)
```

**Description**

The TA sends a message to the gtask to lock the agent.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint32_t agent_id | ID of the agent that requests to be locked. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns {@code TEE_SUCCESS} if the operation is successful.          Returns other information otherwise. |

### tee_agent_unlock()

```c
TEE_Result tee_agent_unlock(uint32_t agent_id)
```

**Description**

Unlock the agent.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint32_t agent_id | ID of the agent that requests to be unlocked. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns {@code TEE_SUCCESS} if the operation is successful.          Returns other information otherwise. |

### tee_send_agent_cmd()

```c
TEE_Result tee_send_agent_cmd(uint32_t agent_id)
```

**Description**

Send agent cmd to gtask.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint32_t agent_id | The agent ID. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns {@code TEE_SUCCESS} if the operation is successful.          Returns other information otherwise. |

### tee_get_agent_buffer()

```c
TEE_Result tee_get_agent_buffer(uint32_t agent_id, void **buffer, uint32_t *length)
```

**Description**

Receive messgage in get agent buffer.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| uint32_t agent_id | The agent ID. |
| void **buffer | The agent buffer. |
| uint32_t *length | The length of the agent buffer. |

**Returns**:

| Type | Description |
| -- | -- |
| TEE_Result | Returns {@code TEE_SUCCESS} if the operation is successful.          Returns other information otherwise. |


