# onFontObserver

## 导入模块

```TypeScript
import { fontManager } from '@kit.LocalizationKit';
```

## onFontObserver

```TypeScript
function onFontObserver(observer: FontClientObserver): void
```

注册字体服务状态变化监听器。

> **说明：** 
> - 每个应用仅可注册一个字体服务状态变化监听器，重复注册会报错。
> - 同一用户最多允许5个应用同时注册，否则会报错。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.UPDATE_SCOPE_FONT

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Global.FontManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| observer | [FontClientObserver](arkts-localization-fontmanager-fontclientobserver-i.md) | 是 | 字体服务状态变化监听器。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [31100110](../errorcode-font-manager.md#31100110-系统异常导致接口调用失败) | Call failed due to system error. |
| [31100113](../errorcode-font-manager.md#31100113-字体服务状态监听器已注册) | The font observer is already registered. |
| [31100114](../errorcode-font-manager.md#31100114-超过字体服务状态监听器最大数量) | The maximum number of font observers has been reached. |
