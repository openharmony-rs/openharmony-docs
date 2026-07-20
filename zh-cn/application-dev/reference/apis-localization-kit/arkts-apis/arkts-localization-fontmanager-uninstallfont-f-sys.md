# uninstallFont（系统接口）

## 导入模块

```TypeScript
import { fontManager } from '@kit.LocalizationKit';
```

<a id="uninstallfont"></a>
## uninstallFont

```TypeScript
function uninstallFont(fullName: string): Promise<number>
```

卸载指定名称的字体，使用promise异步回调。

**起始版本：** 19

**需要权限：** ohos.permission.UPDATE_FONT

<!--Device-fontManager-function uninstallFont(fullName: string): Promise<int>--><!--Device-fontManager-function uninstallFont(fullName: string): Promise<int>-End-->

**系统能力：** SystemCapability.Global.FontManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fullName | string | 是 | 需要卸载的字体名称，字体名称可通过打开.ttf或.ttc字体文件获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | 返回卸载结果。返回为0表示卸载成功，否则卸载失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system application. |
| [31100107](../errorcode-font-manager.md#31100107-卸载的字体文件不存在) | Font file does not exist. |
| [31100108](../errorcode-font-manager.md#31100108-无法删除字体) | Font file delete error. |
| [31100109](../errorcode-font-manager.md#31100109-其他错误导致卸载失败) | Other error. |

