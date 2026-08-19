# getItemsInShapePath（系统接口）

## 导入模块

```TypeScript
import { componentUtils } from '@kit.ArkUI';
```

## getItemsInShapePath

```TypeScript
function getItemsInShapePath(value: GetItemsInShapePathParams): Array<ImageItem>
```

Get the image objects located within the selected area.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-componentUtils-function getItemsInShapePath(value: GetItemsInShapePathParams): Array<ImageItem>--><!--Device-componentUtils-function getItemsInShapePath(value: GetItemsInShapePathParams): Array<ImageItem>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [GetItemsInShapePathParams](arkts-arkui-componentutils-getitemsinshapepathparams-i-sys.md) | 是 | options to get images in shapePath. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[ImageItem](arkts-arkui-componentutils-imageitem-i-sys.md)&gt; | Returns the image objects located within the selected area. |

