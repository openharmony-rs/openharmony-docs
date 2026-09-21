# MediaCachedImage (System API)

MediaCachedImage 组件。

## MediaCachedImage

```TypeScript
MediaCachedImage(src: PixelMap | ResourceStr | DrawableDescriptor | ASTCResource)
```

要获取的图像资源。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | [PixelMap](arkts-arkui-common-comp-pixelmap-t.md) &#124; [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) &#124; DrawableDescriptor &#124; [ASTCResource](arkts-arkui-mediacachedimage-comp-astcresource-i-sys.md) | 是 |  |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [ASTCResource](arkts-arkui-mediacachedimage-comp-astcresource-i-sys.md) | 定义可以使用 ASTC 的资源。 |

## 示例

加载基本类型图片。

```TypeScript
@Entry
@Component
struct MediaCachedImageExample {
  build() {
    Column() {
      Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Start }) {
        Row() {
          // 加载png格式图片。
          MediaCachedImage($r('app.media.ic_camera_master_ai_leaf'))
            .width(110).height(110).margin(15)
            .overlay('png', { align: Alignment.Bottom, offset: { x: 0, y: 20 } })
          // 加载gif格式图片。
          MediaCachedImage($r('app.media.loading'))
            .width(110).height(110).margin(15)
            .overlay('gif', { align: Alignment.Bottom, offset: { x: 0, y: 20 } })
        }
        Row() {
          // 加载svg格式图片。
          MediaCachedImage($r('app.media.ic_camera_master_ai_clouded'))
            .width(110).height(110).margin(15)
            .overlay('svg', { align: Alignment.Bottom, offset: { x: 0, y: 20 } })
          // 加载jpg格式图片。
          MediaCachedImage($r('app.media.ic_public_favor_filled'))
            .width(110).height(110).margin(15)
            .overlay('jpg', { align: Alignment.Bottom, offset: { x: 0, y: 20 } })
        }
      }
    }.height(320).width(360).padding({ right: 10, top: 10 })
  }
}
```
