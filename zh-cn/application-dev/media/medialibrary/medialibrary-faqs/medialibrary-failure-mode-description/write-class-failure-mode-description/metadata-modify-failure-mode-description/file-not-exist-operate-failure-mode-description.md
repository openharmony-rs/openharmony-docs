# 操作的文件不存在故障模式说明
<!--Kit: Media Library Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @zhaochang14-->
<!--Designer: @liweilu1-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

## 根因描述

开发者在调用Media Library Kit接口时，操作的文件不存在导致接口返回错误码13900002（no such file）。常见于查询的文件不存在等场景。

## 问题分析思路

此类问题，通常情况下可能是查询的文件不存在。

问题分析步骤：

1. 检查传入的URI对应的文件是否真实存在。

2. 确认文件是否被删除或移动到回收站。

3. 检查文件路径是否正确，URI格式是否符合要求。

4. 查看媒体库数据库中的记录是否与实际文件一致。

## 关键字

关键字：

- 错误码：13900002
- 错误信息：no such file

## 案例分析

### 问题现象

操作不存在的文件报13900002错误。

### 问题分析

**根因分析**

调用addResource添加资源文件时，传入的文件路径不存在，报错13900002，原因是addResource要求文件必须真实存在，需要使用沙箱路径下实际存在的文件。

**分析步骤**

1. 检查传入的文件路径，确认addResource传入的文件路径是否真实存在。

   - 检查文件是否存在。

     ```typescript
     const request = new photoAccessHelper.MediaAssetChangeRequest(asset);
     request.addResource(photoAccessHelper.ResourceType.IMAGE_RESOURCE, '/data/storage/el2/base/haps/notexist.jpg');
     await phAccessHelper.applyChanges(request);
     ```

   - 结果：传入的文件路径/data/storage/el2/base/haps/notexist.jpg不存在。

2. 验证文件是否在应用的沙箱目录（/data/storage/el2/base/haps/）下。

   - 检查沙箱目录结构。

     ```log
     沙箱路径格式：file://com.example.kittest/data/storage/el2/base/haps/entry/files/xxx.jpg
     或：/data/storage/el2/base/haps/entry/files/xxx.jpg
     ```

   - 结果：文件需要在应用的沙箱目录下存在。

3. 使用正确文件路径，使用实际存在的文件路径或先创建测试文件。

   - 使用实际存在的文件路径。

     ```typescript
     request.addResource(photoAccessHelper.ResourceType.IMAGE_RESOURCE,
         'file://com.example.kittest/data/storage/el2/base/haps/entry/files/IMG_1778242026_010.jpg');
     ```

   - 结果：使用正确的文件路径后，addResource可以正常执行。

4. 验证修复，确认修复后接口正常返回。

   - 使用存在的文件路径调用addResource。

   - 结果：文件存在时，addResource正常执行。


### 复现代码

```typescript
// 案例：文件从回收站恢复后URI已失效。
// 错误码： 13900002 - 文件不存在。

const TAG = 'Case_FileNotExist';

async trigger13900002Error21(context: common.Context): Promise<void> {
  const phAccessHelper = photoAccessHelper.getPhotoAccessHelper(context);

  // 先创建一个测试文件用于后续正确示例。
  let testFilePath = '';
  try {
    const request = photoAccessHelper.MediaAssetChangeRequest.createAssetRequest(
      context, photoAccessHelper.PhotoType.IMAGE, 'jpg', {subtype:photoAccessHelper.PhotoSubtype.DEFAULT}
    );
    await request.addResource(photoAccessHelper.ResourceType.IMAGE_RESOURCE,
      'file://com.example.kittest/data/storage/el2/base/haps/entry/files/IMG_1778242026_010.jpg');
    await phAccessHelper.applyChanges(request);
    console.info(TAG, 'Test file created successfully');
  } catch (err) {
    console.info(TAG, 'Failed to create test file, may already exist');
  }

  // 获取一个有效资产。
  const fetchResult = await phAccessHelper.getAssets({
    fetchColumns: ['uri'],
    predicates: new dataSharePredicates.DataSharePredicates()
  });

  if (fetchResult.getCount() > 0) {
    const asset = await fetchResult.getFirstObject();
    fetchResult.close();

    // 错误示例：添加不存在的资源文件。
    try {
      console.info(TAG, 'Test1: add non-existent resource');
      const request = new photoAccessHelper.MediaAssetChangeRequest(asset);
      request.addResource(photoAccessHelper.ResourceType.IMAGE_RESOURCE, '/data/storage/el2/base/haps/notexist.jpg');
      await phAccessHelper.applyChanges(request);
    } catch (err) {
      const error = err as BusinessError;
      console.error(TAG, 'Test1 Error code:', error.code);
      console.error(TAG, 'Test1 Error message:', error.message);
    }

    // 正确示例：添加存在的资源文件。
    try {
      console.info(TAG, 'Test2: add existing resource correctly');
      const request = new photoAccessHelper.MediaAssetChangeRequest(asset);
      // 使用实际存在的文件路径。
      request.addResource(photoAccessHelper.ResourceType.IMAGE_RESOURCE,
        'file://com.example.kittest/data/storage/el2/base/haps/entry/files/IMG_1778242026_010.jpg');
      await phAccessHelper.applyChanges(request);
      console.info(TAG, 'Test2: add resource success');
    } catch (err) {
      const error = err as BusinessError;
      console.error(TAG, 'Test2 Error code:', error.code);
      console.error(TAG, 'Test2 Error message:', error.message);
    }
  } else {
    fetchResult.close();
    console.info(TAG, 'No assets to test');
  }
}
```

### 日志信息


```log
I     Case_FileNotExist Test file created successfully
I     Case_FileNotExist Test1: add non-existent resource
E     Case_FileNotExist Test1 Error code: 13900002
E     Case_FileNotExist Test1 Error message: no such file
I     Case_FileNotExist Test2: add existing resource correctly
I     Case_FileNotExist Test2: add resource success
```

### 常见易错代码

```typescript
// 错误：使用不存在的文件路径调用addResource。
const request = new photoAccessHelper.MediaAssetChangeRequest(asset);
request.addResource(photoAccessHelper.ResourceType.IMAGE_RESOURCE, '/data/storage/el2/base/haps/notexist.jpg');
await phAccessHelper.applyChanges(request);

// 正确：使用实际存在的文件路径。
const request = new photoAccessHelper.MediaAssetChangeRequest(asset);
request.addResource(photoAccessHelper.ResourceType.IMAGE_RESOURCE,
  'file://com.example.kittest/data/storage/el2/base/haps/entry/files/existing_file.jpg');
await phAccessHelper.applyChanges(request);
```

## 常见易错代码预防建议

1. 在操作文件前先检查文件是否存在。

2. 使用try-catch捕获文件不存在异常。

3. 对于Picker返回的URI，注意用户可能已删除该文件。

4. 定期刷新文件URI，避免使用过期URI。

5. 使用媒体库API检查文件有效性。