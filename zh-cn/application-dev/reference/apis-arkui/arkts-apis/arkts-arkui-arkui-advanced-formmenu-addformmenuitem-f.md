# AddFormMenuItem

## 导入模块

```TypeScript
import { AddFormMenuItem, FormMenuItemStyle, AddFormOptions } from '@kit.ArkUI';
```

## AddFormMenuItem

```TypeScript
export declare function AddFormMenuItem(
  want: Want,
  componentId: string,
  options?: AddFormOptions
): void
```

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 待发布功能组件的want信息。 |
| componentId | string | 是 | 应用内功能组件ID，组件ID对应的界面与待添加的服务卡片界面相似。 |
| options | [AddFormOptions](arkts-arkui-arkui-advanced-formmenu-addformoptions-i.md) | 否 | 添加卡片选项。 |
