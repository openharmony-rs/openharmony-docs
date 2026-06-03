# 用户文件管理器模块参数错误故障模式说明
<!--Kit: Media Library Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @zhaochang14-->
<!--Designer: @liweilu1-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

## 根因描述

开发者在调用Media Library Kit接口时，用户文件管理器模块参数错误导致接口返回错误码14000002（invalid parameter）。常见于URI为空字符串等场景。

## 问题分析思路

问题原因：

1. URI为空字符串。

2. URI格式根本性错误（如不是 photo/audio URI）。

3. URI结构不合法。

4. 底层返回E_URI_INVALID、E_INVALID_URI等错误。

问题分析步骤：

1. 检查调用接口时传入的参数是否完整、类型是否正确、格式是否符合要求。

2. 查看错误码信息，确认参数验证失败的具体原因。

3. 检查NAPI层日志，定位具体是哪个参数校验失败。

4. 根据日志中的具体错误信息，修复对应的参数问题。

## 关键字

日志关键字：

- 错误码：14000002
- 错误信息：invalid parameter

## 案例分析

### 问题现象

自行构造URI导致创建资产失败。

### 问题分析

**根因分析**

使用沙箱路径（如/data/storage/el2/base/haps/test.jpg）调用deleteAssets时报错14000002（operation not support），原因是deleteAssets要求URI必须以file://media/Photo/开头，沙箱路径不符合要求。

**分析步骤**

1. 检查URI格式，确认deleteAssets要求URI的格式。

   - 检查URI格式要求。

     ```log
     有效URI格式：file://media/Photo/xxx/xxx.jpg
     沙箱路径格式：/data/storage/el2/base/haps/entry/files/test.jpg
     ```

   - 结果：deleteAssets要求URI必须以file://media/Photo/开头。

2. 验证URI有效性，确认传入的URI是媒体库URI格式还是沙箱路径。

   - 检查传入的URI。

     ```typescript
     // 错误示例：使用沙箱路径。
     const sandboxUris = ['/data/storage/el2/base/haps/entry/files/test.jpg'];
     await photoAccessHelper.MediaAssetChangeRequest.deleteAssets(context, sandboxUris);
     ```

   - 结果：传入的是沙箱路径，不是媒体库URI格式。

3. 使用正确API，通过getAssets获取有效URI后再进行删除操作。

   - 使用getAssets获取有效URI。

     ```typescript
     const fetchResult = await phAccessHelper.getAssets({
       fetchColumns: ['uri'],
       predicates: new dataSharePredicates.DataSharePredicates()
     });
     if (fetchResult.getCount() > 0) {
       const asset = await fetchResult.getFirstObject();
       console.info(TAG, 'Valid URI format: file://media/Photo/xxx/xxx.jpg');
       console.info(TAG, 'Actual asset URI:', asset.uri);
       await photoAccessHelper.MediaAssetChangeRequest.deleteAssets(context, [asset]);
     }
     ```

   - 结果：使用getAssets获取的有效URI格式为file://media/Photo/xxx/xxx.jpg。

4. 验证修复，确认修复后接口正常返回。

   - 使用正确的媒体库URI进行删除操作。

   - 结果：使用正确的URI格式后，deleteAssets接口正常执行。


### 复现代码

```typescript
// 案例：使用沙箱路径调用deleteAssets导致报错。
// 错误码： 14000002 - Invalid URI。

const TAG = 'Case_URIFormat';

async triggerURIFormatError(context: common.Context): Promise<void> {
  const phAccessHelper = photoAccessHelper.getPhotoAccessHelper(context);

  // 错误示例：使用沙箱路径调用deleteAssets。
  try {
    console.info(TAG, 'Test1: delete assets with sandbox path');
    const sandboxUris = ['/data/storage/el2/base/haps/entry/files/test.jpg'];
    await photoAccessHelper.MediaAssetChangeRequest.deleteAssets(context, sandboxUris);
    console.info(TAG, 'Test1 success');
  } catch (err) {
    const error = err as BusinessError;
    console.error(TAG, 'Test1 Error code:', error.code);
    console.error(TAG, 'Test1 Error message:', error.message);
  }

  // 正确示例：使用媒体库URI调用deleteAssets。
  try {
    console.info(TAG, 'Test2: delete assets with media library URI');
    const fetchResult = await phAccessHelper.getAssets({
      fetchColumns: ['uri'],
      predicates: new dataSharePredicates.DataSharePredicates()
    });
    if (fetchResult.getCount() > 0) {
      const asset = await fetchResult.getFirstObject();
      console.info(TAG, 'Valid URI format: file://media/Photo/xxx/xxx.jpg');
      console.info(TAG, 'Actual asset URI:', asset.uri);
      await photoAccessHelper.MediaAssetChangeRequest.deleteAssets(context, [asset]);
      console.info(TAG, 'Test2 success');
    }
    fetchResult.close();
  } catch (err) {
    const error = err as BusinessError;
    console.error(TAG, 'Test2 Error code:', error.code);
    console.error(TAG, 'Test2 Error message:', error.message);
  }
}
```

### 日志信息


```log
I     Case_URIFormat Test1: delete assets with sandbox path
E     Case_URIFormat Test1 Error code: 14000002
E     Case_URIFormat Test1 Error message: Invalid uri, uri must start with file://media/Photo/
I     Case_URIFormat Test2: delete assets with media library URI
I     Case_URIFormat Valid URI format: file://media/Photo/xxx/xxx.jpg
I     Case_URIFormat Actual asset URI: file://media/Photo/9/IMG_1780494343_008/IMG_20260603_214403.jpg
I     Case_URIFormat Test2 success
```

### 常见易错代码

```typescript
// 错误：使用沙箱路径调用deleteAssets。
const sandboxUris = ['/data/storage/el2/base/haps/entry/files/test.jpg'];
await photoAccessHelper.MediaAssetChangeRequest.deleteAssets(context, sandboxUris);

// 正确：使用媒体库API获取的URI。
const fetchResult = await phAccessHelper.getAssets({
  fetchColumns: ['uri'],
  predicates: new dataSharePredicates.DataSharePredicates()
});
if (fetchResult.getCount() > 0) {
  const asset = await fetchResult.getFirstObject();
  await photoAccessHelper.MediaAssetChangeRequest.deleteAssets(context, [asset]);
}
```

## 常见易错代码预防建议

1. 必须使用PhotoAccessHelper返回的URI，不能自行构造或修改。

2. 在进行文件操作前，验证URI格式是否正确（以file://media/开头）。

3. 使用媒体库API进行文件操作，而非直接使用fs模块操作媒体文件。

4. 定期查阅官方文档，了解URI格式规范。

5. 对于从外部获取的URI，进行格式校验后再使用。