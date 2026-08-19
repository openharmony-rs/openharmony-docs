# isCleartextPermitted

## 导入模块

```TypeScript
import { networkSecurity } from '@kit.NetworkKit';
```

## isCleartextPermitted

```TypeScript
export function isCleartextPermitted(): boolean
```

从应用预置network_config.json文件中获取整体明文HTTP是否允许信息，默认允许明文HTTP访问。

**起始版本：** 23

**需要权限：** ohos.permission.INTERNET

<!--Device-networkSecurity-export function isCleartextPermitted(): boolean--><!--Device-networkSecurity-export function isCleartextPermitted(): boolean-End-->

**系统能力：** SystemCapability.Communication.NetStack

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 整体明文HTTP是否允许。返回true表示允许访问明文HTTP，false表示不允许。默认返回true。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例**

```TypeScript
import { networkSecurity } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let result: boolean = networkSecurity.isCleartextPermitted();
  console.info(`isCleartextPermitted Result: ${JSON.stringify(result)}`);
} catch (error) {
  let businessError = error as BusinessError;
  console.error(`isCleartextPermitted Error: ${JSON.stringify(businessError)}`);
}
```

