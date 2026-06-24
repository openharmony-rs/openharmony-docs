# isInSandbox

## isInSandbox

```TypeScript
function isInSandbox(): Promise<boolean>
```

查询当前应用是否运行在DLP沙箱环境。使用Promise异步回调。

该接口用于判断当前应用是否处于DLP沙箱环境，以便决定是否执行沙箱相关的操作或调用沙箱专用接口。

**起始版本：** 10

**系统能力：** SystemCapability.Security.DataLossPrevention

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示当前应用运行在沙箱中，返回false表示当前应用不是运行在沙箱中。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [19100001](../../errorcode-universal.md#19100001-Invalid) | Invalid parameter value. |
| [19100011](../../errorcode-universal.md#19100011-The) | The system ability works abnormally. |

**示例：**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';

dlpPermission.isInSandbox().then((isInSandbox) => { // 是否在沙箱内。
  console.info('isInSandbox', isInSandbox);
}).catch((error: BusinessError)=> {
  console.error(JSON.stringify(error));
});

```


## isInSandbox

```TypeScript
function isInSandbox(callback: AsyncCallback<boolean>): void
```

查询当前应用是否运行在DLP沙箱环境。使用callback异步回调。

该接口用于判断当前应用是否处于DLP沙箱环境，以便决定是否执行沙箱相关的操作或调用沙箱专用接口。

**起始版本：** 10

**系统能力：** SystemCapability.Security.DataLossPrevention

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;boolean&gt; | 是 | 回调函数。err为undefined时表示查询成功；否则为错误对象。返回true表示当前应用运行在沙箱中，返回false表示当前应用不是<br/>运行在沙箱中。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Incorrect parameter types. |
| [19100001](../../errorcode-universal.md#19100001-Invalid) | Invalid parameter value. |
| [19100011](../../errorcode-universal.md#19100011-The) | The system ability works abnormally. |

**示例：**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';

dlpPermission.isInSandbox((err, isInSandbox) => {
  if (err) {
    console.error('isInSandbox error', err.code, err.message);
  } else {
    console.info('isInSandbox：', JSON.stringify(isInSandbox));
  }
}); // 是否在沙箱内。

```

