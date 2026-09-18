# on (System API)

## Modules to Import

```TypeScript
import { missionManager } from '@kit.AbilityKit';
```

## on('mission')

```TypeScript
function on(type: 'mission', listener: MissionListener): number
```

Registers a listener to observe the mission status.

**Since:** 9

**Required permissions:** ohos.permission.MANAGE_MISSIONS

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'mission' | Yes | Name of the target mission. The value is fixed at **'mission'**, indicating the system mission status listener. |
| listener | [MissionListener](arkts-ability-missionmanager-missionlistener-t-sys.md) | Yes | Mission status listener to register. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Index of the mission status listener, which is created by the system and allocated when the listener is registered. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |


## on('missionEvent')

```TypeScript
function on(type: 'missionEvent', listener: MissionListener): number
```

Registers a listener to observe the mission status.

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [on](#onmission)(type: 'mission', listener: MissionListener)

**Required permissions:** ohos.permission.MANAGE_MISSIONS

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'missionEvent' | Yes | Name of the target mission. The value is fixed at **'missionEvent'**, indicating the system mission status listener. |
| listener | [MissionListener](arkts-ability-missionmanager-missionlistener-t-sys.md) | Yes | Mission status listener to register. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Index of the mission status listener, which is created by the system and allocated when the listener is registered. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
