# insertData

## insertData

```TypeScript
function insertData(options: Options, data: UnifiedData, callback: AsyncCallback<string>): void
```

将数据写入UDMF的公共数据通路中，并生成数据的唯一标识符，使用callback异步回调。 **实现机制：** 系统接收UnifiedData对象后，验证数据完整性并序列化存储。根据intention值路由到对应存储空间，生成唯一标识符key。数据在公共数据通路中由系统管理有效期，默认策略为应用退出后自动清理。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-unifiedDataChannel-function insertData(options: Options, data: UnifiedData, callback: AsyncCallback<string>): void--><!--Device-unifiedDataChannel-function insertData(options: Options, data: UnifiedData, callback: AsyncCallback<string>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | Options | 是 | 配置项参数，参数中intention字段必填，且不支持DRAG，不填时会返回401错误码；其他字段是否填写均不影响接口的使用。 |
| data | UnifiedData | 是 | 要写入或更新的统一数据对象，用于存储数据记录及其属性信息。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;string&gt; | 是 | 回调函数，返回写入UDMF的数据的唯一标识符key的值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; &lt;br&gt;2.Incorrect parameter types; &lt;br&gt;3. Parameter verification failed. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { uniformDataStruct, uniformTypeDescriptor } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

let plainText: uniformDataStruct.PlainText = {
  uniformDataType: 'general.plain-text',
  textContent: 'This is a plain text example',
  abstract: 'This is abstract'
};
let text = new unifiedDataChannel.UnifiedRecord(uniformTypeDescriptor.UniformDataType.PLAIN_TEXT, plainText);
let unifiedData = new unifiedDataChannel.UnifiedData(text);

let options: unifiedDataChannel.Options = {
  intention: unifiedDataChannel.Intention.DATA_HUB
};
try {
  unifiedDataChannel.insertData(options, unifiedData, (err, key) => {
    if (err === undefined) {
      console.info(`Succeeded in inserting data. key = ${key}`);
    } else {
      console.error(`Failed to insert data. code is ${err.code}, message is ${err.message} `);
    }
  });
} catch (e) {
  let error: BusinessError = e as BusinessError;
  console.error(`Insert data throws an exception. code is ${error.code}, message is ${error.message}`);
}
```

ArkTS-Sta示例：

```TypeScript
import { uniformDataStruct, uniformTypeDescriptor } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

let plainText: uniformDataStruct.PlainText = {
  uniformDataType: 'general.plain-text',
  textContent: 'This is a plain text example',
  textAbstract: 'This is a text abstract'
}
let text = new unifiedDataChannel.UnifiedRecord(uniformTypeDescriptor.UniformDataType.PLAIN_TEXT, plainText);
let unifiedData = new unifiedDataChannel.UnifiedData(text);

let options: unifiedDataChannel.Options = {
  intention: unifiedDataChannel.Intention.DATA_HUB
}
try {
  unifiedDataChannel.insertData(options, unifiedData, (err, key) => {
    console.info(`Succeeded in inserting data. key = ${key}`);
  });
} catch (e) {
  let error: BusinessError = e as BusinessError;
  console.error(`Insert data throws an exception. code is ${error.code}, message is ${error.message} `);
}
```


## insertData

```TypeScript
function insertData(options: Options, data: UnifiedData): Promise<string>
```

将数据写入UDMF的公共数据通路中，并生成数据的唯一标识符，使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-unifiedDataChannel-function insertData(options: Options, data: UnifiedData): Promise<string>--><!--Device-unifiedDataChannel-function insertData(options: Options, data: UnifiedData): Promise<string>-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | Options | 是 | 配置项参数，参数中intention字段必填，且不支持DRAG，不填时会返回401错误码；其他字段是否填写均不影响接口的使用。 |
| data | UnifiedData | 是 | 要写入或更新的统一数据对象，用于存储数据记录及其属性信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回写入UDMF的数据的唯一标识符key的值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; &lt;br&gt;2.Incorrect parameter types; &lt;br&gt;3. Parameter verification failed. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { uniformDataStruct, uniformTypeDescriptor } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

let plainText: uniformDataStruct.PlainText = {
  uniformDataType: 'general.plain-text',
  textContent: 'This is a plain text example',
  abstract: 'This is abstract'
};
let text = new unifiedDataChannel.UnifiedRecord(uniformTypeDescriptor.UniformDataType.PLAIN_TEXT, plainText);
let unifiedData = new unifiedDataChannel.UnifiedData(text);

let options: unifiedDataChannel.Options = {
  intention: unifiedDataChannel.Intention.DATA_HUB
};
try {
  unifiedDataChannel.insertData(options, unifiedData).then((key) => {
    console.info(`Succeeded in inserting data. key = ${key}`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to insert data. code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  let error: BusinessError = e as BusinessError;
  console.error(`Insert data throws an exception. code is ${error.code}, message is ${error.message}`);
}
```

ArkTS-Sta示例：

```TypeScript
let options: unifiedDataChannel.Options = {
  intention: unifiedDataChannel.Intention.DATA_HUB
};
let plainTextDetails: Record<string, string> = {
  'attr1': 'value1',
  'attr2': 'value2',
}
let plainText: uniformDataStruct.PlainText = {
  uniformDataType: 'general.plain-text',
  textContent: 'This is plainText textContent example',
  textAbstract: 'This is a text abstract',
  details: plainTextDetails,
}

let text = new unifiedDataChannel.UnifiedRecord(uniformTypeDescriptor.UniformDataType.PLAIN_TEXT, plainText);
let unifiedData = new unifiedDataChannel.UnifiedData(text);
try {
  unifiedDataChannel.insertData(options, unifiedData).then((key) => {
    console.info(`Succeeded in inserting data. key = ${key}`);
  }).catch((err: Error) => {
    const error = err as BusinessError;
    console.error(`Failed to insert data. code is ${err.code}, message is ${err.message} `);
  });
} catch (err) {
  const error = err as BusinessError;
  console.error(`Insert data throws an exception. code is ${error.code}, message is ${error.message} `);
  console.error(' error: ' + JSON.stringify(error));
}
```

