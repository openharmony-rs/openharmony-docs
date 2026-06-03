# 参数的基本合法性错误故障模式说明
<!--Kit: Media Library Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @zhaochang14-->
<!--Designer: @liweilu1-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

## 根因描述

开发者在调用Media Library Kit接口时，参数的基本合法性（数量、类型、格式）错误导致接口返回错误码13900020，常见于系统级和框架级参数验证等场景。

## 问题分析思路

问题原因：

系统级参数验证：

1. 参数数量验证（如：参数数量不在允许范围内）。

2. 参数类型验证（如：参数不是预期的类型）。

3. 数组长度验证（如：数组长度不符合预期）。

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

- 错误码：13900020
- 错误信息：invalid parameter

## 案例分析

### 问题现象

调用Album.getAssets()报错13900020。

### 问题分析

**根因分析**

调用Album.getAssets()时传入无效的fetchOptions（如fetchColumns包含无效列名）。

**分析步骤**

1. 检查错误码和错误信息，确认返回的具体错误类型。

   - 检查错误日志。

     ```log
     errCode=13900020, errMsg=invalid parameter
     ```

   - 结果：通过错误日志确认返回的是13900020参数错误。

2. 检查fetchOptions参数，确认传入的fetchOptions是否符合要求。

   - 检查代码中的fetchOptions参数。

     ```typescript
     // 错误示例：fetchColumns包含无效列名。
     const invalidFetchOptions: photoAccessHelper.FetchOptions = {
       fetchColumns: ['invalid_column'],
       predicates: new dataSharePredicates.DataSharePredicates()
     };
     const assets = await album.getAssets(invalidFetchOptions);
     ```

   - 结果：fetchColumns包含无效列名，不满足接口要求。

3. 验证正确的fetchOptions，使用有效的fetchColumns。

   - 检查正确的用法。

     ```typescript
     // 正确示例：使用有效的fetchColumns。
     const validFetchOptions: photoAccessHelper.FetchOptions = {
       fetchColumns: ['uri', 'display_name'],
       predicates: new dataSharePredicates.DataSharePredicates()
     };
     const assets = await album.getAssets(validFetchOptions);
     console.info(TAG, 'Get assets success, count:', assets.getCount());
     assets.close();
     ```

   - 结果：使用有效的fetchColumns后，接口正常返回查询结果。

### 复现代码

```typescript
const TAG = 'Case_InvalidParam';

async trigger13900020Error(context: common.Context): Promise<void> {
  const phAccessHelper = photoAccessHelper.getPhotoAccessHelper(context);

  // 先获取一个相册。
  const albumFetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: ['album_id', 'album_name'],
    predicates: new dataSharePredicates.DataSharePredicates()
  };
  const albums = await phAccessHelper.getPhotoAlbums(albumFetchOptions);
  const album = await albums.getFirstObject();
  console.info(TAG, 'Got album, count:', albums.getCount());

  // 错误示例：使用无效的fetchOptions触发13900020。
  try {
    console.info(TAG, 'Test: invalid fetchOptions');
    const invalidFetchOptions: photoAccessHelper.FetchOptions = {
      fetchColumns: ['invalid_column'],
      predicates: new dataSharePredicates.DataSharePredicates()
    };
    const assets = await album.getAssets(invalidFetchOptions);
  } catch (err) {
    console.error(TAG, 'Error code:', (err as BusinessError).code);
    console.error(TAG, 'Error message:', (err as BusinessError).message);
  }

  // 正确示例：使用有效的fetchOptions。
  const validFetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: ['uri', 'display_name'],
    predicates: new dataSharePredicates.DataSharePredicates()
  };
  const validAssets = await album.getAssets(validFetchOptions);
  console.info(TAG, 'Get assets success, count:', validAssets.getCount());
  validAssets.close();
  albums.close();
}
```

### 日志信息


```log
I     Case_InvalidParam Got album, count: 12
I     Case_InvalidParam Test: invalid fetchOptions
E     Case_InvalidParam Error code: 13900020
E     Case_InvalidParam Error message: invalid parameter
I     Case_InvalidParam Get assets success, count: 0
```

### 常见易错代码

```typescript
// 错误：fetchColumns包含无效列名。
const invalidFetchOptions: photoAccessHelper.FetchOptions = {
  fetchColumns: ['invalid_column_name'],
  predicates: new dataSharePredicates.DataSharePredicates()
};
const assets = await album.getAssets(invalidFetchOptions);

// 正确：使用有效的fetchColumns。
const validFetchOptions: photoAccessHelper.FetchOptions = {
  fetchColumns: ['uri', 'display_name'],
  predicates: new dataSharePredicates.DataSharePredicates()
};
const assets = await album.getAssets(validFetchOptions);
```

## 常见易错代码预防建议

1. 调用API前检查参数类型是否正确。

2. 使用TypeScript严格类型检查。

3. 对数组参数检查长度是否在允许范围内。

4. 对不确定的参数进行类型断言或转换。
