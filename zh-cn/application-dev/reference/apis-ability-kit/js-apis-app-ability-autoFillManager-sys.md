# @ohos.app.ability.autoFillManager (autoFillManager)(系统接口)

autoFillManager模块提供账号密码保存等功能。

不同于页面切换时触发的系统自动保存功能，该功能需要由用户手动触发。例如用户在网站上输入了账号密码，并点击“保存”按钮，才能触发相应的自动保存操作。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 本模块首批接口从API version 11 开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 本模块接口仅可在Stage模型下使用。
>
> - 当前页面仅包含本模块的系统接口，其他公开接口参见[@ohos.app.ability.autoFillManager (autoFillManager)](js-apis-app-ability-autoFillManager.md)。

## 导入模块

```ts
import { autoFillManager } from '@kit.AbilityKit';
```

## ViewData

type ViewData = _ViewData.default

自动填充的视图数据信息。

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**模型约束**：此接口仅可在Stage模型下使用。

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 11

| 类型 | 说明 |
| --- | --- |
| [_ViewData.default](js-apis-inner-application-viewData-sys.md) | 表示自动填充的视图数据信息。 |

## ViewData<sup>23+</sup>

type ViewData = _ViewData

自动填充的视图数据信息。

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**模型约束**：此接口仅可在Stage模型下使用。

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

| 类型                                                   | 说明                         |
| ------------------------------------------------------ | ---------------------------- |
| [_ViewData](js-apis-inner-application-viewData-sys.md) | 表示自动填充的视图数据信息。 |

## PageNodeInfo

type PageNodeInfo = _PageNodeInfo.default

自动填充的页面节点信息。

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**模型约束**：此接口仅可在Stage模型下使用。

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 11

| 类型 | 说明 |
| --- | --- |
| [_PageNodeInfo.default](js-apis-inner-application-pageNodeInfo-sys.md) | 表示自动填充的页面节点信息。 |

## PageNodeInfo<sup>23+</sup>

type PageNodeInfo = _PageNodeInfo

自动填充的页面节点信息。

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**模型约束**：此接口仅可在Stage模型下使用。

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

| 类型                                                         | 说明                         |
| ------------------------------------------------------------ | ---------------------------- |
| [_PageNodeInfo](js-apis-inner-application-pageNodeInfo-sys.md) | 表示自动填充的页面节点信息。 |

## AutoFillType<sup>23+</sup>

type AutoFillType = _AutoFillType

自动填充的类型信息。

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**模型约束**：此接口仅可在Stage模型下使用。

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

| 类型                                                         | 说明                     |
| ------------------------------------------------------------ | ------------------------ |
| [_AutoFillType](js-apis-inner-application-autoFillType-sys.md) | 表示自动填充的类型信息。 |

## FillRequest

type FillRequest = _AutoFillRequest.FillRequest

自动填充的请求信息。

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**模型约束**：此接口仅可在Stage模型下使用。

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 11

| 类型 | 说明 |
| --- | --- |
| [_AutoFillRequest.FillRequest](js-apis-inner-application-autoFillRequest-sys.md#fillrequest) | 表示自动填充的请求信息。 |

## FillRequest<sup>23+</sup>

type FillRequest = _FillRequest

自动填充的请求信息。

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**模型约束**：此接口仅可在Stage模型下使用。

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

| 类型                                                         | 说明                     |
| ------------------------------------------------------------ | ------------------------ |
| [_FillRequest](js-apis-inner-application-autoFillRequest-sys.md#fillrequest) | 表示自动填充的请求信息。 |

## SaveRequest

type SaveRequest = _AutoFillRequest.SaveRequest

自动保存的请求信息。

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**模型约束**：此接口仅可在Stage模型下使用。

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 11

| 类型 | 说明 |
| --- | --- |
| [_AutoFillRequest.SaveRequest](js-apis-inner-application-autoFillRequest-sys.md#saverequest) | 表示自动保存的请求信息。 |

## SaveRequest<sup>23+</sup>

type SaveRequest = _SaveRequest

自动保存的请求信息。

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**模型约束**：此接口仅可在Stage模型下使用。

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

| 类型                                                         | 说明                     |
| ------------------------------------------------------------ | ------------------------ |
| [_SaveRequest](js-apis-inner-application-autoFillRequest-sys.md#saverequest) | 表示自动保存的请求信息。 |

## UpdateRequest<sup>12+</sup>

type UpdateRequest = _AutoFillRequest.UpdateRequest

自动填充的更新信息。

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**模型约束**：此接口仅可在Stage模型下使用。

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 12

| 类型 | 说明 |
| --- | --- |
| [_AutoFillRequest.UpdateRequest](js-apis-inner-application-autoFillRequest-sys.md#updaterequest12) | 表示自动填充的更新信息。 |

## UpdateRequest<sup>23+</sup>

type UpdateRequest = _UpdateRequest

自动填充的更新信息。

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**模型约束**：此接口仅可在Stage模型下使用。

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

| 类型                                                         | 说明                     |
| ------------------------------------------------------------ | ------------------------ |
| [_UpdateRequest](js-apis-inner-application-autoFillRequest-sys.md#updaterequest12) | 表示自动填充的更新信息。 |

## FillResponse

type FillResponse = _AutoFillRequest.FillResponse

自动填充的响应信息。

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**模型约束**：此接口仅可在Stage模型下使用。

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 11

| 类型 | 说明 |
| --- | --- |
| [_AutoFillRequest.FillResponse](js-apis-inner-application-autoFillRequest-sys.md#fillresponse) | 表示自动填充的响应信息。 |

## FillResponse<sup>23+</sup>

type FillResponse = _FillResponse

自动填充的响应信息。

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**模型约束**：此接口仅可在Stage模型下使用。

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

| 类型                                                         | 说明                     |
| ------------------------------------------------------------ | ------------------------ |
| [_FillResponse](js-apis-inner-application-autoFillRequest-sys.md#fillresponse) | 表示自动填充的响应信息。 |

## FillRequestCallback

type FillRequestCallback = _AutoFillRequest.FillRequestCallback

自动填充或者生成密码时的回调对象，可以通过此回调通知客户端成功或者失败。

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**模型约束**：此接口仅可在Stage模型下使用。

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 11

| 类型 | 说明 |
| --- | --- |
| [_AutoFillRequest.FillRequestCallback](js-apis-inner-application-autoFillRequest-sys.md#fillrequestcallback) | 表示自动填充或者生成密码时的回调对象，可以通过此回调通知客户端成功或者失败。 |

## FillRequestCallback<sup>23+</sup>

type FillRequestCallback = _FillRequestCallback

自动填充或者生成密码时的回调对象，可以通过此回调通知客户端成功或者失败。

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**模型约束**：此接口仅可在Stage模型下使用。

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

| 类型                                                         | 说明                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [_FillRequestCallback](js-apis-inner-application-autoFillRequest-sys.md#fillrequestcallback) | 表示自动填充或者生成密码时的回调对象，可以通过此回调通知客户端成功或者失败。 |

## SaveRequestCallback

type SaveRequestCallback = _AutoFillRequest.SaveRequestCallback

自动保存或者手动保存请求的回调对象。

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**模型约束**：此接口仅可在Stage模型下使用。

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 11

| 类型 | 说明 |
| --- | --- |
| [_AutoFillRequest.SaveRequestCallback](js-apis-inner-application-autoFillRequest-sys.md#saverequestcallback) | 表示自动保存或者手动保存请求的回调对象。 |

## SaveRequestCallback<sup>23+</sup>

type SaveRequestCallback = _SaveRequestCallback

自动保存或者手动保存请求的回调对象。

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**模型约束**：此接口仅可在Stage模型下使用。

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

| 类型                                                         | 说明                                     |
| ------------------------------------------------------------ | ---------------------------------------- |
| [_SaveRequestCallback](js-apis-inner-application-autoFillRequest-sys.md#saverequestcallback) | 表示自动保存或者手动保存请求的回调对象。 |

## CustomData<sup>13+</sup>

type CustomData = _CustomData.default

自定义数据。

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**模型约束**：此接口仅可在Stage模型下使用。

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 13

| 类型 | 说明 |
| --- | --- |
| [_CustomData.default](js-apis-inner-application-customData-sys.md) | 表示自定义数据。 |

## CustomData<sup>23+</sup>

type CustomData = _CustomData

自定义数据。

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**模型约束**：此接口仅可在Stage模型下使用。

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

| 类型                                                       | 说明             |
| ---------------------------------------------------------- | ---------------- |
| [_CustomData](js-apis-inner-application-customData-sys.md) | 表示自定义数据。 |

## AutoFillRect<sup>12+</sup>

type AutoFillRect = _AutoFillRect.default

用于自动填充的矩形区域。

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**模型约束**：此接口仅可在Stage模型下使用。

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 12

| 类型 | 说明 |
| --- | --- |
| [_AutoFillRect.default](js-apis-inner-application-autoFillRect-sys.md) | 表示用于自动填充的矩形区域。 |

## AutoFillRect<sup>23+</sup>

type AutoFillRect = _AutoFillRect

用于自动填充的矩形区域。

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**模型约束**：此接口仅可在Stage模型下使用。

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

| 类型                                                         | 说明                         |
| ------------------------------------------------------------ | ---------------------------- |
| [_AutoFillRect](js-apis-inner-application-autoFillRect-sys.md) | 表示用于自动填充的矩形区域。 |

## AutoFillPopupConfig<sup>12+</sup>

type AutoFillPopupConfig = _AutoFillPopupConfig.default

自动填充气泡弹窗的尺寸和位置信息。

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**模型约束**：此接口仅可在Stage模型下使用。

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 12

| 类型 | 说明 |
| --- | --- |
| [_AutoFillPopupConfig.default](js-apis-inner-application-autoFillPopupConfig-sys.md) | 表示自动填充气泡弹窗的尺寸和位置信息。 |

## AutoFillPopupConfig<sup>23+</sup>

type AutoFillPopupConfig = _AutoFillPopupConfig

自动填充气泡弹窗的尺寸和位置信息。

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**模型约束**：此接口仅可在Stage模型下使用。

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

| 类型                                                         | 说明                                   |
| ------------------------------------------------------------ | -------------------------------------- |
| [_AutoFillPopupConfig](js-apis-inner-application-autoFillPopupConfig-sys.md) | 表示自动填充气泡弹窗的尺寸和位置信息。 |

## PopupSize<sup>12+</sup>

type PopupSize = _AutoFillPopupConfig.PopupSize

气泡弹窗的宽和高。

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**模型约束**：此接口仅可在Stage模型下使用。

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 12

| 类型 | 说明 |
| --- | --- |
| [_AutoFillPopupConfig.PopupSize](js-apis-inner-application-autoFillPopupConfig-sys.md#popupsize) | 表示气泡弹窗的宽和高。 |

## PopupSize<sup>23+</sup>

type PopupSize = _PopupSize

气泡弹窗的宽和高。

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**模型约束**：此接口仅可在Stage模型下使用。

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

| 类型                                                         | 说明                   |
| ------------------------------------------------------------ | ---------------------- |
| [_PopupSize](js-apis-inner-application-autoFillPopupConfig-sys.md#popupsize) | 表示气泡弹窗的宽和高。 |

## PopupPlacement<sup>23+</sup>

type PopupPlacement = _PopupPlacement

气泡弹窗的位置。

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.Ability.AbilityRuntime.AbilityCore

**模型约束**：此接口仅可在Stage模型下使用。

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

| 类型                                                         | 说明                 |
| ------------------------------------------------------------ | -------------------- |
| [_PopupPlacement](js-apis-inner-application-autoFillPopupConfig-sys.md#popupplacement) | 表示气泡弹窗的位置。 |