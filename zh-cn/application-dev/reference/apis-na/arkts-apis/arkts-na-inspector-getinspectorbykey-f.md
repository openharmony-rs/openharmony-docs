# getInspectorByKey

## getInspectorByKey

```TypeScript
function getInspectorByKey(id: string): string
```

获取指定id组件的所有属性，不包括子组件信息。 此接口仅用于对应用的测试，使用时建议等应用启动且布局完成后再调用。由于耗时长，不建议测试之外的场景使用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-inspector-function getInspectorByKey(id: string): string--><!--Device-inspector-function getInspectorByKey(id: string): string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | 要获取属性的组件id。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 组件属性列表的JSON字符串。字符串信息包含组件的tag、id、位置信息（相对于窗口左上角的坐标）以及用于测试检查的组件所包含的相关属性信息。 组件中每个字段的含义请参考getInspectorInfo的返回值说明。 |

