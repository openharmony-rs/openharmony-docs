# ComponentSnapshot

提供获取组件截图的能力，包括已加载的组件的截图和没有加载的组件的截图。
> **说明：**  
>  
> - 本Class首批接口从API version 12开始支持。  
>  
> - 以下API需先使用UIContext中的[getComponentSnapshot()](arkts-arkui-arkui-uicontext-uicontext-c.md#getcomponentsnapshot)方法获取ComponentSnapshot对象，再通过此实例调用对应方法。  
>  
> - 缩放、平移、旋转等图形变换属性只对被截图组件的子组件生效；对目标组件本身应用图形变换属性不生效，显示的还是图形变换前的效果。

**起始版本：** 12

<!--Device-unnamed-export class ComponentSnapshot--><!--Device-unnamed-export class ComponentSnapshot-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { OverlayManager, FrameCallback, ResolvedUIContext, NodeRenderStateChangeCallback, MediaQuery, OverlayManagerOptions, TextMenuController, UIObserver, Font, KeyboardAvoidMode, MarqueeDynamicSyncScene, PromptAction, NodeRenderState, UIContext, TextSelectionClearPolicy, SwiperDynamicSyncScene, Router, MarqueeDynamicSyncSceneType, DialogPresenter, Magnifier, ContextMenuController, UIInspector, CursorController, SwiperDynamicSyncSceneType, AtomicServiceBar, PageInfo, TargetInfo, ComponentUtils, DragController, MeasureUtils, NodeIdentity } from '@kit.ArkUI';
```

## getWithRange

```TypeScript
getWithRange(start: NodeIdentity, end: NodeIdentity, isStartRect: boolean,
    options?: componentSnapshot.SnapshotOptions): Promise<image.PixelMap>
```

传入两个组件的ID，获取范围内的组件的截图，并通过Promise返回结果。
> **说明：**  
>  
> start对应的组件和end对应的组件必须为同一棵组件树上的组件，且start对应的组件需要为end对应的组件的祖先组件。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ComponentSnapshot-getWithRange(start: NodeIdentity, end: NodeIdentity, isStartRect: boolean,    options?: componentSnapshot.SnapshotOptions): Promise<image.PixelMap>--><!--Device-ComponentSnapshot-getWithRange(start: NodeIdentity, end: NodeIdentity, isStartRect: boolean,    options?: componentSnapshot.SnapshotOptions): Promise<image.PixelMap>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| start | [NodeIdentity](arkts-arkui-nodeidentity-t.md) | 是 | 范围开始的组件的ID。 |
| end | [NodeIdentity](arkts-arkui-nodeidentity-t.md) | 是 | 范围结束的组件的ID。 |
| isStartRect | boolean | 是 | 范围是否以开始组件的外接矩形为准。<br/>true表示以开始组件的外接矩形为准，false表示以结束组件的外接矩形为准。<br/>默认值为true。 |
| options | componentSnapshot.SnapshotOptions | 否 | 截图相关的自定义参数，不支持region参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;image.PixelMap&gt; | Result of the snapshot. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | Invalid ID detected. |
| [160003](../errorcode-snapshot.md#160003-截图选项不支持的色彩空间或动态范围模式) | Unsupported color space or dynamic range mode in snapshot options.<br>**适用版本：** 23+ |

**示例：**

```TypeScript
import { image } from '@kit.ImageKit';

@Entry
@Component
struct SnapshotExample {
  @State pixmap: image.PixelMap | undefined = undefined

  build() {
    Column() {
      Row() {
        Row() {
          Row() {
            Column() {
              Text('Text1').id('text1')
              Text('Text2').id('text2')
              Row() {
                Text('Text3').id('text3')
              }.id('root5').backgroundColor('#E4E8F0')
            }
            .width('80%')
            .height('80%')
            .justifyContent(FlexAlign.SpaceAround)
            .backgroundColor('#C1D1F0')
            .id('root4')
          }
          .width('80%')
          .height('80%')
          .justifyContent(FlexAlign.Center)
          .backgroundColor('#FFEEF0')
          .id('root3')
          .backgroundBlurStyle(BlurStyle.Thin, { colorMode: ThemeColorMode.LIGHT })
        }
        .width('80%')
        .height('80%')
        .justifyContent(FlexAlign.Center)
        .backgroundColor('#D5D5D5')
        .id('root2')
      }
      .width('50%')
      .height('50%')
      .justifyContent(FlexAlign.Center)
      .backgroundColor('#E4E8F0')
      .id('root1')

      Row() {
        Button("getWithRange")
          .onClick(() => {
            this.getUIContext()
              .getComponentSnapshot()
              .getWithRange('root2', 'root4', true)
              .then((pixmap: image.PixelMap) => {
                this.pixmap = pixmap
              })
              .catch((err: Error) => {
                console.error("error: " + err)
              })
          }).margin(10)
      }.justifyContent(FlexAlign.SpaceAround)

      Row() {
        Image(this.pixmap).width(200).height(300).border({ color: Color.Black, width: 2 }).margin(5)
      }.justifyContent(FlexAlign.SpaceAround)
    }
    .id('root')
    .width('100%')
    .height('100%')
    .alignItems(HorizontalAlign.Center)
  }
}

```

