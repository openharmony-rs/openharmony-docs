# startCastDeviceDiscovery（系统接口）

## startCastDeviceDiscovery

```TypeScript
function startCastDeviceDiscovery(callback: AsyncCallback<void>): void
```

开始设备搜索发现。结果通过callback异步回调方式返回。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-avSession-function startCastDeviceDiscovery(callback: AsyncCallback<void>): void--><!--Device-avSession-function startCastDeviceDiscovery(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | 回调函数。当命令发送成功并开始搜索，err为undefined，否则返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |

**示例：**

```TypeScript
avSession.startCastDeviceDiscovery(() => {
    console.info('Succeeded in starting cast device discovery.');
});
```


## startCastDeviceDiscovery

```TypeScript
function startCastDeviceDiscovery(filter: int, callback: AsyncCallback<void>): void
```

指定过滤条件，开始设备搜索发现。结果通过callback异步回调方式返回。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-avSession-function startCastDeviceDiscovery(filter: int, callback: AsyncCallback<void>): void--><!--Device-avSession-function startCastDeviceDiscovery(filter: int, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filter | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 进行设备发现的过滤条件，由ProtocolType组合而成。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | 回调函数。当命令发送成功并开始搜索，err为undefined，否则返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Parameter verification failed. |

**示例：**

```TypeScript
let filter = 2;
avSession.startCastDeviceDiscovery(filter, (err) => {
  console.info('startCastDeviceDiscovery successfully');
});
```


## startCastDeviceDiscovery

```TypeScript
function startCastDeviceDiscovery(filter?: int, drmSchemes?: Array<string>): Promise<void>
```

开始设备搜索发现。结果通过Promise异步回调方式返回。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-avSession-function startCastDeviceDiscovery(filter?: int, drmSchemes?: Array<string>): Promise<void>--><!--Device-avSession-function startCastDeviceDiscovery(filter?: int, drmSchemes?: Array<string>): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filter | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 否 | 进行设备发现的过滤条件，由ProtocolType组合而成。\_\_\_HTML\_TAG\_USD\_0\_\_\_**起始版本：** 12 |
| drmSchemes | Array&lt;string&gt; | 否 | 进行支持DRM资源播放的设备发现的过滤条件，由DRM uuid组合而成。 \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_从API version 12开始支持该可选参数。\_\_\_HTML\_TAG\_USD\_0\_\_\_**起始版本：** 12 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。当命令发送成功并开始搜索，无返回结果，否则返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Incorrect parameter types. 3.Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |

**示例：**

```TypeScript
let filter = 2;
let drmSchemes = ['3d5e6d35-9b9a-41e8-b843-dd3c6e72c42c'];
avSession.startCastDeviceDiscovery(filter, drmSchemes).then(() => {
  console.info('startCastDeviceDiscovery successfully');
});
```

