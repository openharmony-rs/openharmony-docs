# FluidLightMode (System API)

```TypeScript
export enum FluidLightMode
```

Enumerates the fluid light modes of the input method.<br> <br>

| Name | Value| Description |  
| ------------ | -- | ------------------ |  
| NONE | 0 | The fluid light mode is not used.|
| [BACKGROUND_FLUID_LIGHT](arkts-ime-inputmethodengine-fluidlightmode-e-sys.md) | 1 | When the background fluid light mode is enabled, the system panel turns transparent.The fluid light effect must be implemented by the host application of the edit box.|

**Since:** 20

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**System API:** This is a system API.

## NONE

```TypeScript
NONE = 0
```

Disable fluid light mode.

**Since:** 20

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**System API:** This is a system API.

## BACKGROUND_FLUID_LIGHT

```TypeScript
BACKGROUND_FLUID_LIGHT = 1
```

When the background fluid light mode is enabled, the system panel turns transparent. The fluid light effect must be implemented by the application.

**Since:** 20

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**System API:** This is a system API.
