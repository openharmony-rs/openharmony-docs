# set（系统接口）

## set

```TypeScript
function set(key: string, value: string, callback: AsyncCallback<void>): void
```

设置系统参数Key对应的值，使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Startup.SystemInfo

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 待设置的系统参数Key。最大长度128字节，只允许字母数字加"."，"-"，"@"，":"或"_"，不允许".."。 |
| value | string | 是 | 待设置的系统参数值。最大长度96字节（包括结束符）。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified;<br/>2.incorrect parameter types; 3.parameter verification failed. |
| [14700102](../../errorcode-universal.md#14700102-Invalid) | Invalid system parameter value. |
| [14700103](../../errorcode-universal.md#14700103-The) | The operation on the system permission is denied. |
| [14700104](../../errorcode-universal.md#14700104-System) | System internal error such as out memory or deadlock. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    systemParameterEnhance.set("test.parameter.key", "testValue", (err: BusinessError, data: void) => {
    if (err == undefined) {
        console.info("set test.parameter.key value success :" + data)
    } else {
        console.error("set test.parameter.key value err:" + err.code)
    }});
} catch(e) {
    console.error("set unexpected error: " + e);
}

```


## set

```TypeScript
function set(key: string, value: string): Promise<void>
```

设置系统参数Key对应的值，使用Promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Startup.SystemInfo

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 待设置的系统参数Key。最大长度128字节，只允许字母数字加"."，"-"，"@"，":"或"_"，不允许".."。 |
| value | string | 是 | 待设置的系统参数值。最大长度96字节（包括结束符）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise示例，用于异步获取结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified;<br/>2.incorrect parameter types; 3.parameter verification failed. |
| [14700102](../../errorcode-universal.md#14700102-Invalid) | Invalid system parameter value. |
| [14700103](../../errorcode-universal.md#14700103-The) | The operation on the system permission is denied. |
| [14700104](../../errorcode-universal.md#14700104-System) | System internal error such as out memory or deadlock. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let p: Promise<void>  = systemParameterEnhance.set("test.parameter.key", "testValue");
    p.then((value: void) => {
        console.info("set test.parameter.key success: " + value);
    }).catch((err: BusinessError) => {
        console.error(" set test.parameter.key error: " + err.code);
    });
} catch(e) {
    console.error("set unexpected error: " + e);
}

```

