# setDiscoverable（系统接口）

## setDiscoverable

```TypeScript
function setDiscoverable(enable: boolean, callback: AsyncCallback<void>): void
```

设置设备是否可被发现，用于投播接收端。结果通过callback异步回调方式返回。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-avSession-function setDiscoverable(enable: boolean, callback: AsyncCallback<void>): void--><!--Device-avSession-function setDiscoverable(enable: boolean, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 是否允许本设备被发现。true表示允许被发现，false表示不允许被发现。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | 回调函数。当设置成功，err为undefined，否则返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Parameter verification failed. |

**示例：**

```TypeScript
avSession.setDiscoverable(true, (err) => {
  console.info('setDiscoverable successfully');
});
```


## setDiscoverable

```TypeScript
function setDiscoverable(enable: boolean): Promise<void>
```

设置设备是否可被发现，用于投播接收端。结果通过Promise异步回调方式返回。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-avSession-function setDiscoverable(enable: boolean): Promise<void>--><!--Device-avSession-function setDiscoverable(enable: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.AVCast

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 是否允许本设备被发现。true表示允许被发现，false表示不允许被发现。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | parameter check failed. 1.Mandatory parameters are left unspecified.2.Parameter verification failed. |

**示例：**

```TypeScript
avSession.setDiscoverable(true).then(() => {
  console.info('setDiscoverable successfully');
});
```

