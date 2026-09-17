# SuppressWarningsType

Defines the warning types that support suppression. Developers can selectively suppress compatibility warnings, multi-device warnings, and permission warnings as required. This helps ensure code quality, reduce unnecessary warning interference, and improve development experience.

**Since:** 23

**System capability:** SystemCapability.Base

## COMPATIBILITY

```TypeScript
COMPATIBILITY = 'compatibility'
```

Compatibility warning. This warning is generated when the start version of the API called is later than the compatible SDK version (**compatibleSdkVersion** specified in **build-profile.json5**) set for the project. It is recommended that this warning be suppressed when version check or compatibility processing has been performed. Suppressing this warning without proper handling may cause devices running earlier versions to malfunction.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.Base

## SYSCAP

```TypeScript
SYSCAP = 'syscap'
```

Multi-device warning. This warning is generated when the system capability obtained by calling the API is not supported on the target device.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.Base

## PERMISSION

```TypeScript
PERMISSION = 'permission'
```

Permission warning. This warning is generated when an API that requires permissions is called but the corresponding permissions are not declared in the configuration file.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.Base
