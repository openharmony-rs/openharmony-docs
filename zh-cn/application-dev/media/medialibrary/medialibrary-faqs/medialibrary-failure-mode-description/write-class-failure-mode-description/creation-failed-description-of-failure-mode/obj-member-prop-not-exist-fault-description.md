# 对象成员属性不存在错误故障模式说明
<!--Kit: Media Library Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @zhaochang14-->
<!--Designer: @liweilu1-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

## 根因描述

开发者在调用Media Library Kit接口时，对象成员属性不存在的错误导致接口返回错误码14000014（member not exist）。常见于访问或设置了不存在的文件属性成员等场景。

## 问题分析思路

问题原因：

访问或设置了不存在的文件属性成员。

问题分析步骤：

1. 检查调用接口时传入的参数是否完整、类型是否正确、格式是否符合要求。

2. 查看错误码信息，确认参数验证失败的具体原因。

3. 检查NAPI层日志，定位具体是哪个参数校验失败。

4. 根据日志中的具体错误信息，修复对应的参数问题。

## 关键字

日志关键字：

- 错误码：14000014
- 错误信息：member not exist

## 案例分析

### 问题现象

访问PhotoAsset不存在的属性导致报错。

### 问题分析

**根因分析**

访问PhotoAsset对象不存在的属性时报错14000014（No such file key），原因是访问的属性未在FetchOptions.fetchColumns中指定。

**分析步骤**

1. 检查错误码和错误信息，根据错误码定位问题类型。

   - 检查错误日志。

     ```log
     errCode=14000014, errMsg=member not exist
     ```

   - 结果：确认错误码为14000014，错误信息表明成员不存在。

2. 检查fetchColumns参数，确认查询时是否指定了要获取的属性。

   - 检查fetchColumns配置。

     ```typescript
     // 错误示例：只获取uri和display_name。
     const fetchResult = await phAccessHelper.getAssets({
       fetchColumns: ['uri', 'display_name'],
       predicates: new dataSharePredicates.DataSharePredicates()
     });
     if (fetchResult.getCount() > 0) {
       const asset = await fetchResult.getFirstObject();
       console.info(TAG, 'Size:', asset.get('size'));  // size未在fetchColumns中指定。
     }
     ```

   - 结果：访问的size属性未在fetchColumns中指定。

3. 分析问题原因，结合文档分析根因。

   - PhotoAsset对象只有已加载的属性才可访问。

   - fetchColumns：指定需要获取的属性。

   - 未在fetchColumns中指定的属性无法通过asset.get()访问。

   - 结果：问题根因为访问了未加载的属性。

4. 验证修复，在fetchColumns中添加需要访问的属性。

   - 在fetchColumns中包含需要访问的属性。

     ```typescript
     const fetchResult = await phAccessHelper.getAssets({
       fetchColumns: ['uri', 'display_name', 'size'],
       predicates: new dataSharePredicates.DataSharePredicates()
     });
     if (fetchResult.getCount() > 0) {
       const asset = await fetchResult.getFirstObject();
       console.info(TAG, 'Size:', asset.get('size'));
     }
     ```

   - 结果：在fetchColumns中添加size属性后，可以正常访问。

### 复现代码

```typescript
// 案例：访问PhotoAsset不存在的属性成员。
// 错误码： 14000014。

const TAG = 'Case16_MemberNotExist';

async trigger14000014Error(context: common.Context): Promise<void> {
  const phAccessHelper = photoAccessHelper.getPhotoAccessHelper(context);

  // 错误示例：只获取uri和display_name，但访问未获取的属性（如size）。
  try {
    console.info(TAG, 'Test1: access property not in fetchColumns');
    const fetchResult = await phAccessHelper.getAssets({
      fetchColumns: ['uri', 'display_name'],
      predicates: new dataSharePredicates.DataSharePredicates()
    });
    if (fetchResult.getCount() > 0) {
      const asset = await fetchResult.getFirstObject();
      fetchResult.close();
      console.info(TAG, 'Size:', asset.get('size'));
    }
  } catch (err) {
    const error = err as BusinessError;
    console.error(TAG, 'Test1 Error code:', error.code);
    console.error(TAG, 'Test1 Error message:', error.message);
  }

  // 正确示例：在fetchColumns中包含需要访问的属性。
  try {
    console.info(TAG, 'Test2: access property in fetchColumns');
    const fetchResult = await phAccessHelper.getAssets({
      fetchColumns: ['uri', 'display_name'],
      predicates: new dataSharePredicates.DataSharePredicates()
    });
    if (fetchResult.getCount() > 0) {
      const asset = await fetchResult.getFirstObject();
      fetchResult.close();
      console.info(TAG, 'Display name:', asset.get('display_name'));
    }
  } catch (err) {
    const error = err as BusinessError;
    console.error(TAG, 'Test2 Error code:', error.code);
    console.error(TAG, 'Test2 Error message:', error.message);
  }
}
```

### 日志信息


```log
E Case16_MemberNotExist Test1 Error code: 14000014
E Case16_MemberNotExist Test1 Error message: member not exist
I Case16_MemberNotExist Display name: xxx.jpg
```

### 常见易错代码

```typescript
// 错误：访问未在fetchColumns中指定的属性。
const fetchResult = await phAccessHelper.getAssets({
  fetchColumns: ['uri', 'display_name'],
  predicates: new dataSharePredicates.DataSharePredicates()
});
const asset = await fetchResult.getFirstObject();
console.info(TAG, 'Size:', asset.get('size')); // size未在fetchColumns中指定。

// 正确：在fetchColumns中包含需要访问的属性。
const fetchResult = await phAccessHelper.getAssets({
  fetchColumns: ['uri', 'display_name', 'size'],
  predicates: new dataSharePredicates.DataSharePredicates()
});
const asset = await fetchResult.getFirstObject();
console.info(TAG, 'Size:', asset.get('size'));
```

## 常见易错代码预防建议

1. 使用FetchOptions.fetchColumns指定需要获取的属性。

2. 参考PhotoKeys文档确认属性名称正确。

3. 不要访问未获取的属性，先检查fetchColumns。

4. 使用正确的属性名。

5. 对未知属性进行防御性编程。
