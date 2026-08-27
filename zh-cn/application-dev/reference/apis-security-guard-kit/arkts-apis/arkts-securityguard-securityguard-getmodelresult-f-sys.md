# getModelResult（系统接口）

## 导入模块

```TypeScript
import { securityGuard } from '@kit.SecurityGuardKit';
```

## getModelResult

```TypeScript
function getModelResult(rule: ModelRule): Promise<ModelResult>
```

请求安全模型检测结果。

**起始版本：** 12

**需要权限：** ohos.permission.QUERY_SECURITY_MODEL_RESULT

**系统能力：** SystemCapability.Security.SecurityGuard

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rule | [ModelRule](arkts-securityguard-securityguard-modelrule-i-sys.md) | 是 | 安全模型规则，指定模型名称与参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[ModelResult](arkts-securityguard-securityguard-modelresult-i-sys.md)&gt; | 以Promise形式返回模型结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | check permission fail. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | non-system application uses the system API. |
| [401](../../errorcode-universal.md#401-参数检查失败) | invalid parameters. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
