# isDLPFeatureProvided

## 导入模块

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
```

## isDLPFeatureProvided

```TypeScript
function isDLPFeatureProvided(): Promise<boolean>
```

查询当前系统是否提供加密保护特性，仅支持企业设备且需[MDM（Mobile Device Management，移动设备管理）](../../../mdm/mdm-kit-intro.md)配置使能。调用成功后返回查询结果，用于判断系统是否支持DLP加密功能。使用Promise异步回调。

该接口用于判断当前系统是否支持DLP加密功能，以便在不支持的设备上做兼容处理或功能降级。
> **说明：**  
>  
> 该接口由[MDM](../../../mdm/mdm-kit-intro.md)配置使能，且使能场景为企业设备。其他设备（如消费者终端设备）无需关注该接口，如若调用该接口，则返回值为false。

**起始版本：** 12

<!--Device-dlpPermission-function isDLPFeatureProvided(): Promise<boolean>--><!--Device-dlpPermission-function isDLPFeatureProvided(): Promise<boolean>-End-->

**系统能力：** SystemCapability.Security.DataLossPrevention

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Pomise对象。返回true表示当前系统提供加密保护特性，返回false表示不提供加密保护特性。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19100011](../errorcode-dlp.md#19100011-系统服务工作异常) | The system ability works abnormally. |

**示例：**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';

dlpPermission.isDLPFeatureProvided().then((isFeatureProvided) => { // 查询当前系统是否提供加密保护特性。
  console.info('isFeatureProvided', JSON.stringify(isFeatureProvided));
}).catch((err: BusinessError) => {
  console.error('error', (err as BusinessError).code, (err as BusinessError).message); // 失败报错。
});

```

