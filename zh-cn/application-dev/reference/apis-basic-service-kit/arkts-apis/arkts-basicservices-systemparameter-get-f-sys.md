# get（系统接口）

## 导入模块

```TypeScript
import { systemParameter } from '@kit.BasicServicesKit';
```

## get

```TypeScript
function get(key: string, callback: AsyncCallback<string>): void
```

获取系统参数key对应的值，使用callback异步回调。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** get

<!--Device-systemParameter-function get(key: string, callback: AsyncCallback<string>): void--><!--Device-systemParameter-function get(key: string, callback: AsyncCallback<string>): void-End-->

**系统能力：** SystemCapability.Startup.SystemInfo

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 待查询的系统参数Key。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | 是 | 回调函数，用于异步返回系统参数值。当获取成功时，err为undefined，data为系统参数值；当获取失败时，err为错误对象，data为undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified;2.incorrect parameter types; 3.parameter verification failed. |
| [14700102](../../apis-basic-services-kit/errorcode-system-parameterV9.md#14700102-系统参数值无效) | Invalid system parameter value. |
| [14700103](../../apis-basic-services-kit/errorcode-device-info.md#14700103-操作因权限被拒绝) | The operation on the system permission is denied. |
| [14700104](../../apis-basic-services-kit/errorcode-system-parameterV9.md#14700104-系统内部错误包括内存不足死锁等) | System internal error such as out memory or deadlock. |

**示例：**

```TypeScript
import { BusinessError } from '@ohos.base';

try {
  systemParameter.get('const.ohos.apiversion', (err: BusinessError, data: string) => {
    if (err) {
      console.error(`Failed to get system parameter. Code: ${err.code}, message: ${err.message}`);
    } else {
      console.info('get const.ohos.apiversion success: ' + data);
    }
  });
} catch (e) {
  console.error('get unexpected error: ' + e);
}

```


## get

```TypeScript
function get(key: string, def: string, callback: AsyncCallback<string>): void
```

获取系统参数key对应的值，使用callback异步回调。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** get

<!--Device-systemParameter-function get(key: string, def: string, callback: AsyncCallback<string>): void--><!--Device-systemParameter-function get(key: string, def: string, callback: AsyncCallback<string>): void-End-->

**系统能力：** SystemCapability.Startup.SystemInfo

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 待查询的系统参数key。 |
| def | string | 是 | def为所要获取的系统参数的默认值。调用时必须传入此参数，但参数值可以传任意字符串类型的值。仅当系统参数不存在时，def参数值生效。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | 是 | 回调函数，用于异步返回系统参数值。当获取成功时，err为undefined，data为系统参数值；当获取失败时，err为错误对象，data为undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified;2.incorrect parameter types; 3.parameter verification failed. |
| [14700102](../../apis-basic-services-kit/errorcode-system-parameterV9.md#14700102-系统参数值无效) | Invalid system parameter value. |
| [14700103](../../apis-basic-services-kit/errorcode-device-info.md#14700103-操作因权限被拒绝) | The operation on the system permission is denied. |
| [14700104](../../apis-basic-services-kit/errorcode-system-parameterV9.md#14700104-系统内部错误包括内存不足死锁等) | System internal error such as out memory or deadlock. |

**示例：**

```TypeScript
import { BusinessError } from '@ohos.base';

try {
  systemParameter.get('const.ohos.apiversion', 'default', (err: BusinessError, data: string) => {
    if (err) {
      console.error(`Failed to get system parameter. Code: ${err.code}, message: ${err.message}`);
    } else {
      console.info('get const.ohos.apiversion success: ' + data);
    }
  });
} catch (e) {
  console.error('get unexpected error: ' + e);
}

```


## get

```TypeScript
function get(key: string, def?: string): Promise<string>
```

获取系统参数key对应的值，使用Promise异步回调。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** get

<!--Device-systemParameter-function get(key: string, def?: string): Promise<string>--><!--Device-systemParameter-function get(key: string, def?: string): Promise<string>-End-->

**系统能力：** SystemCapability.Startup.SystemInfo

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 待查询的系统参数key。 |
| def | string | 否 | def为所要获取的系统参数的默认值。 <br> def为可选参数，仅当系统参数不存在时生效。 <br> def可以传undefined或任意字符串类型的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise示例，用于异步获取结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified;2.incorrect parameter types; 3.parameter verification failed. |
| [14700102](../../apis-basic-services-kit/errorcode-system-parameterV9.md#14700102-系统参数值无效) | Invalid system parameter value. |
| [14700103](../../apis-basic-services-kit/errorcode-device-info.md#14700103-操作因权限被拒绝) | The operation on the system permission is denied. |
| [14700104](../../apis-basic-services-kit/errorcode-system-parameterV9.md#14700104-系统内部错误包括内存不足死锁等) | System internal error such as out memory or deadlock. |

**示例：**

```TypeScript
import { BusinessError } from '@ohos.base';

try {
  let getPromise: Promise<string> = systemParameter.get('const.ohos.apiversion');
  getPromise.then((value: string) => {
    console.info('get const.ohos.apiversion success: ' + value);
  }).catch((err: BusinessError) => {
    console.error(`Failed to get system parameter. Code: ${err.code}, message: ${err.message}`);
  });
} catch (e) {
  console.error('get unexpected error: ' + e);
}

```

