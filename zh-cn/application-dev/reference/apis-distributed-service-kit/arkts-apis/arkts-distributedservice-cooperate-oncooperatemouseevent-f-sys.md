# onCooperateMouseEvent（系统接口）

## 导入模块

```TypeScript
import { cooperate } from '@kit.DistributedServiceKit';
```

## onCooperateMouseEvent

```TypeScript
function onCooperateMouseEvent(networkId: string, callback: Callback<MouseLocation>): void
```

Enables listening for mouse pointer position information on the specified device for cooperation.

**起始版本：** 23

**需要权限：** ohos.permission.COOPERATE_MANAGER

<!--Device-cooperate-function onCooperateMouseEvent(networkId: string, callback: Callback<MouseLocation>): void--><!--Device-cooperate-function onCooperateMouseEvent(networkId: string, callback: Callback<MouseLocation>): void-End-->

**系统能力：** SystemCapability.Msdp.DeviceStatus.Cooperate

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| networkId | string | 是 | Specified device. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[MouseLocation](arkts-distributedservice-cooperate-mouselocation-i-sys.md)&gt; | 是 | Callback for receiving reported events. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified. <br>2. Incorrect parameter types. <br>3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |

**示例**

```TypeScript
function callback(data: cooperate.MouseLocation): void {
  console.info('displayX:' + data.displayX + 'displayY:' + data.displayY + 'displayWidth:' +
    data.displayWidth + 'displayHeight:' + data.displayHeight);
}

try {
  let networkId: string = 'Default';
  cooperate.onCooperateMouseEvent(networkId, callback);
} catch (error) {
  console.error(`Register failed, error: ${JSON.stringify(error, [`code`, `message`])}`);
}
```

