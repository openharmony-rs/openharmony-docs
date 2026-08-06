# getSlotByBundle（系统接口）

## getSlotByBundle

```TypeScript
function getSlotByBundle(bundle: BundleOption, slotType: SlotType): Promise<NotificationSlot>
```

获取指定应用指定类型的通知渠道。使用Promise异步回调。 获取前需要先通过[addSlot]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_创建通知渠道。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notificationManager-function getSlotByBundle(bundle: BundleOption, slotType: SlotType): Promise<NotificationSlot>--><!--Device-notificationManager-function getSlotByBundle(bundle: BundleOption, slotType: SlotType): Promise<NotificationSlot>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundle | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 指定应用的包信息。 |
| slotType | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 渠道类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;NotificationSlot&gt; | 以Promise形式返回获取指定应用指定类型的通知渠道。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application to call the interface. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 18+ |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-序列化或反序列化错误) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |
| [1600012](../errorcode-notification.md#1600012-内存空间不足) | No memory space. |
| [17700001](../../apis-ability-kit/errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundle name was not found. |


## getSlotByBundle

```TypeScript
function getSlotByBundle(bundle: BundleOption, slotType: SlotType): Promise<NotificationSlot|null>
```

获取指定应用指定类型的通知渠道。使用Promise异步回调。 获取前需要先通过[addSlot]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_创建通知渠道。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**需要权限：** ohos.permission.NOTIFICATION_CONTROLLER

<!--Device-notificationManager-function getSlotByBundle(bundle: BundleOption, slotType: SlotType): Promise<NotificationSlot|null>--><!--Device-notificationManager-function getSlotByBundle(bundle: BundleOption, slotType: SlotType): Promise<NotificationSlot|null>-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundle | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 指定应用的包信息。 |
| slotType | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 渠道类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;NotificationSlot \| null&gt; | 以Promise形式返回获取指定应用指定类型的通知渠道。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application to call the interface. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [1600001](../errorcode-notification.md#1600001-内部错误) | Internal error. |
| [1600002](../errorcode-notification.md#1600002-序列化或反序列化错误) | Marshalling or unmarshalling error. |
| [1600003](../errorcode-notification.md#1600003-连接通知服务失败) | Failed to connect to the service. |
| [1600012](../errorcode-notification.md#1600012-内存空间不足) | No memory space. |
| [17700001](../../apis-ability-kit/errorcode-bundle.md#17700001-指定的bundlename不存在) | The specified bundle name was not found. |

