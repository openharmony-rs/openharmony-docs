# searchTarget（系统接口）

## searchTarget

```TypeScript
function searchTarget(target: TargetInfo, params: SearchParams): Promise<SearchResult>
```

Searching for a specified target.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-mechanicManager-function searchTarget(target: TargetInfo, params: SearchParams): Promise<SearchResult>--><!--Device-mechanicManager-function searchTarget(target: TargetInfo, params: SearchParams): Promise<SearchResult>-End-->

**系统能力：** SystemCapability.Mechanic.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| target | TargetInfo | 是 | Target infomation. |
| params | SearchParams | 是 | Parameters to use when searching. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[SearchResult](arkts-mechanic-mechanicmanager-searchresult-i-sys.md)&gt; | Promise that return the Search result. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 33300004 | Camera not opened. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [33300001](../errorcode-mechanic.md#33300001-系统错误) | Service exception. |
| [33300002](../errorcode-mechanic.md#33300002-设备未连接) | Device not connected. |
| [33300003](../errorcode-mechanic.md#33300003-功能不支持) | Feature not supported. |

## 示例

```TypeScript
let targetInfo: mechanicManager.TargetInfo = {
    targetType: mechanicManager.TargetType.HUMAN_FACE
};
let searchParams: mechanicManager.SearchParams = {
    direction: mechanicManager.SearchDirection.DEFAULT
}
mechanicManager.searchTarget(targetInfo,
    searchParams).then((searchResult) => {
    console.info(`'result:' ${searchResult}`);
});
```

