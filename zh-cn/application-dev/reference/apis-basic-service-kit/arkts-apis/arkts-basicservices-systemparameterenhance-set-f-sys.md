# set（系统接口）

## 导入模块

```TypeScript
import { systemParameterEnhance } from '@kit.BasicServicesKit';
```

<a id="set"></a>
## set

```TypeScript
function set(key: string, value: string, callback: AsyncCallback<void>): void
```

设置系统参数key对应的值，使用callback异步回调。

**起始版本：** 9

<!--Device-systemParameterEnhance-function set(key: string, value: string, callback: AsyncCallback<void>): void--><!--Device-systemParameterEnhance-function set(key: string, value: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Startup.SystemInfo

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 待设置的系统参数key。最大长度128字节，只允许字母数字加"."，"-"，"@"，":"或"_"，不允许".."。 |
| value | string | 是 | 待设置的系统参数值。最大长度96字节（包括结束符）。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，异步设置系统参数。成功时err为undefined；失败时err为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified;2.incorrect parameter types; 3.parameter verification failed. |
| [14700102](../../apis-basic-services-kit/errorcode-system-parameterV9.md#14700102-系统参数值无效) | Invalid system parameter value. |
| [14700103](../../apis-basic-services-kit/errorcode-device-info.md#14700103-操作因权限被拒绝) | The operation on the system permission is denied. |
| [14700104](../../apis-basic-services-kit/errorcode-system-parameterV9.md#14700104-系统内部错误包括内存不足死锁等) | System internal error such as out memory or deadlock. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  systemParameterEnhance.set('test.parameter.key', 'testValue', (err: BusinessError, data: void) => {
    if (err) {
      console.error(`Failed to set test.parameter.key value. Code: ${err.code}, message: ${err.message}`);
    } else {
      console.info('set test.parameter.key value success');
    }
  });
} catch (e) {
  console.error('set unexpected error: ' + e);
}

```


<a id="set-1"></a>
## set

```TypeScript
function set(key: string, value: string): Promise<void>
```

设置系统参数key对应的值，使用Promise异步回调。

**起始版本：** 9

<!--Device-systemParameterEnhance-function set(key: string, value: string): Promise<void>--><!--Device-systemParameterEnhance-function set(key: string, value: string): Promise<void>-End-->

**系统能力：** SystemCapability.Startup.SystemInfo

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 待设置的系统参数key。最大长度128字节，只允许字母数字加"."，"-"，"@"，":"或"_"，不允许".."。 |
| value | string | 是 | 待设置的系统参数值。最大长度96字节（包括结束符）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise实例，用于异步获取结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified;2.incorrect parameter types; 3.parameter verification failed. |
| [14700102](../../apis-basic-services-kit/errorcode-system-parameterV9.md#14700102-系统参数值无效) | Invalid system parameter value. |
| [14700103](../../apis-basic-services-kit/errorcode-device-info.md#14700103-操作因权限被拒绝) | The operation on the system permission is denied. |
| [14700104](../../apis-basic-services-kit/errorcode-system-parameterV9.md#14700104-系统内部错误包括内存不足死锁等) | System internal error such as out memory or deadlock. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let promise: Promise<void> = systemParameterEnhance.set('test.parameter.key', 'testValue');
  promise.then((value: void) => {
    console.info('set test.parameter.key success: ' + value);
  }).catch((err: BusinessError) => {
    console.error(`Failed to set test.parameter.key. Code: ${err.code}, message: ${err.message}`);
  });
} catch (e) {
  console.error('set unexpected error: ' + e);
}

```

