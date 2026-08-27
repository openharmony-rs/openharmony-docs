# @ohos.connectedTag(有源标签)

本模块提供有源标签的使用，包括初始化有源标签芯片、读取有源标签内容、写入内容到有源标签等。

**起始版本：** 8

**系统能力：** SystemCapability.Communication.ConnectedTag

## 导入模块

```TypeScript
import { connectedTag } from '@kit.ConnectivityKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [init(有源标签)](arkts-connectivity-connectedtag-init-f.md) | 初始化有源标签芯片。 |
| [initialize(有源标签)](arkts-connectivity-connectedtag-initialize-f.md) | 初始化有源标签芯片。对有源标签进行读写操作前需调用本接口初始化一次，若想再次初始化需先调用[uninitialize](arkts-connectivity-connectedtag-uninitialize-f.md)。 |
| [off(有源标签)](arkts-connectivity-connectedtag-off-f.md#offnotify) | 取消NFC场强状态事件的注册。 |
| [on(有源标签)](arkts-connectivity-connectedtag-on-f.md#onnotify) | 注册NFC场强状态事件。 |
| [read(有源标签)](arkts-connectivity-connectedtag-read-f.md) | 读取有源标签内容。使用Promise异步回调。 |
| [read(有源标签)](arkts-connectivity-connectedtag-read-f.md) | 读取有源标签内容，使用AsyncCallback方式作为异步方法。 |
| [readNdefTag(有源标签)](arkts-connectivity-connectedtag-readndeftag-f.md) | 读取有源标签内容。使用Promise异步回调。 |
| [readNdefTag(有源标签)](arkts-connectivity-connectedtag-readndeftag-f.md) | 读取有源标签内容，使用AsyncCallback方式作为异步方法。 |
| [uninit(有源标签)](arkts-connectivity-connectedtag-uninit-f.md) | 卸载有源标签芯片资源。 |
| [uninitialize(有源标签)](arkts-connectivity-connectedtag-uninitialize-f.md) | 卸载有源标签芯片资源。 |
| [write(有源标签)](arkts-connectivity-connectedtag-write-f.md) | 写入内容到有源标签。使用Promise异步回调。 |
| [write(有源标签)](arkts-connectivity-connectedtag-write-f.md) | 写入内容到有源标签，使用AsyncCallback方式作为异步方法。 |
| [writeNdefTag(有源标签)](arkts-connectivity-connectedtag-writendeftag-f.md) | 写入内容到有源标签。使用Promise异步回调。 |
| [writeNdefTag(有源标签)](arkts-connectivity-connectedtag-writendeftag-f.md) | 写入内容到有源标签，使用AsyncCallback方式作为异步方法。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [NfcRfType(有源标签)](arkts-connectivity-connectedtag-nfcrftype-e.md) | 表示NFC场强状态的枚举。 |
