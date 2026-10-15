# AreaMode

```TypeScript
export enum AreaMode
```

Enumerates the file encryption levels, which are used to ensure data security for applications across different scenarios. You can select the appropriate encryption level based on the application requirements to protect user data.

**Since:** 9

<!--Device-contextConstant-export enum AreaMode--><!--Device-contextConstant-export enum AreaMode-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## EL1

```TypeScript
EL1 = 0
```

Device-level encryption. Directories with this encryption level are accessible after the device is powered on.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-AreaMode-EL1 = 0--><!--Device-AreaMode-EL1 = 0-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## EL2

```TypeScript
EL2 = 1
```

User-level encryption. Directories with this encryption level are accessible only after the device is powered on and the password is entered (for the first time).

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-AreaMode-EL2 = 1--><!--Device-AreaMode-EL2 = 1-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## EL3

```TypeScript
EL3 = 2
```

User-level encryption area. The file permissions in different scenarios are as follows: Opened file: when locked, readable and writable; after unlocking, readable and writable. Unopened file: when locked, cannot be opened, not readable or writable; after unlocking, can be opened, readable and writable. Create a new file: when locked, can be created, can be opened, writable but not readable; after unlocking, can be created, can be opened, readable and writable.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-AreaMode-EL3 = 2--><!--Device-AreaMode-EL3 = 2-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## EL4

```TypeScript
EL4 = 3
```

User-level encryption area. The file permissions in different scenarios are as follows: Opened file: when locked, not readable or writable; after unlocking, readable and writable. Unopened file: when locked, cannot be opened, not readable or writable; after unlocking, can be opened, readable and writable. Create a new file: when locked, cannot be created; after unlocking, can be created, can be opened, readable and writable.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-AreaMode-EL4 = 3--><!--Device-AreaMode-EL4 = 3-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## EL5

```TypeScript
EL5 = 4
```

Application-level encryption area. The file permissions in different scenarios are as follows: Opened file: when locked, readable and writable; after unlocking, readable and writable. Unopened file: when locked, after calling the [Access](arkts-ability-screenlockfilemanager-acquireaccess-f.md) API to obtain the retained key, can be opened, readable and writable; otherwise, cannot be opened, not readable or writable; after unlocking, can be opened, readable and writable. Create a new file: when locked, can be created, can be opened, readable and writable; after unlocking, can be created, can be opened, readable and writable.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-AreaMode-EL5 = 4--><!--Device-AreaMode-EL5 = 4-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
