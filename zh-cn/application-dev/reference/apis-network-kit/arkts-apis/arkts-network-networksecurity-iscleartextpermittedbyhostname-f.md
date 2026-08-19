# isCleartextPermittedByHostName

## 导入模块

```TypeScript
import { networkSecurity } from '@kit.NetworkKit';
```

## isCleartextPermittedByHostName

```TypeScript
export function isCleartextPermittedByHostName(hostName: string): boolean
```

从应用预置network_config.json文件中获取按域名明文HTTP是否允许信息，默认允许明文HTTP访问。

**起始版本：** 23

**需要权限：** ohos.permission.INTERNET

<!--Device-networkSecurity-export function isCleartextPermittedByHostName(hostName: string): boolean--><!--Device-networkSecurity-export function isCleartextPermittedByHostName(hostName: string): boolean-End-->

**系统能力：** SystemCapability.Communication.NetStack

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hostName | string | 是 | 需要查询的主机名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 按域名明文HTTP是否允许。返回true表示允许明文HTTP访问该主机，false表示不允许。默认返回true。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例**

```TypeScript
import { networkSecurity } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let result: boolean = networkSecurity.isCleartextPermittedByHostName("xxx");
  console.info(`isCleartextPermitted Result: ${JSON.stringify(result)}`);
} catch (error) {
  let businessError = error as BusinessError;
  console.error(`isCleartextPermitted Error: ${JSON.stringify(businessError)}`);
}
```

