# installFont（系统接口）

## installFont

```TypeScript
function installFont(path: string): Promise<int>
```

将指定路径下的字体文件安装到系统字体库中。使用Promise异步回调。 安装成功后，应用可以通过字体名称使用该字体。

**起始版本：** 19

**ArkTS模式：** ArkTS-Dyn起始版本为19；ArkTS-Sta起始版本为23。

**需要权限：** ohos.permission.UPDATE_FONT

<!--Device-fontManager-function installFont(path: string): Promise<int>--><!--Device-fontManager-function installFont(path: string): Promise<int>-End-->

**系统能力：** SystemCapability.Global.FontManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 待安装的字体文件路径，仅支持.ttf和.ttc格式的字体文件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: Promise&lt;number&gt;  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：Promise&lt;int&gt; | Promise对象，返回安装结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system application. |
| [31100101](../errorcode-font-manager.md#31100101-字体文件不存在) | Font does not exist. |
| [31100102](../errorcode-font-manager.md#31100102-字体文件不支持安装) | Font is not supported. |
| [31100103](../errorcode-font-manager.md#31100103-字体文件拷贝失败) | Font file copy failed. |
| [31100104](../errorcode-font-manager.md#31100104-字体文件已安装) | Font file installed. |
| [31100105](../errorcode-font-manager.md#31100105-已安装字体文件超过最大数量) | Exceeded maximum number of installed files. |
| [31100106](../errorcode-font-manager.md#31100106-其他错误导致安装失败) | Other error. |

