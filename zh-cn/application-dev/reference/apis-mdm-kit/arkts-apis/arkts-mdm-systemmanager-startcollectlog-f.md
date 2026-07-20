# startCollectLog

## 导入模块

```TypeScript
import { systemManager } from '@kit.MDMKit';
```

<a id="startcollectlog"></a>
## startCollectLog

```TypeScript
function startCollectLog(admin: Want): Promise<void>
```

开始收集设备上已生成并存储至硬盘的[faultlog](../../apis-performance-analysis-kit/arkts-apis/arkts-performanceanalysis-faultlogger-faulttype-e.md)日志，不支持收集未存储至硬盘的faultlog日志、应用业务日志和系统运行日志。

- 调用接口后，系统会启动一个日志收集任务，任务启动后接口立即返回。任务可能会因为系统性能等原因导致收集失败。  
- 允许多个MDM应用调用，不同MDM应用在不同用户下收集的日志分开保存，互不影响。同一时间只允许一个MDM应用启动日志收集任务，在任务执行完成前调用本接口会返回错误码9201009，任务执行完成后，允许其他MDM应用调用。  
- 任务执行完成后，通过[EnterpriseAdminExtensionAbility.onLogCollected](arkts-mdm-enterprise-enterpriseadminextensionability-enterpriseadminextensionability-c.md#onlogcollected-1)回调函数通知给MDM应用，系统将已收集的日志文件挂载到MDM应用沙箱路径，MDM应用可以在回调函数中读取已收集的日志。  
- 如果日志收集任务执行超过5分钟，[EnterpriseAdminExtensionAbility.onLogCollected](arkts-mdm-enterprise-enterpriseadminextensionability-enterpriseadminextensionability-c.md#onlogcollected-1)回调函数会返回日志收集任务失败。  
- 应用取走日志后，建议调用[systemManager.finishLogCollected](arkts-mdm-systemmanager-finishlogcollected-f.md#finishlogcollected-1)删除已收集到的日志。

**起始版本：** 23

**需要权限：** ohos.permission.ENTERPRISE_READ_LOG

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-systemManager-function startCollectLog(admin: Want): Promise<void>--><!--Device-systemManager-function startCollectLog(admin: Want): Promise<void>-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。当收集日志任务创建失败时，会抛出错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9201009](../errorcode-enterpriseDeviceManager.md#9201009-日志收集任务创建失败) | Collecting logs, please try again later. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.Failed to call the API due to limited device capabilities. |

**示例：**

```TypeScript
import { Want } from '@kit.AbilityKit';
import { systemManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

systemManager.startCollectLog(wantTemp).then(() => {
  console.info('Succeeded in starting collect log');
}).catch((err: BusinessError) => {
  console.error(`Failed to start collect log. Code: ${err.code}, message: ${err.message}`);
});

```

