# offActiveStateChange（系统接口）

## offActiveStateChange

```TypeScript
function offActiveStateChange(
    permissionList: Array<Permissions>,
    callback?: Callback<ActiveChangeResponse>): void
```

取消订阅指定权限列表的权限使用状态变更事件。取消订阅成功后，将不再接收指定权限列表的状态变更通知。 取消订阅时，若不传入回调函数，则批量删除permissionList下的所有回调函数。 > **说明：**> 该接口通常与on配套使用，用于取消通过on创建的监听关系。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.PERMISSION_USED_STATS

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-privacyManager-function offActiveStateChange(    permissionList: Array<Permissions>,    callback?: Callback<ActiveChangeResponse>): void--><!--Device-privacyManager-function offActiveStateChange(    permissionList: Array<Permissions>,    callback?: Callback<ActiveChangeResponse>): void-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| permissionList | Array&lt;Permissions&gt; | 是 | 取消订阅的权限名列表，为空时表示取消订阅所有的权限状态变化，必须与on的输入一致。 &lt;br&gt;取值约束：数组长度不能超过1024。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[ActiveChangeResponse](arkts-ability-privacymanager-activechangeresponse-i-sys.md)&gt; | 否 | 回调函数，返回取消订阅指定tokenId与指定权限名状态变更事件的对象。需与 on 传入的callback一致；不传入此参数时，将批量删除permissionList下的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12100008](../errorcode-access-token.md#12100008-内存申请失败) | Out of memory. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. Interface caller does not have permission "ohos.permission.PERMISSION_USED_STATS". |
| [12100001](../errorcode-access-token.md#12100001-入参错误) | Invalid parameter. The permissionList is not in the listening list. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system app. Interface caller is not a system app. |
| [12100004](../errorcode-access-token.md#12100004-接口未配套使用) | The API is not used in pair with 'on'. |
| [12100007](../errorcode-access-token.md#12100007-系统服务工作异常) | Service exception. |

## 示例

```TypeScript
import { privacyManager, Permissions } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let permissionList: Array<Permissions> = [];
try {
    privacyManager.offActiveStateChange(permissionList);
} catch (err) {
    let error = err as BusinessError;
    console.error(`Catch errcode: ${error.code}, message: ${error.message}`);
}
```

