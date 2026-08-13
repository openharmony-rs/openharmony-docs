# getAutoTimeStatus

## getAutoTimeStatus

```TypeScript
function getAutoTimeStatus(): boolean
```

获取自动设置时间开关状态，使用同步方式。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-systemDateTime-function getAutoTimeStatus(): boolean--><!--Device-systemDateTime-function getAutoTimeStatus(): boolean-End-->

**系统能力：** SystemCapability.MiscServices.Time

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回自动设置时间开关状态。&lt;br/&gt;- true：表示自动设置时间开关状态为打开。 &lt;br/&gt;- false：表示自动设置时间开关状态为关闭。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [13000001](../../apis-basic-services-kit/errorcode-time.md#13000001-网络或操作系统异常) | Network connection error or OS error. Possible causes: 1.System memory is insufficient; 2.Calls the underlying system interface failed. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let status: boolean = systemDateTime.getAutoTimeStatus();
} catch(e) {
  let error = e as BusinessError;
  console.error(`Failed to get autotime status. message: ${error.message}, code: ${error.code}`);
}
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let status: boolean = systemDateTime.getAutoTimeStatus();
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get autotime status. Code: ${error.code}, message: ${error.message}`);
}
```

