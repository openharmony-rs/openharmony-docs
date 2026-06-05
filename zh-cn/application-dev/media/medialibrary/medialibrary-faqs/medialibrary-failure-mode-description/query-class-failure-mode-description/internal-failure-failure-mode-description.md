# 内部失败故障模式说明
<!--Kit: Media Library Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @zhaochang14-->
<!--Designer: @liweilu1-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

## 根因描述

开发者在调用Media Library Kit接口时，内部失败导致接口返回错误码14000011（system inner fail）。常见于查询操作内部执行失败等场景。

## 问题分析思路

问题原因：

1. 查询操作内部执行失败。

2. FetchResult创建失败。

3. NAPI对象创建失败。

4. 数据库查询异常。

问题分析步骤：

1. 查看错误码信息，确认内部错误的具体类型。

2. 检查数据库操作是否正常，查询是否成功。

3. 查看系统资源是否充足，如内存、文件描述符等。

4. 检查媒体库服务是否正常运行。

## 关键字

日志关键字：

- 错误码：14000011
- 错误信息：system inner fail

## 案例分析

### 问题现象

获取相册信息的时候报错14000011。

### 问题分析

**根因分析**

传入的URI存在问题或查询操作内部执行失败。

**分析步骤**

1. 检查错误码和错误信息，确认返回的具体错误类型。

   - 检查错误日志。

     ```log
     errCode=14000011, errMsg=system inner fail
     ```

   - 结果：确认错误码为14000011，错误信息表明系统内部错误。

2. 检查传入的URI参数，确认URI是否有效。

   - 检查代码中的URI参数。

     ```typescript
     // 错误示例：查询已被删除的文件。
     const predicates = new dataSharePredicates.DataSharePredicates();
     predicates.equalTo('uri', 'file://media/photo/999999999/xxx.jpg');
     const fetchResult = await phAccessHelper.getAssets({
       fetchColumns: ['uri'],
       predicates: predicates
     });
     const asset = await fetchResult.getFirstObject();
     ```

   - 结果：传入的URI对应的文件已被删除或不存在，导致内部查询失败。

3. 检查数据库操作，确认数据库查询是否正常。

   - 检查FetchResult创建和数据库操作。

     ```typescript
     const fetchResult = await phAccessHelper.getAssets({
       fetchColumns: ['uri'],
       predicates: new dataSharePredicates.DataSharePredicates()
     });
     console.info(TAG, 'Assets count:', fetchResult.getCount());
     ```

   - 结果：使用有效的 predicates 和正确的参数进行查询，内部失败可能与系统资源或数据库状态有关。

4. 验证修复，确认修复后接口正常返回。

   - 使用有效的URI或查询所有资源。

     ```typescript
     const fetchResult2 = await phAccessHelper.getAssets({
       fetchColumns: ['uri'],
       predicates: new dataSharePredicates.DataSharePredicates()
     });
     console.info(TAG, 'Assets count:', fetchResult2.getCount());
     fetchResult2.close();
     ```

   - 结果：使用有效的查询条件后，接口正常返回结果。


### 复现代码

```typescript
// 案例：FetchResult内部数据异常时报错14000011。
// 错误码： 14000011 - 内部错误。

const TAG = 'Case_InnerFail';

async trigger14000011Error(context: common.Context): Promise<void> {
  const phAccessHelper = photoAccessHelper.getPhotoAccessHelper(context);

  // 错误示例：查询已被删除的文件。
  try {
    console.info(TAG, 'Test1: access deleted file');
    const predicates = new dataSharePredicates.DataSharePredicates();
    predicates.equalTo('uri', 'file://media/photo/999999999/xxx.jpg');
    const fetchResult = await phAccessHelper.getAssets({
      fetchColumns: ['uri'],
      predicates: predicates
    });
    const asset = await fetchResult.getFirstObject();
    fetchResult.close();
  } catch (err) {
    const error = err as BusinessError;
    console.error(TAG, 'Test1 Error code:', error.code);
    console.error(TAG, 'Test1 Error message:', error.message);
  }

  // 正确示例：使用有效URI查询。
  try {
    console.info(TAG, 'Test2: query with valid URI');
    const fetchResult2 = await phAccessHelper.getAssets({
      fetchColumns: ['uri'],
      predicates: new dataSharePredicates.DataSharePredicates()
    });
    console.info(TAG, 'Assets count:', fetchResult2.getCount());
    fetchResult2.close();
  } catch (err) {
    const error = err as BusinessError;
    console.error(TAG, 'Test2 Error code:', error.code);
    console.error(TAG, 'Test2 Error message:', error.message);
  }
}
```

### 日志信息

```log
E     Case_InnerFail Test1 Error code: 14000011
E     Case_InnerFail Test1 Error message: System inner fail
I     Case_InnerFail Test2: query with valid URI
I     Case_InnerFail Assets count: 1
```

### 常见易错代码

```typescript
// 错误：使用不存在或已被删除的资源的URI查询。
const predicates = new dataSharePredicates.DataSharePredicates();
predicates.equalTo('uri', 'file://media/photo/999999999/xxx.jpg');
const fetchResult = await phAccessHelper.getAssets({
  fetchColumns: ['uri'],
  predicates: predicates
});
const asset = await fetchResult.getFirstObject();

// 正确：使用有效的URI或查询所有资源。
const fetchResult2 = await phAccessHelper.getAssets({
  fetchColumns: ['uri'],
  predicates: new dataSharePredicates.DataSharePredicates()
});
console.info(TAG, 'Assets count:', fetchResult2.getCount());
fetchResult2.close();
```

## 常见易错代码预防建议

1. 使用正确的URI格式，确保是媒体库返回的有效URI。

2. 在进行数据库操作前检查数据库连接状态。

3. 对异步操作添加超时处理和错误捕获。

4. 检查设备存储空间是否充足。

5. 定期重启应用或清理缓存避免内存泄漏。
