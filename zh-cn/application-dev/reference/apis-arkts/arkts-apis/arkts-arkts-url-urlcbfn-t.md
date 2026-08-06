# UrlCbFn

```TypeScript
type UrlCbFn = (value: string, key: string, searchParams: URLParams) => void
```

[forEach]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_函数所需的回调函数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-url-type UrlCbFn = (value: string, key: string, searchParams: URLParams) => void--><!--Device-url-type UrlCbFn = (value: string, key: string, searchParams: URLParams) => void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string | 是 | 当前遍历到的键值。  |
| key | string | 是 | 当前遍历到的键名。  |
| searchParams | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 当前调用[forEach]\_\_\_JSDOC\_LINK\_USD\_0\_\_\_方法的实例对象。  |

