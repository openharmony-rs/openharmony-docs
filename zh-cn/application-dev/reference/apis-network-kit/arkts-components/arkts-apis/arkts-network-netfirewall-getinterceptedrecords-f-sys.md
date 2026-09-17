# getInterceptedRecords（系统接口）

## 导入模块

```TypeScript
import { netFirewall } from '@kit.NetworkKit';
```

## getInterceptedRecords

```TypeScript
function getInterceptedRecords(userId: number, requestParam: RequestParam): Promise<InterceptedRecordPage>
```

按userId获取截获的记录，需要指定分页查询参数。

**起始版本：** 14

**需要权限：** ohos.permission.GET_NET_FIREWALL

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userId | number | 是 | Indicates the user ID. It cannot be the ID of a user that does not exist. |
| requestParam | [RequestParam](arkts-network-netfirewall-requestparam-i.md) | 是 | Paging query input parameters. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[InterceptedRecordPage](arkts-network-netfirewall-interceptedrecordpage-i-sys.md)&gt; | Block Record List. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2100001](../errorcode-net-connection.md#2100001-非法参数值) | Invalid parameter value. |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Operation failed. Cannot connect to service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |
| [29400000](../errorcode-net-netfirewall.md#29400000-指定用户不存在) | The specified user does not exist. |

**示例**

```TypeScript
import { netFirewall } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let interceptRecordParam: netFirewall.RequestParam = {
  page: 1,
  pageSize: 10,
  orderField: netFirewall.NetFirewallOrderField.ORDER_BY_RECORD_TIME,
  orderType: netFirewall.NetFirewallOrderType.ORDER_DESC
};
netFirewall.getInterceptedRecords(100, interceptRecordParam).then((result: netFirewall.InterceptedRecordPage) => {
  console.info("result:", JSON.stringify(result));
}, (error: BusinessError) => {
  console.error("get intercept records failed: " + JSON.stringify(error));
});
```
