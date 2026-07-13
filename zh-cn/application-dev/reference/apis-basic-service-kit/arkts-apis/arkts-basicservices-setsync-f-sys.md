# setSync（系统接口）

## setSync

```TypeScript
function setSync(key: string, value: string): void
```

设置系统参数Key对应的值。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** etSync

**系统能力：** SystemCapability.Startup.SystemInfo

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 待设置的系统参数Key。 |
| value | string | 是 | 待设置的系统参数值。 |

**示例：**

```TypeScript
try {
  systemParameter.setSync('test.parameter.key', 'default');
} catch (e) {
  console.error('set unexpected error: ' + e);
}

```

