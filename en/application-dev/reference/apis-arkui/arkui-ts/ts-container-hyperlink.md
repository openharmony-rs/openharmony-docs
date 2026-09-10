# Hyperlink

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hddgzw-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=92567145241181b97abe57e944e177355e50f4eb translatedAt=2026-08-04T12:07:40.661Z pushedAt=2026-08-07T03:11:50.563Z -->

The **Hyperlink** component supports two display forms: text and image. Tapping within the component area redirects to a specified web page. It is suitable for scenarios where external web links are opened within an app. This component must be used with the system browser.

>  **NOTE**
>
>  - This component is supported since API version 7. Updates will be marked with a superscript to indicate their earliest API version.
>  - This component must be used with the system browser.

## Required Permissions

When a network connection is required to redirect to the target web page, you need to apply for the **ohos.permission.INTERNET** permission. For details about how to apply, see [Declaring Permissions](../../../security/AccessToken/declare-permissions.md).

## Child Components

This component can contain the [Image](ts-basic-components-image.md) child component.

## APIs

Hyperlink(address: string | Resource, content?: string | Resource)

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| address | string&nbsp;\|&nbsp;[Resource](ts-types.md#resource) | Yes | Web page address that the **Hyperlink** component navigates to. |
| content | string&nbsp;\|&nbsp;[Resource](ts-types.md#resource) | No | Text displayed for the hyperlink in the **Hyperlink** component.<br>Default value: **''**. If this parameter is not set and the component has no child components, the **address** parameter value is displayed by default.<br>**NOTE**<br>If the component has child components, the hyperlink text is not displayed. |

## Attributes

In addition to the [universal attributes](ts-component-general-attributes.md), the following attributes are supported.

### color

color(value: Color | number | string | Resource)

Sets the color of the hyperlink text.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description              |
| ------ | ------------------------------------------------------------ | ---- | ------------------ |
| value  | [Color](ts-appendix-enums.md#color)&nbsp;\|&nbsp;number&nbsp;\|&nbsp;string&nbsp;\|&nbsp;[Resource](ts-types.md#resource) | Yes  | Color of the hyperlink text<br><!--RP1-->Default value: '#ff007dff', indicating blue.<!--RP1End-->|

## Example

This example shows how to create hyperlinks with both images and text that can be clicked to navigate to a specified URL.

```ts
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

![hyperlink](figures/hyperlink.PNG)