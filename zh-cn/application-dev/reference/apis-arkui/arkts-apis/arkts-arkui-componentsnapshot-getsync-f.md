# getSync

## 导入模块

```TypeScript
import { componentSnapshot } from '@kit.ArkUI';
```

<a id="getsync"></a>
## getSync

```TypeScript
function getSync(id: string, options?: SnapshotOptions): image.PixelMap
```

获取已加载的组件的截图，传入组件的[组件标识](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)，找到对应组件进行截图。同步等待截图完成返回[PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)。

> **说明：**  
>  
> 截图会获取最近一帧的绘制内容。如果在组件触发更新的同时调用截图，更新的渲染内容不会被截取到，截图会返回上一帧的绘制内容。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-componentSnapshot-function getSync(id: string, options?: SnapshotOptions): image.PixelMap--><!--Device-componentSnapshot-function getSync(id: string, options?: SnapshotOptions): image.PixelMap-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | 目标组件的[组件标识](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)。 |
| options | [SnapshotOptions](arkts-arkui-componentsnapshot-snapshotoptions-i.md) | 否 | 截图相关的自定义参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| image.PixelMap | 截图返回的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameters types.<br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | Invalid ID. |
| [160002](../errorcode-snapshot.md#160002-截图超时) | Timeout. |
| [160003](../errorcode-snapshot.md#160003-截图选项不支持的色彩空间或动态范围模式) | Unsupported color space or dynamic range mode in snapshot options.<br>**适用版本：** 23+ |

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
          .id('root')
      }

      Button('click to generate UI snapshot')
        .onClick(() => {
          try {
            // 建议使用this.getUIContext().getComponentSnapshot().getSync()
            let pixelmap = componentSnapshot.getSync('root', { scale: 2, waitUntilRenderFinished: true });
            this.pixmap = pixelmap;
          } catch (error) {
            console.error(`getSync error message:${error.message}`);
          }
        }).margin(10)
    }
    .width('100%')
    .height('100%')
    .alignItems(HorizontalAlign.Center)
  }
}

```

