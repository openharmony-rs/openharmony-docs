# FormCallbackInfo(系统接口)（系统接口）

卡片查询或者卸载时获取formId的参数。

**起始版本：** 12

<!--Device-unnamed-interface FormCallbackInfo--><!--Device-unnamed-interface FormCallbackInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
```

## id

```TypeScript
id: number
```

卡片标识。 **说明：** 如果获取到的id为-1，说明id大于等于2^53，需要使用idString获取。

**类型：** number

**起始版本：** 12

<!--Device-FormCallbackInfo-id: number--><!--Device-FormCallbackInfo-id: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## idString

```TypeScript
idString: string
```

卡片标识。

**类型：** string

**起始版本：** 12

<!--Device-FormCallbackInfo-idString: string--><!--Device-FormCallbackInfo-idString: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## isLocked

```TypeScript
isLocked: boolean
```

表示卡片是否被锁定，true表示卡片被锁定，false表示卡片没有被锁定。

**类型：** boolean

**起始版本：** 22

<!--Device-FormCallbackInfo-isLocked: boolean--><!--Device-FormCallbackInfo-isLocked: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

