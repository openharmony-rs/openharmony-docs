# onDeviceOffline（系统接口）

## onDeviceOffline

```TypeScript
function onDeviceOffline(callback: Callback<string>): void
```

Register device offline callback

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-avSession-function onDeviceOffline(callback: Callback<string>): void--><!--Device-avSession-function onDeviceOffline(callback: Callback<string>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;string&gt; | 是 | Used to returns the device info |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |

## 示例

```TypeScript
let castDeviceId: string;
avSession.onDeviceOffline((deviceId: string) => {
  castDeviceId = deviceId;
  console.info(`onDeviceOffline  : ${deviceId} `);
});
```

