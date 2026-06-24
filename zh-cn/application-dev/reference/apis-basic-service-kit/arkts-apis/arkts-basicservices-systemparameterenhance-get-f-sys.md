# get（系统接口）

## get

```TypeScript
function get(key: string, callback: AsyncCallback<string>): void
```

获取系统参数Key对应的值，使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Startup.SystemInfo

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 待查询的系统参数Key。最大长度128字节，只允许字母数字加"."，"-"，"@"，":"或"_"，不允许".."。 |
| callback | AsyncCallback&lt;string&gt; | 是 | 回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified;<br/>2.incorrect parameter types; 3.parameter verification failed. |
| [14700101](../../errorcode-universal.md#14700101-System) | System parameter not found. |
| [14700103](../../errorcode-universal.md#14700103-The) | The operation on the system permission is denied. |
| [14700104](../../errorcode-universal.md#14700104-System) | System internal error such as out memory or deadlock. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    systemParameterEnhance.get("const.ohos.apiversion", (err: BusinessError, data: string) => {
    if (err == undefined) {
        console.info("get test.parameter.key value success:" + data)
    } else {
        console.error(" get test.parameter.key value err:" + err.code)
    }});
} catch(e) {
    console.error("get unexpected error: " + e);
}

```


## get

```TypeScript
function get(key: string, def: string, callback: AsyncCallback<string>): void
```

获取系统参数Key对应的值，使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Startup.SystemInfo

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 待查询的系统参数Key。最大长度128字节，只允许字母数字加"."，"-"，"@"，":"或"_"，不允许".."。 |
| def | string | 是 | 默认值。 |
| callback | AsyncCallback&lt;string&gt; | 是 | 回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified;<br/>2.incorrect parameter types; 3.parameter verification failed. |
| [14700101](../../errorcode-universal.md#14700101-System) | System parameter not found. |
| [14700103](../../errorcode-universal.md#14700103-The) | The operation on the system permission is denied. |
| [14700104](../../errorcode-universal.md#14700104-System) | System internal error such as out memory or deadlock. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    systemParameterEnhance.get("const.ohos.apiversion", "default", (err: BusinessError, data: string) => {
        if (err == undefined) {
            console.info("get test.parameter.key value success:" + data)
        } else {
            console.error(" get test.parameter.key value err:" + err.code)
        }
    });
} catch(e) {
    console.error("get unexpected error:" + e)
}

```


## get

```TypeScript
function get(key: string, def?: string): Promise<string>
```

获取系统参数Key对应的值，使用Promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Startup.SystemInfo

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 待查询的系统参数Key。最大长度128字节，只允许字母数字加"."，"-"，"@"，":"或"_"，不允许".."。 |
| def | string | 否 | def为所要获取的系统参数的默认值；<br/>def为可选参数，仅当系统参数不存在时生效；<br/>def可以传undefined或自定义的任意值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise示例，用于异步获取结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified;<br/>2.incorrect parameter types; 3.parameter verification failed. |
| [14700101](../../errorcode-universal.md#14700101-System) | System parameter not found. |
| [14700103](../../errorcode-universal.md#14700103-The) | The operation on the system permission is denied. |
| [14700104](../../errorcode-universal.md#14700104-System) | System internal error such as out memory or deadlock. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let p: Promise<string> = systemParameterEnhance.get("const.ohos.apiversion");
    p.then((value: string) => {
        console.info("get test.parameter.key success: " + value);
    }).catch((err: BusinessError) => {
        console.error("get test.parameter.key error: " + err.code);
    });
} catch(e) {
    console.error("get unexpected error: " + e);
}

```

