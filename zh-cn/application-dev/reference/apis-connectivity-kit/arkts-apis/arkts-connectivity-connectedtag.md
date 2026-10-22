# @ohos.connectedTag(有源标签)

本模块提供有源标签的使用，包括初始化有源标签芯片、读取有源标签内容、写入内容到有源标签等。

**起始版本：** 8

<!--Device-unnamed-declare namespace connectedTag--><!--Device-unnamed-declare namespace connectedTag-End-->

**系统能力：** SystemCapability.Communication.ConnectedTag

## 导入模块

```TypeScript
import { connectedTag } from '@kit.ConnectivityKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [initialize](arkts-connectivity-connectedtag-initialize-f.md#initialize-1) | 初始化有源标签芯片。对有源标签进行读写操作前需调用本接口初始化一次，若想再次初始化需先调用[uninitialize](arkts-connectivity-connectedtag-uninitialize-f.md)。 |
| [off('notify')](arkts-connectivity-connectedtag-off-f.md#offnotify) | 取消NFC场强状态事件的注册。 |
| [on('notify')](arkts-connectivity-connectedtag-on-f.md#onnotify) | 注册NFC场强状态事件。 |
| [read](arkts-connectivity-connectedtag-read-f.md#read-1) | 读取有源标签内容。使用Promise异步回调。 |
| [read](arkts-connectivity-connectedtag-read-f.md#read-2) | 读取有源标签内容，使用AsyncCallback方式作为异步方法。 |
| [uninitialize](arkts-connectivity-connectedtag-uninitialize-f.md#uninitialize-1) | 卸载有源标签芯片资源。 |
| [write](arkts-connectivity-connectedtag-write-f.md#write-1) | 写入内容到有源标签。使用Promise异步回调。 |
| [write](arkts-connectivity-connectedtag-write-f.md#write-2) | 写入内容到有源标签，使用AsyncCallback方式作为异步方法。 |
| [init](arkts-connectivity-connectedtag-init-f.md#init-1) | 初始化有源标签芯片。 |
| [readNdefTag](arkts-connectivity-connectedtag-readndeftag-f.md#readndeftag-1) | 读取有源标签内容。使用Promise异步回调。 |
| [readNdefTag](arkts-connectivity-connectedtag-readndeftag-f.md#readndeftag-2) | 读取有源标签内容，使用AsyncCallback方式作为异步方法。 |
| [uninit](arkts-connectivity-connectedtag-uninit-f.md#uninit-1) | 卸载有源标签芯片资源。 |
| [writeNdefTag](arkts-connectivity-connectedtag-writendeftag-f.md#writendeftag-1) | 写入内容到有源标签。使用Promise异步回调。 |
| [writeNdefTag](arkts-connectivity-connectedtag-writendeftag-f.md#writendeftag-2) | 写入内容到有源标签，使用AsyncCallback方式作为异步方法。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [NfcRfType](arkts-connectivity-connectedtag-nfcrftype-e.md) | 表示NFC场强状态的枚举。 |
