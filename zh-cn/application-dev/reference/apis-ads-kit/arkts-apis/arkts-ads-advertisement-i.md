# Advertisement

本模块为请求的广告内容。

**起始版本：** 11

**系统能力：** SystemCapability.Advertising.Ads

## adType

```TypeScript
adType: number
```

广告类型。

- 1：开屏广告。
- 3：原生广告。
- 7：激励广告。
- 8：横幅广告。
- 12：插屏广告。
- 60：贴片广告。

不填默认为原生广告类型。

**类型：** number

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Advertising.Ads

## clicked

```TypeScript
clicked: boolean
```

广告是否被点击。

- true：被点击。
- false：未被点击。

**类型：** boolean

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Advertising.Ads

## key

```TypeScript
[key:string]: Object
```

自定义参数。

<!--RP1--><!--RP1End-->

**类型：** Object

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Advertising.Ads

## rewardVerifyConfig

```TypeScript
rewardVerifyConfig: Map<string, string>
```

服务器验证参数。

{

customData: "test",

userId: "12345"

}

**类型：** Map<string, string>

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Advertising.Ads

## rewarded

```TypeScript
rewarded: boolean
```

广告是否获得奖励。

- true：获得奖励。
- false：没有获得奖励。

**类型：** boolean

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Advertising.Ads

## shown

```TypeScript
shown: boolean
```

广告是否展示。

- true：展示。
- false：未展示。

**类型：** boolean

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Advertising.Ads

## uniqueId

```TypeScript
uniqueId: string
```

广告唯一标识。

**类型：** string

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Advertising.Ads

