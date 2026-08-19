# AlphabetIndexer

可以与容器组件联动，用于按逻辑结构快速定位容器显示区域，适用于通讯录、城市列表、分类列表等需要快速定位内容的场景。 > **说明：** > > > 从API version 12开始，触控反馈默认开启；使用前请按[enableHapticFeedback](#enablehapticfeedback12)的说明配置振动权限。

## 子组件 无

## AlphabetIndexer

```TypeScript
AlphabetIndexer(options: AlphabetIndexerOptions)
```

创建索引条组件。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AlphabetIndexerInterface-(options: AlphabetIndexerOptions): AlphabetIndexerAttribute--><!--Device-AlphabetIndexerInterface-(options: AlphabetIndexerOptions): AlphabetIndexerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [AlphabetIndexerOptions](arkts-arkui-alphabetindexeroptions-i.md) | 是 | 设置索引条组件参数。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [AlphabetIndexerOptions](arkts-arkui-alphabetindexeroptions-i.md) | 用于设置索引条参数。 @since版本号高于内层元素版本号的情况，但这不影响接口的使用。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [OnAlphabetIndexerPopupSelectCallback](arkts-arkui-onalphabetindexerpopupselectcallback-t.md) | 提示弹窗二级索引项被选中时触发的事件。 |
| [OnAlphabetIndexerRequestPopupDataCallback](arkts-arkui-onalphabetindexerrequestpopupdatacallback-t.md) | [usingPopup](arkts-arkui-alphabetindexer-attribute.md#usingpopup)设置值为true，索引项被选中时触发的事件。 |
| [OnAlphabetIndexerSelectCallback](arkts-arkui-onalphabetindexerselectcallback-t.md) | 索引项被选中时触发的事件。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [IndexerAlign](arkts-arkui-indexeralign-e.md) | 索引条提示弹窗的对齐样式枚举。 |

