# onActiveStateChange（系统接口）

## onActiveStateChange

```TypeScript
function onActiveStateChange(
    permissionList: Array<Permissions>,
    callback: Callback<ActiveChangeResponse>): void
```

订阅指定权限列表的权限使用状态变更事件。权限使用状态变更由 [startUsingPermission]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_和 [stopUsingPermission]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_调用触发。订阅成功 后，当权限使用状态变更时，回调函数会被触发，返回[ActiveChangeResponse]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_对象，包含权限使用状态变化的详情。使用 callback异步回调。 允许相同permissionList订阅多个回调函数。 > **说明** > 不允许使用有交集的两个permissionList分别订阅同一个回调函数。即如果两个permissionList包含相同的权限名，则不能使用同一个回调函数进行订阅。 > 该接口通常与[offActiveStateChange]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_配套使用，在不再需要监听时应调用offActiveStateChange取消订阅。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**需要权限：** ohos.permission.PERMISSION_USED_STATS

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-privacyManager-function onActiveStateChange(    permissionList: Array<Permissions>,    callback: Callback<ActiveChangeResponse>): void--><!--Device-privacyManager-function onActiveStateChange(    permissionList: Array<Permissions>,    callback: Callback<ActiveChangeResponse>): void-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| permissionList | Array&lt;Permissions&gt; | 是 | 订阅的权限名列表。为空时表示订阅所有的权限使用状态变化。传入无效值时返回错误码12100001。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_取值约束：数组长度不能超过1024。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;ActiveChangeResponse&gt; | 是 | 回调函数，返回订阅指定权限使用状态变更事件的对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. Interface caller does not have permission"ohos.permission.PERMISSION\_\_\_ESCAPED\_UNDERSCORE\_\_\_USED\_\_\_ESCAPED\_UNDERSCORE\_\_\_STATS". |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system app. Interface caller is not a system app. |
| [12100001](../errorcode-access-token.md#12100001-入参错误) | Invalid parameter. The permissionList exceeds the size limit,or the permissionNames in the list are all invalid. |
| [12100004](../errorcode-access-token.md#12100004-接口未配套使用) | The API is used repeatedly with the same input. |
| [12100005](../errorcode-access-token.md#12100005-监听器数量超过限制) | The registration time has exceeded the limit. |
| [12100007](../errorcode-access-token.md#12100007-系统服务工作异常) | Service exception. |
| [12100008](../errorcode-access-token.md#12100008-内存申请失败) | Out of memory. |

**示例：**

```TypeScript
import { privacyManager, Permissions } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let permissionList: Array<Permissions> = [];
try {
  privacyManager.onActiveStateChange(permissionList, (data: privacyManager.ActiveChangeResponse) => {
    console.debug('receive permission state change');
    console.debug(`data calling tokenId: ${data.callingTokenId}, tokenId: ${data.tokenId}`);
    console.debug(`data permission name: ${data.permissionName}, deviceId: ${data.deviceId}`);
    console.debug(`data active status: ${data.activeStatus}, used type: ${data.usedType}`);
  });
} catch (err) {
    let error = err as BusinessError;
    console.error(`Catch errcode: ${error.code}, message: ${error.message}`);
}
```

