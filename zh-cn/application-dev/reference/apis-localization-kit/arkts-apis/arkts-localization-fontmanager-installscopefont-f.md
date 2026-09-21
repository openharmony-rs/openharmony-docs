# installScopeFont

## 导入模块

```TypeScript
import { fontManager } from '@kit.LocalizationKit';
```

## installScopeFont

```TypeScript
function installScopeFont(url: string, scope: FontScope): Promise<void>
```

安装指定路径下的字体文件为应用级或会话级字体。使用Promise异步回调。

> **说明：** 
> - 当安装应用级字体时，需先调用[onFontObserver](arkts-localization-fontmanager-onfontobserver-f.md)接口注册字体服务状态变化监听器。
> - 安装成功后，应用可以通过字体名称使用该字体。同一字体路径不可重复安装。
> - PC/2in1支持安装的字体文件最大数量为800，其他设备支持安装的字体文件个数最大数量为200。

**起始版本：** 26.0.1

**需要权限：** ohos.permission.UPDATE_SCOPE_FONT

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Global.FontManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | 待安装的字体文件路径，仅支持.ttf、.ttc和.otf格式的字体文件。 |
| scope | [FontScope](arkts-localization-fontmanager-fontscope-e.md) | 是 | 字体作用范围。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [31100101](../errorcode-font-manager.md#31100101-字体文件不存在) | The font does not exist. |
| [31100102](../errorcode-font-manager.md#31100102-字体文件不支持安装) | The font is not supported. |
| [31100103](../errorcode-font-manager.md#31100103-字体文件拷贝失败) | Failed to copy the font file. |
| [31100104](../errorcode-font-manager.md#31100104-字体文件已安装) | The font file is installed. |
| [31100105](../errorcode-font-manager.md#31100105-已安装字体文件超过最大数量) | Exceeded the maximum number of installed files. |
| [31100110](../errorcode-font-manager.md#31100110-系统异常导致接口调用失败) | Call failed due to system error. |
| 31100115 | The font observer is not registered. |
