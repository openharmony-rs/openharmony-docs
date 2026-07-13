# get（系统接口）

## get

```TypeScript
function get(key: string, callback: AsyncCallback<string>): void
```

获取系统参数Key对应的值，使用callback异步回调。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** get

**系统能力：** SystemCapability.Startup.SystemInfo

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 待查询的系统参数Key。 |
| callback | AsyncCallback&lt;string&gt; | 是 | 回调函数。 |

**示例：**

```TypeScript
import { BusinessError } from '@ohos.base';

try {
  systemParameter.get('const.ohos.apiversion', (err: BusinessError, data: string) => {
    if (err) {
      console.error('get const.ohos.apiversion value err:' + err.code);
    } else {
      console.info('get const.ohos.apiversion value success:' + data);
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

**起始版本：** 6

**废弃版本：** 9

**替代接口：** get

**系统能力：** SystemCapability.Startup.SystemInfo

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 待查询的系统参数Key。 |
| def | string | 是 | 默认值。 |
| callback | AsyncCallback&lt;string&gt; | 是 | 回调函数。 |

**示例：**

```TypeScript
import { BusinessError } from '@ohos.base';

try {
  systemParameter.get('const.ohos.apiversion', 'default', (err: BusinessError, data: string) => {
    if (err) {
      console.error('get const.ohos.apiversion value err:' + err.code);
    } else {
      console.info('get const.ohos.apiversion value success:' + data);
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

获取系统参数Key对应的值，使用Promise异步回调。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** get

**系统能力：** SystemCapability.Startup.SystemInfo

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 待查询的系统参数Key。 |
| def | string | 否 | def为所要获取的系统参数的默认值。 <br> def为可选参数，仅当系统参数不存在时生效。 <br> def可以传undefined或自定义的任意值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise示例，用于异步获取结果。 |

**示例：**

```TypeScript
import { BusinessError } from '@ohos.base';

try {
  let getPromise: Promise<string> = systemParameter.get('const.ohos.apiversion');
  getPromise.then((value: string) => {
    console.info('get const.ohos.apiversion success: ' + value);
  }).catch((err: BusinessError) => {
    console.error('get const.ohos.apiversion error: ' + err.code);
  });
} catch (e) {
  console.error('get unexpected error: ' + e);
}

```

