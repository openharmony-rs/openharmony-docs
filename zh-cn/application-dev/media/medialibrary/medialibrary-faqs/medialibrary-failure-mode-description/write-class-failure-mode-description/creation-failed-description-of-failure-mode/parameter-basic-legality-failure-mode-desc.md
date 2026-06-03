# 参数的基本合法性错误故障模式说明
<!--Kit: Media Library Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @zhaochang14-->
<!--Designer: @liweilu1-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

## 根因描述

开发者在调用Media Library Kit接口时，参数的基本合法性（数量、类型、格式）错误导致接口返回错误码401（invalid parameter）。常见于系统级和框架级参数验证等场景。

## 问题分析思路

问题原因：

系统级参数验证：

1. 参数数量验证（如：参数数量不在允许范围内）。

2. 参数类型验证（如：参数不是预期的类型）。

3. 数组长度验证（如：数组长度不符合预期 ）。

4. 数组元素验证（如：数组元素为nullptr或获取失败）。

5. 对象解包验证（如：从napi_value解包对象失败或对象为nullptr）。

6. FormId验证（如：FormId缺失、为空或底层返回不符合预期）。

框架级参数验证：

1. URI格式验证（如：URI不包含指定的前缀）。

2. FetchMode验证（如：FetchMode不是允许的值）。

3. 回调引用验证（如：创建回调引用失败、引用为空或从引用获取值失败）。

4. NAPI操作验证（如：各种NAPI操作失败（获取字符串、整型、数组等））。

问题分析步骤：

1. 检查调用接口时传入的参数是否完整、类型是否正确、格式是否符合要求。

2. 查看错误码信息，确认参数验证失败的具体原因。

3. 检查NAPI层日志，定位具体是哪个参数校验失败。

4. 根据日志中的具体错误信息，修复对应的参数问题。

## 关键字

日志关键字：

- 错误码：401
- 错误信息：invalid parameter

## 案例分析

### 问题现象

调用showAssetsCreationDialog保存图片时报错401。

### 问题分析

**根因分析**

调用showAssetsCreationDialog保存图片时，报401错误码（错误信息Invalid input parameter），原因是srcFileUris参数为空或photoCreationConfigs参数无效。

**分析步骤**

1. 检查参数完整性，确认接口调用时是否传入了所有必填参数。

   - 检查srcFileUris和photoCreationConfigs参数。

     ```typescript
     // 错误示例：传入空srcFileUris。
     const srcFileUris: string[] = [];
     const photoCreationConfigs: photoAccessHelper.PhotoCreationConfig[] = [{
       title: 'test',
       fileNameExtension: 'jpg',
       photoType: photoAccessHelper.PhotoType.IMAGE,
       subtype: photoAccessHelper.PhotoSubtype.DEFAULT,
     }];
     await phAccessHelper.showAssetsCreationDialog(srcFileUris, photoCreationConfigs);
     ```

   - 结果：srcFileUris为空数组，缺少必填参数。

2. 检查参数类型，确认参数类型是否符合API要求。

   - 检查photoCreationConfigs类型。

     ```typescript
     // 错误示例：photoCreationConfigs为空。
     const srcFileUris: string[] = ['/test/image.jpg'];
     const photoCreationConfigs: photoAccessHelper.PhotoCreationConfig[] = [];
     await phAccessHelper.showAssetsCreationDialog(srcFileUris, photoCreationConfigs);
     ```

   - 结果：photoCreationConfigs为空数组，参数类型不正确。

3. 检查配置正确性，确认photoCreationConfigs配置是否正确，module.json是否缺少label和icon配置项。

   - 检查photoCreationConfigs的配置项。

     ```typescript
     const photoCreationConfigs: photoAccessHelper.PhotoCreationConfig[] = [{
       title: 'test',
       fileNameExtension: 'jpg',
       photoType: photoAccessHelper.PhotoType.IMAGE,
       subtype: photoAccessHelper.PhotoSubtype.DEFAULT,
     }];
     ```

   - 结果：photoCreationConfigs配置项完整且有效。

4. 验证修复，确认修复后接口正常返回。

   - 传入有效的参数。

     ```typescript
     const srcFileUris: string[] = ['/test/image.jpg'];
     const photoCreationConfigs: photoAccessHelper.PhotoCreationConfig[] = [{
       title: 'test',
       fileNameExtension: 'jpg',
       photoType: photoAccessHelper.PhotoType.IMAGE,
       subtype: photoAccessHelper.PhotoSubtype.DEFAULT,
     }];
     await phAccessHelper.showAssetsCreationDialog(srcFileUris, photoCreationConfigs);
     ```

   - 结果：传入有效参数后，接口正常返回。


### 复现代码

```typescript
// 案例：调用showAssetsCreationDialog保存图片时报错401。
// 错误码： 401 - 参数错误。

const TAG = 'Case_ParamInvalid';

async triggerParamInvalidError(context: common.Context): Promise<void> {
  const phAccessHelper = photoAccessHelper.getPhotoAccessHelper(context);

  // 错误示例1：传入空srcFileUris。
  try {
    console.info(TAG, 'Test1: empty srcFileUris');
    const srcFileUris: string[] = [];
    const photoCreationConfigs: photoAccessHelper.PhotoCreationConfig[] = [{
      title: 'test',
      fileNameExtension: 'jpg',
      photoType: photoAccessHelper.PhotoType.IMAGE,
      subtype: photoAccessHelper.PhotoSubtype.DEFAULT,
    }];
    await phAccessHelper.showAssetsCreationDialog(srcFileUris, photoCreationConfigs);
    console.info(TAG, 'Test1 success');
  } catch (err) {
    const error = err as BusinessError;
    console.error(TAG, 'Test1 Error code:', error.code);
    console.error(TAG, 'Test1 Error message:', error.message);
  }

  // 错误示例2：photoCreationConfigs为空。
  try {
    console.info(TAG, 'Test2: empty photoCreationConfigs');
    const srcFileUris: string[] = ['/test/image.jpg'];
    const photoCreationConfigs: photoAccessHelper.PhotoCreationConfig[] = [];
    await phAccessHelper.showAssetsCreationDialog(srcFileUris, photoCreationConfigs);
    console.info(TAG, 'Test2 success');
  } catch (err) {
    const error = err as BusinessError;
    console.error(TAG, 'Test2 Error code:', error.code);
    console.error(TAG, 'Test2 Error message:', error.message);
  }

  // 正确示例。
  try {
    console.info(TAG, 'Test3: valid parameters');
    const srcFileUris: string[] = ['/test/image.jpg'];
    const photoCreationConfigs: photoAccessHelper.PhotoCreationConfig[] = [{
      title: 'test',
      fileNameExtension: 'jpg',
      photoType: photoAccessHelper.PhotoType.IMAGE,
      subtype: photoAccessHelper.PhotoSubtype.DEFAULT,
    }];
    await phAccessHelper.showAssetsCreationDialog(srcFileUris, photoCreationConfigs);
    console.info(TAG, 'Test3 success');
  } catch (err) {
    const error = err as BusinessError;
    console.error(TAG, 'Test3 Error code:', error.code);
    console.error(TAG, 'Test3 Error message:', error.message);
  }
}
```

### 日志信息


```log
I     Case_ParamInvalid Test1: empty srcFileUris
E     Case_ParamInvalid Test1 Error code: 401
E     Case_ParamInvalid Test1 Error message: srcFileUris must be an array with size between 1 and 100.
I     Case_ParamInvalid Test2: empty photoCreationConfigs
E     Case_ParamInvalid Test2 Error code: 401
E     Case_ParamInvalid Test2 Error message: photoCreationConfigs must be an array with size between 1 and 100.
I     Case_ParamInvalid Test3: valid parameters
I     Case_ParamInvalid Test3 success
```

### 常见易错代码

```typescript
// 错误：srcFileUris为空。
const srcFileUris: string[] = [];
const photoCreationConfigs = [{ title: 'test', fileNameExtension: 'jpg', ... }];
await phAccessHelper.showAssetsCreationDialog(srcFileUris, photoCreationConfigs);

// 正确：传入有效的参数。
const srcFileUris: string[] = ['/test/image.jpg'];
const photoCreationConfigs = [{ title: 'test', fileNameExtension: 'jpg', ... }];
await phAccessHelper.showAssetsCreationDialog(srcFileUris, photoCreationConfigs);
```

## 常见易错代码预防建议

1. 调用API接口前，务必检查所有必填参数是否存在且类型正确。

2. 使用TypeScript类型检查，确保参数类型符合API要求。

3. 对于可选参数，提供合理的默认值。

4. 使用try-catch捕获参数验证失败异常。