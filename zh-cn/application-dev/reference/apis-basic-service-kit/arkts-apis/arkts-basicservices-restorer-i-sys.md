# Restorer（系统接口）

提供设备恢复出厂设置功能的工具类。

**起始版本：** 9

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## deepFactoryReset

```TypeScript
deepFactoryReset(factoryResetStrategy: FactoryResetStrategy): Promise<void>
```

通过覆写等方式，深度清除用户数据分区、操作系统分区。使用 Promise 异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.FACTORY_RESET

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| factoryResetStrategy | FactoryResetStrategy | 是 | 恢复出厂设置策略。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [203](../../errorcode-universal.md#203-企业管理策略禁止使用此系统功能) | This function is prohibited by enterprise management policies. |
| [11500104](../../apis-basic-services-kit/errorcode-update.md#11500104-ipc通信异常) | IPC error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
try {
  // 获取恢复出厂设置对象
  let factoryRestorer = update.getRestorer();
  // 创建恢复出厂设置策略对象
  let factoryResetStrategy: update.FactoryResetStrategy = {
    scope: update.FactoryResetScope.DATA, // 重置范围为用户数据
    strategy: 'deepFactoryReset test' // 重置范围描述
  };
  // 执行深度恢复出厂设置
  factoryRestorer.deepFactoryReset(factoryResetStrategy).then(() => {
    console.info(`deepFactoryReset success`);
  }).catch((deepResetError: BusinessError) => {
    console.error(`deepFactoryReset error, code:${deepResetError.code}, message:${deepResetError.message}.`);
  });
} catch (error) {
  console.error(`Fail to get factoryRestorer: ${error}`);
}

```

## factoryReset

```TypeScript
factoryReset(callback: AsyncCallback<void>): void
```

清除用户数据分区。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.FACTORY_RESET

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当恢复出厂执行成功时，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [203](../../errorcode-universal.md#203-企业管理策略禁止使用此系统功能) | This function is prohibited by enterprise management policies. |
| [11500104](../../apis-basic-services-kit/errorcode-update.md#11500104-ipc通信异常) | IPC error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 获取恢复出厂设置对象
  let factoryRestorer = update.getRestorer();
  // 执行恢复出厂设置
  factoryRestorer.factoryReset((resetError: BusinessError) => {
    if (resetError) {
      console.error(`factoryReset error, code:${resetError.code}, message:${resetError.message}.`);
      return;
    }
    console.info(`factoryReset success`);
  });
} catch (error) {
  let err: BusinessError = error as BusinessError;
  console.error(`Fail to get factoryRestorer. Code: ${err.code}, message: ${err.message}.`);
}

```

## factoryReset

```TypeScript
factoryReset(): Promise<void>
```

清除用户数据分区。使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.FACTORY_RESET

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [203](../../errorcode-universal.md#203-企业管理策略禁止使用此系统功能) | This function is prohibited by enterprise management policies. |
| [11500104](../../apis-basic-services-kit/errorcode-update.md#11500104-ipc通信异常) | IPC error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 获取恢复出厂设置对象
  let factoryRestorer = update.getRestorer();
  // 执行恢复出厂设置
  factoryRestorer.factoryReset().then(() => {
    console.info(`factoryReset success`);
  }).catch((resetError: BusinessError) => {
    console.error(`factoryReset error, code:${resetError.code}, message:${resetError.message}.`);
  });
} catch (error) {
  console.error(`Fail to get factoryRestorer: ${error}`);
}

```

## forceFactoryReset

```TypeScript
forceFactoryReset(): Promise<void>
```

清除用户数据分区，同步清除文件秘钥。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.FORCE_FACTORY_RESET

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [203](../../errorcode-universal.md#203-企业管理策略禁止使用此系统功能) | This function is prohibited by enterprise management policies. |
| [11500104](../../apis-basic-services-kit/errorcode-update.md#11500104-ipc通信异常) | IPC error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
try {
  // 获取恢复出厂设置对象
  let factoryRestorer = update.getRestorer();
  // 执行强制恢复出厂设置
  factoryRestorer.forceFactoryReset().then(() => {
    console.info(`forceFactoryReset success`);
  }).catch((forceResetError: BusinessError) => {
    console.error(`forceFactoryReset error, code:${forceResetError.code}, message:${forceResetError.message}.`);
  });
} catch (error) {
  console.error(`Fail to get factoryRestorer: ${error}`);
}

```

## getDeepFactoryResetInfo

```TypeScript
getDeepFactoryResetInfo(factoryResetStrategy: FactoryResetStrategy): Promise<FactoryResetInfo>
```

获取深度恢复出厂设置信息。使用 Promise 异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.FACTORY_RESET

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| factoryResetStrategy | FactoryResetStrategy | 是 | 恢复出厂设置策略。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;FactoryResetInfo&gt; | Promise对象，返回深度恢复出厂设置信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [11500104](../../apis-basic-services-kit/errorcode-update.md#11500104-ipc通信异常) | IPC error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// 创建恢复出厂设置策略对象
let factoryResetStrategy: update.FactoryResetStrategy = {
  scope: update.FactoryResetScope.DATA, // 重置范围为用户数据 
  strategy: 'getDeepFactoryResetInfo test' // 重置范围描述
};
try {
  // 获取恢复出厂设置对象
  let factoryRestorer = update.getRestorer();
  // 查询深度恢复出厂策略信息
  factoryRestorer.getDeepFactoryResetInfo(factoryResetStrategy).then((deepResetInfo: update.FactoryResetInfo) => {
    console.info(`getDeepFactoryResetInfo success`);
  }).catch((resetInfoError: BusinessError) => {
    console.error(`getDeepFactoryResetInfo promise error, code:${resetInfoError.code}, message:${resetInfoError.message}.`);
  });
} catch (error) {
  console.error(`Fail to get factoryRestorer: ${error}`);
}

```

