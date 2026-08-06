# updateData

## updateData

```TypeScript
function updateData(options: Options, data: UnifiedData, callback: AsyncCallback<void>): void
```

更新已写入UDMF的公共数据通路的数据，使用callback异步回调。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-unifiedDataChannel-function updateData(options: Options, data: UnifiedData, callback: AsyncCallback<void>): void--><!--Device-unifiedDataChannel-function updateData(options: Options, data: UnifiedData, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 配置项参数，参数中key字段必填，不填时会返回401错误码；intention参数仅支持DATA\_\_\_ESCAPED\_UNDERSCORE\_\_\_HUB；其他字段是否填写均不影响接口的使用。 |
| data | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 目标数据。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | 回调函数。当更新数据成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2.Incorrect parameter types;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_3. Parameter verification failed. |

**示例：**

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
    let updateOptions: unifiedDataChannel.Options = {
      intention: unifiedDataChannel.Intention.DATA_HUB,
      key: key
    };
    let plainTextUpdate: uniformDataStruct.PlainText = {
      uniformDataType: 'general.plain-text',
      textContent: 'This is plainText textContent for update',
      abstract: 'This is abstract for update'
    };
    let textUpdate =
      new unifiedDataChannel.UnifiedRecord(uniformTypeDescriptor.UniformDataType.PLAIN_TEXT, plainTextUpdate);
    let unifiedDataUpdate = new unifiedDataChannel.UnifiedData(textUpdate);
    try {
      unifiedDataChannel.updateData(updateOptions, unifiedDataUpdate, (err) => {
        if (err === undefined) {
          console.info('Succeeded in updating data.');
        } else {
          console.error(`Failed to update data. code is ${err.code}, message is ${err.message}`);
        }
      });
    } catch (e) {
      let error: BusinessError = e as BusinessError;
      console.error(`Update data throws an exception. code is ${error.code}, message is ${error.message}`);
    }
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
    let updateOptions: unifiedDataChannel.Options = {
      intention: unifiedDataChannel.Intention.DATA_HUB,
      key: key
    }
    let plainTextUpdate: uniformDataStruct.PlainText = {
      uniformDataType: 'general.plain-text',
      textContent: 'This is plainText textContent for update',
      textAbstract: 'This is a text abstract'
    }
    let textUpdate =
      new unifiedDataChannel.UnifiedRecord(uniformTypeDescriptor.UniformDataType.PLAIN_TEXT, plainTextUpdate);
    let unifiedDataUpdate = new unifiedDataChannel.UnifiedData(textUpdate);
    try {
      unifiedDataChannel.updateData(updateOptions, unifiedDataUpdate, (err) => {
        console.info('Succeeded in updating data.');
      });
    } catch (e) {
      let error: BusinessError = e as BusinessError;
      console.error(`Update data throws an exception. code is ${error.code}, message is ${error.message} `);
    }
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


## updateData

```TypeScript
function updateData(options: Options, data: UnifiedData): Promise<void>
```

更新已写入UDMF的公共数据通路的数据，使用Promise异步回调。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-unifiedDataChannel-function updateData(options: Options, data: UnifiedData): Promise<void>--><!--Device-unifiedDataChannel-function updateData(options: Options, data: UnifiedData): Promise<void>-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 配置项参数，参数中key字段必填，不填时会返回401错误码；intention参数仅支持DATA\_\_\_ESCAPED\_UNDERSCORE\_\_\_HUB；其他字段是否填写均不影响接口的使用。 |
| data | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 目标数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2.Incorrect parameter types;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_3. Parameter verification failed. |

**示例：**

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
    let updateOptions: unifiedDataChannel.Options = {
      intention: unifiedDataChannel.Intention.DATA_HUB,
      key: key
    };
    let plainTextUpdate: uniformDataStruct.PlainText = {
      uniformDataType: 'general.plain-text',
      textContent: 'This is plainText textContent for update',
      abstract: 'This is abstract for update'
    };
    let textUpdate =
      new unifiedDataChannel.UnifiedRecord(uniformTypeDescriptor.UniformDataType.PLAIN_TEXT, plainTextUpdate);
    let unifiedDataUpdate = new unifiedDataChannel.UnifiedData(textUpdate);
    try {
      unifiedDataChannel.updateData(updateOptions, unifiedDataUpdate).then(() => {
        console.info('Succeeded in updating data.');
      }).catch((err: BusinessError) => {
        console.error(`Failed to update data. code is ${err.code}, message is ${err.message} `);
      });
    } catch (e) {
      let error: BusinessError = e as BusinessError;
      console.error(`Update data throws an exception. code is ${error.code}, message is ${error.message} `);
    }
  }).catch((err: BusinessError) => {
    console.error(`Failed to insert data. code is ${err.code}, message is ${err.message} `);
  });
} catch (e) {
  let error: BusinessError = e as BusinessError;
  console.error(`Insert data throws an exception. code is ${error.code}, message is ${error.message} `);
}
```

ArkTS-Sta示例：

```TypeScript
let insertDataptions: unifiedDataChannel.Options = {
  intention: unifiedDataChannel.Intention.DATA_HUB
};
let plainTextDetails: Record<string, string> = {
  'attr1': 'value1',
  'attr2': 'value2',
}
let insertDataPlainText: uniformDataStruct.PlainText = {
  uniformDataType: 'general.plain-text',
  textContent: 'This is plainText textContent example',
  textAbstract: 'This is a text abstract',
  details: plainTextDetails,
}
let text = new unifiedDataChannel.UnifiedRecord(uniformTypeDescriptor.UniformDataType.PLAIN_TEXT, insertDataPlainText);
let insertDataUnifiedData = new unifiedDataChannel.UnifiedData(text);

const updateOptions: unifiedDataChannel.Options = {
  intention: unifiedDataChannel.Intention.DATA_HUB,
  visibility: unifiedDataChannel.Visibility.ALL
};
const plainTextUpdate = new unifiedDataChannel.PlainText();
plainTextUpdate.textContent = 'hello world!';
const unifiedDataUpdate = new unifiedDataChannel.UnifiedData(plainTextUpdate);
try {
  unifiedDataChannel.insertData(insertDataptions, insertDataUnifiedData).then((key) => {
    console.info(`insertData success, key=${key}`);
    unifiedDataChannel.updateData({ visibility: updateOptions.visibility, key }, unifiedDataUpdate)
      .then(() => {
        console.info(`updateData success`);
      })
      .catch((updateErr) => {
        console.error(`updateData fail: ${JSON.stringify(updateErr)}`);
      });
  }).catch((err) => {
    let error: BusinessError = err as BusinessError;
    console.error(`Failed to insert data. code is ${error.code}, message is ${error.message} `);
  });
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error(`Insert data throws an exception. code is ${error.code}, message is ${error.message} `);
  console.error(' error: ' + JSON.stringify(error));
}
```

