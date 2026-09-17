# WindowState

Enumerates application window states.

**Since:** 26.0.0

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## DISCONNECT

```TypeScript
DISCONNECT = 0
```

The window has been created but is currently unavailable.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## CONNECT

```TypeScript
CONNECT = 1
```

The window has been created and is available for use.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## FOREGROUND

```TypeScript
FOREGROUND = 2
```

Foreground state, indicating that the window has entered the foreground display. This is a transitional state.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## ACTIVE

```TypeScript
ACTIVE = 3
```

Foreground active state, indicating that the window is currently displayed in the foreground.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## INACTIVE

```TypeScript
INACTIVE = 4
```

Foreground inactive state, indicating that the window is about to enter the background. This is a transitional state.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## BACKGROUND

```TypeScript
BACKGROUND = 5
```

Background state, indicating that the window has been moved to the background and is not visible.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager
