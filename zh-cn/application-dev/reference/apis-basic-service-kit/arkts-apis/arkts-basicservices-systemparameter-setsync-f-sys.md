# setSync（系统接口）

## 导入模块

```TypeScript
import { systemParameter } from '@kit.BasicServicesKit';
```

## setSync

```TypeScript
function setSync(key: string, value: string): void
```

设置系统参数key对应的值。
> **说明：**  
>  
> setSync和set方法都用于设置系统参数值：  
> - setSync：同步方法，直接设置系统参数并立即返回，适用于简单同步场景。  
> - set：异步方法，使用callback或Promise异步返回结果，适用于需要异步处理的场景。  
>  
> 开发者应根据具体场景选择合适的方法。

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
| value | string | 是 | 待设置的系统参数值。长度限制请参考[系统参数](../../../../device-dev/subsystems/subsys-boot-init-sysparam.md)。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified;2.incorrect parameter types; 3.parameter verification failed. |
| [14700102](../../apis-basic-services-kit/errorcode-system-parameterV9.md#14700102-系统参数值无效) | Invalid system parameter value. |
| [14700103](../../apis-basic-services-kit/errorcode-device-info.md#14700103-操作因权限被拒绝) | The operation on the system permission is denied. |
| [14700104](../../apis-basic-services-kit/errorcode-system-parameterV9.md#14700104-系统内部错误包括内存不足死锁等) | System internal error such as out memory or deadlock. |

**示例：**

```TypeScript
import { BusinessError } from '@ohos.base';

try {
  systemParameter.setSync('test.parameter.key', 'default');
} catch (e) {
  console.error(`Failed to set system parameter. Code: ${(e as BusinessError).code}, message: ${(e as BusinessError).message}`);
}

```

