# queryBusinessAbilityInfo（系统接口）

## queryBusinessAbilityInfo

```TypeScript
function queryBusinessAbilityInfo(
    filter: BusinessAbilityFilter,
    callback: AsyncCallback<Array<BusinessAbilityInfo>>
  ): void
```

通过给定的过滤条件查询Ability信息。使用callback异步回调，成功时返回查询到的路由Ability信息，失败时返回错误信息。

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

<!--Device-businessAbilityRouter-function queryBusinessAbilityInfo(    filter: BusinessAbilityFilter,    callback: AsyncCallback<Array<BusinessAbilityInfo>>  ): void--><!--Device-businessAbilityRouter-function queryBusinessAbilityInfo(    filter: BusinessAbilityFilter,    callback: AsyncCallback<Array<BusinessAbilityInfo>>  ): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filter | [BusinessAbilityFilter](arkts-ability-businessabilityrouter-businessabilityfilter-i-sys.md) | 是 | 用于按业务类型过滤的对象。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;Array&lt;BusinessAbilityInfo&gt;&gt; | 是 | 回调函数。返回查询到的Ability信息，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | non-system app called system api. |

## 示例

```TypeScript
import { businessAbilityRouter } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let filter: businessAbilityRouter.BusinessAbilityFilter = { businessType: businessAbilityRouter.BusinessType.SHARE };

try {
  businessAbilityRouter.queryBusinessAbilityInfo(filter, (error, data) => {
    if (error) {
      console.error('queryBusinessAbilityInfo failed ' + error.message);
      return;
    }
    console.info('queryBusinessAbilityInfo success');
  });
} catch (error) {
  let message = (error as BusinessError).message;
  console.error('queryBusinessAbilityInfo failed ' + message);
}
```


## queryBusinessAbilityInfo

```TypeScript
function queryBusinessAbilityInfo(filter: BusinessAbilityFilter): Promise<Array<BusinessAbilityInfo>>
```

通过给定的过滤条件查询Ability信息。使用Promise异步回调，成功时返回查询到的路由Ability信息，失败时返回错误信息。

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

<!--Device-businessAbilityRouter-function queryBusinessAbilityInfo(filter: BusinessAbilityFilter): Promise<Array<BusinessAbilityInfo>>--><!--Device-businessAbilityRouter-function queryBusinessAbilityInfo(filter: BusinessAbilityFilter): Promise<Array<BusinessAbilityInfo>>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filter | [BusinessAbilityFilter](arkts-ability-businessabilityrouter-businessabilityfilter-i-sys.md) | 是 | 包含要查询的Ability信息的筛选类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;BusinessAbilityInfo&gt;&gt; | Promise对象，返回符合过滤条件的Ability信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | non-system app called system api. |

## 示例

```TypeScript
import { businessAbilityRouter } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let filter: businessAbilityRouter.BusinessAbilityFilter = { businessType: businessAbilityRouter.BusinessType.SHARE };

try {
  businessAbilityRouter.queryBusinessAbilityInfo(filter)
    .then(() => {
      console.info('queryBusinessAbilityInfo success');
    }).catch((error: BusinessError) => {
    console.error('queryBusinessAbilityInfo failed ' + error.message);
  });
} catch (error) {
  let message = (error as BusinessError).message;
  console.error('queryBusinessAbilityInfo failed ' + message);
}
```

