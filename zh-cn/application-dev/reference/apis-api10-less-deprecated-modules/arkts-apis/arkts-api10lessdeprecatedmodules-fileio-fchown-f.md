# fchown

## fchown

```TypeScript
declare function fchown(fd: number, uid: number, gid: number): Promise<void>
```

基于文件描述符改变文件所有者，使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | number | 是 | 待改变文件的文件描述符。 |
| uid | number | 是 | 文件所有者的UID。 |
| gid | number | 是 | 文件所有组的GID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回值。 |


## fchown

```TypeScript
declare function fchown(fd: number, uid: number, gid: number, callback: AsyncCallback<void>): void
```

基于文件描述符改变文件所有者，使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | number | 是 | 待改变文件的文件描述符。 |
| uid | number | 是 | 文件所有者的UID。 |
| gid | number | 是 | 文件所有组的GID。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 异步改变文件所有者之后的回调。 |

