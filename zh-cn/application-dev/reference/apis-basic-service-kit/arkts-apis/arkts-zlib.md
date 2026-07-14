# @ohos.zlib

本模块提供压缩解压缩文件的能力。

**起始版本：** 7

**系统能力：** SystemCapability.BundleManager.Zlib

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [compressFile](arkts-basicservices-compressfile-f.md#compressfile-1) | 压缩文件，压缩的结果。使用callback异步回调。 |
| [compressFile](arkts-basicservices-compressfile-f.md#compressfile-2) | 压缩文件，压缩的结果。使用Promise异步回调。 |
| [compressFiles](arkts-basicservices-compressfiles-f.md#compressfiles-1) | 压缩指定的多个文件。使用Promise异步回调。 |
| [createChecksum](arkts-basicservices-createchecksum-f.md#createchecksum-1) | 创建校验对象。使用Promise异步回调。 |
| [createChecksumSync](arkts-basicservices-createchecksumsync-f.md#createchecksumsync-1) | 创建校验对象。成功时返回Checksum对象实例。 |
| [createGZip](arkts-basicservices-creategzip-f.md#creategzip-1) | 创建GZip对象。使用Promise异步回调。 |
| [createGZipSync](arkts-basicservices-creategzipsync-f.md#creategzipsync-1) | 创建GZip对象。成功时返回GZip对象实例。 |
| [createZip](arkts-basicservices-createzip-f.md#createzip-1) | 创建压缩解压缩对象实例。使用Promise异步回调。 |
| [createZipSync](arkts-basicservices-createzipsync-f.md#createzipsync-1) | 创建压缩解压缩对象实例，成功时返回压缩解压缩对象实例。 |
| [decompressFile](arkts-basicservices-decompressfile-f.md#decompressfile-1) | 解压文件，解压的结果。使用callback异步回调。 |
| [decompressFile](arkts-basicservices-decompressfile-f.md#decompressfile-2) | 解压文件，解压的结果。使用callback异步回调。 |
| [decompressFile](arkts-basicservices-decompressfile-f.md#decompressfile-3) | 解压文件，解压的结果。使用Promise异步回调。 |
| [getOriginalSize](arkts-basicservices-getoriginalsize-f.md#getoriginalsize-1) | 获取压缩文件的原始大小。使用Promise异步回调。 |
| [unzipFile](arkts-basicservices-unzipfile-f.md#unzipfile-1) | 解压文件，解压完成后返回执行结果。使用Promise异步回调。@link zlib.decompressFile(inFile: string, outFile: string, options: Options, callback: AsyncCallback&lt;void&gt;)}&gt; 替代。&gt;&gt; 传入的压缩包内部文件或者文件夹名称不能包含“../”，否则会返回-1错误码。 |
| [zipFile](arkts-basicservices-zipfile-f.md#zipfile-1) | 压缩接口，压缩完成后返回执行结果。使用Promise异步回调。@link zlib.compressFile(inFile: string, outFile: string, options: Options, callback: AsyncCallback&lt;void&gt;)}&gt; 替代。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [Checksum](arkts-basicservices-checksum-i.md) | 校验对象。 |
| [DecompressionOutputInfo](arkts-basicservices-decompressionoutputinfo-i.md) | 解压缩返回信息。 |
| [DeflatePendingOutputInfo](arkts-basicservices-deflatependingoutputinfo-i.md) | 压缩等待返回信息。 |
| [DictionaryOutputInfo](arkts-basicservices-dictionaryoutputinfo-i.md) | InflateGetDictionary和deflateGetDictionary这两个函数会返回值的相关信息。 |
| [GZip](arkts-basicservices-gzip-i.md) | Gzip相关接口。 |
| [GzErrorOutputInfo](arkts-basicservices-gzerroroutputinfo-i.md) | GzError返回信息。 |
| [GzHeader](arkts-basicservices-gzheader-i.md) | 传递从zlib例程中获取的Gzip头部信息。 |
| [Options](arkts-basicservices-options-i.md) | Options用于指定在压缩或解压Zip文件时的选项。 |
| [ZStream](arkts-basicservices-zstream-i.md) | 处理所有用于压缩和解压缩所需的信息。 |
| [Zip](arkts-basicservices-zip-i.md) | 压缩解压缩对象实例，支持以zlib、deflate、gzip格式对数据进行压缩与解压。 |
| [ZipOutputInfo](arkts-basicservices-zipoutputinfo-i.md) | 压缩和解压缩的返回值信息。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [CompressFlushMode](arkts-basicservices-compressflushmode-e.md) | 压缩刷新模式。 |
| [CompressLevel](arkts-basicservices-compresslevel-e.md) | 压缩等级。 |
| [CompressMethod](arkts-basicservices-compressmethod-e.md) | 压缩模式。 |
| [CompressStrategy](arkts-basicservices-compressstrategy-e.md) | CompressStrategy作为[Options](arkts-basicservices-options-i.md)的一个属性，用于指定压缩时的压缩策略。 |
| [ErrorCode](arkts-basicservices-errorcode-e.md) | 错误码。 |
| [MemLevel](arkts-basicservices-memlevel-e.md) | 内存等级。 |
| [OffsetReferencePoint](arkts-basicservices-offsetreferencepoint-e.md) | 偏移参考点。 |
| [ParallelStrategy](arkts-basicservices-parallelstrategy-e.md) | ParallelStrategy作为[Options](arkts-basicservices-options-i.md)的一个属性，用于指定压缩或解压时的串行或并行策略。 |
| [PathSeparatorStrategy](arkts-basicservices-pathseparatorstrategy-e.md) | PathSeparatorStrategy作为[Options](arkts-basicservices-options-i.md)的一个属性，用于指定解压时目标压缩包内文件路径中分隔符的处理策略。 |
| [ReturnStatus](arkts-basicservices-returnstatus-e.md) | 压缩/解压缩函数的返回代码。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [InflateBackInputCallback](arkts-basicservices-inflatebackinputcallback-t.md) | 一个用于读取用户提供的输入数据的回调函数。当解压缩过程需要更多输入数据时，zlib 将调用此函数。此函数应从数据源读取数据并将其写入缓冲区中。 |
| [InflateBackOutputCallback](arkts-basicservices-inflatebackoutputcallback-t.md) | 用户提供的输出数据会被写入回调函数中。每当解压后的数据准备好进行输出时，zlib 就会调用此函数将缓冲区中的数据写入目标位置。 |

