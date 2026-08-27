# acquireFormState（系统接口）

## 导入模块

```TypeScript
```

## acquireFormState

```TypeScript
function acquireFormState(want: Want, callback: AsyncCallback<formInfo.FormStateInfo>): void
```

获取卡片状态。使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [acquireFormState](arkts-form-formhost-acquireformstate-f-sys.md)

**需要权限：** ohos.permission.REQUIRE_FORM and ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 查询卡片状态时携带的want信息。需要包含bundle名、ability名、module名、卡片名、卡片规格等。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;formInfo.FormStateInfo&gt; | 是 | 回调函数。当获取卡片状态成功，error为undefined，data为获取到的卡片状态；否则为错误对象。 |

**示例**

```TypeScript
import Want from '@ohos.app.ability.Want';
import formInfo from '@ohos.app.form.formInfo';
import Base from '@ohos.base';

let want: Want = {
  'deviceId': '',
  'bundleName': 'ohos.samples.FormApplication',
  'abilityName': 'FormAbility',
  'parameters': {
    'ohos.extra.param.key.module_name': 'entry',
    'ohos.extra.param.key.form_name': 'widget',
    'ohos.extra.param.key.form_dimension': 2
  }
};
formHost.acquireFormState(want, (error: Base.BusinessError, data: formInfo.FormStateInfo) => {
  if (error.code) {
    console.error(`formHost acquireFormState, error: ${JSON.stringify(error)}`);
  } else {
    console.info(`formHost acquireFormState, data: ${JSON.stringify(data)}`);
  }
});
```


## acquireFormState

```TypeScript
function acquireFormState(want: Want): Promise<formInfo.FormStateInfo>
```

获取卡片状态。使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [acquireFormState](arkts-form-formhost-acquireformstate-f-sys.md)

**需要权限：** ohos.permission.REQUIRE_FORM and ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 查询卡片状态时携带的want信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;formInfo.FormStateInfo & gt; | Promise对象。返回卡片状态。 |

**示例**

```TypeScript
import Want from '@ohos.app.ability.Want';
import formInfo from '@ohos.app.form.formInfo';
import Base from '@ohos.base';

let want: Want = {
  'deviceId': '',
  'bundleName': 'ohos.samples.FormApplication',
  'abilityName': 'FormAbility',
  'parameters': {
    'ohos.extra.param.key.module_name': 'entry',
    'ohos.extra.param.key.form_name': 'widget',
    'ohos.extra.param.key.form_dimension': 2
  }
};
formHost.acquireFormState(want).then((data: formInfo.FormStateInfo) => {
  console.info(`formHost acquireFormState, data: ${JSON.stringify(data)}`);
}).catch((error: Base.BusinessError) => {
  console.error(`formHost acquireFormState, error: ${JSON.stringify(error)}`);
});
```
