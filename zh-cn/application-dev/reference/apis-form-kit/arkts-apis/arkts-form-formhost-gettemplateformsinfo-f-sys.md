# getTemplateFormsInfo（系统接口）

## 导入模块

```TypeScript
import { formHost } from '@kit.FormKit';
```

## getTemplateFormsInfo

```TypeScript
function getTemplateFormsInfo(bundleName: string, moduleName?: string): Promise<Array<formInfo.FormInfo>>
```

获取设备上指定应用程序提供的模板卡片信息。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

<!--Device-formHost-function getTemplateFormsInfo(bundleName: string, moduleName?: string): Promise<Array<formInfo.FormInfo>>--><!--Device-formHost-function getTemplateFormsInfo(bundleName: string, moduleName?: string): Promise<Array<formInfo.FormInfo>>-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 要查询的应用Bundle名称。 |
| moduleName | string | 否 | 要查询的模块名称，缺省默认为空。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;formInfo.FormInfo&gt;&gt; | Promise对象。返回查询到的卡片信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permissions denied. |
| [16500050](../errorcode-form.md#16500050-进程间通信失败) | IPC connection error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |

