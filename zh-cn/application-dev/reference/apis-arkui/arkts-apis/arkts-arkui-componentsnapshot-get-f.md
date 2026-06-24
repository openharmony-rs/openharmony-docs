# get

## get

```TypeScript
function get(id: string, callback: AsyncCallback<image.PixelMap>, options?: SnapshotOptions): void
```

获取已加载的组件的截图，传入组件的[组件标识](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md#common)，找到对应组件进行截图。通过回调返回结果。

> **说明：**
>
> - 从API version 12开始，可以通过使用[UIContext](arkts-arkui-uicontext.md)中的
> [getComponentSnapshot](arkts-arkui-uicontext-c.md#getComponentSnapshot-1)方法
> 获取当前UI上下文关联的[ComponentSnapshot](arkts-arkui-componentsnapshot-c.md#ComponentSnapshot)对象。
>
> - 截图会获取最近一帧的绘制内容。如果在组件触发更新的同时调用截图，更新的渲染内容不会被截取到，截图会返回上一帧的绘制内容。

**起始版本：** 10

**废弃版本：** 18

**替代接口：** get

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | 目标组件的[组件标识](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md#common)。 |
| callback | AsyncCallback&lt;image.PixelMap&gt; | 是 | 截图返回结果的回调。 |
| options | SnapshotOptions | 否 | 截图相关的自定义参数。 [since 12] |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameters types.<br/><br/>3. Parameter verification failed. |
| [100001](../../errorcode-universal.md#100001-Invalid) | Invalid ID. |

**示例：**

```TypeScript
import { componentSnapshot } from '@kit.ArkUI';
import { image } from '@kit.ImageKit';

@Entry
@Component
struct SnapshotExample {
  @State pixmap: image.PixelMap | undefined = undefined

  build() {
    Column() {
      Row() {
        Image(this.pixmap).width(200).height(200).border({ color: Color.Black, width: 2 }).margin(5)
        // $r('app.media.img')需要替换为开发者所需的图像资源文件
        Image($r('app.media.img'))
          .autoResize(true)
          .width(200)
          .height(200)
          .margin(5)
          .id("root")
      }

      Button("click to generate UI snapshot")
        .onClick(() => {
          // 建议使用this.getUIContext().getComponentSnapshot().get()
          componentSnapshot.get("root", (error: Error, pixmap: image.PixelMap) => {
            if (error) {
              console.error(`error:${JSON.stringify(error)}`)
              return;
            }
            this.pixmap = pixmap
          }, { scale: 2, waitUntilRenderFinished: true })
        }).margin(10)
    }
    .width('100%')
    .height('100%')
    .alignItems(HorizontalAlign.Center)
  }
}

```


## get

```TypeScript
function get(id: string, options?: SnapshotOptions): Promise<image.PixelMap>
```

获取已加载的组件的截图，传入组件的[组件标识](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md#common)，找到对应组件进行截图。通过Promise返回结果。

> **说明：**
>
> - 从API version 12开始，可以通过使用[UIContext](arkts-arkui-uicontext.md)中的
> [getComponentSnapshot](arkts-arkui-uicontext-c.md#getComponentSnapshot-1)方法
> 获取当前UI上下文关联的[ComponentSnapshot](arkts-arkui-componentsnapshot-c.md#ComponentSnapshot)对象。
>
> - 截图会获取最近一帧的绘制内容。如果在组件触发更新的同时调用截图，更新的渲染内容不会被截取到，截图会返回上一帧的绘制内容。

**起始版本：** 10

**废弃版本：** 18

**替代接口：** get

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | 目标组件的[组件标识](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md#common)。 |
| options | SnapshotOptions | 否 | 截图相关的自定义参数。 [since 12] |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;image.PixelMap&gt; | Promise used to return the result. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/><br/>1. Mandatory parameters are left unspecified.<br/><br/>2. Incorrect parameters types.<br/><br/>3. Parameter verification failed. |
| [100001](../../errorcode-universal.md#100001-Invalid) | Invalid ID. |

**示例：**

```TypeScript
import { componentSnapshot } from '@kit.ArkUI';
import { image } from '@kit.ImageKit';

@Entry
@Component
struct SnapshotExample {
  @State pixmap: image.PixelMap | undefined = undefined

  build() {
    Column() {
      Row() {
        Image(this.pixmap).width(200).height(200).border({ color: Color.Black, width: 2 }).margin(5)
        // $r('app.media.img')需要替换为开发者所需的图像资源文件
        Image($r('app.media.img'))
          .autoResize(true)
          .width(200)
          .height(200)
          .margin(5)
          .id("root")
      }

      Button("click to generate UI snapshot")
        .onClick(() => {
          // 建议使用this.getUIContext().getComponentSnapshot().get()
          componentSnapshot.get("root", { scale: 2, waitUntilRenderFinished: true })
            .then((pixmap: image.PixelMap) => {
              this.pixmap = pixmap
            }).catch((err: Error) => {
            console.error(`error:${err}`)
          })
        }).margin(10)
    }
    .width('100%')
    .height('100%')
    .alignItems(HorizontalAlign.Center)
  }
}

```

