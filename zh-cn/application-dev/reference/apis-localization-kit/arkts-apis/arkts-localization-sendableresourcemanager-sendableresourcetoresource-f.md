# sendableResourceToResource

## sendableResourceToResource

```TypeScript
export function sendableResourceToResource(resource: SendableResource): Resource
```

将跨线程传输的SendableResource对象转换为Resource对象。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-sendableResourceManager-export function sendableResourceToResource(resource: SendableResource): Resource--><!--Device-sendableResourceManager-export function sendableResourceToResource(resource: SendableResource): Resource-End-->

**系统能力：** SystemCapability.Global.ResourceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resource | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | SendableResource对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 转换后的Resource对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1.Incorrect parameter types;2.Parameter verification failed. |

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
    let resource: sendableResourceManager.Resource = sendableResourceManager.sendableResourceToResource(sendableResourceManager.resourceToSendableResource($r('app.string.test')));
} catch (error) {
    let code = (error as BusinessError).code;
    let message = (error as BusinessError).message;
    console.error(`sendableResourceToResource failed, error code: ${code}, message: ${message}.`);
}
```

