# resetOAID（系统接口）

## 导入模块

```TypeScript
import { identifier } from '@kit.AdsKit';
```

<a id="resetoaid"></a>
## resetOAID

```TypeScript
function resetOAID(): void
```

重置开放匿名设备标识符（OAID）。

**起始版本：** 10

<!--Device-identifier-function resetOAID(): void--><!--Device-identifier-function resetOAID(): void-End-->

**系统能力：** SystemCapability.Advertising.OAID

**系统接口：** 此接口为系统接口。

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [17300001](../errorcode-oaid.md#17300001-系统内部错误) | System internal error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 12+ |
| 17300002 | Not in the trust list.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { identifier } from '@kit.AdsKit';

identifier.resetOAID();

```

