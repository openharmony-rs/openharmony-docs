# QueryRule（系统接口）

系统事件查询规则对象接口。

**起始版本：** 9

**系统能力：** SystemCapability.HiviewDFX.HiSysEvent

**系统接口：** 此接口为系统接口。

## condition

```TypeScript
condition?: string
```

事件的额外参数条件，格式：{"version":"V1","condition":{"and":[{"param":"参数","op":"操作符","value":"比较值"}]}}。

参数：指定事件参数的键值。

操作符支持：=、!=、<、<=、>和>=。

支持在“and”数组中配置多个条件，查询结果取交集。

**类型：** string

**起始版本：** 10

**系统能力：** SystemCapability.HiviewDFX.HiSysEvent

**系统接口：** 此接口为系统接口。

## domain

```TypeScript
domain: string
```

查询包含的事件领域。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.HiviewDFX.HiSysEvent

**系统接口：** 此接口为系统接口。

## names

```TypeScript
names: string[]
```

查询所包含的多个事件名称，每个查询规则对象包含多个系统事件名称。

**类型：** string[]

**起始版本：** 9

**系统能力：** SystemCapability.HiviewDFX.HiSysEvent

**系统接口：** 此接口为系统接口。

