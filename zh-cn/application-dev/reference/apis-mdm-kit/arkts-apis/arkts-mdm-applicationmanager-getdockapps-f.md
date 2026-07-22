# getDockApps

## 导入模块

```TypeScript
import { applicationManager } from '@kit.MDMKit';
```

## getDockApps

```TypeScript
function getDockApps(admin: Want): Array<DockInfo>
```

获取当前快捷栏中应用信息的列表。

**起始版本：** 24

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-applicationManager-function getDockApps(admin: Want): Array<DockInfo>--><!--Device-applicationManager-function getDockApps(admin: Want): Array<DockInfo>-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;DockInfo&gt; | 快捷栏中的应用信息数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.Failed to call the API due to limited device capabilities. |

**示例：**

```TypeScript
import { applicationManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  let result: Array<applicationManager.DockInfo> = applicationManager.getDockApps(wantTemp);
  console.info(`Succeeded in getting dock apps, result : ${JSON.stringify(result)}`);
} catch(err) {
  console.error(`Failed to get dock apps. Code: ${err.code}, message: ${err.message}`);
}

```

```TypeScript
// 返回示例
[
  {
    "bundleName": "com.example.edmtest",
    "abilityName": "EntryAbility",
    "index": 5
  },
  // ...
]

```

