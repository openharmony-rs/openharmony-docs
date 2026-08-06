# DisposedRuleConfiguration（系统接口）

标识批量设置拦截规则的配置。

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

<!--Device-appControl-export interface DisposedRuleConfiguration--><!--Device-appControl-export interface DisposedRuleConfiguration-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.AppControl

**系统接口：** 此接口为系统接口。

## appId

```TypeScript
appId: string
```

要被设置拦截规则应用的appId或appIdentifier。appId和appIdentifier可以标识同一个应用，因此针对同一应用如果用appIdentifier设置拦截规则，可以覆盖之前采用appId设置的，反之同理。 **说明：** appId是应用的唯一标识，由应用Bundle名称和签名信息决定，获取方法参见 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_。 [appIdentifier]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_也是应用的唯一标识，详情信息可参考 \_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_，获取方法参见 \_\_\_MD\_LINK\_DESC\_USD\_2\_\_\_。

**类型：** string

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

<!--Device-DisposedRuleConfiguration-appId: string--><!--Device-DisposedRuleConfiguration-appId: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.AppControl

**系统接口：** 此接口为系统接口。

## appIndex

```TypeScript
appIndex: int
```

表示分身应用的索引，默认值为0。 appIndex为0时，表示设置主应用的拦截规则。appIndex大于0时，表示设置指定分身应用的拦截规则。

**类型：** int

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

<!--Device-DisposedRuleConfiguration-appIndex: int--><!--Device-DisposedRuleConfiguration-appIndex: int-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.AppControl

**系统接口：** 此接口为系统接口。

## disposedRule

```TypeScript
disposedRule: DisposedRule
```

表示对应用的拦截规则，包括拦截时将拉起能力的类型等。

**类型：** DisposedRule

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

<!--Device-DisposedRuleConfiguration-disposedRule: DisposedRule--><!--Device-DisposedRuleConfiguration-disposedRule: DisposedRule-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.AppControl

**系统接口：** 此接口为系统接口。

