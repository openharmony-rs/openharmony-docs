# LoginEvent

```TypeScript
type LoginEvent = (controlType: LoginType, id?: string) => Promise<QrCodeInfo[]>
```

登录事件。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-avMusicTemplate-type LoginEvent = (controlType: LoginType, id?: string) => Promise<QrCodeInfo[]>--><!--Device-avMusicTemplate-type LoginEvent = (controlType: LoginType, id?: string) => Promise<QrCodeInfo[]>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVMusicTemplate

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| controlType | LoginType | 是 | 登录类型。 |
| id | string | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;QrCodeInfo[]&gt; | Promise对象，返回二维码信息的数组。 |

