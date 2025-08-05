# @ohos.arkui.componentSnapshot (组件截图)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @jiangtao92-->
<!--SE: @piggyguy-->
<!--TSE: @songyanhong-->

本模块提供获取组件截图的能力，包括已加载的组件的截图和没有加载的组件的截图。组件截图只能够截取组件大小的区域，如果组件的绘制超出了它的区域，或子组件的绘制超出了父组件的区域，这些在组件区域外绘制的内容不会在截图中呈现。兄弟节点堆叠在组件区域内，截图不会显示兄弟组件。

缩放、平移、旋转等图形变换属性只对被截图组件的子组件生效；对目标组件本身应用图形变换属性不生效，显示的是还是图形变换前的效果。

组件截图典型使用场景（如长截图）及最佳实践请参考[使用组件截图](../../ui/arkts-uicontext-component-snapshot.md)。


> **说明：**
>
> 本模块首批接口从 API version 10 开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
>对于使用[XComponent](arkui-ts/ts-basic-components-xcomponent.md)的场景，例如：Video或者相机流媒体展示类组件，不建议使用组件截图相关接口，建议从[surface](../apis-image-kit/arkts-apis-image-f.md#imagecreatepixelmapfromsurface11)直接获取图片。
>
>如果组件自身内容不能填满组件大小区域，那么剩余位置截图返回的内容为透明像素。如果组件使用了[图像效果](arkui-ts/ts-universal-attributes-image-effect.md)类属性或其他的效果类属性，则可能产生非用户预期的截图结果。请排查是否需要填充组件透明内容区域，或使用[窗口截图](arkts-apis-window-Window.md#snapshot9)替代。
>
> 示例效果请以真机运行为准，当前 DevEco Studio预览器不支持。


## 导入模块

```ts
import { componentSnapshot } from '@kit.ArkUI';
```

## componentSnapshot.get<sup>(deprecated)</sup>

get(id: string, callback: AsyncCallback<image.PixelMap>, options?: SnapshotOptions): void

获取已加载的组件的截图，传入组件的[组件标识](arkui-ts/ts-universal-attributes-component-id.md)，找到对应组件进行截图。通过回调返回结果。

> **说明：** 
>
> 从API version 18开始废弃，建议使用[UIContext](arkts-apis-uicontext-uicontext.md)中的[getComponentSnapshot](arkts-apis-uicontext-uicontext.md#getcomponentsnapshot12)获取[ComponentSnapshot](arkts-apis-uicontext-componentsnapshot.md)实例，再通过此实例调用替代方法[get](arkts-apis-uicontext-componentsnapshot.md#get12)。
>
> 从API version 12开始，可以通过使用[UIContext](arkts-apis-uicontext-uicontext.md)中的[getComponentSnapshot](arkts-apis-uicontext-uicontext.md#getcomponentsnapshot12)方法获取当前UI上下文关联的[ComponentSnapshot](arkts-apis-uicontext-componentsnapshot.md)对象。
> 
> 截图会获取最近一帧的绘制内容。如果在组件触发更新的同时调用截图，更新的渲染内容不会被截取到，截图会返回上一帧的绘制内容。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名      | 类型                                  | 必填   | 说明                                       |
| -------- | ----------------------------------- | ---- | ---------------------------------------- |
| id       | string                              | 是    | 目标组件的[组件标识](arkui-ts/ts-universal-attributes-component-id.md)。 |
| callback | [AsyncCallback](../apis-basic-services-kit/js-apis-base.md#asynccallback)&lt;image.[PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md)&gt; | 是    | 截图返回结果的回调。                               |
| options<sup>12+</sup>       | [SnapshotOptions](#snapshotoptions12)                              | 否    | 截图相关的自定义参数。 |

**错误码：** 

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息            |
| -------- | ------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 100001   | Invalid ID. |

**示例：**

> **说明：**
> 
> 直接使用componentSnapshot可能导致[UI上下文不明确](../../ui/arkts-global-interface.md#ui上下文不明确)的问题，建议使用getUIContext()获取[UIContext](arkts-apis-uicontext-uicontext.md)实例，并使用[getComponentSnapshot](arkts-apis-uicontext-uicontext.md#getcomponentsnapshot12)获取绑定实例的componentSnapshot。

```ts
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
        Image($r('app.media.img')).autoResize(true).width(200).height(200).margin(5).id("root")
      }
      Button("click to generate UI snapshot")
        .onClick(() => {
          // 建议使用this.getUIContext().getComponentSnapshot().get()
          componentSnapshot.get("root", (error: Error, pixmap: image.PixelMap) => {
            if (error) {
              console.error("error: " + JSON.stringify(error))
              return;
            }
            this.pixmap = pixmap
          }, {scale : 2, waitUntilRenderFinished : true})
        }).margin(10)
    }
    .width('100%')
    .height('100%')
    .alignItems(HorizontalAlign.Center)
  }
}
```

![componentget](figures/componentget.gif) 

## componentSnapshot.get<sup>(deprecated)</sup>

get(id: string, options?: SnapshotOptions): Promise<image.PixelMap>

获取已加载的组件的截图，传入组件的[组件标识](arkui-ts/ts-universal-attributes-component-id.md)，找到对应组件进行截图。通过Promise返回结果。

> **说明：**
>
> 从API version 18开始废弃，建议使用[UIContext](arkts-apis-uicontext-uicontext.md)中的[getComponentSnapshot](arkts-apis-uicontext-uicontext.md#getcomponentsnapshot12)获取[ComponentSnapshot](arkts-apis-uicontext-componentsnapshot.md)实例，再通过此实例调用替代方法[get](arkts-apis-uicontext-componentsnapshot.md#get12-1)。
>
> 从API version 12开始，可以通过使用[UIContext](arkts-apis-uicontext-uicontext.md)中的[getComponentSnapshot](arkts-apis-uicontext-uicontext.md#getcomponentsnapshot12)方法获取当前UI上下文关联的[ComponentSnapshot](arkts-apis-uicontext-componentsnapshot.md)对象。
> 
> 截图会获取最近一帧的绘制内容。如果在组件触发更新的同时调用截图，更新的渲染内容不会被截取到，截图会返回上一帧的绘制内容。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名  | 类型     | 必填   | 说明                                       |
| ---- | ------ | ---- | ---------------------------------------- |
| id   | string | 是    | 目标组件的[组件标识](arkui-ts/ts-universal-attributes-component-id.md)。 |
| options<sup>12+</sup>       | [SnapshotOptions](#snapshotoptions12)                              | 否    | 截图相关的自定义参数。 |

**返回值：**

| 类型                            | 说明       |
| ----------------------------- | -------- |
| Promise&lt;image.[PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md)&gt; | 截图返回的结果。 |

**错误码：** 

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息                |
| ------ | ------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 100001 | Invalid ID. |

**示例：**

> **说明：**
> 
> 直接使用componentSnapshot可能导致[UI上下文不明确](../../ui/arkts-global-interface.md#ui上下文不明确)的问题，建议使用getUIContext()获取[UIContext](arkts-apis-uicontext-uicontext.md)实例，并使用[getComponentSnapshot](arkts-apis-uicontext-uicontext.md#getcomponentsnapshot12)获取绑定实例的componentSnapshot。

```ts
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
        Image($r('app.media.img')).autoResize(true).width(200).height(200).margin(5).id("root")
      }
      Button("click to generate UI snapshot")
        .onClick(() => {
          // 建议使用this.getUIContext().getComponentSnapshot().get()
          componentSnapshot.get("root", {scale : 2, waitUntilRenderFinished : true})
            .then((pixmap: image.PixelMap) => {
              this.pixmap = pixmap
            }).catch((err:Error) => {
            console.error("error: " + err)
          })
        }).margin(10)
    }
    .width('100%')
    .height('100%')
    .alignItems(HorizontalAlign.Center)
  }
}
```

![componentget](figures/componentget.gif) 

## componentSnapshot.createFromBuilder<sup>(deprecated)</sup>

createFromBuilder(builder: CustomBuilder, callback: AsyncCallback<image.PixelMap>, delay?: number, checkImageStatus?: boolean, options?: SnapshotOptions): void

在应用后台渲染CustomBuilder自定义组件，并输出其截图。通过回调返回结果并支持在回调中获取离屏组件绘制区域坐标和大小。

> **说明：** 
>
> 从API version 18开始废弃，建议使用[UIContext](arkts-apis-uicontext-uicontext.md)中的[getComponentSnapshot](arkts-apis-uicontext-uicontext.md#getcomponentsnapshot12)获取[ComponentSnapshot](arkts-apis-uicontext-componentsnapshot.md)实例，再通过此实例调用替代方法[createFromBuilder](arkts-apis-uicontext-componentsnapshot.md#createfrombuilder12)。
>
> 从API version 12开始，可以通过使用[UIContext](arkts-apis-uicontext-uicontext.md)中的[getComponentSnapshot](arkts-apis-uicontext-uicontext.md#getcomponentsnapshot12)方法获取当前UI上下文关联的[ComponentSnapshot](arkts-apis-uicontext-componentsnapshot.md)对象。
>
> 由于需要等待组件构建、渲染成功，离屏截图的回调有500ms以内的延迟。
>
> builder中的组件不支持设置动画相关的属性，如[transition](arkui-ts/ts-transition-animation-component.md)。
>
> 部分执行耗时任务的组件可能无法及时在截图前加载完成，因此会截取不到加载成功后的图像。例如：加载网络图片的[Image](arkui-ts/ts-basic-components-image.md)组件、[Web](../apis-arkweb/arkts-basic-components-web.md)组件。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名      | 类型                                       | 必填   | 说明         |
| -------- | ---------------------------------------- | ---- | ---------- |
| builder  | [CustomBuilder](arkui-ts/ts-types.md#custombuilder8) | 是    | 自定义组件构建函数。<br/>**说明：** 不支持全局builder。<br/>builder的根组件宽高为0时，截图操作会失败并抛出100001错误码。|
| callback | [AsyncCallback](../apis-basic-services-kit/js-apis-base.md#asynccallback)&lt;image.[PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md)&gt;      | 是    | 截图返回结果的回调。支持在回调中获取离屏组件绘制区域坐标和大小。 |
| delay<sup>12+</sup>   | number | 否    | 指定触发截图指令的延迟时间。当布局中使用了图片组件时，需要指定延迟时间，以便系统解码图片资源。资源越大，解码需要的时间越长，建议尽量使用不需要解码的PixelMap资源。<br/> 当使用PixelMap资源或对Image组件设置syncload为true时，可以配置delay为0，强制不等待触发截图。该延迟时间并非指接口从调用到返回的时间，由于系统需要对传入的builder进行临时离屏构建，因此返回的时间通常要比该延迟时间长。<br/>**说明：** 截图接口传入的builder中，不应使用状态变量控制子组件的构建，如果必须要使用，在调用截图接口时，也不应再有变化，以避免出现截图不符合预期的情况。<br/> 默认值：300 <br/> 单位：毫秒 <br/> 取值范围：[0, +∞)，小于0时按默认值处理。 |
| checkImageStatus<sup>12+</sup>  | boolean | 否    | 指定是否允许在截图之前，校验图片解码状态。如果为true，则会在截图之前检查所有Image组件是否已经解码完成。为false，则不会校验图片解码状态。如果没有完成检查，则会放弃截图并返回异常。<br/>默认值：false|
| options<sup>12+</sup>       | [SnapshotOptions](#snapshotoptions12)           | 否    | 截图相关的自定义参数。 |

**错误码：** 

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed. |
| 100001   | The builder is not a valid build function.                   |
| 160001   | An image component in builder is not ready for taking a snapshot. The check for the ready state is required when the checkImageStatus option is enabled. |

**示例：**

> **说明：**
> 
> 直接使用componentSnapshot可能导致[UI上下文不明确](../../ui/arkts-global-interface.md#ui上下文不明确)的问题，建议使用getUIContext()获取[UIContext](arkts-apis-uicontext-uicontext.md)实例，并使用[getComponentSnapshot](arkts-apis-uicontext-uicontext.md#getcomponentsnapshot12)获取绑定实例的componentSnapshot。

```ts
import { componentSnapshot } from '@kit.ArkUI';
import { image } from '@kit.ImageKit';

@Entry
@Component
struct OffscreenSnapshotExample {
  @State pixmap: image.PixelMap | undefined = undefined

  @Builder
  RandomBuilder() {
    Flex({ direction: FlexDirection.Column, justifyContent: FlexAlign.Center, alignItems: ItemAlign.Center }) {
      Text('Test menu item 1')
        .fontSize(20)
        .width(100)
        .height(50)
        .textAlign(TextAlign.Center)
      Divider().height(10)
      Text('Test menu item 2')
        .fontSize(20)
        .width(100)
        .height(50)
        .textAlign(TextAlign.Center)
    }
    .width(100)
    .id("builder")
  }

  build() {
    Column() {
      Button("click to generate offscreen UI snapshot")
        .onClick(() => {
          // 建议使用this.getUIContext().getComponentSnapshot().createFromBuilder()
          componentSnapshot.createFromBuilder(()=>{this.RandomBuilder()},
            (error: Error, pixmap: image.PixelMap) => {
              if(error){
                console.error("error: " + JSON.stringify(error))
                return;
              }
              this.pixmap = pixmap
              // 保存pixmap到文件中
              // ....
              // 获取组件大小和位置
              let info = this.getUIContext().getComponentUtils().getRectangleById("builder")
              console.info(info.size.width + ' ' + info.size.height + ' ' + info.localOffset.x + ' ' + info.localOffset.y + ' ' + info.windowOffset.x + ' ' + info.windowOffset.y)
            }, 320, true, {scale : 2, waitUntilRenderFinished : true})
        })
      Image(this.pixmap)
        .margin(10)
        .height(200)
        .width(200)
        .border({ color: Color.Black, width: 2 })
    }.width('100%').margin({ left: 10, top: 5, bottom: 5 }).height(300)
  }
}
```

![componentcreate](figures/componentcreate.gif) 

## componentSnapshot.createFromBuilder<sup>(deprecated)</sup>

createFromBuilder(builder: CustomBuilder, delay?: number, checkImageStatus?: boolean, options?: SnapshotOptions): Promise<image.PixelMap>

在应用后台渲染CustomBuilder自定义组件，并输出其截图。通过Promise返回结果并支持获取离屏组件绘制区域坐标和大小。

> **说明：** 
>
> 从API version 18开始废弃，建议使用[UIContext](arkts-apis-uicontext-uicontext.md)中的[getComponentSnapshot](arkts-apis-uicontext-uicontext.md#getcomponentsnapshot12)获取[ComponentSnapshot](arkts-apis-uicontext-componentsnapshot.md)实例，再通过此实例调用替代方法[createFromBuilder](arkts-apis-uicontext-componentsnapshot.md#createfrombuilder12-1)。
>
> 从API version 12开始，可以通过使用[UIContext](arkts-apis-uicontext-uicontext.md)中的[getComponentSnapshot](arkts-apis-uicontext-uicontext.md#getcomponentsnapshot12)方法获取当前UI上下文关联的[ComponentSnapshot](arkts-apis-uicontext-componentsnapshot.md)对象。
> 
> 由于需要等待组件构建、渲染成功，离屏截图的回调有500ms以内的延迟。
>
> builder中的组件不支持设置动画相关的属性，如[transition](arkui-ts/ts-transition-animation-component.md)。
>
> 部分执行耗时任务的组件可能无法及时在截图前加载完成，因此会截取不到加载成功后的图像。例如：加载网络图片的[Image](arkui-ts/ts-basic-components-image.md)组件、[Web](../apis-arkweb/arkts-basic-components-web.md)组件。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名     | 类型                                       | 必填   | 说明         |
| ------- | ---------------------------------------- | ---- | ---------- |
| builder | [CustomBuilder](arkui-ts/ts-types.md#custombuilder8) | 是    | 自定义组件构建函数。<br/>**说明：** 不支持全局builder。<br/>builder的根组件宽高为0时，截图操作会失败并抛出100001错误码。 |
| delay<sup>12+</sup>   | number | 否    | 指定触发截图指令的延迟时间。当布局中使用了图片组件时，需要指定延迟时间，以便系统解码图片资源。资源越大，解码需要的时间越长，建议尽量使用不需要解码的PixelMap资源。<br/> 当使用PixelMap资源或对Image组件设置syncload为true时，可以配置delay为0，强制不等待触发截图。该延迟时间并非指接口从调用到返回的时间，由于系统需要对传入的builder进行临时离屏构建，因此返回的时间通常要比该延迟时间长。<br/>**说明：** 截图接口传入的builder中，不应使用状态变量控制子组件的构建，如果必须要使用，在调用截图接口时，也不应再有变化，以避免出现截图不符合预期的情况。<br/> 默认值：300 <br/> 单位：毫秒|
| checkImageStatus<sup>12+</sup>  | boolean | 否    | 指定是否允许在截图之前，校验图片解码状态。如果为true，则会在截图之前检查所有Image组件是否已经解码完成。为false，则不会校验图片解码状态。如果没有完成检查，则会放弃截图并返回异常。<br/>默认值：false|
| options<sup>12+</sup>       | [SnapshotOptions](#snapshotoptions12)           | 否    | 截图相关的自定义参数。 |

**返回值：**

| 类型                            | 说明       |
| ----------------------------- | -------- |
| Promise&lt;image.[PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md)&gt; | 截图返回的结果。 |

**错误码：** 
以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息                                     |
| ------ | ---------------------------------------- |
| 401     | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 100001 | The builder is not a valid build function. |
| 160001 | An image component in builder is not ready for taking a snapshot. The check for the ready state is required when the checkImageStatus option is enabled. |

**示例：**

> **说明：**
> 
> 直接使用componentSnapshot可能导致[UI上下文不明确](../../ui/arkts-global-interface.md#ui上下文不明确)的问题，建议使用getUIContext()获取[UIContext](arkts-apis-uicontext-uicontext.md)实例，并使用[getComponentSnapshot](arkts-apis-uicontext-uicontext.md#getcomponentsnapshot12)获取绑定实例的componentSnapshot。

```ts
import { componentSnapshot } from '@kit.ArkUI'
import { image } from '@kit.ImageKit'

@Entry
@Component
struct OffscreenSnapshotExample {
  @State pixmap: image.PixelMap | undefined = undefined

  @Builder
  RandomBuilder() {
    Flex({ direction: FlexDirection.Column, justifyContent: FlexAlign.Center, alignItems: ItemAlign.Center }) {
      Text('Test menu item 1')
        .fontSize(20)
        .width(100)
        .height(50)
        .textAlign(TextAlign.Center)
      Divider().height(10)
      Text('Test menu item 2')
        .fontSize(20)
        .width(100)
        .height(50)
        .textAlign(TextAlign.Center)
    }
    .width(100)
    .id("builder")
  }

  build() {
    Column() {
      Button("click to generate offscreen UI snapshot")
        .onClick(() => {
          // 建议使用this.getUIContext().getComponentSnapshot().createFromBuilder()
          componentSnapshot.createFromBuilder(()=>{this.RandomBuilder()}, 320, true, {scale : 2, waitUntilRenderFinished : true})
            .then((pixmap: image.PixelMap) => {
              this.pixmap = pixmap
              // 保存pixmap到文件中
              // ....
              // 获取组件大小和位置
              let info = this.getUIContext().getComponentUtils().getRectangleById("builder")
              console.info(info.size.width + ' ' + info.size.height + ' ' + info.localOffset.x + ' ' + info.localOffset.y + ' ' + info.windowOffset.x + ' ' + info.windowOffset.y)
            }).catch((err:Error) => {
            console.error("error: " + err)
          })
        })
      Image(this.pixmap)
        .margin(10)
        .height(200)
        .width(200)
        .border({ color: Color.Black, width: 2 })
    }.width('100%').margin({ left: 10, top: 5, bottom: 5 }).height(300)
  }
}
```

![componentcreate](figures/componentcreate.gif) 

## componentSnapshot.getSync<sup>12+</sup>

getSync(id: string, options?: SnapshotOptions): image.PixelMap

获取已加载的组件的截图，传入组件的[组件标识](arkui-ts/ts-universal-attributes-component-id.md)，找到对应组件进行截图。同步等待截图完成返回[PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md)。

> **说明：**
>
> 截图会获取最近一帧的绘制内容。如果在组件触发更新的同时调用截图，更新的渲染内容不会被截取到，截图会返回上一帧的绘制内容。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名  | 类型     | 必填   | 说明                                       |
| ---- | ------ | ---- | ---------------------------------------- |
| id   | string | 是    | 目标组件的[组件标识](arkui-ts/ts-universal-attributes-component-id.md)。 |
| options       | [SnapshotOptions](#snapshotoptions12)                              | 否    | 截图相关的自定义参数。 |

**返回值：**

| 类型                            | 说明       |
| ----------------------------- | -------- |
| image.[PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md) | 截图返回的结果。 |

**错误码：** 

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息                |
| ------ | ------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 100001 | Invalid ID. |
| 160002 | Timeout. |

**示例：**

> **说明：**
> 
> 直接使用componentSnapshot可能导致[UI上下文不明确](../../ui/arkts-global-interface.md#ui上下文不明确)的问题，建议使用getUIContext()获取[UIContext](arkts-apis-uicontext-uicontext.md)实例，并使用[getComponentSnapshot](arkts-apis-uicontext-uicontext.md#getcomponentsnapshot12)获取绑定实例的componentSnapshot。

```ts
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
        Image($r('app.media.img')).autoResize(true).width(200).height(200).margin(5).id("root")
      }
      Button("click to generate UI snapshot")
        .onClick(() => {
          try {
          // 建议使用this.getUIContext().getComponentSnapshot().getSync()
            let pixelmap = componentSnapshot.getSync("root", {scale : 2, waitUntilRenderFinished : true})
            this.pixmap = pixelmap
          } catch (error) {
            console.error("getSync errorCode: " + error.code + " message: " + error.message)
          }
        }).margin(10)
    }
    .width('100%')
    .height('100%')
    .alignItems(HorizontalAlign.Center)
  }
}
```

![componentget](figures/componentget.gif) 

## SnapshotOptions<sup>12+</sup>

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称           | 类型             | 必填           | 说明                         |
| ---------------|------------     | -----------------------------| -----------------------------|
| scale           | number | 否 | 指定截图时图形侧绘制pixelmap的缩放比例，比例过大时截图时间会变长，或者截图可能会失败。<br/>取值范围：[0, +∞)，当小于等于0时按默认情况处理。 <br/> 默认值：1 <br/>**说明：** <br/>请不要截取过大尺寸的图片，截图不建议超过屏幕尺寸的大小。当要截取的图片目标长宽超过底层限制时，截图会返回失败，不同设备的底层限制不同。<br/>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。    |
| waitUntilRenderFinished    | boolean | 否 | 设置是否强制系统在截图前等待所有绘制指令执行完毕。true表示强制系统在截图前等待所有绘制指令执行完毕，false表示不强制系统在截图前等待所有绘制指令执行完毕。该选项可尽可能确保截图内容是最新的状态，应尽量开启。需要注意的是，开启后接口可能需要更长的时间返回，具体的时间依赖页面当时时刻需要重绘区域的大小。<br>默认值：false <br/>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。         |
| region<sup>15+</sup> | [SnapshotRegionType](#snapshotregiontype15) | 否 | 指定截图的矩形区域范围，默认为整个组件。<br/>**原子化服务API：** 从API version 15开始，该接口支持在原子化服务中使用。 |

## SnapshotRegionType<sup>15+</sup>

type SnapshotRegionType =  SnapshotRegion | LocalizedSnapshotRegion

表示组件截图区域，取值类型为下表中的任一类型。

**原子化服务API：** 从API version 15开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 类型   | 说明   |
| ------ | ------ |
| [SnapshotRegion](#snapshotregion15) | 表示组件截图的矩形区域。 |
| [LocalizedSnapshotRegion ](#localizedsnapshotregion15) | 表示组件截图的矩形区域，根据布局方向确定是否对矩形区域水平翻转，若布局方向为RTL，则把指定的截图区域做左右翻转处理以适应RTL布局方向。 |

## SnapshotRegion<sup>15+</sup>

定义组件截图的矩形区域。

**原子化服务API：** 从API version 15开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称   | 类型   | 必填 | 说明                                    |
| ------ | ------ | ---- | --------------------------------------- |
| left   | number | 是   | 截图区域矩形左上角的x轴坐标。<br>单位：px <br>取值范围：[0, 组件宽度] |
| top    | number | 是   | 截图区域矩形左上角的y轴坐标。<br>单位：px <br>取值范围：[0, 组件高度] |
| right  | number | 是   | 截图区域矩形右下角的x轴坐标。<br>单位：px <br>取值范围：[0, 组件宽度] |
| bottom | number | 是   | 截图区域矩形右下角的y轴坐标。<br>单位：px <br>取值范围：[0, 组件高度] |

## LocalizedSnapshotRegion<sup>15+</sup>

定义组件截图的矩形区域，start和end的值在布局方向为LTR时指定为left和right，在布局方向为RTL时指定为right和left。

**原子化服务API：** 从API version 15开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称   | 类型   | 必填 | 说明                                                         |
| ------ | ------ | ---- | ------------------------------------------------------------ |
| start  | number | 是   | 布局方向为LTR时表示截图区域矩形左上角的x轴坐标，布局方向为RTL时表示截图区域矩形右下角的x轴坐标。<br>单位：px <br>取值范围：[0, 组件宽度] |
| top    | number | 是   | 布局方向为LTR时表示截图区域矩形左上角的y轴坐标，布局方向为RTL时表示截图区域矩形右下角的y轴坐标。<br>单位：px <br>取值范围：[0, 组件高度] |
| end    | number | 是   | 布局方向为LTR时表示截图区域矩形右上角的x轴坐标，布局方向为RTL时表示截图区域矩形左下角的x轴坐标。<br>单位：px <br>取值范围：[0, 组件宽度] |
| bottom | number | 是   | 布局方向为LTR时表示截图区域矩形右上角的y轴坐标，布局方向为RTL时表示截图区域矩形左下角的y轴坐标。<br>单位：px <br>取值范围：[0, 组件高度] |

**示例：**

> **说明：**
> 
> 直接使用componentSnapshot可能导致[UI上下文不明确](../../ui/arkts-global-interface.md#ui上下文不明确)的问题，建议使用getUIContext()获取[UIContext](arkts-apis-uicontext-uicontext.md)实例，并使用[getComponentSnapshot](arkts-apis-uicontext-uicontext.md#getcomponentsnapshot12)获取绑定实例的componentSnapshot。

```ts
import { image } from '@kit.ImageKit';
@Entry
@Component
struct SnapshotExample {
  @State pixmap: image.PixelMap | undefined = undefined
  build() {
    Column() {
      Row() {
        Column(){
          TextClock()
          Button("Button ABCDE").type(ButtonType.Normal)
          Row() {
            Checkbox()
            Text("√")
            Text(" | ")
            Checkbox()
            Text("×")
          }.align(Alignment.Start)
          TextInput()
        }
        .align(Alignment.Start)
        .id("component1")
        .width("600px")
        .height("600px")
        .borderRadius(6)
        .borderWidth(2)
        .borderColor(Color.Green)

      }
      Button("get capture")
      .onClick(() => {
          try {
            let pixelmap = this.getUIContext().getComponentSnapshot().getSync("component1",
              {scale : 2, waitUntilRenderFinished : true,region: {start:20,top:20, end:200,bottom:240}})
            this.pixmap = pixelmap
          } catch (error) {
            console.error("getSync errorCode: " + error.code + " message: " + error.message)
          }
        }).margin(10)
      Image(this.pixmap).border({ color: Color.Black, width: 2 }).width("600px")
    }.width("100%").align(Alignment.Center)
  }
}