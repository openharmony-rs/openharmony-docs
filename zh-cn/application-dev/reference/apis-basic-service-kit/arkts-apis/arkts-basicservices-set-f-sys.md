# set（系统接口）

## set

```TypeScript
function set(key: string, value: string, callback: AsyncCallback<void>): void
```

设置系统参数Key对应的值，使用callback异步回调。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** set

**系统能力：** SystemCapability.Startup.SystemInfo

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 待设置的系统参数Key。 |
| value | string | 是 | 待设置的系统参数值。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。 |

**示例：**

```TypeScript
import { BusinessError } from '@ohos.base';

try {
  systemParameter.set('test.parameter.key', 'testValue', (err: BusinessError, data: void) => {
    if (err) {
      console.error('set test.parameter.key value err:' + err.code);
    } else {
      console.info('set test.parameter.key value success');
    }
  });
} catch (e) {
  console.error('set unexpected error: ' + e);
}

```


## set

```TypeScript
function set(key: string, value: string): Promise<void>
```

设置系统参数Key对应的值，使用Promise异步回调。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** set

**系统能力：** SystemCapability.Startup.SystemInfo

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 待设置的系统参数Key。 |
| value | string | 是 | 待设置的系统参数值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise示例，用于异步获取结果。 |

**示例：**

```TypeScript
import { BusinessError } from '@ohos.base';

try {
  let setPromise: Promise<void> = systemParameter.set('test.parameter.key', 'testValue');
  setPromise.then((value: void) => {
    console.info('set test.parameter.key success: ' + value);
  }).catch((err: BusinessError) => {
    console.error('set test.parameter.key error: ' + err.code);
  });
} catch (e) {
  console.error('set unexpected error: ' + e);
}

```

