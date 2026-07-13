# GridColColumnOption

用于自定义指定在不同宽度设备类型上，栅格子组件占据的栅格数量单位。

- API version 20之前，仅配置部分断点下GridCol组件所占列数，取已配置的更小断点的列数补全未配置的列数。若未配置更小断点的列数，取默认值1。
<!--code_no_check-->
```ts
span: {xs:2, md:4, lg:8} // 等于配置 span: {xs:2, sm:2, md:4, lg:8, xl:8, xxl:8}
span: {md:4, lg:8} // 等于配置 span: {xs:1, sm:1, md:4, lg:8, xl:8, xxl:8}
```
- API version 20及以后，仅配置部分断点下GridCol组件所占列数，取已配置的更小断点的列数补全未配置的列数。若未配置更小断点的列数，取已配置的更大断点的列数补全未配置的列数。
<!--code_no_check-->
```ts
span: {xs:2, md:4, lg:8} // 等于配置 span: {xs:2, sm:2, md:4, lg:8, xl:8, xxl:8}
span: {md:4, lg:8} // 等于配置 span: {xs:4, sm:4, md:4, lg:8, xl:8, xxl:8}
```
- 建议手动配置不同断点下GridCol组件所占列数，避免默认补全列数的布局效果不符合预期。

**起始版本：** 9

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## lg

```TypeScript
lg?: number
```

在栅格大小为lg的设备上，栅格容器组件的栅格列数。

**类型：** number

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## md

```TypeScript
md?: number
```

在栅格大小为md的设备上，栅格容器组件的栅格列数。

**类型：** number

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## sm

```TypeScript
sm?: number
```

在栅格大小为sm的设备上，栅格容器组件的栅格列数。

**类型：** number

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## xl

```TypeScript
xl?: number
```

在栅格大小为xl的设备上，栅格容器组件的栅格列数。

**类型：** number

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## xs

```TypeScript
xs?: number
```

在栅格大小为xs的设备上，栅格容器组件的栅格列数。

**类型：** number

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## xxl

```TypeScript
xxl?: number
```

在栅格大小为xxl的设备上，栅格容器组件的栅格列数。

**类型：** number

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

