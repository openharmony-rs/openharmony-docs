# Hyperlink

The **Hyperlink** component implements a link from a location in the component to another location.

> **NOTE** > > - This component must be used with the system browser.

## Required Permissions

If Internet access is required, you must apply for the **ohos.permission.INTERNET** permission. For details about how to apply for a permission, see [Declaring Permissions](../../../security/AccessToken/declare-permissions.md).

## Child Components

This component can contain the Image child component.

## Hyperlink

```TypeScript
Hyperlink(address: string | Resource, content?: string | Resource)
```

Defines the constructor of Hyperlink.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| address | string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Web page to which the hyperlink is redirected. |
| content | string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | No | Text displayed in the hyperlink.<br>Default value: **''**. If this parameter is not passed and the component does not have child components, the value of the **address** parameter is displayed by default.<br>**NOTE:** <br>If this component has child components, the hyperlink text is not displayed. |

## Summary

## Examples

```TypeScript
This example shows how to create hyperlinks with both images and text that can be clicked to navigate to a specified URL.
```
