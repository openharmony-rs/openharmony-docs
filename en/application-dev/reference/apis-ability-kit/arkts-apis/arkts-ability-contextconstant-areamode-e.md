# AreaMode

Enumerates the file encryption levels, which are used to ensure data security for applications across different scenarios. You can select the appropriate encryption level based on the application requirements to protect user data.

**Since:** 9

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## EL1

```TypeScript
EL1 = 0
```

Device-level encryption. Directories with this encryption level are accessible after the device is powered on.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## EL2

```TypeScript
EL2 = 1
```

User-level encryption. Directories with this encryption level are accessible only after the device is powered on and the password is entered (for the first time).

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## EL3

```TypeScript
EL3 = 2
```

User-level encryption. The file permissions vary according to their scenarios.

- An open file is always readable and writable regardless of whether the screen is locked.  
- When the screen is locked, a closed file cannot be opened, read, or written. When the screen is unlocked, such  
a file can be opened, read, and written.  
- When the screen is locked, a file can be created and then opened and written but not read. When the screen is  
unlocked, a file can be created and then opened, read, and written.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## EL4

```TypeScript
EL4 = 3
```

User-level encryption. The file permissions vary according to their scenarios.

- When the screen is locked, an open file is not readable or writable. When the screen is unlocked, such a file  
is readable and writable.  
- When the screen is locked, a closed file cannot be opened, read, or written. When the screen is unlocked, such  
a file can be opened, read, and written.  
- When the screen is locked, a file cannot be created. When the screen is unlocked, a file can be created and  
then opened, read, and written.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## EL5

```TypeScript
EL5 = 4
```

Application-level encryption. The file permissions vary according to their scenarios.

- An open file is always readable and writable regardless of whether the screen is locked.

When the screen is locked, a closed file can be opened, read, and written only if the reserved key is obtained by calling [Access](arkts-ability-screenlockfilemanager-acquireaccess-f.md). When the screen is unlocked, such a file can be opened, read, and written.

A file can be created and then opened, read, and written regardless of whether the screen is locked.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
