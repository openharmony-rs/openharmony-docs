# onAutoSyncTrigger

## 导入模块

```TypeScript
import { cloudData } from '@kit.ArkData';
```

## onAutoSyncTrigger

```TypeScript
function onAutoSyncTrigger(observer: Callback<AutoSyncTriggerInfo>): void
```

在已打开端云同步且应用关闭自动同步的条件下，注册自动同步触发事件通知。当满足自动触发条件时，回调函数会被调用。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-cloudData-function onAutoSyncTrigger(observer: Callback<AutoSyncTriggerInfo>): void--><!--Device-cloudData-function onAutoSyncTrigger(observer: Callback<AutoSyncTriggerInfo>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Client

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| observer | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;AutoSyncTriggerInfo&gt; | 是 | 回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例：**

```TypeScript
function autoSyncTriggerObserver(info: cloudData.AutoSyncTriggerInfo) {
  console.info(`Auto sync triggered, mode: ${info.mode}`);
}

cloudData.onAutoSyncTrigger(autoSyncTriggerObserver);

```

