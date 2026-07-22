# get

## 导入模块

```TypeScript
import { componentSnapshot } from '@kit.ArkUI';
```

## get

```TypeScript
function get(id: string, callback: AsyncCallback<image.PixelMap>, options?: SnapshotOptions): void
```

获取已加载的组件的截图，传入组件的[组件标识](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)，找到对应组件进行截图。通过回调返回结果。
> **说明：**  
>  
> - 从API version 12开始，可以通过使用[UIContext](arkts-arkui-uicontext.md)中的  
> [getComponentSnapshot](arkts-arkui-arkui-uicontext-uicontext-c.md#getcomponentsnapshot)方法  
> 获取当前UI上下文关联的[ComponentSnapshot](arkts-arkui-arkui-uicontext-componentsnapshot-c.md)对象。  
>  
> - 截图会获取最近一帧的绘制内容。如果在组件触发更新的同时调用截图，更新的渲染内容不会被截取到，截图会返回上一帧的绘制内容。

**起始版本：** 10

**废弃版本：** 18

**替代接口：** get

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-componentSnapshot-function get(id: string, callback: AsyncCallback<image.PixelMap>, options?: SnapshotOptions): void--><!--Device-componentSnapshot-function get(id: string, callback: AsyncCallback<image.PixelMap>, options?: SnapshotOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | 目标组件的[组件标识](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;image.PixelMap&gt; | 是 | 截图返回结果的回调。 |
| options | [SnapshotOptions](arkts-arkui-componentsnapshot-snapshotoptions-i.md) | 否 | 截图相关的自定义参数。<br>**起始版本：** 12 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameters types.<br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | Invalid ID. |

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

获取已加载的组件的截图，传入组件的[组件标识](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)，找到对应组件进行截图。通过Promise返回结果。
> **说明：**  
>  
> - 从API version 12开始，可以通过使用[UIContext](arkts-arkui-uicontext.md)中的  
> [getComponentSnapshot](arkts-arkui-arkui-uicontext-uicontext-c.md#getcomponentsnapshot)方法  
> 获取当前UI上下文关联的[ComponentSnapshot](arkts-arkui-arkui-uicontext-componentsnapshot-c.md)对象。  
>  
> - 截图会获取最近一帧的绘制内容。如果在组件触发更新的同时调用截图，更新的渲染内容不会被截取到，截图会返回上一帧的绘制内容。

**起始版本：** 10

**废弃版本：** 18

**替代接口：** get

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-componentSnapshot-function get(id: string, options?: SnapshotOptions): Promise<image.PixelMap>--><!--Device-componentSnapshot-function get(id: string, options?: SnapshotOptions): Promise<image.PixelMap>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | 目标组件的[组件标识](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)。 |
| options | [SnapshotOptions](arkts-arkui-componentsnapshot-snapshotoptions-i.md) | 否 | 截图相关的自定义参数。<br>**起始版本：** 12 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;image.PixelMap&gt; | 截图返回的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameters types.<br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | Invalid ID. |

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

