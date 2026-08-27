# EventType

事件类型枚举，定义了XmlPullParser在解析XML过程中可能触发的各类事件。解析时事件按START_DOCUMENT→START_TAG→TEXT/CDSECT→END_TAG→END_DOCUMENT等顺序依次触发， 开发者可通过tokenValueCallbackFunction回调接收对应事件。  
**ArkTS-Dyn起始版本：** 8  
**ArkTS-Sta起始版本：** 23

**起始版本：** 8

**系统能力：** SystemCapability.Utils.Lang

## START_DOCUMENT

```TypeScript
START_DOCUMENT
```

启动文件事件。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## END_DOCUMENT

```TypeScript
END_DOCUMENT
```

结束文件事件。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## START_TAG

```TypeScript
START_TAG
```

启动标签事件。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## END_TAG

```TypeScript
END_TAG
```

结束标签事件。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## TEXT

```TypeScript
TEXT
```

文本事件。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## CDSECT

```TypeScript
CDSECT
```

CDATA事件。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## COMMENT

```TypeScript
COMMENT
```

XML注释事件。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## DOCDECL

```TypeScript
DOCDECL
```

XML文档类型声明事件。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## INSTRUCTION

```TypeScript
INSTRUCTION
```

XML处理指令声明事件。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## ENTITY_REFERENCE

```TypeScript
ENTITY_REFERENCE
```

实体引用事件。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## WHITESPACE

```TypeScript
WHITESPACE
```

空白事件。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Utils.Lang
