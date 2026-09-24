# uninstallScopeFont

## 导入模块

```TypeScript
import { fontManager } from '@kit.LocalizationKit';
```

## uninstallScopeFont

```TypeScript
function uninstallScopeFont(url: string): Promise<void>
```

根据字体路径卸载已安装的应用级或会话级字体。使用Promise异步回调。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.UPDATE_SCOPE_FONT

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Global.FontManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | 需要卸载的字体路径。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 31100108 | Failed to delete the font file. |
| 31100110 | Call failed due to system error. |
| 31100112 | The scope font is not found. |
