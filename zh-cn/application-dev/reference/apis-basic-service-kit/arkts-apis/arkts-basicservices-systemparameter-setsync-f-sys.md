# setSync（系统接口）

## 导入模块

```TypeScript
import { systemParameter } from '@kit.BasicServicesKit';
```

<a id="setsync"></a>
## setSync

```TypeScript
function setSync(key: string, value: string): void
```

设置系统参数key对应的值。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** etSync

<!--Device-systemParameter-function setSync(key: string, value: string): void--><!--Device-systemParameter-function setSync(key: string, value: string): void-End-->

**系统能力：** SystemCapability.Startup.SystemInfo

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 待设置的系统参数key。 |
| value | string | 是 | 待设置的系统参数值。长度限制请参考[系统参数](docroot://../device-dev/subsystems/subsys-boot-init-sysparam.md)。 |

**示例：**

```TypeScript
import { BusinessError } from '@ohos.base';

try {
  systemParameter.setSync('test.parameter.key', 'default');
} catch (e) {
  console.error(`Failed to set system parameter. Code: ${(e as BusinessError).code}, message: ${(e as BusinessError).message}`);
}

```

