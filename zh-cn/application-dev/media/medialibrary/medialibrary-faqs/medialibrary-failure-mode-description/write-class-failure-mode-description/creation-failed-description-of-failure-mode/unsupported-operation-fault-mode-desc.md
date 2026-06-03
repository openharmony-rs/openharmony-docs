# 不支持的操作故障模式说明
<!--Kit: Media Library Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @zhaochang14-->
<!--Designer: @liweilu1-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

## 根因描述

开发者在调用Media Library Kit接口时，执行了不支持的操作导致接口返回错误。

常见的不支持操作包括：

1. 对动态照片（Moving Photo）执行不支持的操作。

2. 对不支持的资源类型执行写入操作。

3. 空指针或无效对象引用。

4. 文件类型与ResourceType不匹配的操作。

典型错误码：401 (Failed to check resourceType)、13900020 (invalid parameter)。

## 问题分析思路

问题原因：

1. 对动态照片（Moving Photo）执行不支持的操作。

2. 对不支持的资源类型执行写入操作（如对现有资产使用addResource）。

3. 空指针或无效对象引用。

4. 文件类型与ResourceType不匹配（如IMAGE_RESOURCE使用.mp4文件）。

问题分析步骤：

1. 确认操作对象的类型（IMAGE、VIDEO、MovingPhoto）。

2. 检查使用的ResourceType是否与资产类型匹配。

3. 检查是否对现有资产错误使用addResource。

4. 检查文件路径是否有效、文件类型是否正确。

5. 查看NAPI层日志，确认不支持的具体原因。

6. 根据错误信息和文档确认正确的使用方法。

## 关键字

关键字：

- 错误码：401=Failed to check resourceType
- 错误信息：Failed to check resourceType

## 案例分析

### 问题现象

调用Media Library Kit接口时返回错误码401（Failed to check resourceType），原因是ResourceType与photoType不匹配。

### 问题分析

**根因分析**

调用addResource添加资源时，传入的ResourceType与创建的资产类型不匹配，报错401，原因是创建IMAGE类型资产却使用VIDEO_RESOURCE。

**分析步骤**

1. 确认创建的资产类型，确认使用createAssetRequest创建的资产类型是IMAGE还是VIDEO。

   - 检查createAssetRequest参数。

     ```typescript
     const request = photoAccessHelper.MediaAssetChangeRequest.createAssetRequest(context,
       photoAccessHelper.PhotoType.IMAGE, 'jpg', { title: 'test' });
     ```

   - 结果：确认创建的资产类型为IMAGE。

2. 检查使用的ResourceType，确认addResource使用的ResourceType是否与资产类型匹配。

   - 检查addResource调用。

      ```typescript
      request.addResource(photoAccessHelper.ResourceType.VIDEO_RESOURCE, imageFileUri);
      ```

   - 结果：IMAGE类型资产却使用了VIDEO_RESOURCE，类型不匹配。

3. 使用正确的ResourceType，使用与资产类型匹配的ResourceType。

   - 正确的ResourceType使用。

     ```typescript
     request.addResource(photoAccessHelper.ResourceType.IMAGE_RESOURCE, imageFileUri);
     ```

   - 结果：IMAGE类型资产使用IMAGE_RESOURCE后，接口正常执行。

4. 验证修复，确认修复后接口正常返回。

   - 使用正确的ResourceType调用addResource。

   - 结果：ResourceType与photoType匹配时，addResource正常执行。

### 复现代码

```typescript
// 案例：ResourceType与photoType不匹配。
// 错误码： 401 - Failed to check resourceType。

const TAG = 'Case_ResourceTypeMismatch';

async trigger401Error17(context: common.Context): Promise<void> {
  const phAccessHelper = photoAccessHelper.getPhotoAccessHelper(context);
  const imageFileUri = 'file://' + context.filesDir + '/IMG_1778242026_010.jpg';
  
  // 错误示例：创建IMAGE类型资产却使用VIDEO_RESOURCE。
  try {
    console.info(TAG, 'Error: create IMAGE with VIDEO_RESOURCE (type mismatch)');
    const request: photoAccessHelper.MediaAssetChangeRequest = 
      photoAccessHelper.MediaAssetChangeRequest.createAssetRequest(context,
        photoAccessHelper.PhotoType.IMAGE, 'jpg', { title: 'test' });
    request.addResource(photoAccessHelper.ResourceType.VIDEO_RESOURCE, imageFileUri);
    await phAccessHelper.applyChanges(request);
  } catch (err) {
    const error = err as BusinessError;
    console.error(TAG, 'Error code:', error.code);
    console.error(TAG, 'Error message:', error.message);
  }
  
  // 正确示例：创建IMAGE类型资产使用IMAGE_RESOURCE。
  try {
    console.info(TAG, 'Correct: create IMAGE with IMAGE_RESOURCE');
    const request: photoAccessHelper.MediaAssetChangeRequest = 
      photoAccessHelper.MediaAssetChangeRequest.createAssetRequest(context,
        photoAccessHelper.PhotoType.IMAGE, 'jpg', { title: 'test_ok' });
    request.addResource(photoAccessHelper.ResourceType.IMAGE_RESOURCE, imageFileUri);
    await phAccessHelper.applyChanges(request);
    console.info(TAG, 'Correct: succeed');
  } catch (err) {
    const error = err as BusinessError;
    console.error(TAG, 'Correct Error code:', error.code);
    console.error(TAG, 'Correct Error message:', error.message);
  }
}
```

### 日志信息

```log
I Case_ResourceTypeMismatch Error: create IMAGE with VIDEO_RESOURCE (type mismatch)
E Case_ResourceTypeMismatch Error code: 401
E Case_ResourceTypeMismatch Error message: Failed to check resourceType
I Case_ResourceTypeMismatch Correct: create IMAGE with IMAGE_RESOURCE
I Case_ResourceTypeMismatch Correct: succeed
```

### 常见易错代码

```typescript
// 错误：创建IMAGE类型资产却使用VIDEO_RESOURCE作参数。
const request = photoAccessHelper.MediaAssetChangeRequest.createAssetRequest(context,
  photoAccessHelper.PhotoType.IMAGE, 'jpg', { title: 'test' });
request.addResource(photoAccessHelper.ResourceType.VIDEO_RESOURCE, imageFileUri);
await phAccessHelper.applyChanges(request);

// 正确：创建IMAGE类型资产使用IMAGE_RESOURCE作参数。
const request = photoAccessHelper.MediaAssetChangeRequest.createAssetRequest(context,
  photoAccessHelper.PhotoType.IMAGE, 'jpg', { title: 'test' });
request.addResource(photoAccessHelper.ResourceType.IMAGE_RESOURCE, imageFileUri);
await phAccessHelper.applyChanges(request);
```

## 常见易错代码预防建议

1. addResource仅用于创建新资产（配合createAssetRequest），不支持修改现有资产。

2. ResourceType必须与photoType匹配：IMAGE用IMAGE_RESOURCE作参数，VIDEO用VIDEO_RESOURCE作参数。

3. 使用前先确认资产的photoType类型。

4. 确保文件路径有效且文件真实存在。

5. 文件类型必须与ResourceType匹配：IMAGE_RESOURCE使用.jpg/.png等图片文件，VIDEO_RESOURCE使用.mp4等视频文件。

6. 对MovingPhoto操作时需同时提供图片和视频。
