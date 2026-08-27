# MenuAlignParams

下拉按钮与下拉菜单间的对齐方式设置项。

**起始版本：** 18

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AtomicServiceSearch, InputFilterParams, SearchButtonParams, MenuAlignParams, SearchParams, SelectParams, OperationParams, } from '@kit.ArkUI';
```

## alignType

```TypeScript
alignType: MenuAlignType
```

对齐方式类型。默认值：`MenuAlignType.START`。

**类型：** [MenuAlignType](../arkts-components/arkts-arkui-menualigntype-e.md)

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset?: Offset
```

按照对齐类型对齐后，下拉菜单相对下拉按钮的偏移量。默认值：`{dx: 0, dy: 0}`。

**类型：** Offset

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
