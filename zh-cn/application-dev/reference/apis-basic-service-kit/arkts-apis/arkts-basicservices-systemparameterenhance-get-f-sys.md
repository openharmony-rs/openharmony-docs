# get（系统接口）

## 导入模块

```TypeScript
import { systemParameterEnhance } from '@kit.BasicServicesKit';
```

## get

```TypeScript
function get(key: string, callback: AsyncCallback<string>): void
```

获取系统参数key对应的值，使用callback异步回调。

**起始版本：** 9

<!--Device-systemParameterEnhance-function get(key: string, callback: AsyncCallback<string>): void--><!--Device-systemParameterEnhance-function get(key: string, callback: AsyncCallback<string>): void-End-->

**系统能力：** SystemCapability.Startup.SystemInfo

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 待查询的系统参数key。最大长度128字节，只允许字母数字加"."，"-"，"@"，":"或"_"，不允许".."。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)<string> | 是 | 回调函数，异步获取系统参数值。成功时err为undefined，data为系统参数值；失败时err为错误对象，data为undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified;2.incorrect parameter types; 3.parameter verification failed. |
| [14700101](../../apis-basic-services-kit/errorcode-system-parameterV9.md#14700101-系统参数查找失败) | System parameter not found. |
| [14700103](../../apis-basic-services-kit/errorcode-device-info.md#14700103-操作因权限被拒绝) | The operation on the system permission is denied. |
| [14700104](../../apis-basic-services-kit/errorcode-system-parameterV9.md#14700104-系统内部错误包括内存不足死锁等) | System internal error such as out memory or deadlock. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  systemParameterEnhance.get('const.ohos.apiversion', (err: BusinessError, data: string) => {
    if (err) {
      console.error(`Failed to get const.ohos.apiversion value. Code: ${err.code}, message: ${err.message}`);
    } else {
      console.info(`get const.ohos.apiversion value success: ${data}`);
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

获取系统参数Key对应的值，使用callback异步回调。

**起始版本：** 9

<!--Device-systemParameterEnhance-function get(key: string, def: string, callback: AsyncCallback<string>): void--><!--Device-systemParameterEnhance-function get(key: string, def: string, callback: AsyncCallback<string>): void-End-->

**系统能力：** SystemCapability.Startup.SystemInfo

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 待查询的系统参数Key。最大长度128字节，只允许字母数字加"."，"-"，"@"，":"或"_"，不允许".."。 |
| def | string | 是 | def为所要获取的系统参数的默认值，仅当系统参数不存在时生效； <br> def可以传任意字符串值。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)<string> | 是 | 回调函数，异步获取系统参数值。成功时err为undefined，data为系统参数值；失败时err为错误对象，data为undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified;2.incorrect parameter types; 3.parameter verification failed. |
| [14700101](../../apis-basic-services-kit/errorcode-system-parameterV9.md#14700101-系统参数查找失败) | System parameter not found. |
| [14700103](../../apis-basic-services-kit/errorcode-device-info.md#14700103-操作因权限被拒绝) | The operation on the system permission is denied. |
| [14700104](../../apis-basic-services-kit/errorcode-system-parameterV9.md#14700104-系统内部错误包括内存不足死锁等) | System internal error such as out memory or deadlock. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  systemParameterEnhance.get('const.ohos.apiversion', 'default', (err: BusinessError, data: string) => {
    if (err) {
      console.error(`Failed to get const.ohos.apiversion value. Code: ${err.code}, message: ${err.message}`);
    } else {
      console.info(`get const.ohos.apiversion value success: ${data}`);
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

**起始版本：** 9

<!--Device-systemParameterEnhance-function get(key: string, def?: string): Promise<string>--><!--Device-systemParameterEnhance-function get(key: string, def?: string): Promise<string>-End-->

**系统能力：** SystemCapability.Startup.SystemInfo

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 待查询的系统参数key。最大长度128字节，只允许字母数字加"."，"-"，"@"，":"或"_"，不允许".."。 |
| def | string | 否 | def为所要获取的系统参数的默认值； <br> def为可选参数，仅当系统参数不存在时生效； <br> def可以传undefined或任意字符串值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<string> | Promise对象，用于异步获取结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified;2.incorrect parameter types; 3.parameter verification failed. |
| [14700101](../../apis-basic-services-kit/errorcode-system-parameterV9.md#14700101-系统参数查找失败) | System parameter not found. |
| [14700103](../../apis-basic-services-kit/errorcode-device-info.md#14700103-操作因权限被拒绝) | The operation on the system permission is denied. |
| [14700104](../../apis-basic-services-kit/errorcode-system-parameterV9.md#14700104-系统内部错误包括内存不足死锁等) | System internal error such as out memory or deadlock. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let promise: Promise<string> = systemParameterEnhance.get('const.ohos.apiversion');
  promise.then((value: string) => {
    console.info('get const.ohos.apiversion success: ' + value);
  }).catch((err: BusinessError) => {
    console.error(`Failed to get const.ohos.apiversion. Code: ${err.code}, message: ${err.message}`);
  });
} catch (e) {
  console.error('get unexpected error: ' + e);
}

```

