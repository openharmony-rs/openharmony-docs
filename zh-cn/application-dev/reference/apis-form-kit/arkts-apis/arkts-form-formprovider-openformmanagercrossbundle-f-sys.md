# openFormManagerCrossBundle（系统接口）

## 导入模块

```TypeScript
import { formProvider } from '@kit.FormKit';
```

## openFormManagerCrossBundle

```TypeScript
function openFormManagerCrossBundle(want: Want): void
```

Open the view of forms belonging to the specified bundle. Client to communication with FormManagerService.

**起始版本：** 20

**需要权限：** ohos.permission.PUBLISH_FORM_CROSS_BUNDLE

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | The want of the form to open. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permissions denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [16500050](../errorcode-form.md#16500050-进程间通信失败) | IPC connection error. |
