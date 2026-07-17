# TextMoveUnit

```TypeScript
type TextMoveUnit = 'char' | 'word' | 'line' | 'page' | 'paragraph'
```

文本无障碍导航移动粒度。

**起始版本：** 7

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

<!--Device-accessibility-type TextMoveUnit = 'char' | 'word' | 'line' | 'page' | 'paragraph'--><!--Device-accessibility-type TextMoveUnit = 'char' | 'word' | 'line' | 'page' | 'paragraph'-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

| 类型 | 说明 |
| --- | --- |
| 'char' | 表示以字符为移动粒度遍历节点文本。 |
| 'word' | 表示以词为移动粒度遍历节点文本。 |
| 'line' | 表示以行为移动粒度遍历节点文本。 |
| 'page' | 表示以页为移动粒度遍历节点文本。 |
| 'paragraph' | 表示以段落为移动粒度遍历节点文本。 |

