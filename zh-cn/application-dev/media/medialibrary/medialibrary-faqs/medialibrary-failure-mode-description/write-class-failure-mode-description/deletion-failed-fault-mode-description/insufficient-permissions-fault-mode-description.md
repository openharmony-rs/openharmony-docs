# 权限不足故障模式说明
<!--Kit: Media Library Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @zhaochang14-->
<!--Designer: @liweilu1-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

## 根因描述

开发者在调用Media Library Kit接口时，权限不足导致接口返回错误码201（Permission denied）。常见于没有媒体库访问权限等场景。

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

关键字：

- 错误码：201
- 错误信息：Permission denied

## 案例分析

### 问题现象

用户拒绝授权导致权限不足。

### 问题分析

**根因分析**

创建资产场景，报201错误码，原因是应用未配置或未获得所需权限。

**分析步骤**

1. 检查权限申请，确认应用是否已声明所需权限。

   - 检查module.json5中的权限配置。

     ```json
     "requestPermissions": [
       {
         "name": "ohos.permission.READ_IMAGEVIDEO"
       },
       {
         "name": "ohos.permission.WRITE_IMAGEVIDEO"
       }
     ]
     ```

   - 结果：确认应用已在module.json5中声明所需权限（ohos.permission.READ_IMAGEVIDEO等）。

2. 检查权限授予，确认用户是否已授予对应权限。

   - 检查系统设置中的权限状态，确认用户已授予对应权限，可在系统设置中查看权限状态。

   - 结果：用户已授予对应权限。

3. 检查权限方式，确认使用的是正确的权限申请方式。

   - 检查权限申请代码。

     ```typescript
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
     atManager.requestPermissionsFromUser(context, ['ohos.permission.WRITE_IMAGEVIDEO'], (err: BusinessError, data: PermissionRequestResult) => {
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

   - 结果：配置权限后，创建资产接口正常执行。

### 复现代码

```typescript
// 案例：用户拒绝授权导致权限不足。
// 错误码： 201 - 权限不足。

const TAG = 'Case_PermissionDenied';

async triggerPermissionDeniedError(context: common.Context): Promise<void> {
  const phAccessHelper = photoAccessHelper.getPhotoAccessHelper(context);

  // 错误示例：使用deleteAssets删除资产（无权限时）。
  try {
    console.info(TAG, 'Test1: delete asset without permission');
    const fetchResult = await phAccessHelper.getAssets({
      fetchColumns: ['uri'],
      predicates: new dataSharePredicates.DataSharePredicates()
    });
    if (fetchResult.getCount() > 0) {
      const asset = await fetchResult.getFirstObject();
      await photoAccessHelper.MediaAssetChangeRequest.deleteAssets(context, [asset]);
      console.info(TAG, 'Delete success');
    }
    fetchResult.close();
  } catch (err) {
    const error = err as BusinessError;
    console.error(TAG, 'Error code:', error.code);
    console.error(TAG, 'Error message:', error.message);
  }
}
```

### 日志信息


```log
I     Case_PermissionDenied Test1: delete asset without permission
E     Case_PermissionDenied Error code: 201
E     Case_PermissionDenied Error message: Permission denied
// 申请权限后。
I     Case_PermissionDenied Test1: delete asset without permission
I     Case_PermissionDenied Delete success
```

### 常见易错代码

```typescript
// 错误：在未申请权限的情况下调用受保护API。
const fetchResult = await phAccessHelper.getAssets({...});

// 正确：先申请权限再调用受保护API。
let atManager: abilityAccessCtrl.AtManager = abilityAccessCtrl.createAtManager();
let context: Context = this.getUIContext().getHostContext() as common.UIAbilityContext;
atManager.requestPermissionsFromUser(context, ['ohos.permission.READ_IMAGEVIDEO'], (err: BusinessError, data: PermissionRequestResult) => {
  if (err) {
    console.error(TAG + `requestPermissionsFromUser fail, err->${JSON.stringify(err)}`);
  } else {
    console.info(TAG + 'data:' + JSON.stringify(data));
    console.info(TAG + 'data permissions:' + data.permissions);
    console.info(TAG + 'data authResults:' + data.authResults);
    console.info(TAG + 'data dialogShownResults:' + data.dialogShownResults);
  }
});
atManager.requestPermissionsFromUser(context, ['ohos.permission.WRITE_IMAGEVIDEO'], (err: BusinessError, data: PermissionRequestResult) => {
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

## 常见易错代码预防建议

1. 在module.json5中正确配置所需权限。

2. 调用受保护API前先使用permissionsVerify检查权限。

3. 引导用户在系统设置中授予权限。

4. 处理权限被拒绝的场景，提供备选方案。

5. 隐私政策不允许静默保存，需要用户主动授权。

6. 使用requestPermissionsFromUser回调方式申请权限。