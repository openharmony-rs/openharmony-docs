# clearUpApplicationData（系统接口）

## clearUpApplicationData

```TypeScript
function clearUpApplicationData(bundleName: string): Promise<void>
```

通过Bundle名称清除应用数据。使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** clearUpApplicationData

**需要权限：** ohos.permission.CLEAN_APPLICATION_DATA

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 表示Bundle名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**示例：**

```TypeScript
import appManager from '@ohos.application.appManager';
import { BusinessError } from '@ohos.base';

let bundleName = 'bundleName';
appManager.clearUpApplicationData(bundleName)
  .then((data) => {
    console.info(`ClearUpApplicationData success, data: ${JSON.stringify(data)}.`);
  })
  .catch((err: BusinessError) => {
    console.error(`ClearUpApplicationData failed, error code: ${err.code}, error msg: ${err.message}.`);
  });

```


## clearUpApplicationData

```TypeScript
function clearUpApplicationData(bundleName: string, callback: AsyncCallback<void>)
```

通过Bundle名称清除应用数据。使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** clearUpApplicationData

**需要权限：** ohos.permission.CLEAN_APPLICATION_DATA

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 表示Bundle名称。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数，当通过Bundle名称清除应用数据成功，err为undefined，否则为错误对象。 |

**示例：**

```TypeScript
import appManager from '@ohos.application.appManager';
import { BusinessError } from '@ohos.base';

let bundleName = 'bundleName';

function clearUpApplicationDataCallback(err: BusinessError, data: void) {
  if (err) {
    console.error(`ClearUpApplicationDataCallback failed, error code: ${err.code}, error msg: ${err.message}.`);
  } else {
    console.info(`ClearUpApplicationDataCallback success, data: ${JSON.stringify(data)}.`);
  }
}

appManager.clearUpApplicationData(bundleName, clearUpApplicationDataCallback);

```

