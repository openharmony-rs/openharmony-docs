# @ohos.arkui.advanced.ChipGroupV2

## 导入模块

```TypeScript
import { ChipGroupV2ItemConfig, ChipGroupV2Item, ChipGroupV2Items, ChipGroupV2ItemStyleConfig, ChipGroupV2ItemStyle, ChipGroupV2SpaceConfig, ChipGroupV2Space, ChipGroupV2IconItemConfig, ChipGroupV2SymbolItemConfig, ChipGroupV2PaddingConfig, ChipGroupV2Padding, ChipGroupV2IconGroupSuffix, ChipGroupV2 } from '@kit.ArkUI';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [ChipGroupV2Item](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2item-c.md) | ChipGroupV2Item定义了ChipGroupV2组件中的单个操作块项。 |
| [ChipGroupV2Items](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2items-c.md) | ChipGroupV2Items定义了ChipGroupV2项的数组类，继承自Array&lt;[ChipGroupV2Item](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2item-c.md)&gt;。 |
| [ChipGroupV2ItemStyle](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2itemstyle-c.md) | ChipGroupV2ItemStyleConfig定义了ChipV2的共通属性配置。 |
| [ChipGroupV2Padding](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2padding-c.md) | ChipGroupV2Padding定义了ChipGroupV2的上下内边距，用于控制其整体高度。 |
| [ChipGroupV2Space](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2space-c.md) | ChipGroupV2Space定义了ChipGroupV2左右内边距，以及ChipV2与ChipV2之间的间距。 |

### 结构体

| 名称 | 说明 |
| --- | --- |
| [ChipGroupV2](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2-s.md) | ChipGroupV2组件提供操作块群组容器，支持单选或多选、自定义样式和间距、以及尾部自定义内容。该组件适用于文件或资源内容的分类、标签选择、筛选等场景，可帮助开发者快速构建美观且交互丰富的标签组界面。 |
| [ChipGroupV2IconGroupSuffix](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2icongroupsuffix-s.md) | ChipGroupV2组件提供操作块群组容器，支持单选或多选、自定义样式和间距、以及尾部自定义内容。该组件适用于文件或资源内容的分类、标签选择、筛选等场景，可帮助开发者快速构建美观且交互丰富的标签组界面。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ChipGroupV2IconItemConfig](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2iconitemconfig-i.md) | ChipGroupV2IconItemConfig定义了尾部图标项的配置，用于设置尾部图标的样式、交互和无障碍属性。 |
| [ChipGroupV2ItemConfig](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2itemconfig-i.md) | ChipGroupV2ItemConfig定义每个ChipV2的非通用属性配置。 |
| [ChipGroupV2ItemStyleConfig](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2itemstyleconfig-i.md) | ChipGroupV2ItemStyleConfig定义了ChipV2的共通属性配置。 |
| [ChipGroupV2PaddingConfig](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2paddingconfig-i.md) | ChipGroupV2PaddingConfig定义了ChipGroupV2的上下内边距配置，用于控制其整体高度。 |
| [ChipGroupV2SpaceConfig](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2spaceconfig-i.md) | ChipGroupV2SpaceConfig定义了ChipGroupV2左右内边距，以及ChipV2与ChipV2之间的间距配置。 |
| [ChipGroupV2SymbolItemConfig](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2symbolitemconfig-i.md) | ChipGroupV2SymbolItemConfig定义了尾部Symbol图标的配置类型。 |

## 示例

```TypeScript
### 示例1（ChipGroupV2无最右侧自定义组件）

该示例通过不设置suffix参数，实现了[ChipGroupV2](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2-s.md)没有最右侧自定义组件时的效果。


```

```TypeScript
### 示例2（ChipGroupV2设置最右侧自定义组件）

该示例通过设置suffix参数，实现了[ChipGroupV2](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2-s.md)最右侧的自定义组件效果。

从API版本26.0.0开始，ChipGroupV2新增suffix属性。


```

```TypeScript
### 示例3（设置Symbol类型图标）

该示例通过[SymbolGlyphModifier](ts-universal-attributes-attribute-symbolglyphmodifier.md#symbolglyphmodifier)实现了[ChipGroupV2IconGroupSuffix](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2icongroupsuffix-s.md)和[ChipGroupV2](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2-s.md)设置Symbol类型图标。

从API版本26.0.0开始，新增ChipGroupV2IconGroupSuffix和ChipGroupV2。


```

```TypeScript
### 示例4（监听ChipGroupV2内对象类型属性的内部属性变化）

[ChipGroupV2Items](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2items-c.md)、[ChipGroupV2Item](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2item-c.md)、[ChipGroupV2ItemStyle](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2itemstyle-c.md)等类使用了@ObservedV2装饰器，ChipGroupV2组件通过@Param接收各属性参数。对于@Trace装饰的基本类型属性（如ChipGroupV2Space的itemSpace等），@Param已能观测到属性变化并触发UI刷新，无需额外处理。但对于这些类中对象类型属性（如ChipGroupV2Item中prefixIcon的size）的内部属性，这些对象类型本身未被@ObservedV2装饰，其内部属性变化无法被@Param感知，导致修改内部属性时UI不会自动刷新。使用makeObserved接口对对象类型属性进行包裹，可以为该对象的内部属性补充深度观察能力。makeObserved接口的详细说明请参考[makeObserved接口：将非观察数据变为可观察数据](../../../ui/state-management/arkts-new-makeObserved.md)。

以下示例对比了两种场景：点击“修改itemSpace间距”按钮修改chipGroupSpace的itemSpace属性（@Trace装饰的基本类型属性，已支持观测），UI自动刷新；点击“修改图标大小”按钮修改ChipGroupV2Item中prefixIcon的size内部属性（对象类型属性的内部属性，需通过UIUtils.makeObserved包裹size才能观测），UI同样自动刷新。


```

```TypeScript
### 示例5（设置系统材质样式）

该示例通过设置[ChipGroupV2ItemStyle](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2itemstyle-c.md)的backgroundSystemMaterial属性，实现了[ChipGroupV2](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2-s.md)的系统材质样式效果，包括沉浸式材质和自动反色功能。组件需放置在Navigation的标题栏中，沉浸光感效果才会生效。

从API版本26.0.0开始，[ChipGroupV2ItemStyle](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2itemstyle-c.md)新增backgroundSystemMaterial属性。
```
