# WatchEvent

事件类

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export interface WatchEvent--><!--Device-unnamed-export interface WatchEvent-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## cookie

```TypeScript
readonly cookie: int
```

绑定相关事件的cookie。当前仅支持事件IN\_MOVED\_FROM与IN\_MOVED\_TO，同一个文件的移动事件IN\_MOVED\_FROM和IN\_MOVED\_TO具有相同的cookie值。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-WatchEvent-readonly cookie: int--><!--Device-WatchEvent-readonly cookie: int-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## event

```TypeScript
readonly event: int
```

监听变动的事件集，多个事件通过或(|)的方式进行集合。 - 0x1: IN\_ACCESS， 文件被访问。 - 0x2: IN\_MODIFY，文件内容被修改。 - 0x4: IN\_ATTRIB，文件元数据被修改。 - 0x8: IN\_CLOSE\_WRITE，文件在打开时进行了写操作，然后被关闭。 - 0x10: IN\_CLOSE\_NOWRITE，文件或目录在打开时未进行写操作，然后被关闭。 - 0x20: IN\_OPEN，文件或目录被打开。 - 0x40: IN\_MOVED\_FROM，监听目录中文件被移动走。 - 0x80: IN\_MOVED\_TO，监听目录中文件被移动过来。 - 0x100: IN\_CREATE，监听目录中文件或子目录被创建。 - 0x200: IN\_DELETE，监听目录中文件或子目录被删除。 - 0x400: IN\_DELETE\_SELF，监听的目录被删除，删除后监听停止。 - 0x800: IN\_MOVE\_SELF，监听的文件或目录被移动，移动后监听继续。 - 0xfff: IN\_ALL\_EVENTS，监听以上所有事件。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-WatchEvent-readonly event: int--><!--Device-WatchEvent-readonly event: int-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## fileName

```TypeScript
readonly fileName: string
```

发生监听事件对应文件的沙箱路径，该沙箱路径包含文件名称。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-WatchEvent-readonly fileName: string--><!--Device-WatchEvent-readonly fileName: string-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

