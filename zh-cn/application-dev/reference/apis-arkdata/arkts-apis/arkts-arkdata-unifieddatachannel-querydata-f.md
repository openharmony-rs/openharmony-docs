# queryData

## 导入模块

```TypeScript
import { unifiedDataChannel } from '@kit.ArkData';
```

<a id="querydata"></a>
## queryData

```TypeScript
function queryData(options: Options, callback: AsyncCallback<Array<UnifiedData>>): void
```

查询UDMF公共数据通路的数据，使用callback异步回调。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-unifiedDataChannel-function queryData(options: Options, callback: AsyncCallback<Array<UnifiedData>>): void--><!--Device-unifiedDataChannel-function queryData(options: Options, callback: AsyncCallback<Array<UnifiedData>>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [Options](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-zlib-options-i.md) | 是 | 配置项参数，key和intention均为可选，且intention参数不支持DRAG，根据传入的参数做相应的校验以返回不同的值。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;UnifiedData&gt;&gt; | 是 | 回调函数，返回查询到的所有数据。<br>如果options中填入的是key，则返回key对应的数据；<br>如果options中填入的是intention，则返回intention下所有数据。<br>如intention和key均填写了，取两者查询数据的交集，与options只填入key的获取结果一致；如没有交集报错。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types;<br>3. Parameter verification failed. |

**示例：**

```TypeScript
import { uniformDataStruct, uniformTypeDescriptor } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

let options: unifiedDataChannel.Options = {
  intention: unifiedDataChannel.Intention.DATA_HUB
};

try {
  unifiedDataChannel.queryData(options, (err, data) => {
    if (err === undefined) {
      console.info(`Succeeded in querying data. size = ${data.length}`);
      for (let i = 0; i < data.length; i++) {
        let records = data[i].getRecords();
        for (let j = 0; j < records.length; j++) {
          if (records[j].getTypes().includes(uniformTypeDescriptor.UniformDataType.PLAIN_TEXT)) {
            let text =
              records[j].getEntry(uniformTypeDescriptor.UniformDataType.PLAIN_TEXT) as uniformDataStruct.PlainText;
            console.info(`${i + 1}.${text.textContent}`);
          }
        }
      }
    } else {
      console.error(`Failed to query data. code is ${err.code}, message is ${err.message}`);
    }
  });
} catch (e) {
  let error: BusinessError = e as BusinessError;
  console.error(`Query data throws an exception. code is ${error.code}, message is ${error.message}`);
}

```


<a id="querydata-1"></a>
## queryData

```TypeScript
function queryData(options: Options): Promise<Array<UnifiedData>>
```

查询UDMF公共数据通路的数据，使用Promise异步回调。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-unifiedDataChannel-function queryData(options: Options): Promise<Array<UnifiedData>>--><!--Device-unifiedDataChannel-function queryData(options: Options): Promise<Array<UnifiedData>>-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [Options](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-zlib-options-i.md) | 是 | 配置项参数，key和intention均为可选，且intention参数不支持DRAG，根据传入的参数做相应的校验以返回不同的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;UnifiedData&gt;&gt; | Promise对象，返回查询到的所有数据。<br>如果options中填入的是key，则返回key对应的数据。<br>如果options中填入的是intention，则返回intention下所有数据。<br>如intention和key均填写了，取两者查询数据的交集，与options只填入key的获取结果一致；如没有交集报错。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types;<br>3. Parameter verification failed. |

**示例：**

```TypeScript
import { uniformDataStruct, uniformTypeDescriptor } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

let options: unifiedDataChannel.Options = {
  key: 'udmf://DataHub/com.ohos.test/0123456789'
};

try {
  unifiedDataChannel.queryData(options).then((data) => {
    console.info(`Succeeded in querying data. size = ${data.length}`);
    for (let i = 0; i < data.length; i++) {
      let records = data[i].getRecords();
      for (let j = 0; j < records.length; j++) {
        if (records[j].getTypes().includes(uniformTypeDescriptor.UniformDataType.PLAIN_TEXT)) {
          let text =
            records[j].getEntry(uniformTypeDescriptor.UniformDataType.PLAIN_TEXT) as uniformDataStruct.PlainText;
          console.info(`${i + 1}.${text.textContent}`);
        }
      }
    }
  }).catch((err: BusinessError) => {
    console.error(`Failed to query data. code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  let error: BusinessError = e as BusinessError;
  console.error(`Query data throws an exception. code is ${error.code}, message is ${error.message}`);
}

```

