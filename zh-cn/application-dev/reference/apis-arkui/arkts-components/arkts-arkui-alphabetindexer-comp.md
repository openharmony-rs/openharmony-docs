# AlphabetIndexer

可以与容器组件联动，用于按逻辑结构快速定位容器显示区域，适用于通讯录、城市列表、分类列表等需要快速定位内容的场景。

> **说明：** > > > 从API version 12开始，触控反馈默认开启；使用前请按[enableHapticFeedback](arkts-arkui-alphabetindexer-comp-attribute.md#enablehapticfeedback)的说明配置振动权限。

## 子组件

无

## AlphabetIndexer

```TypeScript
AlphabetIndexer(options: AlphabetIndexerOptions)
```

创建索引条组件。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [AlphabetIndexerOptions](arkts-arkui-alphabetindexeroptions-i.md) | 是 | 设置索引条组件参数。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [AlphabetIndexerOptions](arkts-arkui-alphabetindexeroptions-i.md) | 用于设置索引条参数。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [OnAlphabetIndexerPopupSelectCallback](arkts-arkui-onalphabetindexerpopupselectcallback-t.md) | 提示弹窗二级索引项被选中时触发的事件。 |
| [OnAlphabetIndexerRequestPopupDataCallback](arkts-arkui-onalphabetindexerrequestpopupdatacallback-t.md) | [usingPopup](arkts-arkui-alphabetindexer-comp-attribute.md#usingpopup)设置值为true，索引项被选中时触发的事件。 |
| [OnAlphabetIndexerSelectCallback](arkts-arkui-onalphabetindexerselectcallback-t.md) | 索引项被选中时触发的事件。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [IndexerAlign](arkts-arkui-indexeralign-e.md) | 索引条提示弹窗的对齐样式枚举。 |

## 示例

```TypeScript
### 示例1（设置提示弹窗显示文本内容）

通过[onRequestPopupData](arkts-arkui-alphabetindexer-comp-attribute.md#onrequestpopupdata)事件自定义提示弹窗显示文本内容。


```

```TypeScript
### 示例2（开启自适应折叠模式）

通过[autoCollapse](#autocollapse11)属性开启自适应折叠模式。


```

```TypeScript
### 示例3（设置提示弹窗背景模糊材质）

通过[popupBackgroundBlurStyle](#popupbackgroundblurstyle12)属性实现提示弹窗的背景模糊效果。


```

```TypeScript
### 示例4（设置提示弹窗的沉浸光感效果）

该示例展示索引条提示弹窗的沉浸光感效果。

该示例配图为高算力设备强档效果，组件沉浸光感效果会根据设备算力与用户在系统中设置的沉浸光感效果自适应调整，开发者无需额外适配。

从API版本26.0.0开始，索引条参数[popupBackground](#popupbackground)和[popupBackgroundBlurStyle](#popupbackgroundblurstyle12)均未主动设置（或参数value传入undefined）时，提示弹窗默认开启沉浸光感，默认材质样式为THICK。
```
