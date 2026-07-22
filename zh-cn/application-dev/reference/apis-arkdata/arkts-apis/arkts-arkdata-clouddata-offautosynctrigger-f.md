# offAutoSyncTrigger

## 导入模块

```TypeScript
import { cloudData } from '@kit.ArkData';
```

## offAutoSyncTrigger

```TypeScript
function offAutoSyncTrigger(observer?: Callback<AutoSyncTriggerInfo>): void
```

取消订阅自动同步触发事件通知。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-cloudData-function offAutoSyncTrigger(observer?: Callback<AutoSyncTriggerInfo>): void--><!--Device-cloudData-function offAutoSyncTrigger(observer?: Callback<AutoSyncTriggerInfo>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Client

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| observer | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;AutoSyncTriggerInfo&gt; | 否 | 回调函数。 若传入observer，则取消指定回调函数的订阅；若不传入observer，则取消所有已注册的订阅。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例：**

```TypeScript
function autoSyncTriggerObserver(info: cloudData.AutoSyncTriggerInfo) {
  console.info(`Auto sync triggered, mode: ${info.mode}`);
}

// 订阅
cloudData.onAutoSyncTrigger(autoSyncTriggerObserver);

// 取消指定订阅
cloudData.offAutoSyncTrigger(autoSyncTriggerObserver);

// 取消所有订阅
cloudData.offAutoSyncTrigger();

```

