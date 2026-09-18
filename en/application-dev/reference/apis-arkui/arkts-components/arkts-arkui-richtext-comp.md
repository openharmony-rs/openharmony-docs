# RichText

Defines RichText Component.

## RichText

```TypeScript
RichText(content: string | Resource)
```

Set value.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11 - 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| content | string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes |  |

## Summary

## Examples

```TypeScript
You can preview how this component looks on a real device, but not in DevEco Studio Previewer.
```

```TypeScript


Loads local resource files.

Loads local resource files through $rawfile.
```

```TypeScript
Load through the resource protocol, which applies to the Webview loading links with "#" routes.

When $rawfile is used to load a URL contains a number sign (#), the content following the number sign is treated as a fragment. To avoid this issue, you can use the resource://rawfile/ protocol prefix instead. If the URL contains a number sign (#), the content following the number sign is treated as an anchor (fragment).
```

```TypeScript
Create an index.html file in src/main/resources/rawfile.

HTML file to be loaded:
```
