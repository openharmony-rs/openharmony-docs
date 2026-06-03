# 存储IO失败故障模式说明
<!--Kit: Media Library Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @zhaochang14-->
<!--Designer: @liweilu1-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

## 根因描述

开发者在调用Media Library Kit接口时，存储I/O失败导致接口返回错误码13900002（no such file）。常见于操作的文件不存在等场景。

## 问题分析思路

此类问题，通常情况下是操作的文件不存在。

问题分析步骤：

1. 查看错误码信息，确认内部错误的具体类型。

2. 检查数据库操作是否正常，查询是否成功。

3. 查看系统资源是否充足，如内存、文件描述符等。

4. 检查媒体库服务是否正常运行。

## 关键字

日志关键字：

- 错误码：13900002
- 错误信息：no such file

## 案例分析

### 问题现象

应用通过Media Library Kit接口查询媒体文件后，使用文件系统API（fs.statSync）访问文件时返回13900002错误：No such file or directory。

### 问题分析

**根因分析**

使用Media Library Kit接口查询媒体文件URI后，通过文件系统API（fs.statSync）访问该文件时报错13900002（No such file or directory）。原因是URI对应的文件已被删除或移动，或者直接访问了不存在的文件路径。

**分析步骤**

1. 检查文件状态，确认文件是否被删除或移动。

   - 检查URI对应的实际文件是否存在。

     ```bash
     ls -la file://media/Photo/220/IMG_1779157664_125/IMG_20260519_102604_3.jpg
     ```

   - 结果：文件不存在或路径已变更。

2. 检查URI有效性，确认URI对应的资源是否存在。

   - 通过Media Library Kit API重新查询该资源。

     ```typescript
     const fetchResult = await phAccessHelper.getAssets({
       fetchColumns: ['uri', 'display_name'],
       predicates: new dataSharePredicates.DataSharePredicates()
     });
     ```

   - 结果：资源已从媒体库中删除，getAssets无法返回该记录。

3. 检查访问方式，确认使用正确的API访问媒体文件。

   - 对比文件系统API与媒体库API的访问差异。

   - fs.statSync()：直接访问文件系统，文件不存在即报错。

   - Media Library Kit API：通过数据库记录访问，有缓存机制。

   - 结论：直接使用文件系统API访问URI时，未做文件存在性校验。

4. 验证修复，重新调用确认操作正常。

   - 修复后使用媒体库API访问。

     ```typescript
     const fetchResult = await phAccessHelper.getAssets({...});
     if (fetchResult.getCount() > 0) {
       const asset = await fetchResult.getFirstObject();
       // 使用asset对象进行后续操作。
     }
     ```

   - 结果：使用媒体库API后，不再出现13900002错误。

### 复现代码

```typescript
// 案例：存储I/O失败：fs.stat()报错13900002 No such file or directory。
// 错误码： 13900002 - 文件不存在。
// 说明：使用文件系统API访问不存在的文件时触发错误。

import fs from '@ohos.file.fs';

const TAG = 'Case_StorageIO';

async triggerStorageIOError(context: common.Context): Promise<void> {
  const phAccessHelper = photoAccessHelper.getPhotoAccessHelper(context);

  // 测试1：使用getAssets获取URI，然后用fs.statSync()访问。
  // 如果文件不存在，fs.statSync()会触发13900002。
  try {
    console.info(TAG, 'Test1: get asset then access with fs');
    const fetchResult = await phAccessHelper.getAssets({
      fetchColumns: ['uri', 'display_name'],
      predicates: new dataSharePredicates.DataSharePredicates()
    });

    if (fetchResult.getCount() > 0) {
      const asset = await fetchResult.getFirstObject();
      const uri = asset.uri;
      console.info(TAG, 'Test1 Asset uri:', uri);
      fetchResult.close();

      // 用fs.statSync()访问文件。
      // 如果文件已被删除或移动，会触发13900002。
      try {
        let stat: fs.Stat = fs.statSync(uri);
        console.info(TAG, 'Test1 stat success');
      } catch (statErr) {
        const error = statErr as BusinessError;
        console.error(TAG, 'Test1 fs.statSync Error code:', error.code);
        console.error(TAG, 'Test1 fs.statSync Error message:', error.message);
      }
    } else {
      fetchResult.close();
      console.info(TAG, 'Test1 No assets');
    }
  } catch (err) {
    const error = err as BusinessError;
    console.error(TAG, 'Test1 Error code:', error.code);
    console.error(TAG, 'Test1 Error message:', error.message);
  }

  // 测试2：直接用fs.statSync()访问不存在的URI。
  try {
    console.info(TAG, 'Test2: fs.statSync with non-existent file');
    let stat: fs.Stat = fs.statSync('file://media/photo/999999999/nonexistent.jpg');
    console.info(TAG, 'Test2 stat success');
  } catch (statErr) {
    const error = statErr as BusinessError;
    console.error(TAG, 'Test2 fs.statSync Error code:', error.code);
    console.error(TAG, 'Test2 fs.statSync Error message:', error.message);
  }

  // 正确示例：使用媒体库API访问资源。
  try {
    console.info(TAG, 'Correct: use media library API');
    const fetchResult = await phAccessHelper.getAssets({
      fetchColumns: ['uri', 'display_name'],
      predicates: new dataSharePredicates.DataSharePredicates()
    });
    console.info(TAG, 'Correct Count:', fetchResult.getCount());
    fetchResult.close();
  } catch (err) {
    const error = err as BusinessError;
    console.error(TAG, 'Correct Error code:', error.code);
    console.error(TAG, 'Correct Error message:', error.message);
  }
}
```

### 日志信息

```log
I     Case_StorageIO Test1: get asset then access with fs
I     Case_StorageIO Test1 Asset uri: file://media/Photo/220/IMG_1779157664_125/IMG_20260519_102604_3.jpg
I     Case_StorageIO Test1 stat success
I     Case_StorageIO Test2: fs.statSync with non-existent file
E     Case_StorageIO Test2 fs.statSync Error code: 13900002
E     Case_StorageIO Test2 fs.statSync Error message: No such file or directory
I     Case_StorageIO Correct: use media library API
I     Case_StorageIO Correct Count: 4
```

### 常见易错代码

```typescript
// 错误：直接使用fs访问URI，未检查文件是否存在。
let stat: fs.Stat = fs.statSync('file://media/photo/999999999/nonexistent.jpg');

// 正确：使用媒体库API访问资源。
const fetchResult = await phAccessHelper.getAssets({
  fetchColumns: ['uri', 'display_name'],
  predicates: new dataSharePredicates.DataSharePredicates()
});
if (fetchResult.getCount() > 0) {
  const asset = await fetchResult.getFirstObject();
  // 使用asset对象进行后续操作。
}
```

## 常见易错代码预防建议

1. 在操作文件前先检查文件是否存在。

2. 使用try-catch捕获文件不存在异常。

3. 对于Picker返回的URI，注意用户可能已删除该文件。

4. 定期刷新文件URI，避免使用过期URI。

5. 使用媒体库查询类API检查文件有效性。
