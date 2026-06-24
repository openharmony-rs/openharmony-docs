# @ohos.zlib

本模块提供压缩解压缩文件的能力。

**起始版本：** 7

**系统能力：** SystemCapability.BundleManager.Zlib

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [compressFile](arkts-basicservices-zlib-compressfile-f.md#compressFile-1) | 压缩文件，压缩的结果。使用callback异步回调。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 为了避免路径穿越，从API version 13开始，inFile和outFile传入的参数不允许包含“../”，否则会返回900001、900002错误码。<br/> |
| [compressFile](arkts-basicservices-zlib-compressfile-f.md#compressFile-2) | 压缩文件，压缩的结果。使用Promise异步回调。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 为了避免路径穿越，从API version 13开始，inFile和outFile传入的参数不允许包含“../”，否则会返回900001、900002错误码。<br/> |
| [compressFiles](arkts-basicservices-zlib-compressfiles-f.md#compressFiles-1) | 压缩指定的多个文件。使用Promise异步回调。<br/> |
| [createChecksum](arkts-basicservices-zlib-createchecksum-f.md#createChecksum-1) | 创建校验对象。使用Promise异步回调。<br/> |
| [createChecksumSync](arkts-basicservices-zlib-createchecksumsync-f.md#createChecksumSync-1) | 创建校验对象。成功时返回Checksum对象实例。<br/> |
| [createGZip](arkts-basicservices-zlib-creategzip-f.md#createGZip-1) | 创建GZip对象。使用Promise异步回调。<br/> |
| [createGZipSync](arkts-basicservices-zlib-creategzipsync-f.md#createGZipSync-1) | 创建GZip对象。成功时返回GZip对象实例。<br/> |
| [createZip](arkts-basicservices-zlib-createzip-f.md#createZip-1) | 创建压缩解压缩对象实例。使用Promise异步回调。<br/> |
| [createZipSync](arkts-basicservices-zlib-createzipsync-f.md#createZipSync-1) | 创建压缩解压缩对象实例，成功时返回压缩解压缩对象实例。<br/> |
| [decompressFile](arkts-basicservices-zlib-decompressfile-f.md#decompressFile-1) | 解压文件，解压的结果。使用callback异步回调。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 为了避免路径穿越，从API version 13开始，inFile和outFile传入的参数不允许包含“../”，否则会返回900001、900002错误码。<br/>&gt;<br/>&gt; 传入的压缩包内部文件或者文件夹名称不能包含“../”，否则会返回900003错误码。<br/> |
| [decompressFile](arkts-basicservices-zlib-decompressfile-f.md#decompressFile-2) | 解压文件，解压的结果。使用callback异步回调。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 为了避免路径穿越，从API version 13开始，inFile和outFile传入的参数不允许包含“../”，否则会返回900001、900002错误码。<br/>&gt;<br/>&gt; 传入的压缩包内部文件或者文件夹名称不能包含“../”，否则会返回900003错误码。<br/> |
| [decompressFile](arkts-basicservices-zlib-decompressfile-f.md#decompressFile-3) | 解压文件，解压的结果。使用Promise异步回调。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 为了避免路径穿越，从API version 13开始，inFile和outFile传入的参数不允许包含“../”，否则会返回900001、900002错误码。<br/>&gt;<br/>&gt; 传入的压缩包内部文件或者文件夹名称不能包含“../”，否则会返回900003错误码。<br/> |
| [getOriginalSize](arkts-basicservices-zlib-getoriginalsize-f.md#getOriginalSize-1) | 获取压缩文件的原始大小。使用Promise异步回调。<br/> |
| [unzipFile](arkts-basicservices-zlib-unzipfile-f.md#unzipFile-1) | 解压文件，解压完成后返回执行结果。使用Promise异步回调。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 从API version 7开始支持，从API version 9开始废弃。建议使用<br/>&gt; [zlib.decompressFile](zlib.decompressFile(inFile: string, outFile: string, options: Options, callback: AsyncCallback&lt;void&gt;))<br/>&gt; 替代。<br/>&gt;<br/>&gt; 传入的压缩包内部文件或者文件夹名称不能包含“../”，否则会返回-1错误码。<br/> |
| [zipFile](arkts-basicservices-zlib-zipfile-f.md#zipFile-1) | 压缩接口，压缩完成后返回执行结果。使用Promise异步回调。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 从API version 7开始支持，从API version 9开始废弃。建议使用<br/>&gt; [zlib.compressFile](zlib.compressFile(inFile: string, outFile: string, options: Options, callback: AsyncCallback&lt;void&gt;))<br/>&gt; 替代。<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| [Checksum](arkts-basicservices-zlib-checksum-i.md) | 校验对象。<br/> |
| [DecompressionOutputInfo](arkts-basicservices-zlib-decompressionoutputinfo-i.md) | 解压缩返回信息。<br/> |
| [DeflatePendingOutputInfo](arkts-basicservices-zlib-deflatependingoutputinfo-i.md) | 压缩等待返回信息。<br/> |
| [DictionaryOutputInfo](arkts-basicservices-zlib-dictionaryoutputinfo-i.md) | InflateGetDictionary和deflateGetDictionary这两个函数会返回值的相关信息。<br/> |
| [GZip](arkts-basicservices-zlib-gzip-i.md) | Gzip相关接口。<br/> |
| [GzErrorOutputInfo](arkts-basicservices-zlib-gzerroroutputinfo-i.md) | GzError返回信息。<br/> |
| [GzHeader](arkts-basicservices-zlib-gzheader-i.md) | 传递从zlib例程中获取的Gzip头部信息。<br/> |
| [Options](arkts-basicservices-zlib-options-i.md) | Options用于指定在压缩或解压Zip文件时的选项。<br/> |
| [ZStream](arkts-basicservices-zlib-zstream-i.md) | 处理所有用于压缩和解压缩所需的信息。<br/> |
| [Zip](arkts-basicservices-zlib-zip-i.md) | 压缩解压缩对象实例，支持以zlib、deflate、gzip格式对数据进行压缩与解压。<br/> |
| [ZipOutputInfo](arkts-basicservices-zlib-zipoutputinfo-i.md) | 压缩和解压缩的返回值信息。<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [CompressFlushMode](arkts-basicservices-zlib-compressflushmode-e.md) | 压缩刷新模式。<br/> |
| [CompressLevel](arkts-basicservices-zlib-compresslevel-e.md) | 压缩等级。<br/> |
| [CompressMethod](arkts-basicservices-zlib-compressmethod-e.md) | 压缩模式。<br/> |
| [CompressStrategy](arkts-basicservices-zlib-compressstrategy-e.md) | CompressStrategy作为[Options](arkts-basicservices-zlib-options-i.md#Options)的一个属性，用于指定压缩时的压缩策略。<br/> |
| [ErrorCode](arkts-basicservices-zlib-errorcode-e.md) | 错误码。<br/> |
| [MemLevel](arkts-basicservices-zlib-memlevel-e.md) | 内存等级。<br/> |
| [OffsetReferencePoint](arkts-basicservices-zlib-offsetreferencepoint-e.md) | 偏移参考点。<br/> |
| [ParallelStrategy](arkts-basicservices-zlib-parallelstrategy-e.md) | ParallelStrategy作为[Options](arkts-basicservices-zlib-options-i.md#Options)的一个属性，用于指定压缩或解压时的串行或并行策略。<br/> |
| [PathSeparatorStrategy](arkts-basicservices-zlib-pathseparatorstrategy-e.md) | PathSeparatorStrategy作为[Options](arkts-basicservices-zlib-options-i.md#Options)的一个属性，用于指定解压时目标压缩包内文件路径中分隔符的处理策略。<br/> |
| [ReturnStatus](arkts-basicservices-zlib-returnstatus-e.md) | 压缩/解压缩函数的返回代码。<br/> |

### 类型

| 名称 | 说明 |
| --- | --- |
| [InflateBackInputCallback](arkts-basicservices-zlib-inflatebackinputcallback-t.md) | 一个用于读取用户提供的输入数据的回调函数。当解压缩过程需要更多输入数据时，zlib 将调用此函数。此函数应从数据源读取数据并将其写入缓冲区中。<br/> |
| [InflateBackOutputCallback](arkts-basicservices-zlib-inflatebackoutputcallback-t.md) | 用户提供的输出数据会被写入回调函数中。每当解压后的数据准备好进行输出时，zlib 就会调用此函数将缓冲区中的数据写入目标位置。<br/> |

