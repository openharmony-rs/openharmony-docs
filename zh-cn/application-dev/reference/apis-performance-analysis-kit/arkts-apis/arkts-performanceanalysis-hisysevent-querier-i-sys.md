# Querier（系统接口）

系统事件查询者对象接口。

**起始版本：** 9

**系统能力：** SystemCapability.HiviewDFX.HiSysEvent

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
```

## onComplete

```TypeScript
onComplete: (reason: number, total: number) => void
```

查询结果统计的回调方法(reason: number, total: number) =&gt; void。

**起始版本：** 9

**系统能力：** SystemCapability.HiviewDFX.HiSysEvent

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| reason | number | 是 |  |
| total | number | 是 |  |

## onQuery

```TypeScript
onQuery: (infos: SysEventInfo[]) => void
```

返回查询到的系统事件的回调方法(infos: [SysEventInfo](arkts-performanceanalysis-hisysevent-syseventinfo-i-sys.md)[]) =&gt; void。

**起始版本：** 9

**系统能力：** SystemCapability.HiviewDFX.HiSysEvent

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| infos | [SysEventInfo](arkts-performanceanalysis-hisysevent-syseventinfo-i-sys.md)[] | 是 |  |
