# MediaCachedImage (System API)

MediaCachedImage component.

## MediaCachedImage

```TypeScript
MediaCachedImage(src: PixelMap | ResourceStr | DrawableDescriptor | ASTCResource)
```

Image resource to be obtained.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| src | [PixelMap](arkts-arkui-common-comp-pixelmap-t.md) &#124; [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) &#124; DrawableDescriptor &#124; [ASTCResource](arkts-arkui-mediacachedimage-comp-astcresource-i-sys.md) | Yes |  |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [ASTCResource](arkts-arkui-mediacachedimage-comp-astcresource-i-sys.md) | Defines the resource which can use ASTC. |

## Examples

This example loads images of basic types.

```TypeScript
@Entry
@Component
struct MediaCachedImageExample {
  build() {
    Column() {
      Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Start }) {
        Row() {
          // Load a PNG image.
          MediaCachedImage($r('app.media.ic_camera_master_ai_leaf'))
            .width(110).height(110).margin(15)
            .overlay('png', { align: Alignment.Bottom, offset: { x: 0, y: 20 } })
          // Load a GIF image.
          MediaCachedImage($r('app.media.loading'))
            .width(110).height(110).margin(15)
            .overlay('gif', { align: Alignment.Bottom, offset: { x: 0, y: 20 } })
        }
        Row() {
          // Load an SVG image.
          MediaCachedImage($r('app.media.ic_camera_master_ai_clouded'))
            .width(110).height(110).margin(15)
            .overlay('svg', { align: Alignment.Bottom, offset: { x: 0, y: 20 } })
          // Load a JPG image.
          MediaCachedImage($r('app.media.ic_public_favor_filled'))
            .width(110).height(110).margin(15)
            .overlay('jpg', { align: Alignment.Bottom, offset: { x: 0, y: 20 } })
        }
      }
    }.height(320).width(360).padding({ right: 10, top: 10 })
  }
}
```
