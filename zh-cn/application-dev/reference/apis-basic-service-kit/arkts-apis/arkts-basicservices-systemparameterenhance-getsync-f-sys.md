# getSync（系统接口）

## 导入模块

```TypeScript
import { systemParameterEnhance } from '@kit.BasicServicesKit';
```

## getSync

```TypeScript
function getSync(key: string, def?: string): string
```

获取系统参数key对应的值。

**起始版本：** 9

<!--Device-systemParameterEnhance-function getSync(key: string, def?: string): string--><!--Device-systemParameterEnhance-function getSync(key: string, def?: string): string-End-->

**系统能力：** SystemCapability.Startup.SystemInfo

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 待查询的系统参数key。最大长度128字节，只允许字母数字加"."，"-"，"@"，":"或"_"，不允许".."。 |
| def | string | 否 | def为所要获取的系统参数的默认值； <br> def为可选参数，仅当系统参数不存在时生效； <br> def可以传undefined或任意字符串值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 系统参数值。<br> 若key存在,返回设定的值。<br> 若key不存在且未指定def或def为undefined，抛异常。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified;2.incorrect parameter types; 3.parameter verification failed. |
| [14700101](../../apis-basic-services-kit/errorcode-system-parameterV9.md#14700101-系统参数查找失败) | System parameter not found. |
| [14700103](../../apis-basic-services-kit/errorcode-device-info.md#14700103-操作因权限被拒绝) | The operation on the system permission is denied. |
| [14700104](../../apis-basic-services-kit/errorcode-system-parameterV9.md#14700104-系统内部错误包括内存不足死锁等) | System internal error such as out memory or deadlock. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let info: string = systemParameterEnhance.getSync('const.ohos.apiversion');
  console.info('getSync result: ' + info);
} catch (e) {
  console.error(`getSync failed. Code: ${(e as BusinessError).code}, message: ${(e as BusinessError).message}`);
}

```

