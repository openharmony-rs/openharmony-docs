# getItemsInShapePath（系统接口）

## getItemsInShapePath

```TypeScript
function getItemsInShapePath(value: GetItemsInShapePathParams): Array<ImageItem>
```

获取位于选定区域内的图像对象。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | GetItemsInShapePathParams | 是 | 获取形状路径中图像的选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;ImageItem&gt; | 返回位于选定区域内的图像对象。 |

