# UIElementInfo

UI事件的相关信息。

**起始版本：** 10

**系统能力：** SystemCapability.Test.UiTest

## bundleName

```TypeScript
readonly bundleName: string
```

应用包名。

从API version 11开始，该接口支持在原子化服务中使用。

**类型：** string

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Test.UiTest

## componentEventType

```TypeScript
readonly componentEventType?: ComponentEventType
```

控件操作事件类型，若非控件操作事件返回ComponentEventType.COMPONENT_UNDEFINED。

从API version 22开始，该接口支持在原子化服务中使用。

**类型：** ComponentEventType

**起始版本：** 22

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Test.UiTest

## componentId

```TypeScript
readonly componentId?: string
```

控件id，若非控件操作事件返回空字符串。

从API version 22开始，该接口支持在原子化服务中使用。

**类型：** string

**起始版本：** 22

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Test.UiTest

## componentRect

```TypeScript
readonly componentRect?: Rect
```

控件边框信息，若非控件操作事件则返回属性值均为0的Rect对象。

从API version 22开始，该接口支持在原子化服务中使用。

**类型：** Rect

**起始版本：** 22

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Test.UiTest

## text

```TypeScript
readonly text: string
```

控件/窗口的文本信息。 从API version 11开始，该接口支持在原子化服务中使用。

**类型：** string

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Test.UiTest

## type

```TypeScript
readonly type: string
```

控件/窗口类型。

从API version 11开始，该接口支持在原子化服务中使用。

**类型：** string

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Test.UiTest

## windowChangeType

```TypeScript
readonly windowChangeType?: WindowChangeType
```

窗口变化事件类型，若非窗口变化事件返回WindowChangeType.WINDOW_UNDEFINED。

从API version 22开始，该接口支持在原子化服务中使用。

**类型：** WindowChangeType

**起始版本：** 22

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Test.UiTest

## windowId

```TypeScript
readonly windowId?: number
```

控件所属窗口id。

从API version 22开始，该接口支持在原子化服务中使用。

**类型：** number

**起始版本：** 22

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Test.UiTest

