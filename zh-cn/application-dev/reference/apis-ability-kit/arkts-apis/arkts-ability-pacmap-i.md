# PacMap

用于存储数据的PacMap类型。

**起始版本：** 7

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

## key

```TypeScript
[key: string]: number | string | boolean | Array<string | number | boolean> | null
```

用于存储数据的PacMap类型。
如果自定义sequencable对象被放入PacMap对象中，并将跨进程传输，你必须调用BasePacMap.setClassLoader(ClassLoader)为自定义对象设置一个类加载器。
如果要将PacMap对象传输到非ohos进程，支持基本类型的值，但不支持自定义可序列对象。

**类型：** number | string | boolean | Array<string | number | boolean> | null

**起始版本：** 7

**模型约束：** 
- API版本7-10：此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

