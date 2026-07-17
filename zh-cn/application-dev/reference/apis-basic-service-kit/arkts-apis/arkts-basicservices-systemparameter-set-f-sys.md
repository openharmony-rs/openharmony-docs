# set（系统接口）

## 导入模块

```TypeScript
import { systemParameter } from '@kit.BasicServicesKit';
```

## set

```TypeScript
function set(key: string, value: string, callback: AsyncCallback<void>): void
```

设置系统参数key对应的值，使用callback异步回调。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** set

<!--Device-systemParameter-function set(key: string, value: string, callback: AsyncCallback<void>): void--><!--Device-systemParameter-function set(key: string, value: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Startup.SystemInfo

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 待设置的系统参数key。 |
| value | string | 是 | 待设置的系统参数值。长度限制请参考[系统参数](../../../../../device-dev/subsystems/subsys-boot-init-sysparam.md)。 |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数，用于异步返回设置结果。当设置成功时，err为undefined；当设置失败时，err为错误对象。 |

**示例：**

```TypeScript
import { BusinessError } from '@ohos.base';

try {
  systemParameter.set('test.parameter.key', 'testValue', (err: BusinessError, data: void) => {
    if (err) {
      console.error(`Failed to set system parameter. Code: ${err.code}, message: ${err.message}`);
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

设置系统参数key对应的值，使用Promise异步回调。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** set

<!--Device-systemParameter-function set(key: string, value: string): Promise<void>--><!--Device-systemParameter-function set(key: string, value: string): Promise<void>-End-->

**系统能力：** SystemCapability.Startup.SystemInfo

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 待设置的系统参数key。 |
| value | string | 是 | 待设置的系统参数值。长度限制请参考[系统参数](../../../../../device-dev/subsystems/subsys-boot-init-sysparam.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise实例，用于异步获取结果。 |

**示例：**

```TypeScript
import { BusinessError } from '@ohos.base';

try {
  let setPromise: Promise<void> = systemParameter.set('test.parameter.key', 'testValue');
  setPromise.then(() => {
    console.info('set test.parameter.key success');
  }).catch((err: BusinessError) => {
    console.error(`Failed to set system parameter. Code: ${err.code}, message: ${err.message}`);
  });
} catch (e) {
  console.error('set unexpected error: ' + e);
}

```

