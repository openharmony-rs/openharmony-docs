# 自定义节点错误码

> **说明：**
>
> 以下仅介绍本模块特有错误码，通用错误码请参考[通用错误码说明文档](../errorcode-universal.md)。

## 100021 FrameNode节点不可修改

**错误信息**

The FrameNode is not modifiable.

**错误描述**

当前FrameNode节点不可修改，无法对其进行当前的操作。可能触发的操作有设置属性、增删子节点、绑定控制器。

**可能原因**

开发者尝试对声明式节点进行修改性操作，例如，设置属性、增删子节点、绑定控制器。

**处理步骤**

避免对不可修改的节点进行修改性操作。可通过try catch捕捉并处理错误，避免影响其他逻辑。

## 100022 FrameNode节点的组件类型不支持调整跨语言的属性设置权限

**错误信息**

The FrameNode cannot be set whether to support cross-language common attribute setting.

**错误描述**

当前FrameNode节点不支持跨语言属性设置，无法调整其跨语言的属性设置权限。

**可能原因**

开发者尝试调整目标FrameNode节点的跨语言属性设置权限。

**处理步骤**

NA

## 100024 当前节点和目标节点没有共同父节点

**错误信息**

The current FrameNode and the target FrameNode do not have a common ancestor node.

**错误描述**

当前节点和目标节点没有共同父节点。

**可能原因**

找不到当前节点和目标节点的共同父节点。

**处理步骤**

修改传入的参数值。

## 100025 传入参数不符合要求

**错误信息**

The parameter is invalid. Details about the invalid parameter and the reason are included in the error message. For example: "The parameter 'targetNode' is invalid: it cannot be disposed."

**错误描述**

传入参数有误。

**可能原因**

如果传入null、undefined或其他有误参数，请查看错误信息以了解具体原因。

**处理步骤**

1. 当报错信息显示传入参数为null，改为传入一个非空的FrameNode对象。
2. 当报错信息显示找不到公共父节点，传入之前判断目标节点是否为离屏节点，修改目标节点。
3. 其他原因的报错可参考错误信息进行修改。

## 106103 对应的操作不支持ArkTS创建的节点

**错误信息**

The corresponding operation does not support nodes created by ArkTS.

**错误描述**

对应的操作不支持ArkTS创建的节点。

**可能原因**

当前操作不支持ArkTS创建的节点。

**处理步骤**

传入非ArkTS创建的节点。

## 106203 传入的节点未挂载到组件树上

**错误信息**

**错误描述**

传入的节点未挂载到组件树上。

**可能原因**

当前传入的节点未挂载到组件树上。

**处理步骤**

调整函数调用时机，确保传入的节点已挂载到组件树上。