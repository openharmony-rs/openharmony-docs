# XMPTagType

表示XMP标签类型的枚举。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Multimedia.Image.Core

## UNKNOWN

```TypeScript
UNKNOWN = 0
```

未知类型。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## STRING

```TypeScript
STRING = 1
```

字符串类型。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## UNORDERED_ARRAY

```TypeScript
UNORDERED_ARRAY = 2
```

无序数组类型。序列化时，此类型在XMP元数据中的格式为<rdf:Bag>。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## ORDERED_ARRAY

```TypeScript
ORDERED_ARRAY = 3
```

有序数组类型。序列化时，此类型在XMP元数据中的格式为<rdf:Seq>。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## ALTERNATE_ARRAY

```TypeScript
ALTERNATE_ARRAY = 4
```

备选数组类型。序列化时，此类型在XMP元数据中的格式为<rdf:Alt>。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## ALTERNATE_TEXT

```TypeScript
ALTERNATE_TEXT = 5
```

多语言文本类型。序列化时，此类型为XMP格式的xml:lang限定符组成的备选数组。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## STRUCTURE

```TypeScript
STRUCTURE = 6
```

结构体类型。不同于数组元素，结构体字段可以属于不同的命名空间。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

