# updateConfiguration（系统接口）

## 导入模块

```TypeScript
```

## updateConfiguration

```TypeScript
function updateConfiguration(config: Configuration, callback: AsyncCallback<void>): void
```

通过传入要修改的配置项来更新配置。使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [updateConfiguration](arkts-ability-abilitymanager-updateconfiguration-f-sys.md)

**需要权限：** ohos.permission.UPDATE_CONFIGURATION

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [Configuration](arkts-ability-application-configuration-configuration-depr-i.md) | 是 | 新的配置项。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，当通过修改配置来更新配置成功，err为undefined，否则为错误对象。 |

**示例**

```TypeScript
import abilityManager from '@ohos.application.abilityManager';
import { Configuration } from '@ohos.application.Configuration';
import { BusinessError } from '@ohos.base';

let config: Configuration = {
  language: 'chinese' 
};

// 更新配置项
abilityManager.updateConfiguration(config, (err: BusinessError) => {
  if (err) {
    console.error(`updateConfiguration fail, error code: ${err.code}, error msg: ${err.message}.`);
    return;
  }
  console.info('------------ updateConfiguration success-----------');
});
```


## updateConfiguration

```TypeScript
function updateConfiguration(config: Configuration): Promise<void>
```

通过传入要修改的配置项来更新配置。使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [updateConfiguration](arkts-ability-abilitymanager-updateconfiguration-f-sys.md)

**需要权限：** ohos.permission.UPDATE_CONFIGURATION

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [Configuration](arkts-ability-application-configuration-configuration-depr-i.md) | 是 | 新的配置项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象。无返回结果的Promise对象。 |

**示例**

```TypeScript
import abilityManager from '@ohos.application.abilityManager';
import { Configuration } from '@ohos.application.Configuration';
import { BusinessError } from '@ohos.base';

let config: Configuration = {
  language: 'chinese' 
};

// 更新配置信息
abilityManager.updateConfiguration(config).then(() => {
  console.info('updateConfiguration success');
}).catch((err: BusinessError) => {
  console.error('updateConfiguration fail');
});
```
