# on（系统接口）

## 导入模块

```TypeScript
```

## on('formUninstall')

```TypeScript
function on(type: 'formUninstall', callback: Callback<string>): void
```

订阅卡片卸载事件。使用callback异步回调。

> **说明：**
> 
> 卡片卸载与卡片移除不同。当应用卸载时，对应的卡片会自动卸载。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [on](arkts-form-formhost-on-f-sys.md)

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'formUninstall' | 是 | 填写'formUninstall'，表示卡片卸载事件。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;string&gt; | 是 | 回调函数，返回卡片标识。 |
