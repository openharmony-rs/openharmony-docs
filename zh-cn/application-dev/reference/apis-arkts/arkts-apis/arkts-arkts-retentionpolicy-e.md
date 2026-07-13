# RetentionPolicy

描述注解类型保留策略的枚举类型。其枚举值和Retention结合使用，以指定注解的生命周期。

**起始版本：** 24

**系统能力：** SystemCapability.Utils.Lang

## SOURCE

```TypeScript
SOURCE = 'source'
```

注解将在编译期被移除。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Utils.Lang

## BYTECODE

```TypeScript
BYTECODE = 'bytecode'
```

注解将保留到编译产物中。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Utils.Lang

