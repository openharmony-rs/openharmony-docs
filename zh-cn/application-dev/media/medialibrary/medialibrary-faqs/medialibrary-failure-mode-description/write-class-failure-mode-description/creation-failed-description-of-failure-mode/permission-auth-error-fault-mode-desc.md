# 权限授权失败故障模式说明
<!--Kit: Media Library Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @zhaochang14-->
<!--Designer: @liweilu1-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

## 根因描述

开发者在调用Media Library Kit接口时，权限/授权错误导致接口返回错误码201/13900012。

部分接口在API version 13及之前的版本，无相关权限返回错误码13900012。

从API version 14开始，无相关权限返回错误码201或13900012（Permission denied）。

以上情况常见于没有媒体库访问权限等场景。

## 问题分析思路

问题原因：

1. 没有媒体库访问权限。

2. 没有相册访问权限。

3. 系统应用验证失败。

问题分析步骤：

1. 检查应用是否已申请并获得媒体库访问权限。

2. 查看错误码信息，确认是缺少权限还是权限被拒绝。

3. 检查权限申请流程是否正确，包括权限申请和用户授权。

4. 根据日志确认权限验证的具体失败点。

## 关键字

日志关键字：

- 错误码：201（API version 14开始）。
- 错误信息：Permission denied

## 案例分析

### 问题现象

创建资产时无权限报13900012/201错误码。

### 问题分析

**根因分析**

创建资产场景，报201错误码，原因是应用未配置或未获得所需权限（ohos.permission.READ_MEDIA等）。

**分析步骤**

1. 检查权限申请，确认应用是否已声明所需权限。

   - 检查module.json5中的权限配置。

     ```json
     "requestPermissions": [
       {
         "name": "ohos.permission.READ_MEDIA"
       },
       {
         "name": "ohos.permission.WRITE_MEDIA"
       }
     ]
     ```

   - 结果：确认应用已在module.json5中声明所需权限（ohos.permission.READ_MEDIA等）。

2. 检查权限授予，确认用户是否已授予对应权限。

   - 检查系统设置中的权限状态，确认用户已授予对应权限，可在系统设置中查看权限状态。

   - 结果：用户已授予对应权限。

3. 检查权限方式，确认使用的是正确的权限申请方式。

   - 检查权限申请代码。

     ```typescript
     // 动态申请权限（正确方式）。
     let atManager: abilityAccessCtrl.AtManager = abilityAccessCtrl.createAtManager();
     let context: Context = this.getUIContext().getHostContext() as common.UIAbilityContext;
     atManager.requestPermissionsFromUser(context, ['ohos.permission.READ_IMAGEVIDEO'], (err: BusinessError, data:  PermissionRequestResult) => {
       if (err) {
         console.error(TAG + `requestPermissionsFromUser fail, err->${JSON.stringify(err)}`);
       } else {
         console.info(TAG + 'data:' + JSON.stringify(data));
         console.info(TAG + 'data permissions:' + data.permissions);
         console.info(TAG + 'data authResults:' + data.authResults);
         console.info(TAG + 'data dialogShownResults:' + data.dialogShownResults);
       }
     });
     atManager.requestPermissionsFromUser(context, ['ohos.permission.WRITE_IMAGEVIDEO'], (err: BusinessError, data:  PermissionRequestResult) => {
       if (err) {
         console.error(TAG + `requestPermissionsFromUser fail, err->${JSON.stringify(err)}`);
       } else {
         console.info(TAG + 'data:' + JSON.stringify(data));
         console.info(TAG + 'data permissions:' + data.permissions);
         console.info(TAG + 'data authResults:' + data.authResults);
         console.info(TAG + 'data dialogShownResults:' + data.dialogShownResults);
       }
     });
     ```

   - 结果：确认使用的是正确的权限申请方式（动态申请+权限弹窗）。

4. 验证修复，确认修复后接口正常返回。

   - 添加权限后重新运行应用，确认功能正常。

   - 结果：配置权限后，创建资产接口正常返回。

### 复现代码

```typescript
// 案例：调用createAssetRequest创建资产时无权限。
// 错误码： 201 - Permission denied

const TAG = 'Case_AuthFailed';

async triggerAuthFailedError(context: common.Context): Promise<void> {
  const phAccessHelper = photoAccessHelper.getPhotoAccessHelper(context);

  // 错误示例：使用createAssetRequest创建资产（无WRITE_MEDIA权限时），注意目录下要有对应文件，否则会报文件不存在错误码。
  try {
    console.info(TAG, 'Test1: create asset without permission');
    const request = photoAccessHelper.MediaAssetChangeRequest.createAssetRequest(
      context, photoAccessHelper.PhotoType.IMAGE, 'jpg', {subtype:photoAccessHelper.PhotoSubtype.DEFAULT}
    );
    await request.addResource(photoAccessHelper.ResourceType.IMAGE_RESOURCE,
      'file://com.example.kittest/data/storage/el2/base/haps/entry/files/IMG_1778242026_010.jpg');
    await phAccessHelper.applyChanges(request);
    console.info(TAG, 'Create success');
  } catch (err) {
    const error = err as BusinessError;
    console.error(TAG, 'Error code:', error.code);
    console.error(TAG, 'Error message:', error.message);
  }
}
```

### 日志信息

```log
E     Case_AuthFailed Error code: 201
E     Case_AuthFailed Error message: Permission denied
// 申请权限后。
I     Case_AuthFailed Test1: create asset without permission
I     Case_AuthFailed Create success
```

### 常见易错代码

```typescript
// 错误：未配置权限直接调用创建资产API。
const request = photoAccessHelper.MediaAssetChangeRequest.createAssetRequest(
  context, photoAccessHelper.PhotoType.IMAGE, 'jpg'
);
await phAccessHelper.applyChanges(request);

// 正确：确保已配置所需权限。
// 1. 在module.json5中配置权限。
"requestPermissions": [
 {
   "name": "ohos.permission.READ_MEDIA"
 },
 {
   "name": "ohos.permission.WRITE_MEDIA"
 }
]
// 2. 运行时动态申请权限。
```

## 常见易错代码预防建议

1. 在module.json5中正确配置所需权限。

2. 调用受保护API前先使用permissionsVerify检查权限。

3. 引导用户在系统设置中授予权限。

4. 处理权限被拒绝的场景，提供备选方案。

5. 隐私政策不允许静默保存，需要用户主动授权。
