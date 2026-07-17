# TypeDecorator

```TypeScript
export declare type TypeDecorator = <T>(type: TypeConstructor<T>) => PropertyDecorator
```

属性装饰器，用于装饰嵌套类中属于自定义class类的属性。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-export declare type TypeDecorator = <T>(type: TypeConstructor<T>) => PropertyDecorator--><!--Device-unnamed-export declare type TypeDecorator = <T>(type: TypeConstructor<T>) => PropertyDecorator-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | TypeConstructor&lt;T&gt; | 是 | 标记类属性的类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| PropertyDecorator | 属性装饰器。 |

