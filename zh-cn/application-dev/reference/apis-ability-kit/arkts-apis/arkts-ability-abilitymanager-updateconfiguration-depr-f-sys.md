# updateConfiguration（系统接口）

## updateConfiguration

```TypeScript
function updateConfiguration(config: Configuration, callback: AsyncCallback<void>): void
```

通过传入要修改的配置项来更新配置。使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** updateConfiguration

**需要权限：** ohos.permission.UPDATE_CONFIGURATION

<!--Device-abilityManager-function updateConfiguration(config: Configuration, callback: AsyncCallback<void>): void--><!--Device-abilityManager-function updateConfiguration(config: Configuration, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [Configuration](../../apis-arkui/arkts-components/arkts-arkui-common-configuration-i.md) | 是 | 新的配置项。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数，当通过修改配置来更新配置成功，err为undefined，否则为错误对象。 |


## updateConfiguration

```TypeScript
function updateConfiguration(config: Configuration): Promise<void>
```

通过传入要修改的配置项来更新配置。使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** updateConfiguration

**需要权限：** ohos.permission.UPDATE_CONFIGURATION

<!--Device-abilityManager-function updateConfiguration(config: Configuration): Promise<void>--><!--Device-abilityManager-function updateConfiguration(config: Configuration): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [Configuration](../../apis-arkui/arkts-components/arkts-arkui-common-configuration-i.md) | 是 | 新的配置项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象。无返回结果的Promise对象。 |

