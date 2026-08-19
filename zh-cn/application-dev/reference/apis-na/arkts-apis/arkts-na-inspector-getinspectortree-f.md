# getInspectorTree

## 导入模块

```TypeScript
```

## getInspectorTree

```TypeScript
function getInspectorTree(): RecordData
```

获取组件树及组件属性。 此接口仅用于对应用的测试。由于耗时长，不建议测试之外的场景使用。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-inspector-function getInspectorTree(): RecordData--><!--Device-inspector-function getInspectorTree(): RecordData-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RecordData](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-recorddata-t.md) | 组件树及组件属性列表的JSON对象。组件中每个字段的含义请参考getInspectorInfo的返回值说明。 |

