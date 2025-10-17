# 压缩与解压
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @jsjzju-->
<!--Designer: @jsjzju-->
<!--Tester: @lixueqing-->
<!--Adviser: @Brilliantry_Rui-->

本文针对常见的几种压缩、解压场景，介绍相关函数的使用方法。

## 接口说明

以下是示例中使用的主要接口，更多接口及使用方式请见[接口文档](../../reference/apis-basic-services-kit/js-apis-zlib.md)。

| 接口名                                                       | 接口描述                     |
| ------------------------------------------------------------ | ---------------------------- |
| compressFile(inFile: string, outFile: string, options: Options): Promise&lt;void&gt; | 压缩文件。               |
| decompressFile(inFile: string, outFile: string, options?: Options): Promise&lt;void&gt; | 解压文件。               |
| compress(dest: ArrayBuffer, source: ArrayBuffer, sourceLen?: number): Promise&lt;ZipOutputInfo&gt; | 将源缓冲区压缩到目标缓冲区。               |
| compressBound(sourceLen: number): Promise&lt;number&gt; | 计算返回压缩大小的上限。              |
| uncompress(dest:ArrayBuffer, source: ArrayBuffer, sourceLen?: number): Promise&lt;ZipOutputInfo&gt; | 将压缩后的数据解压缩为原始的未压缩形式。               |
| deflate(strm: ZStream, flush: CompressFlushMode): Promise&lt;ReturnStatus&gt; | 压缩数据。               |
| inflate(strm: ZStream, flush: CompressFlushMode): Promise&lt;ReturnStatus&gt; | 解压数据。|

## 开发步骤

### 环境准备

在应用沙箱目录下创建一个测试文件data.txt，并写入测试数据。示例代码如下。

  <!-- @[deflate_and_inflate_001](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/bmsSample/DeflateAndInflate/entry/src/main/ets/pages/Index.ets) -->

### Zip文件的压缩与解压

采用接口[zlib.compressFile()](../../reference/apis-basic-services-kit/js-apis-zlib.md#zlibcompressfile9-1)将文件data.txt压缩并归档到data.zip中，采用接口[zlib.decompressFile()](../../reference/apis-basic-services-kit/js-apis-zlib.md#zlibdecompressfile9-1)将data.zip解压到应用沙箱目录下，示例代码如下。
  
  <!-- @[deflate_and_inflate_002](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/bmsSample/DeflateAndInflate/entry/src/main/ets/pages1/Index.ets) -->

### 已知大小缓冲区的压缩与解压

针对一个已知大小的缓冲区中的数据，使用接口[compress()](../../reference/apis-basic-services-kit/js-apis-zlib.md#compress12)将其压缩到一个目的缓冲区中，使用接口[compressBound()](../../reference/apis-basic-services-kit/js-apis-zlib.md#compressbound12)计算压缩目的缓冲区大小的上限值，使用接口[uncompress()](../../reference/apis-basic-services-kit/js-apis-zlib.md#uncompress12)对存储压缩数据的缓冲区进行解压。由于解压时无法获取解压后原始数据的大小，为了确认解压后目的缓冲区的大小，需要在压缩前获取原始数据的大小并保存，示例代码如下。

  <!-- @[deflate_and_inflate_003](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/bmsSample/DeflateAndInflate/entry/src/main/ets/pages2/Index.ets) -->

### 未知大小缓冲区的压缩与解压（zlib格式）

针对一个未知大小的缓冲区中的数据，使用接口[deflate()](../../reference/apis-basic-services-kit/js-apis-zlib.md#deflate12)将从一个原始输入流中读取的数据进行压缩，使用接口[inflate()](../../reference/apis-basic-services-kit/js-apis-zlib.md#inflate12)将从一个压缩输入流中读取的数据进行解压，示例代码如下。

  <!-- @[deflate_and_inflate_004](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/bmsSample/DeflateAndInflate/entry/src/main/ets/pages3/Index.ets) -->


### 未知大小缓冲区的压缩与解压（gzip格式）

采用gzip格式，针对一个未知大小的缓冲区中的数据，使用接口[deflate()](../../reference/apis-basic-services-kit/js-apis-zlib.md#deflate12)将从一个原始输入流中读取的数据进行压缩，使用接口[inflate()](../../reference/apis-basic-services-kit/js-apis-zlib.md#inflate12)将从一个压缩输入流中读取的数据进行解压，示例代码如下。

  <!-- @[deflate_and_inflate_005](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/bmsSample/DeflateAndInflate/entry/src/main/ets/pages4/Index.ets) -->


## 常见问题

1. 17800005 传入的数据错误

   可能原因和处理步骤，请参见[错误码17800005](../../reference/apis-basic-services-kit/errorcode-zlib.md#17800005-传入的数据错误)。

2. 17800007 传入的缓冲区错误

   可能原因和处理步骤，请参见[错误码17800007](../../reference/apis-basic-services-kit/errorcode-zlib.md#17800007-传入的缓冲区错误)。