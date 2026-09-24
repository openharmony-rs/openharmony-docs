# SecurityComponentMethod

```TypeScript
declare class SecurityComponentMethod<T>
```

The universal attributes module for security components enables unified configuration of universal attributes such as layout, size, text, icon, color, border, and interaction behaviors.

This module is mainly used in the following scenarios:  
- Set layout, size, text, icon, color, border, and interaction-related attributes for security components  
such as [PasteButton](../arkts-components/arkts-arkui-pastebutton-comp.md#paste_button) and [SaveButton](../arkts-components/arkts-arkui-savebutton-comp.md#save_button).  
- Adjust the display effect and interaction experience of security components while ensuring compliance with  
the security component specifications. For specific constraints, see [Constraints](../../../security/AccessToken/security-component-overview.md#constraints).  
- Reuse the universal attribute capabilities of security components through chained calls.

## Key Enums

- [SecurityComponentLayoutDirection](arkts-arkui-securitycomponentlayoutdirection-e.md): Enumeration of icon and text  
layout directions for the security component. Specifies horizontal or vertical layout.  
- ButtonType: Enumeration of button styles for the security component.  
Specifies capsule, circle, rounded rectangle, or normal button style.

## Key APIs

- [SecurityComponentMethod](arkts-arkui-securitycomponentmethod-c.md): A collection of universal attribute methods for  
security components. Configures layout, size, text, icon, color, border, and interaction attributes for specific security components.

## Child Components

- Not supported

Defines the method of a security component.

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## key

```TypeScript
key(value: string): T
```

Sets the unique ID for the component. You shall guarantee its uniqueness. Upon successful invocation, the component is assigned the specified ID for precise positioning of the component instance during testing. If this API is used together with [id](arkts-arkui-securitycomponentmethod-c.md#id), the value set later overrides the value set earlier. You are advised to set only **id**.

<br>This API is intended exclusively for app testing to verify attribute configurations and interactive behaviors of security components. In production environments, use the public API [id](arkts-arkui-securitycomponentmethod-c.md#id).

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string | Yes | Unique ID for the component. You shall guarantee its uniqueness. This parameter is used to accurately locate security component instances by ID in test scenarios. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Attributes of the security component. |
