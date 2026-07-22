# Restorer（系统接口）

提供清除用户数据分区、深度清除用户数据和操作系统分区、同步清除文件密钥等恢复出厂设置功能的工具类。
> **恢复出厂设置流程**：

- 开发者调用getRestorer方法获取Restorer对象。  
- 开发者根据需求选择恢复出厂方式：1. factoryReset：普通恢复出厂，仅清除用户数据分区。2. forceFactoryReset：强制恢复出厂，清除用户数据分区并同步清除文件密钥。3. deepFactoryReset：深度恢复出厂，可通过scope参数指定清除范围：DATA仅清除用户数据分区，DATA_AND_OS同时清除用户数据和操作系统分区。  
- 开发者调用相应的恢复出厂方法执行恢复出厂操作，设备将清除数据并恢复到出厂状态。

选取建议：日常维护场景优先选择factoryReset；涉及敏感数据或设备交接场景选择forceFactoryReset；设备报废或需要物理销毁数据场景选择deepFactoryReset。

**收益说明**：

帮助用户快速解决系统异常、释放存储空间、保护隐私数据，支持设备交接和安全销毁场景，满足不同安全级别的数据清除需求。

**起始版本：** 9

<!--Device-update-export interface Restorer--><!--Device-update-export interface Restorer-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { update } from '@kit.BasicServicesKit';
```

## deepFactoryReset

```TypeScript
deepFactoryReset(factoryResetStrategy: FactoryResetStrategy): Promise<void>
```

通过覆盖等方式，深度清除用户数据分区、操作系统分区，彻底销毁数据，恢复设备出厂状态。调用成功后，系统执行深度恢复出厂流程：根据策略确定清除范围 → 对数据分区执行多次覆盖写入 → 销毁操作系统分区关键数据 → 验证数据销毁完整性 → 设备自动重启恢复到出厂初始状态。深度清除通过物理覆盖方式确保数据无法被任何工具恢复。使用Promise异步回调。

使用场景：设备丢失，需要彻底销毁数据。

**原理说明**：

该方法提供最高安全级别的数据清除。与factoryReset（仅清除数据分区）和forceFactoryReset（清除数据分区和密钥）不同，deepFactoryReset通过多次覆盖写入（如多次写入随机数据）物理销毁数据，防止数据恢复工具提取残留数据。清除范围可配置：DATA仅清除用户数据分区，DATA_AND_OS同时清除用户数据和操作系统分区。

**约束和限制**：

- 数据销毁不可逆，无法通过任何技术手段恢复，执行前必须获得用户明确授权。  
- 需要系统权限ohos.permission.FACTORY_RESET。  
- 深度清除耗时较长(可能数小时)，必须确保设备电量充足(建议电量>50%)。  
- 仅可在Stage模型下使用。  
- 适用于设备报废、高安全销毁等极端场景，不建议普通恢复出厂场景使用。  
- 执行前必须明确告知用户操作后果并获得确认。  
- 建议仅在用户明确确认后执行恢复出厂操作。  
- 必须先调用getDeepFactoryResetInfo查询预计耗时，向用户提示等待时长，确保设备电量充足后再执行深度恢复出厂操作。  
- 执行完成后设备将自动重启恢复到出厂初始状态，应用需提前做好状态保存。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.FACTORY_RESET

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Restorer-deepFactoryReset(factoryResetStrategy: FactoryResetStrategy): Promise<void>--><!--Device-Restorer-deepFactoryReset(factoryResetStrategy: FactoryResetStrategy): Promise<void>-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| factoryResetStrategy | [FactoryResetStrategy](arkts-basicservices-update-factoryresetstrategy-i-sys.md) | 是 | 恢复出厂设置策略(FactoryResetStrategy)，包含scope(重置范围)和strategy(重置策略描述)字段，用于控制恢复出厂设置的范围和方式。scope指定清除范围(DATA仅清除用户数据分区，适用于仅清除数据的场景；DATA_AND_OS同时清除用户数据和操作系统分区，适用于同时清除系统和数据的场景)。strategy为重置操作的自定义描述文本，长度范围[0，64]，单位：字符。有效字符包括字母、数字、下划线、连字符和空格。超出范围或包含无效字符时抛出异常。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。成功时resolve无返回结果，失败时reject返回错误信息。 |

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

清除用户数据分区，删除用户安装的应用、用户文件和个人设置，恢复设备出厂状态。使用callback异步回调。

使用场景：用户选择恢复出厂设置。

**原理说明**：

该方法执行普通恢复出厂流程：验证调用权限 → 清除用户数据分区（删除用户安装的应用、用户文件和个人设置） → 保留系统分区和预置应用 → 清除系统缓存 → 设置恢复出厂标志 → 设备自动重启。清除过程采用快速擦除方式，仅删除数据分区索引和数据文件，不进行深度覆盖。清除范围仅限用户数据分区，不影响系统分区和预置应用。重启后设备恢复到出厂初始状态，用户数据已清空，系统文件完好。

**约束和限制**：

- 操作不可逆，需提醒用户备份重要数据并获得明确确认。  
- 需要系统权限ohos.permission.FACTORY_RESET。  
- 操作过程中设备会自动重启，应用需做好状态保存。  
- 建议仅在用户明确确认后执行恢复出厂操作。

**起始版本：** 9

**需要权限：** ohos.permission.FACTORY_RESET

<!--Device-Restorer-factoryReset(callback: AsyncCallback<void>): void--><!--Device-Restorer-factoryReset(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，用于接收恢复出厂结果。回调参数包括err（错误对象，成功时为null，失败时为错误对象）。 |

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

清除用户数据分区，删除用户安装的应用、用户文件和个人设置，恢复设备出厂状态。使用Promise异步回调。

使用场景：用户选择恢复出厂设置。

**原理说明**：

该方法执行普通恢复出厂流程：验证调用权限 → 清除用户数据分区（删除用户安装的应用、用户文件和个人设置） → 保留系统分区和预置应用 → 清除系统缓存 → 设置恢复出厂标志 → 设备自动重启。清除过程采用快速擦除方式，仅删除数据分区索引和数据文件，不进行深度覆盖。清除范围仅限用户数据分区，不影响系统分区和预置应用。重启后设备恢复到出厂初始状态，用户数据已清空，系统文件完好。

**约束和限制**：

- 操作不可逆，需提醒用户备份重要数据并获得明确确认。  
- 需要系统权限ohos.permission.FACTORY_RESET。  
- 操作过程中设备会自动重启，应用需做好状态保存。  
- 建议仅在用户明确确认后执行恢复出厂操作。

**起始版本：** 9

**需要权限：** ohos.permission.FACTORY_RESET

<!--Device-Restorer-factoryReset(): Promise<void>--><!--Device-Restorer-factoryReset(): Promise<void>-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。成功时resolve无返回结果，失败时reject返回错误信息。 |

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

清除用户数据分区，同步清除文件密钥（系统为用户数据加密生成的密钥，存储在安全存储区域，用于保护用户敏感数据），删除用户安装的应用、用户文件，恢复设备出厂状态。调用成功后，系统立即执行强制恢复出厂流程：清除用户数据分区 → 同步清除文件密钥 → 清除系统缓存和临时文件 → 设备自动重启恢复到出厂初始状态。使用Promise异步回调。

使用场景：需要彻底清除敏感数据、设备交接前清除数据等安全操作。

**原理说明**：

该方法与factoryReset的区别在于同步清除文件密钥。文件密钥是系统为用户数据加密生成的密钥，存储在安全存储区域（如密钥库或专用分区）。密钥作用：对用户数据分区中的个人文件、应用数据、配置信息等进行加密保护。清除影响：同步清除文件密钥后，即使残留的加密数据也无法被解密和恢复，实现更彻底的数据销毁。清除机制：forceFactoryReset不仅删除用户数据分区，还会向密钥管理系统发送清除指令，将密钥从安全存储中彻底删除，确保加密数据完全无法恢复，适用于安全销毁场景。

**约束和限制**：

- 操作不可逆，将永久删除所有用户数据和加密密钥，需提前提醒用户备份重要数据，无法恢复。  
- 需要系统权限ohos.permission.FORCE_FACTORY_RESET。  
- 执行前必须明确提醒用户备份重要数据并确认操作。  
- 建议仅在用户明确确认后执行恢复出厂操作。  
- 适用于敏感数据销毁、设备交接等高安全场景。  
- 操作过程中设备会立即重启，应用需提前做好状态保存。

**起始版本：** 23

**需要权限：** ohos.permission.FORCE_FACTORY_RESET

<!--Device-Restorer-forceFactoryReset(): Promise<void>--><!--Device-Restorer-forceFactoryReset(): Promise<void>-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。成功时resolve无返回结果，失败时reject返回错误信息。 |

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

获取深度恢复出厂设置信息，用于预估恢复操作耗时。调用此方法后，系统根据清除范围（DATA或DATA_AND_OS）和设备存储容量计算深度清除所需时间，返回包含预计持续时间的FactoryResetInfo对象。使用Promise异步回调。

使用场景：执行深度恢复出厂前向用户提示等待时长、规划操作时间、确保电量充足。

**原理说明**：

该方法通过分析清除范围和存储介质特性计算耗时。深度清除通过多次覆盖写入销毁数据，耗时与清除范围成正比：DATA仅清除用户数据分区耗时较短，DATA_AND_OS清除用户数据和操作系统分区耗时较长。系统根据存储容量、覆盖次数、写入速度等因素计算预计时间。

**约束和限制**：

- 仅可在Stage模型下使用。  
- 需要系统权限ohos.permission.FACTORY_RESET。  
- 返回的时间为预估值，实际耗时可能因设备状态略有差异。  
- 当设备电量不足（建议电量高于50%）时，不应执行深度恢复出厂操作，以避免中途断电导致操作失败。  
- 必须在执行deepFactoryReset前调用，帮助用户做好时间和电量准备。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.FACTORY_RESET

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Restorer-getDeepFactoryResetInfo(factoryResetStrategy: FactoryResetStrategy): Promise<FactoryResetInfo>--><!--Device-Restorer-getDeepFactoryResetInfo(factoryResetStrategy: FactoryResetStrategy): Promise<FactoryResetInfo>-End-->

**系统能力：** SystemCapability.Update.UpdateService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| factoryResetStrategy | [FactoryResetStrategy](arkts-basicservices-update-factoryresetstrategy-i-sys.md) | 是 | 恢复出厂设置策略(FactoryResetStrategy)，包含scope(重置范围)和strategy(重置策略描述)字段，用于控制恢复出厂设置的范围和方式。scope指定清除范围(DATA仅清除用户数据分区，适用于仅清除数据的场景；DATA_AND_OS同时清除用户数据和操作系统分区，适用于同时清除系统和数据的场景)。strategy为重置操作的自定义描述文本，长度范围[0，64]，单位：字符。有效字符包括字母、数字、下划线、连字符和空格。超出范围或包含无效字符时抛出异常。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;FactoryResetInfo&gt; | Promise对象。成功时resolve返回深度恢复出厂设置信息对象（FactoryResetInfo），包含预计耗时等；失败时reject返回错误信息。 |

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

