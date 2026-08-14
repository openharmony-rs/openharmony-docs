# AdOptions

广告配置参数。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

<!--Device-advertising-export interface AdOptions--><!--Device-advertising-export interface AdOptions-End-->

**系统能力：** SystemCapability.Advertising.Ads

## adContentClassification

```TypeScript
adContentClassification?: string
```

设置广告内容分级上限。 W：3+，所有受众。 PI：7+，家长指导。 J：12+，青少年。 A：16+/18+，成人受众。 不填以业务逻辑为准。

**类型：** string

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AdOptions-adContentClassification?: string--><!--Device-AdOptions-adContentClassification?: string-End-->

**系统能力：** SystemCapability.Advertising.Ads

## nonPersonalizedAd

```TypeScript
nonPersonalizedAd?: number
```

设置是否只请求非个性化广告。 0：请求个性化广告与非个性化广告。 1：只请求非个性化广告。 不填以业务逻辑为准。

**类型：** number

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AdOptions-nonPersonalizedAd?: number--><!--Device-AdOptions-nonPersonalizedAd?: number-End-->

**系统能力：** SystemCapability.Advertising.Ads

## tagForChildProtection

```TypeScript
tagForChildProtection?: number
```

是否希望根据 COPPA 的规定将您的内容视为面向儿童的内容。 -1：默认值，不确定。 0：不希望。 1：希望。 默认为-1。

**类型：** number

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AdOptions-tagForChildProtection?: number--><!--Device-AdOptions-tagForChildProtection?: number-End-->

**系统能力：** SystemCapability.Advertising.Ads

