# ComponentInfo

组件大小、位置、平移缩放旋转及仿射矩阵属性信息。

**起始版本：** 10

<!--Device-componentUtils-interface ComponentInfo--><!--Device-componentUtils-interface ComponentInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { componentUtils } from '@kit.ArkUI';
```

## localOffset

```TypeScript
localOffset: Offset
```

组件相对于父组件信息。

**类型：** Offset

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ComponentInfo-localOffset: Offset--><!--Device-ComponentInfo-localOffset: Offset-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## rotate

```TypeScript
rotate: RotateResult
```

组件旋转信息。

**类型：** RotateResult

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ComponentInfo-rotate: RotateResult--><!--Device-ComponentInfo-rotate: RotateResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## scale

```TypeScript
scale: ScaleResult
```

组件缩放信息。

**类型：** ScaleResult

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ComponentInfo-scale: ScaleResult--><!--Device-ComponentInfo-scale: ScaleResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## screenOffset

```TypeScript
screenOffset: Offset
```

组件相对于屏幕信息。

**类型：** Offset

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ComponentInfo-screenOffset: Offset--><!--Device-ComponentInfo-screenOffset: Offset-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size: Size
```

组件大小。

**类型：** Size

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ComponentInfo-size: Size--><!--Device-ComponentInfo-size: Size-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## transform

```TypeScript
transform: Matrix4Result
```

仿射矩阵信息，根据入参创建的四阶矩阵对象。

**类型：** Matrix4Result

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ComponentInfo-transform: Matrix4Result--><!--Device-ComponentInfo-transform: Matrix4Result-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## translate

```TypeScript
translate: TranslateResult
```

组件平移信息。

**类型：** TranslateResult

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ComponentInfo-translate: TranslateResult--><!--Device-ComponentInfo-translate: TranslateResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## windowOffset

```TypeScript
windowOffset: Offset
```

组件相对于窗口信息。

**类型：** Offset

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ComponentInfo-windowOffset: Offset--><!--Device-ComponentInfo-windowOffset: Offset-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

