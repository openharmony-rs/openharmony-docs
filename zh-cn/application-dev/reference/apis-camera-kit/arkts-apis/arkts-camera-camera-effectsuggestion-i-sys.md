# EffectSuggestion（系统接口）

```TypeScript
interface EffectSuggestion
```

效果建议对象。

**起始版本：** 12

<!--Device-camera-interface EffectSuggestion--><!--Device-camera-interface EffectSuggestion-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
```

## enableEffectSuggestion

```TypeScript
enableEffectSuggestion(enabled: boolean): void
```

为会话启用效果建议。

**起始版本：** 12

<!--Device-EffectSuggestion-enableEffectSuggestion(enabled: boolean): void--><!--Device-EffectSuggestion-enableEffectSuggestion(enabled: boolean): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 为 TRUE 时为会话启用效果建议。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## getSupportedEffectSuggestionTypes

```TypeScript
getSupportedEffectSuggestionTypes(): Array<EffectSuggestionType>
```

获取支持的效果建议类型。

**起始版本：** 12

<!--Device-EffectSuggestion-getSupportedEffectSuggestionTypes(): Array<EffectSuggestionType>--><!--Device-EffectSuggestion-getSupportedEffectSuggestionTypes(): Array<EffectSuggestionType>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[EffectSuggestionType](arkts-camera-camera-effectsuggestiontype-e-sys.md)&gt; | 效果建议类型数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## isEffectSuggestionSupported

```TypeScript
isEffectSuggestionSupported(): boolean
```

查询是否支持效果建议。

**起始版本：** 12

<!--Device-EffectSuggestion-isEffectSuggestionSupported(): boolean--><!--Device-EffectSuggestion-isEffectSuggestionSupported(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 是否支持效果建议。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## setEffectSuggestionStatus

```TypeScript
setEffectSuggestionStatus(status: Array<EffectSuggestionStatus>): void
```

设置效果建议类型的范围和启用状态。应用启动时应完整设置所有数据。

**起始版本：** 12

<!--Device-EffectSuggestion-setEffectSuggestionStatus(status: Array<EffectSuggestionStatus>): void--><!--Device-EffectSuggestion-setEffectSuggestionStatus(status: Array<EffectSuggestionStatus>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| status | Array&lt;[EffectSuggestionStatus](arkts-camera-camera-effectsuggestionstatus-c-sys.md)&gt; | 是 | 效果建议状态数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## updateEffectSuggestion

```TypeScript
updateEffectSuggestion(type: EffectSuggestionType, enabled: boolean): void
```

更新效果建议类型的启用状态。

**起始版本：** 12

<!--Device-EffectSuggestion-updateEffectSuggestion(type: EffectSuggestionType, enabled: boolean): void--><!--Device-EffectSuggestion-updateEffectSuggestion(type: EffectSuggestionType, enabled: boolean): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [EffectSuggestionType](arkts-camera-camera-effectsuggestiontype-e-sys.md) | 是 | 效果建议类型。 |
| enabled | boolean | 是 | 效果建议类型的启用状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
