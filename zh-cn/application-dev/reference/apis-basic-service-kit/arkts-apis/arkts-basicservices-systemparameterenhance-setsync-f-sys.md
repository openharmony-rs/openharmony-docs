# setSync（系统接口）

## 导入模块

```TypeScript
import { systemParameterEnhance } from '@kit.BasicServicesKit';
```

## setSync

```TypeScript
function setSync(key: string, value: string): void
```

设置系统参数key对应的值。

**起始版本：** 9

<!--Device-systemParameterEnhance-function setSync(key: string, value: string): void--><!--Device-systemParameterEnhance-function setSync(key: string, value: string): void-End-->

**系统能力：** SystemCapability.Startup.SystemInfo

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 待设置的系统参数key。最大长度128字节，只允许字母数字加"."，"-"，"@"，":"或"_"，不允许".."。 |
| value | string | 是 | 待设置的系统参数值。最大长度96字节（包括结束符）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified;2.incorrect parameter types; 3.parameter verification failed. |
| [14700102](../../apis-basic-services-kit/errorcode-system-parameterV9.md#14700102-系统参数值无效) | Invalid system parameter value. |
| [14700103](../../apis-basic-services-kit/errorcode-device-info.md#14700103-操作因权限被拒绝) | The operation on the system permission is denied. |
| [14700104](../../apis-basic-services-kit/errorcode-system-parameterV9.md#14700104-系统内部错误包括内存不足死锁等) | System internal error such as out memory or deadlock. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  systemParameterEnhance.setSync('test.parameter.key', 'default');
} catch (e) {
  const err: BusinessError = e as BusinessError;
  console.error(`Failed to set system parameter. Code: ${err.code}, message: ${err.message}`);
}

```

