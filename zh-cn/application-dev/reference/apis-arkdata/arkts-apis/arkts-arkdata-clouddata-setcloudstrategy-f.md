# setCloudStrategy

## 导入模块

```TypeScript
import { cloudData } from '@kit.ArkData';
```

## setCloudStrategy

```TypeScript
function setCloudStrategy(strategy: StrategyType, param?: Array<commonType.ValueType>): Promise<void>
```

设置应用自身的云同步策略，使用Promise异步回调。

**起始版本：** 12

<!--Device-cloudData-function setCloudStrategy(strategy: StrategyType, param?: Array<commonType.ValueType>): Promise<void>--><!--Device-cloudData-function setCloudStrategy(strategy: StrategyType, param?: Array<commonType.ValueType>): Promise<void>-End-->

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Client

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| strategy | [StrategyType](arkts-arkdata-clouddata-strategytype-e.md) | 是 | 配置的策略类型。 |
| param | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<commonType.ValueType> | 否 | 策略参数，类型为Array&lt;commonType.ValueType&gt;，实际传入值为[NetWorkStrategy](arkts-arkdata-clouddata-networkstrategy-e.md)枚举值，取值范围为WIFI和CELLULAR，默认支持WIFI和蜂窝网络策略。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameter types;3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 仅WIFI同步
cloudData.setCloudStrategy(cloudData.StrategyType.NETWORK, [cloudData.NetWorkStrategy.WIFI]).then(() => {
  console.info('Succeeded in setting the cloud strategy');
}).catch((err: BusinessError) => {
  console.error(`Failed to set cloud strategy. Code: ${err.code}, message: ${err.message}`);
});


```

