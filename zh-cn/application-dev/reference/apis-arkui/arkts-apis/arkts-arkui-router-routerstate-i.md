# RouterState

页面状态信息。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** -1

<!--Device-router-interface RouterState--><!--Device-router-interface RouterState-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## index

```TypeScript
index: number
```

表示当前页面在页面栈中的索引。从栈底到栈顶，index从1开始递增。

**类型：** number

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RouterState-index: number--><!--Device-RouterState-index: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## name

```TypeScript
name: string
```

表示当前页面的名称，即对应文件名。

**类型：** string

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RouterState-name: string--><!--Device-RouterState-name: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## params

```TypeScript
params: Object
```

表示当前页面携带的参数。 **说明：** params参数只能传递可序列化的参数，不能传递方法和系统接口返回的对象（例如，媒体接口定义和返回的PixelMap对象）。建议开发者提取系统接口返回的对象中需要被传递的基础类型属性，自行构造object类型对象进行传递。 从API version 12开始，该接口支持在原子化服务中使用。 此接口仅可在Stage模型下使用。

**类型：** Object

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RouterState-params: Object--><!--Device-RouterState-params: Object-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## path

```TypeScript
path: string
```

表示当前页面的路径。

**类型：** string

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RouterState-path: string--><!--Device-RouterState-path: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

