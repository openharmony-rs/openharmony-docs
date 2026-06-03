# 权限授权错误故障模式说明
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

1. 检查调用接口时传入的参数是否完整、类型是否正确、格式是否符合要求。

2. 查看错误码信息，确认参数验证失败的具体原因。

3. 检查NAPI层日志，定位具体是哪个参数校验失败。

4. 根据日志中的具体错误信息，修复对应的参数问题。

## 关键字

日志关键字：

- 错误码：201/13900012，部分接口在API version 13及之前的版本，无相关权限返回错误码13900012；从API version 14开始，无相关权限返回错误码201或13900012（Permission denied）。
- 错误信息：Permission denied

## 案例分析

### 问题现象

未配置读权限时查询资产报错。

### 问题分析

**根因分析**

调用getAssets查询媒体资源时报错201（Permission denied），原因是应用未在module.json5中配置ohos.permission.READ_IMAGEVIDEO权限。

**分析步骤**

1. 检查错误码和错误信息，确认返回的具体错误类型。

   - 检查错误日志。

     ```log
     errCode=201, errMsg=Permission denied
     ```

   - 结果：确认错误码为201，错误信息表明权限被拒绝。

2. 检查应用权限配置，确认应用是否已声明所需权限。

   - 检查module.json5中的权限配置。

     ```json
     "requestPermissions": [
       {
         "name": "ohos.permission.READ_IMAGEVIDEO"
       }
     ]
     ```

   - 结果：应用未在module.json5中配置ohos.permission.READ_IMAGEVIDEO权限。

3. 检查权限授予状态，确认用户是否已授予对应权限。

   - 检查系统设置中的权限状态，确认用户已在系统设置中授予对应权限。

   - 结果：权限未授予或被拒绝。

4. 验证修复，确认修复后接口正常返回。

   - 在module.json5中添加权限配置后重新运行应用。

     ```json
     "requestPermissions": [
       {
         "name": "ohos.permission.READ_IMAGEVIDEO"
       }
     ]
     ```

   - 结果：配置权限后，接口正常返回查询结果。

### 复现代码

```typescript
const TAG = 'Case_Permission';

async trigger201Error(context: common.Context): Promise<void> {
  const phAccessHelper = photoAccessHelper.getPhotoAccessHelper(context);

  // 错误示例：未配置读权限时尝试查询资产。
  try {
    console.info(TAG, 'Test: query assets without read permission');
    const fetchOptions: photoAccessHelper.FetchOptions = {
      fetchColumns: ['uri', 'display_name'],
      predicates: new dataSharePredicates.DataSharePredicates()
    };
    const fetchResult = await phAccessHelper.getAssets(fetchOptions);
    console.info(TAG, 'Query success, count:', fetchResult.getCount());
    fetchResult.close();
  } catch (err) {
    console.error(TAG, 'Error code:', (err as BusinessError).code);    // 输出： 201。
    console.error(TAG, 'Error message:', (err as BusinessError).message);  // Permission denied
  }
}
```

### 日志信息


```log
I     Case_Permission Test: query assets without read permission
E     Case_Permission Error code: 201
E     Case_Permission Error message: Permission denied
// 申请权限后。
I     Case_Permission Test: query assets without read permission
I     Case_Permission Query success, count: 3
```

### 常见易错代码

```typescript
// 错误：未配置权限直接调用媒体库API。
const fetchOptions: photoAccessHelper.FetchOptions = {
  fetchColumns: ['uri', 'display_name'],
  predicates: new dataSharePredicates.DataSharePredicates()
};
const fetchResult = await phAccessHelper.getAssets(fetchOptions);

// 正确：确保已配置所需权限。
// 1. 在module.json5中配置权限。
"requestPermissions": [
   {
     "name": "ohos.permission.READ_IMAGEVIDEO"
   }
 ]
// 2. 运行时动态申请权限（如需要）。
```

## 常见易错代码预防建议

1. 在module.json5中正确配置所需权限。

2. 调用受保护API前先使用permissionsVerify检查权限。

3. 引导用户在系统设置中授予权限。

4. 处理权限被拒绝的场景，提供备选方案。

5. 隐私政策不允许静默保存，需要用户主动授权。
