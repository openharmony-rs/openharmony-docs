# choose

## choose

```TypeScript
declare function choose(types?: string[]): Promise<string>
```

通过文件管理器选择文件，异步返回文件URI，使用promise形式返回结果。

**起始版本：** 6

**废弃版本：** 9

<!--Device-unnamed-declare function choose(types?: string[]): Promise<string>--><!--Device-unnamed-declare function choose(types?: string[]): Promise<string>-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| types | string[] | 否 | 限定文件选择的类型 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<string> | 异步返回文件URI（注：当前返回错误码） |


## choose

```TypeScript
declare function choose(callback: AsyncCallback<string>): void
```

通过文件管理器选择文件，异步返回文件URI，使用callback形式返回结果。

**起始版本：** 6

**废弃版本：** 9

<!--Device-unnamed-declare function choose(callback: AsyncCallback<string>): void--><!--Device-unnamed-declare function choose(callback: AsyncCallback<string>): void-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<string> | 是 | 异步获取对应文件URI（注：当前返回错误码） |


## choose

```TypeScript
declare function choose(types: string[], callback: AsyncCallback<string>): void
```

通过文件管理器选择文件，异步返回文件URI，使用callback形式返回结果。

**起始版本：** 6

**废弃版本：** 9

<!--Device-unnamed-declare function choose(types: string[], callback: AsyncCallback<string>): void--><!--Device-unnamed-declare function choose(types: string[], callback: AsyncCallback<string>): void-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| types | string[] | 是 | 限定选择文件的类型 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<string> | 是 | 异步获取对应文件URI（注：当前返回错误码） |

