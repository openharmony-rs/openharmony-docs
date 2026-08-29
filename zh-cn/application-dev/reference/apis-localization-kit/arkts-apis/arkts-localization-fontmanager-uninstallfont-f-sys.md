# uninstallFont（系统接口）

## 导入模块

```TypeScript
import { fontManager } from '@kit.LocalizationKit';
```

## uninstallFont

```TypeScript
function uninstallFont(fullName: string): Promise<number>
```

根据字体名称从系统字体库中卸载已安装的字体文件。使用Promise异步回调。

**起始版本：** 19

**需要权限：** ohos.permission.UPDATE_FONT

**系统能力：** SystemCapability.Global.FontManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fullName | string | 是 | 需要卸载的字体名称，可通过打开.ttf或.ttc字体文件获取。 字体名称区分大小写，请确保与实际字体名称完全一致。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;number&gt; | Promise对象，返回卸载结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [31100107](../errorcode-font-manager.md#31100107-卸载的字体文件不存在) | The font file does not exist. |
| [31100108](../errorcode-font-manager.md#31100108-无法删除字体) | Failed to delete the font file. |
| [31100109](../errorcode-font-manager.md#31100109-其他错误导致卸载失败) | The system ability works abnormally. |

**示例**

```TypeScript
import { fontManager } from '@kit.LocalizationKit';

async function uninstallFont() {
  try {
    let res = await fontManager.uninstallFont('fontName');
    console.info('uninstallFont suc. res is ' + res);
  } catch (error) {
    console.error('uninstallFont err.' + error.code);
  }
  return;
}
```
