# resetOAID（系统接口）

## resetOAID

```TypeScript
function resetOAID(): void
```

重置开放匿名设备标识符（OAID）。

**起始版本：** 10

**系统能力：** SystemCapability.Advertising.OAID

**系统接口：** 此接口为系统接口。

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17300001](../../errorcode-universal.md#17300001-System) | System internal error. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system<br/>API.&lt;br&gt;**适用版本：** 12+ |
| [17300002](../../errorcode-universal.md#17300002-Not) | Not in the trust list.&lt;br&gt;**适用版本：** 12+ |

**示例：**

```TypeScript
import { identifier } from '@kit.AdsKit';

identifier.resetOAID();

```

