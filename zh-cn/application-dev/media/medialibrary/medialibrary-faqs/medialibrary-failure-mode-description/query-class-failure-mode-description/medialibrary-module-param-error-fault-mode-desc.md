# 媒体库模块参数错误故障模式说明
<!--Kit: Media Library Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @zhaochang14-->
<!--Designer: @liweilu1-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

## 根因描述

开发者在调用Media Library Kit接口时，媒体库模块参数错误导致接口返回错误码238000151。

错误码238000151（invalid parameter）常见于URI数量超过限制（如最多100个）等场景。

## 问题分析思路

问题原因：

1. URI数量超过限制（如最多100个）。

2. 数组大小超过限制。

3. 对象解包失败或为nullptr。

4. 对象状态不符合要求（如隐藏资源、回收站资源）。

5. 业务规则验证失败（如文件类型不匹配、扩展名不匹配）。

6. 参数值不在允许范围内。

7. 注册数量超过限制。

问题分析步骤：

1. 检查调用接口时传入的参数是否完整、类型是否正确、格式是否符合要求。

2. 查看错误码信息，确认参数验证失败的具体原因。

3. 检查NAPI层日志，定位具体是哪个参数校验失败。

4. 根据日志中的具体错误信息，修复对应的参数问题。

## 关键字

日志关键字：

- 错误码：238000151
- 错误信息：indexSet.size exceeds MAX_SIZE

## 案例分析

### 问题现象

indexSet参数错误导致操作失败。

### 问题分析

**根因分析**

调用getObjectsByIndexSet时传入无效的indexSet，报错238000151，原因是indexSet不能为空且不能超过500个，索引不能超出查询结果范围。

**分析步骤**

1. 检查错误码和错误信息，确认返回的具体错误类型。

   - 检查错误日志。

     ```log
     errCode=238000151, errMsg=indexSet.size exceeds MAX_SIZE
     ```

   - 结果：确认错误码为238000151，错误信息表明indexSet大小超过限制。

2. 检查indexSet参数，确认传入的indexSet是否符合要求。

   - 检查代码中的indexSet参数。

     ```typescript
     // 错误示例1：indexSet超过500个。
     const largeIndexSet: number[] = [];
     for (let i = 0; i <= 500; i++) {
       largeIndexSet.push(i);
     }
     const assets = fetchResult.getObjectsByIndexSet(largeIndexSet);
     ```

   - 结果：indexSet包含501个元素，超过了500的限制。

3. 验证indexSet有效性，确认indexSet是否为空或索引超出范围。

   - 检查其他无效场景。

     ```typescript
     // 错误示例2：indexSet为空。
     const emptyIndexSet: number[] = [];

     // 错误示例3：索引超出范围。
     const invalidIndexSet: number[] = [99999];
     ```

   - 结果：indexSet为空或索引超出查询结果范围时也会触发238000151错误。

4. 修复并验证，确认修复后接口正常返回。

   - 使用有效的indexSet。

     ```typescript
     if (count > 500) {
       const validIndexSet: number[] = [0, 1, 2];
       const validAssets = fetchResult.getObjectsByIndexSet(validIndexSet);
     }
     ```

   - 结果：使用有效的indexSet后，接口正常返回查询结果。

### 复现代码

```typescript
const TAG = 'Case_GetObjectsByIndexSet';

async triggerMediaParamError(context: common.Context): Promise<void> {
  const phAccessHelper = photoAccessHelper.getPhotoAccessHelper(context);

  // 先获取查询结果。
  const predicates = new dataSharePredicates.DataSharePredicates();
  const fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: ['uri', 'display_name'],
    predicates: predicates
  };
  const fetchResult = await phAccessHelper.getAssets(fetchOptions);
  const count = fetchResult.getCount();
  console.info(TAG, 'Query asset count:', count);

  // 错误示例1：indexSet超过500个触发238000151。
  const largeIndexSet: number[] = [];
  for (let i = 0; i <= 500; i++) {
    largeIndexSet.push(i);
  }
  try {
    console.info(TAG, 'Test1: indexSet size > 500');
    const assets = fetchResult.getObjectsByIndexSet(largeIndexSet);
  } catch (err) {
    console.error(TAG, 'Test1 Error code:', (err as BusinessError).code);
    console.error(TAG, 'Test1 Error message:', (err as BusinessError).message);
  }

  // 错误示例2：indexSet为空触发238000151。
  try {
    console.info(TAG, 'Test2: indexSet is empty');
    const emptyIndexSet: number[] = [];
    const assets = fetchResult.getObjectsByIndexSet(emptyIndexSet);
  } catch (err) {
    console.error(TAG, 'Test2 Error code:', (err as BusinessError).code);
    console.error(TAG, 'Test2 Error message:', (err as BusinessError).message);
  }

  // 错误示例3：索引超出范围触发238000151。
  try {
    console.info(TAG, 'Test3: index exceeds range');
    const invalidIndexSet: number[] = [99999];
    const assets = fetchResult.getObjectsByIndexSet(invalidIndexSet);
  } catch (err) {
    console.error(TAG, 'Test3 Error code:', (err as BusinessError).code);
    console.error(TAG, 'Test3 Error message:', (err as BusinessError).message);
  }

  // 正确示例：先确保有足够的数据，再执行操作。
  if (count > 500) {
    const validIndexSet: number[] = [0, 1, 2];
    const validAssets = fetchResult.getObjectsByIndexSet(validIndexSet);
    console.info(TAG, 'Get assets success');
  } else {
    console.info(TAG, 'Not enough assets for valid indexSet, need more than 500 assets');
  }

  fetchResult.close();
}
```

### 日志信息


```log
I     Case_GetObjectsByIndexSet Query asset count: 1
I     Case_GetObjectsByIndexSet Test1: indexSet size > 500
E     Case_GetObjectsByIndexSet Test1 Error code: 23800151
E     Case_GetObjectsByIndexSet Test1 Error message: indexSet.size exceeds MAX_SIZE
I     Case_GetObjectsByIndexSet Test2: indexSet is empty
E     Case_GetObjectsByIndexSet Test2 Error code: 23800151
E     Case_GetObjectsByIndexSet Test2 Error message: indexSet is empty
I     Case_GetObjectsByIndexSet Test3: index exceeds range
E     Case_GetObjectsByIndexSet Test3 Error code: 23800151
E     Case_GetObjectsByIndexSet Test3 Error message: Index exceeds range of objects
I     Case_GetObjectsByIndexSet Not enough assets for valid indexSet, need more than 500 assets
```

### 常见易错代码

```typescript
const TAG = 'Case_GetObjectsByIndexSet';

// 错误：indexSet超过限制。
const largeIndexSet: number[] = [];
for (let i = 0; i <= 500; i++) {
  largeIndexSet.push(i);
}
const assets = fetchResult.getObjectsByIndexSet(largeIndexSet);

// 正确：先确保有足够的数据，再执行操作。
if (count > 500) {
  const batchSize = 500;
  for (let i = 0; i < count; i += batchSize) {
    const batch: number[] = [];
    for (let j = i; j < i + batchSize && j < count; j++) {
      batch.push(j);
    }
    const assets = fetchResult.getObjectsByIndexSet(batch);
  }
} else {
  console.info(TAG, 'Not enough assets, need more than 500 assets for this operation');
}
fetchResult.close();
```

## 常见易错代码预防建议

1. 批量操作时控制单次数量不超过100个URI。

2. 分批次处理大量文件，避免超过限制。

3. 使用分页查询处理大量数据。

4. 对批量操作进行错误处理，部分失败时能回滚或记录。
