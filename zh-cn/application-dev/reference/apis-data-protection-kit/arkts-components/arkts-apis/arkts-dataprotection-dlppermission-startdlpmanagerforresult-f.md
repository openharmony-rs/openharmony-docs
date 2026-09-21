# startDLPManagerForResult

## 导入模块

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
```

## startDLPManagerForResult

```TypeScript
function startDLPManagerForResult(context: common.UIAbilityContext, want: Want): Promise<DLPManagerResult>
```

在当前[UIAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiability-uiability-c.md)界面以无边框形式打开DLP权限管理应用。使用Promise异步回调。

该接口用于拉起DLP权限管理应用配置文件权限，并将用户操作结果返回给调用方。

> **说明：** 
> 
> 该接口仅支持域账号调用。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.DataLossPrevention

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [common.UIAbilityContext](../../apis-ability-kit/arkts-apis/arkts-ability-common-uiabilitycontext-t.md) | 是 | 当前窗口[UIAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiability-uiability-c.md) 上下文。 |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 请求对象，必须包含uri和displayName字段。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[DLPManagerResult](arkts-dataprotection-dlppermission-dlpmanagerresult-i.md)&gt; | Promise对象。打开DLP权限管理应用并退出后的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported because car not support DLP feature.<br>**适用版本：** 26.0.1+ |
| [19100001](../errorcode-dlp.md#19100001-入参错误) | Invalid parameter value. |
| [19100011](../errorcode-dlp.md#19100011-系统服务工作异常) | The system ability works abnormally. |
| [19100016](../errorcode-dlp.md#19100016-want参数中没有uri) | The uri field is missing in the want parameter. |
| [19100017](../errorcode-dlp.md#19100017-want参数中parameters内没有displayname) | The displayName field is missing in the want parameter. |

**示例**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
import { common, Want } from '@kit.AbilityKit';
import { UIContext } from '@kit.ArkUI';

let context = new UIContext().getHostContext() as common.UIAbilityContext; // 获取当前UIAbilityContext。
if (context !== undefined) {
    let want: Want = {
        "uri": "file://docs/storage/Users/currentUser/Desktop/1.txt",
        "parameters": {
        "displayName": "1.txt"
        }
    }; // 构造请求参数，必须包含文件uri和displayName。
    dlpPermission.startDLPManagerForResult(context, want).then((res) => {
        console.info('res.resultCode', res.resultCode);
        console.info('res.want', JSON.stringify(res.want));
    }); // 打开DLP权限管理应用。
}
```


<a id="startdlpmanagerforresult-1"></a>

## startDLPManagerForResult

```TypeScript
function startDLPManagerForResult(context: common.Context, want: Want, window: window.Window): Promise<DLPManagerResult>
```

在指定窗口内以无边框形式打开DLP权限管理应用。使用Promise异步回调。

该接口用于拉起DLP权限管理应用配置文件权限，并将用户操作结果返回给调用方。

> **说明：** 
> 
> 该接口仅支持域账号调用。

**起始版本：** 26.2.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.DataLossPrevention

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [common.Context](../../apis-ability-kit/arkts-apis/arkts-ability-common-context-t.md) | 是 | 当前应用上下文。 |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 请求对象，必须包含uri和displayName字段。 |
| window | [window.Window](../../apis-arkui/arkts-apis/arkts-arkui-window-window-i.md) | 是 | 应用创建的窗口实例。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[DLPManagerResult](arkts-dataprotection-dlppermission-dlpmanagerresult-i.md)&gt; | Promise对象。打开DLP权限管理应用并退出后的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported because car not support DLP feature. |
| [19100001](../errorcode-dlp.md#19100001-入参错误) | Invalid parameter value. |
| [19100011](../errorcode-dlp.md#19100011-系统服务工作异常) | The system ability works abnormally. |
| [19100016](../errorcode-dlp.md#19100016-want参数中没有uri) | The uri field is missing in the want parameter. |
| [19100017](../errorcode-dlp.md#19100017-want参数中parameters内没有displayname) | The displayName field is missing in the want parameter. |

**示例**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
import { common, Want } from '@kit.AbilityKit';
import { UIContext, window } from '@kit.ArkUI';

let config: window.Configuration = {
  name: "dlp_test_window",
  windowType: window.WindowType.TYPE_FLOAT,
  ctx: new UIContext().getHostContext() as common.Context
};
window.createWindow(config).then((windowClass) => {
  windowClass.setUIContent('pages/index/BlankPage');
  windowClass.setWindowFocusable(true);
  windowClass.setWindowBackgroundColor("#00000000");

  let context = new UIContext().getHostContext() as common.Context; // 获取当前Context。
  if (context !== undefined) {
    let want: Want = {
      "uri": "file://docs/storage/Users/currentUser/Desktop/1.txt",
      "parameters": {
        "displayName": "1.txt"
      }
    }; // 构造请求参数，必须包含文件uri和displayName。
    dlpPermission.startDLPManagerForResult(context, want, windowClass).then((res) => {
      console.info('res.resultCode', res.resultCode);
      console.info('res.want', JSON.stringify(res.want));
      windowClass.destroyWindow();
    }); // 打开DLP权限管理应用。
  }
});
```
