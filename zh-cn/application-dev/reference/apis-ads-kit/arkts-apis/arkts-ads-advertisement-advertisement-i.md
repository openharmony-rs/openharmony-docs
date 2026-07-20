# Advertisement

本模块为请求的广告内容。

**起始版本：** 11

<!--Device-unnamed-export interface Advertisement--><!--Device-unnamed-export interface Advertisement-End-->

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

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Advertisement-adType: number--><!--Device-Advertisement-adType: number-End-->

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

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Advertisement-clicked: boolean--><!--Device-Advertisement-clicked: boolean-End-->

**系统能力：** SystemCapability.Advertising.Ads

## key

```TypeScript
[key:string]: Object
```

自定义参数。

<!--RP1--><!--RP1End-->

**类型：** Object

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Advertisement-[key:string]: Object--><!--Device-Advertisement-[key:string]: Object-End-->

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

**类型：** Map&lt;string, string&gt;

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Advertisement-rewardVerifyConfig: Map<string, string>--><!--Device-Advertisement-rewardVerifyConfig: Map<string, string>-End-->

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

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Advertisement-rewarded: boolean--><!--Device-Advertisement-rewarded: boolean-End-->

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

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Advertisement-shown: boolean--><!--Device-Advertisement-shown: boolean-End-->

**系统能力：** SystemCapability.Advertising.Ads

## uniqueId

```TypeScript
uniqueId: string
```

广告唯一标识。

**类型：** string

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-Advertisement-uniqueId: string--><!--Device-Advertisement-uniqueId: string-End-->

**系统能力：** SystemCapability.Advertising.Ads

