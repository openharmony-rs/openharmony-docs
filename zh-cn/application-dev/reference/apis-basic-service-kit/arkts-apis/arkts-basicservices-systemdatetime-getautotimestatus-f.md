# getAutoTimeStatus

## 导入模块

```TypeScript
import { systemDateTime } from '@kit.BasicServicesKit';
```

<a id="getautotimestatus"></a>
## getAutoTimeStatus

```TypeScript
function getAutoTimeStatus(): boolean
```

获取自动设置时间开关状态，使用同步方式。

**起始版本：** 21

<!--Device-systemDateTime-function getAutoTimeStatus(): boolean--><!--Device-systemDateTime-function getAutoTimeStatus(): boolean-End-->

**系统能力：** SystemCapability.MiscServices.Time

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回自动设置时间开关状态。<br/>- true：表示自动设置时间开关状态为打开。 <br/>- false：表示自动设置时间开关状态为关闭。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [13000001](../../apis-basic-services-kit/errorcode-time.md#13000001-网络或操作系统异常) | Network connection error or OS error. Possible causes: 1.System memory is insufficient; 2.Calls the underlying system interface failed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let status: boolean = systemDateTime.getAutoTimeStatus();
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get autotime status. Code: ${error.code}, message: ${error.message}`);
}

```

