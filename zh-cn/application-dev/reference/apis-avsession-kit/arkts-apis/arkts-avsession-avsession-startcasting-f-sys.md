# startCasting（系统接口）

## startCasting

```TypeScript
function startCasting(session: SessionToken, device: OutputDeviceInfo, callback: AsyncCallback<void>): void
```

启动投播。结果通过callback异步回调方式返回。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.MANAGE_MEDIA_RESOURCES

<!--Device-avSession-function startCasting(session: SessionToken, device: OutputDeviceInfo, callback: AsyncCallback<void>): void--><!--Device-avSession-function startCasting(session: SessionToken, device: OutputDeviceInfo, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| session | [SessionToken](arkts-avsession-avsession-sessiontoken-i-sys.md) | 是 | 会话令牌。SessionToken表示单个token。 |
| device | [OutputDeviceInfo](arkts-avsession-avsession-outputdeviceinfo-i.md) | 是 | 设备相关信息。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当命令发送成功并启动投播，err为undefined，否则返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |
| [6600108](../errorcode-avsession.md#6600108-设备连接失败) | Device connecting failed |
| [201](../../errorcode-universal.md#201-权限校验失败) | permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |


## startCasting

```TypeScript
function startCasting(session: SessionToken, device: OutputDeviceInfo): Promise<void>
```

启动投播。结果通过Promise异步回调方式返回。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.MANAGE_MEDIA_RESOURCES

<!--Device-avSession-function startCasting(session: SessionToken, device: OutputDeviceInfo): Promise<void>--><!--Device-avSession-function startCasting(session: SessionToken, device: OutputDeviceInfo): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| session | [SessionToken](arkts-avsession-avsession-sessiontoken-i-sys.md) | 是 | 会话令牌。SessionToken表示单个token。 |
| device | [OutputDeviceInfo](arkts-avsession-avsession-outputdeviceinfo-i.md) | 是 | 设备相关信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。当命令发送成功并启动投播，无返回结果，否则返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | parameter check failed. 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [6600101](../errorcode-avsession.md#6600101-会话服务端异常) | Session service exception |
| [6600108](../errorcode-avsession.md#6600108-设备连接失败) | Device connecting failed |
| [201](../../errorcode-universal.md#201-权限校验失败) | permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |

## 示例

```TypeScript
let myToken: avSession.SessionToken = {
  sessionId: sessionId,
}
let castDevice: avSession.OutputDeviceInfo | undefined = undefined;
avSession.on('deviceAvailable', (device: avSession.OutputDeviceInfo) => {
  castDevice = device;
  console.info(`on deviceAvailable  : ${device} `);
  if (castDevice !== undefined) {
    avSession.startCasting(myToken, castDevice, () => {
        console.info('Succeeded in starting casting.');
    });
  }
});
```

