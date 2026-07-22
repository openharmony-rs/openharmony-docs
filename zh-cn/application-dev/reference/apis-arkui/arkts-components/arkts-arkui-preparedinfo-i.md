# PreparedInfo

用于描述当前视频的时长。
> **说明：**  
>  
> 为规范匿名对象的定义，API 18版本修改了此处的元素定义。其中，保留了历史匿名对象的起始版本信息，会出现外层元素@since版本号高于内层元素版本号的情况，但这不影响接口的使用。

**起始版本：** 18

<!--Device-unnamed-interface PreparedInfo--><!--Device-unnamed-interface PreparedInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## duration

```TypeScript
duration: number
```

当前视频的时长。

单位：秒

取值范围：[0,+∞)

**类型：** number

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PreparedInfo-duration: number--><!--Device-PreparedInfo-duration: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

