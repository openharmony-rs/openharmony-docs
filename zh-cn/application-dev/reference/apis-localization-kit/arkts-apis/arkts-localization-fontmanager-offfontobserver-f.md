# offFontObserver

## 导入模块

```TypeScript
import { fontManager } from '@kit.LocalizationKit';
```

## offFontObserver

```TypeScript
function offFontObserver(): void
```

注销字体服务状态变化监听器。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.UPDATE_SCOPE_FONT

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Global.FontManager

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [31100110](../errorcode-font-manager.md#31100110-系统异常导致接口调用失败) | Call failed due to system error. |
| [31100115](../errorcode-font-manager.md#31100115-字体服务状态变化监听器未注册) | The font observer is not registered. |
