# 显示名称无效创建失败故障模式说明
<!--Kit: Media Library Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @zhaochang14-->
<!--Designer: @liweilu1-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

## 根因描述

开发者在调用Media Library Kit接口时，显示名称无效导致接口返回错误码13900020。常见于文件名不符合规范等场景。

## 问题分析思路

问题原因：

1. 文件名不符合规范。

2. 文件名包含非法字符。

问题分析步骤：

1. 查看错误码和错误信息，确认问题类型。

2. 根据错误码查阅相关错误定义。

3. 分析调用栈和日志，定位问题根因。

4. 根据分析结果进行修复。

## 关键字

日志关键字：

- 错误码：13900020
- 错误信息：invalid parameter

## 案例分析

### 问题现象

创建资产时显示名称包含非法字符导致失败。

### 问题分析

**根因分析**

调用createAsset创建媒体资产时报错13900020（Display name invalid），原因是显示名称包含非法字符或长度超出限制。

**分析步骤**

1. 检查displayName合法性，确认显示名称是否包含非法字符。

   - 检查displayName是否包含非法字符。

     ```typescript
     // 错误示例：包含非法字符。
     const asset1 = await phAccessHelper.createAsset('test<>image.jpg');
     const asset2 = await phAccessHelper.createAsset('test/image.jpg');
     const asset3 = await phAccessHelper.createAsset('test:image.jpg');
     ```

   - 结果：displayName包含<> / :等非法字符，不符合文件命名规范。

2. 检查显示名称长度，确认显示名称长度是否超出限制。

   - 检查displayName长度。

     ```typescript
     const longName = 'a'.repeat(300) + '.jpg';
     const asset = await phAccessHelper.createAsset(longName);
     ```

   - 结果：显示名称长度超过256字符限制。

3. 检查文件扩展名，确认文件扩展名是否合法。

   - 检查文件扩展名。

     ```typescript
     const asset = await phAccessHelper.createAsset('valid_image.jpg');
     ```

   - 结果：使用合法的文件扩展名。

4. 验证修复，确认修复后接口正常返回。

   - 使用合法的displayName。

     ```typescript
     const asset = await phAccessHelper.createAsset('valid_image.jpg');
     ```

   - 结果：使用合法的displayName后，接口正常返回创建的资产。


### 复现代码

```typescript
// 案例：创建资产时displayName包含非法字符导致失败。
// 错误码： 13900020 - Display name invalid
// 接口: createAsset

const TAG = 'Case_DisplayNameInvalid';

async trigger13900020Error(context: common.Context): Promise<void> {
  const phAccessHelper = photoAccessHelper.getPhotoAccessHelper(context);

  // 错误示例1：错误使用包含非法字符的displayName创建资产。
  try {
    console.info(TAG, 'Test1: create asset with illegal chars in displayName');
    const asset1 = await phAccessHelper.createAsset('test<>image.jpg');
    console.info(TAG, 'Test1 success');
  } catch (err) {
    console.error(TAG, 'Test1 Error code:', (err as BusinessError).code);
    console.error(TAG, 'Test1 Error message:', (err as BusinessError).message);
  }

  // 错误示例2：使用包含斜杠的displayName创建资产。
  try {
    console.info(TAG, 'Test2: create asset with slash in displayName');
    const asset2 = await phAccessHelper.createAsset('test/image.jpg');
    console.info(TAG, 'Test2 success');
  } catch (err) {
    console.error(TAG, 'Test2 Error code:', (err as BusinessError).code);
    console.error(TAG, 'Test2 Error message:', (err as BusinessError).message);
  }

  // 错误示例3：使用冒号的displayName创建资产。
  try {
    console.info(TAG, 'Test3: create asset with colon in displayName');
    const asset3 = await phAccessHelper.createAsset('test:image.jpg');
    console.info(TAG, 'Test3 success');
  } catch (err) {
    console.error(TAG, 'Test3 Error code:', (err as BusinessError).code);
    console.error(TAG, 'Test3 Error message:', (err as BusinessError).message);
  }

  // 正确示例：使用合法的displayName创建资产。
  try {
    console.info(TAG, 'Test4: create asset with valid displayName');
    const asset4 = await phAccessHelper.createAsset('valid_image.jpg');
    console.info(TAG, 'Test4 success, uri:', asset4.uri);
  } catch (err) {
    console.error(TAG, 'Test4 Error code:', (err as BusinessError).code);
    console.error(TAG, 'Test4 Error message:', (err as BusinessError).message);
  }
}
```

### 日志信息


```log
I     Case_DisplayNameInvalid Test1: create asset with illegal chars in displayName
E     Case_DisplayNameInvalid Test1 Error code: 13900020
E     Case_DisplayNameInvalid Test1 Error message: invalid parameter
I     Case_DisplayNameInvalid Test2: create asset with slash in displayName
E     Case_DisplayNameInvalid Test2 Error code: 13900020
E     Case_DisplayNameInvalid Test2 Error message: invalid parameter
I     Case_DisplayNameInvalid Test3: create asset with colon in displayName
E     Case_DisplayNameInvalid Test3 Error code: 13900020
E     Case_DisplayNameInvalid Test3 Error message: invalid parameter
I     Case_DisplayNameInvalid Test4: create asset with valid displayName
I     Case_DisplayNameInvalid Test4 success, uri: file://media/Photo/6/IMG_1780493682_005/valid_image.jpg
```

### 常见易错代码

```typescript
// 错误：displayName包含非法字符。
const asset1 = await phAccessHelper.createAsset('test<>image.jpg');

// 正确：使用合法的displayName。
const asset2 = await phAccessHelper.createAsset('valid_image.jpg');
```

## 常见易错代码预防建议

1. 文件名不能包含 \ / : * ? " < > | 等非法字符。

2. 文件名长度不超过256个字符。

3. 使用displayName属性设置显示名称。

4. 对用户输入的文件名进行合法性校验。

5. 参考系统规范命名文件。
