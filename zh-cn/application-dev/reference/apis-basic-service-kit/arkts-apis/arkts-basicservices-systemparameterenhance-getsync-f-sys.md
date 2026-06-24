# getSync（系统接口）

## getSync

```TypeScript
function getSync(key: string, def?: string): string
```

获取系统参数Key对应的值。

**起始版本：** 9

**系统能力：** SystemCapability.Startup.SystemInfo

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 待查询的系统参数Key。最大长度128字节，只允许字母数字加"."，"-"，"@"，":"或"_"，不允许".."。 |
| def | string | 否 | def为所要获取的系统参数的默认值；<br/>def为可选参数，仅当系统参数不存在时生效；<br/>def可以传undefined或自定义的任意值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 系统参数值。<br/><br/>若key存在,返回设定的值。<br/><br/>若key不存在且def有效，返回def；若未指定def或def无效(如undefined)，抛异常。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified;<br/>2.incorrect parameter types; 3.parameter verification failed. |
| [14700101](../../errorcode-universal.md#14700101-System) | System parameter not found. |
| [14700103](../../errorcode-universal.md#14700103-The) | The operation on the system permission is denied. |
| [14700104](../../errorcode-universal.md#14700104-System) | System internal error such as out memory or deadlock. |

**示例：**

```TypeScript
try {
    let info: string = systemParameterEnhance.getSync("const.ohos.apiversion");
    console.info(JSON.stringify(info));
} catch(e) {
    console.error("getSync unexpected error: " + e);
}

```

