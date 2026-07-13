# resourceToSendableResource

## resourceToSendableResource

```TypeScript
export function resourceToSendableResource(resource: Resource): SendableResource
```

将Resource对象转换为SendableResource对象。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resource | Resource | 是 | Resource对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| SendableResource | 转换后的SendableResource对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: 1.Incorrect parameter types;2.Parameter verification failed. |

**示例：**

```TypeScript
// 资源文件路径: src/main/resources/base/element/string.json
{
  "string": [
    {
      "name": "test",
      "value": "I'm a test string resource."
    }
  ]
}

```

```TypeScript
import { sendableResourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let sendableResource: sendableResourceManager.SendableResource = sendableResourceManager.resourceToSendableResource($r('app.string.test'));
} catch (error) {
    let code = (error as BusinessError).code;
    let message = (error as BusinessError).message;
    console.error(`resourceToSendableResource failed, error code: ${code}, message: ${message}.`);
}

```

