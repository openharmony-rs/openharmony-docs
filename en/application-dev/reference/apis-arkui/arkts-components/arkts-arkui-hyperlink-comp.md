# Hyperlink

The **Hyperlink** component supports two display forms: text and image. Tapping within the component area redirects to a specified web page. It is suitable for scenarios where external web links are opened within an app. This component must be used with the system browser.

> **NOTE:** 
> 
> - This component must be used with the system browser.

## Required Permissions

When a network connection is required to redirect to the target web page, you need to apply for the **ohos.permission.INTERNET** permission. For details about how to apply, see [Declaring Permissions](../../../security/AccessToken/declare-permissions.md).

## Child Components

This component can contain the [Image](arkts-arkui-image-comp.md) child component.

## Hyperlink

```TypeScript
Hyperlink(address: string | Resource, content?: string | Resource)
```

Defines the constructor of Hyperlink.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-HyperlinkInterface-(address: string | Resource, content?: string | Resource): HyperlinkAttribute--><!--Device-HyperlinkInterface-(address: string | Resource, content?: string | Resource): HyperlinkAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| address | string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Web page address that the **Hyperlink** component navigates to. |
| content | string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | No | Text displayed for the hyperlink in the **Hyperlink** component.<br>Default value: **''**. If this parameter is not set and the component has no child components, the **address** parameter value is displayed by default. <br>**NOTE:** <br>If the component has child components, the hyperlink text is not displayed. |

## Summary

## Examples

This example shows how to create hyperlinks with both images and text that can be clicked to navigate to a specified URL.

```TypeScript
@Entry
@Component
struct HyperlinkExample {
  build() {
    Column() {
      Column() {
        Hyperlink('https://example.com/') {
          // Replace $r('app.media.bg') with the image resource file you use.
          Image($r('app.media.bg'))
            .width(200)
            .height(100)
        }
      }

      Column() {
        Hyperlink('https://example.com/', 'Go to the developer website') {
        }
        .color(Color.Blue)
      }
    }.width('100%').height('100%').justifyContent(FlexAlign.Center)
  }
}
```
