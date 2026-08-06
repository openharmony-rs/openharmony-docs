# setUserProperty

## setUserProperty

```TypeScript
function setUserProperty(name: string, value: string): void
```

设置用户属性值。用于在配置[Processor]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_数据处理者时进行关联。

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-hiAppEvent-function setUserProperty(name: string, value: string): void--><!--Device-hiAppEvent-function setUserProperty(name: string, value: string): void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 用户属性的key。只能包含大小写字母、数字、下划线和 \_\_\_ESCAPED\_DOLLAR\_\_\_，不能以数字开头，长度非空且不超过256个字符。 |
| value | string | 是 | 用户属性的值。长度不超过1024个字符，当值为null或空字符串时，则清除用户属性。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types. |

**示例：**

ArkTS-Dyn示例：

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  hiAppEvent.setUserProperty('key', 'value');
} catch (error) {
  hilog.error(0x0000, 'hiAppEvent', `failed to setUserProperty event, code=${error.code}`);
}
```

ArkTS-Sta示例：

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@ohos.base';

try {
  hiAppEvent.setUserProperty('key', 'value');
} catch (error: BusinessError) {
  hilog.error(0x0000, 'hiAppEvent', `failed to setUserProperty event, code=${error.code}`);
}
```

