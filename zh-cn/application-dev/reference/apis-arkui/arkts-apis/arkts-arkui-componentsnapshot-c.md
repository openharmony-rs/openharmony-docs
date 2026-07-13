# ComponentSnapshot

提供获取组件截图的能力，包括已加载的组件的截图和没有加载的组件的截图。

> **说明：**
>
> - 本Class首批接口从API version 12开始支持。
>
> - 以下API需先使用UIContext中的[getComponentSnapshot()](arkts-arkui-uicontext-c.md#getcomponentsnapshot-1)方法获取ComponentSnapshot对象，再通过此实例调用对应方法。
>
> - 缩放、平移、旋转等图形变换属性只对被截图组件的子组件生效；对目标组件本身应用图形变换属性不生效，显示的还是图形变换前的效果。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## createFromBuilder

```TypeScript
createFromBuilder(builder: CustomBuilder, callback: AsyncCallback<image.PixelMap>,
    delay?: number, checkImageStatus?: boolean, options?: componentSnapshot.SnapshotOptions): void
```

传入[CustomBuilder](../arkts-components/arkts-arkui-custombuilder-t.md)自定义组件，系统对其进行离屏构建后进行截图。使用callback异步回调。

> **说明：**
>
> - 由于需要等待组件构建、渲染成功，离屏截图的回调有500ms以内的延迟，不适宜使用在对性能敏感的场景。
>
> - 部分执行耗时任务的组件可能无法及时在截图前加载完成，因此会截取不到加载成功后的图像。例如：加载网络图片的[Image](../../apis-image-kit/arkts-apis/arkts-multimedia-image.md)组件、[Web](../../apis-arkweb/arkts-components/arkts-arkweb-web.md)组件。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| builder | CustomBuilder | 是 | 自定义组件构建函数。<br/>**说明：** 不支持全局builder。<br/>builder的根组件宽高为0时，截图操作会失败并抛出100001错误码。 |
| callback | AsyncCallback&lt;image.PixelMap&gt; | 是 | 回调函数。当截图返回结果成功，err为undefined，data为获取到的image.[PixelMap](../../apis-image-kit/arkts-apis/arkts-image-pixelmap-i.md)；否则为错误对象。支持在回调中获取离屏组件绘制区域坐标和大小。 |
| delay | number | 否 | 指定触发截图指令的延迟时间。当布局中使用了图片组件时，需要指定延迟时间，以便系统解码图片资源。资源越大，解码需要的时间越长，建议尽量使用不需要解码的PixelMap资源。<br/>当使用PixelMap资源或对Image组件设置[syncLoad](ImageAttribute#syncLoad)为true时，可以配置delay为0，强制不等待触发截图。该延迟时间并非指接口从调用到返回的时间，由于系统需要对传入的builder进行临时离屏构建，因此返回的时间通常要比该延迟时间长。<br/>**说明：** 截图接口传入的builder中，不应使用状态变量控制子组件的构建，如果必须要使用，在调用截图接口时，也不应再有变化，以避免出现截图不符合预期的情况。<br/> 默认值：300 <br/> 单位：毫秒 <br/> 取值范围：[0, +∞)，小于0时按默认值处理。 |
| checkImageStatus | boolean | 否 | 指定是否允许在截图之前，校验图片解码状态。如果为true，则会在截图之前检查所有Image组件是否已经解码完成，如果没有完成检查，则会放弃截图并返回异常。<br/>默认值：false |
| options | componentSnapshot.SnapshotOptions | 否 | 截图相关的自定义参数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameters types.<br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | The builder is not a valid build function. |
| [160001](../errorcode-snapshot.md#160001-图像加载错误) | An image component in builder is not ready for taking a snapshot. The check forthe ready state is required when the checkImageStatus option is enabled. |
| [160003](../errorcode-snapshot.md#160003-截图选项不支持的色彩空间或动态范围模式) | Unsupported color space or dynamic range mode in snapshot options.<br>**适用版本：** 23+ |
| [160004](../errorcode-snapshot.md#160004-离屏节点截图不支持色彩空间或动态范围模式的isauto参数设置为true) | isAuto(true) is not supported for offscreen node snapshots.<br>**适用版本：** 23+ |

## createFromBuilder

```TypeScript
createFromBuilder(builder: CustomBuilder, delay?: number,
    checkImageStatus?: boolean, options?: componentSnapshot.SnapshotOptions): Promise<image.PixelMap>
```

传入[CustomBuilder](../arkts-components/arkts-arkui-custombuilder-t.md)自定义组件，系统对其进行离屏构建后进行截图。使用Promise异步回调。

> **说明：**
>
> - 由于需要等待组件构建、渲染成功，离屏截图的回调有500ms以内的延迟，不适宜使用在对性能敏感的场景。
>
> - 部分执行耗时任务的组件可能无法及时在截图前加载完成，因此会截取不到加载成功后的图像。例如：加载网络图片的[Image](../../apis-image-kit/arkts-apis/arkts-multimedia-image.md)组件、[Web](../../apis-arkweb/arkts-components/arkts-arkweb-web.md)组件。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| builder | CustomBuilder | 是 | 自定义组件构建函数。<br/>**说明：** 不支持全局builder。<br/>builder的根组件宽高为0时，截图操作会失败并抛出100001错误码。 |
| delay | number | 否 | 指定触发截图指令的延迟时间。当布局中使用了图片组件时，需要指定延迟时间，以便系统解码图片资源。资源越大，解码需要的时间越长，建议尽量使用不需要解码的PixelMap资源。&lt;br/&gt; 当使用PixelMap资源或对Image组件设置[syncLoad](ImageAttribute#syncLoad)为true时，可以配置delay为0，强制不等待触发截图。该延迟时间并非指接口从调用到返回的时间，由于系统需要对传入的builder进行临时离屏构建，因此返回的时间通常要比该延迟时间长。<br/>**说明：** 截图接口传入的builder中，不应使用状态变量控制子组件的构建，如果必须要使用，在调用截图接口时，也不应再有变化，以避免出现截图不符合预期的情况。<br/> 默认值：300 <br/> 单位：毫秒<br/> 取值范围：[0, +∞)，小于0时按默认值处理。 |
| checkImageStatus | boolean | 否 | 指定是否允许在截图之前，校验图片解码状态。如果为true，则会在截图之前检查所有Image组件是否已经解码完成，如果没有完成检查，则会放弃截图并返回异常。<br/>默认值：false |
| options | componentSnapshot.SnapshotOptions | 否 | 截图相关的自定义参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;image.PixelMap&gt; | Promise used to return the snapshot object. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameters types.<br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | The builder is not a valid build function. |
| [160001](../errorcode-snapshot.md#160001-图像加载错误) | An image component in builder is not ready for taking a snapshot. The check forthe ready state is required when the checkImageStatus option is enabled. |
| [160003](../errorcode-snapshot.md#160003-截图选项不支持的色彩空间或动态范围模式) | Unsupported color space or dynamic range mode in snapshot options.<br>**适用版本：** 23+ |
| [160004](../errorcode-snapshot.md#160004-离屏节点截图不支持色彩空间或动态范围模式的isauto参数设置为true) | isAuto(true) is not supported for offscreen node snapshots.<br>**适用版本：** 23+ |

## createFromComponent

```TypeScript
createFromComponent<T extends Object>(content: ComponentContent<T>, delay?: number,
    checkImageStatus?: boolean, options?: componentSnapshot.SnapshotOptions): Promise<image.PixelMap>
```

将传入的content对象进行截图。使用Promise异步回调。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | ComponentContent&lt;T&gt; | 是 | 当前UIContext显示的组件内容。 |
| delay | number | 否 | 指定触发截图指令的延迟时间。当布局中使用了图片组件时，需要指定延迟时间，以便系统解码图片资源。资源越大，解码需要的时间越长，建议尽量使用不需要解码的PixelMap资源。&lt;br/&gt; 当使用PixelMap资源或对Image组件设置[syncLoad](ImageAttribute#syncLoad)为true时，可以配置delay为0，强制不等待触发截图。该延迟时间并非指接口从调用到返回的时间，由于系统需要对传入的builder进行临时离屏构建，因此返回的时间通常要比该延迟时间长。<br/>**说明：** 截图接口传入的builder中，不应使用状态变量控制子组件的构建，如果必须要使用，在调用截图接口时，也不应再有变化，以避免出现截图不符合预期的情况。<br/> 取值范围：[0,+∞) ，小于0时按默认值处理。<br/>默认值：300 <br/> 单位：毫秒 |
| checkImageStatus | boolean | 否 | 指定是否允许在截图之前，校验图片解码状态。如果为true，则会在截图之前检查所有Image组件是否已经解码完成，如果没有完成检查，则会放弃截图并返回异常。<br/>默认值：false |
| options | componentSnapshot.SnapshotOptions | 否 | 截图相关的自定义参数。可以指定截图时图形侧绘制pixelmap的缩放比例与是否强制等待系统执行截图指令前所有绘制指令都执行完成之后再截图。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;image.PixelMap&gt; | Promise used to return the snapshot object. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameters types.<br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | The builder is not a valid build function. |
| [160001](../errorcode-snapshot.md#160001-图像加载错误) | An image component in builder is not ready for taking a snapshot. The check forthe ready state is required when the checkImageStatus option is enabled. |
| [160003](../errorcode-snapshot.md#160003-截图选项不支持的色彩空间或动态范围模式) | Unsupported color space or dynamic range mode in snapshot options.<br>**适用版本：** 23+ |
| [160004](../errorcode-snapshot.md#160004-离屏节点截图不支持色彩空间或动态范围模式的isauto参数设置为true) | isAuto(true) is not supported for offscreen node snapshots.<br>**适用版本：** 23+ |

## get

```TypeScript
get(id: string, callback: AsyncCallback<image.PixelMap>, options?: componentSnapshot.SnapshotOptions): void
```

获取已加载的组件的截图，传入组件的[组件标识](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)，找到对应组件进行截图。使用callback异步回调。

> **说明：**
>
> 截图会获取最近一帧的绘制内容。如果在组件触发更新的同时调用截图，更新的渲染内容不会被截取到，截图会返回上一帧的绘制内容。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | 目标组件的[组件标识](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)。<br/>**说明：** 不支持未挂树组件，当传入的组件标识是离屏或缓存未挂树的节点时，系统不会对其进行截图。 |
| callback | AsyncCallback&lt;image.PixelMap&gt; | 是 | 回调函数。当截图返回结果成功，err为undefined，data为获取到的image.[PixelMap](../../apis-image-kit/arkts-apis/arkts-image-pixelmap-i.md)；否则为错误对象。 |
| options | componentSnapshot.SnapshotOptions | 否 | 截图相关的自定义参数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameters types.<br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | Invalid ID. |
| [160003](../errorcode-snapshot.md#160003-截图选项不支持的色彩空间或动态范围模式) | Unsupported color space or dynamic range mode in snapshot options.<br>**适用版本：** 23+ |

## get

```TypeScript
get(id: string, options?: componentSnapshot.SnapshotOptions): Promise<image.PixelMap>
```

获取已加载的组件的截图，传入组件的[组件标识](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)，找到对应组件进行截图。使用Promise异步回调。

> **说明：**
>
> 截图会获取最近一帧的绘制内容。如果在组件触发更新的同时调用截图，更新的渲染内容不会被截取到，截图会返回上一帧的绘制内容。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | 目标组件的[组件标识](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)。<br/>**说明：** 不支持未挂树组件，当传入的组件标识是离屏或缓存未挂树的节点时，系统不会对其进行截图。 |
| options | componentSnapshot.SnapshotOptions | 否 | 截图相关的自定义参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;image.PixelMap&gt; | Promise used to return the snapshot object. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameters types.<br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | Invalid ID. |
| [160003](../errorcode-snapshot.md#160003-截图选项不支持的色彩空间或动态范围模式) | Unsupported color space or dynamic range mode in snapshot options.<br>**适用版本：** 23+ |

## getSizeLimitation

```TypeScript
getSizeLimitation(): componentSnapshot.SnapshotSizeLimitation
```

查询组件截图的最大尺寸限制。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| componentSnapshot.SnapshotSizeLimitation | Size limit of a component screenshot. |

## getSync

```TypeScript
getSync(id: string, options?: componentSnapshot.SnapshotOptions): image.PixelMap
```

获取已加载的组件的截图。传入组件的[组件标识](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)，找到对应组件进行截图，同步等待截图完成返回[PixelMap](../../apis-image-kit/arkts-apis/arkts-image-pixelmap-i.md)。
本方法会阻塞主线程，请谨慎使用。接口的最大等待时间为3s，如果3s后未返回将会抛出异常。

> **说明：**
>
> 截图会获取最近一帧的绘制内容。如果在组件触发更新的同时调用截图，更新的渲染内容不会被截取到，截图会返回上一帧的绘制内容。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | 目标组件的[组件标识](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)。 <br/>**说明：** 不支持未挂树组件，当传入的组件标识是离屏或缓存未挂树的节点时，系统不会对其进行截图。 |
| options | componentSnapshot.SnapshotOptions | 否 | 截图相关的自定义参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| image.PixelMap | Promise used to return the result. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameters types.<br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | Invalid ID. |
| [160002](../errorcode-snapshot.md#160002-截图超时) | Timeout. |
| [160003](../errorcode-snapshot.md#160003-截图选项不支持的色彩空间或动态范围模式) | Unsupported color space or dynamic range mode in snapshot options.<br>**适用版本：** 23+ |

## getSyncWithUniqueId

```TypeScript
getSyncWithUniqueId(uniqueId: number, options?: componentSnapshot.SnapshotOptions): image.PixelMap
```

获取已加载的组件的截图，传入组件的uniqueId，找到对应组件进行截图。同步等待截图完成返回[PixelMap](../../apis-image-kit/arkts-apis/arkts-image-pixelmap-i.md)。

> **说明：**
>
> 截图会获取最近一帧的绘制内容。如果在组件触发更新的同时调用截图，更新的渲染内容不会被截取到，截图会返回上一帧的绘制内容。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本15开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uniqueId | number | 是 | 目标组件的uniqueId。FrameNode节点的uniqueId可通过[getUniqueId](arkts-arkui-framenode-c.md#getuniqueid-1)接口获取。<br/>**说明：** 不支持未挂树组件，当传入的组件标识是离屏或缓存未挂树的节点时，系统不会对其进行截图。 |
| options | componentSnapshot.SnapshotOptions | 否 | 截图相关的自定义参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| image.PixelMap | Promise used to return the result. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameters types.<br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | Invalid ID. |
| [160002](../errorcode-snapshot.md#160002-截图超时) | Timeout. |
| [160003](../errorcode-snapshot.md#160003-截图选项不支持的色彩空间或动态范围模式) | Unsupported color space or dynamic range mode in snapshot options.<br>**适用版本：** 23+ |

## getWithUniqueId

```TypeScript
getWithUniqueId(uniqueId: number, options?: componentSnapshot.SnapshotOptions): Promise<image.PixelMap>
```

获取已加载的组件的截图，传入组件的uniqueId，找到对应组件进行截图。使用Promise异步回调。

> **说明：**
>
> 截图会获取最近一帧的绘制内容。如果在组件触发更新的同时调用截图，更新的渲染内容不会被截取到，截图会返回上一帧的绘制内容。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本15开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uniqueId | number | 是 | 目标组件的uniqueId。FrameNode节点的uniqueId可通过[getUniqueId](arkts-arkui-framenode-c.md#getuniqueid-1)接口获取。 <br/>**说明：** 不支持未挂树组件，当传入的组件标识是离屏或缓存未挂树的节点时，系统不会对其进行截图。 |
| options | componentSnapshot.SnapshotOptions | 否 | 截图相关的自定义参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;image.PixelMap&gt; | Promise used to return the snapshot object. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameters types.<br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | Invalid ID. |
| [160003](../errorcode-snapshot.md#160003-截图选项不支持的色彩空间或动态范围模式) | Unsupported color space or dynamic range mode in snapshot options.<br>**适用版本：** 23+ |

