# @ohos.data.DataShareResultSet(数据共享结果集)

**结果集(DataShareResultSet)** 可提供访问由查询数据库生成的结果集的相关方法，根据提供的行数，查询相应的值，也可查询指定数据类型的值。

## 使用说明

需要通过调用[query](arkts-arkdata-datashare-datasharehelper-i-sys.md#query)接口获取DataShareResultSet对象。

```ts
 import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
 import { DataShareResultSet, dataShare, dataSharePredicates } from '@kit.ArkData';
 import { BusinessError } from '@kit.BasicServicesKit';
 export default class EntryAbility extends UIAbility {
 onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
 let dataShareHelper: dataShare.DataShareHelper | undefined = undefined;
 let uri = "datashare:///com.samples.datasharetest.DataShare";
 let context = this.context;
 dataShare.createDataShareHelper(context, uri, (err:BusinessError, data:dataShare.DataShareHelper) =&gt; {
 if (err != undefined) {
 console.error(`Failed to create DataShareHelper. Code: &#36;{err.code}, message: &#36;{err.message}`);
 } else {
 console.info("createDataShareHelper end, data : " + data);
 dataShareHelper = data;
 }
 let columns = ["*"];
 let predicates = new dataSharePredicates.DataSharePredicates();
 let resultSet: DataShareResultSet | undefined = undefined;
 predicates.equalTo("name0", "ZhangSan");
 if (dataShareHelper != undefined) {
 (dataShareHelper as dataShare.DataShareHelper).query(uri, predicates, columns).then((data: DataShareResultSet) =&gt; {
 console.info("query end, data : " + data);
 resultSet = data;
 }).catch((err: BusinessError) =&gt; {
 console.error(`Failed to query. Code: &#36;{err.code}, message: &#36;{err.message}`);
 });
 }
 });
 };
 };
 ```

## 导入模块

```TypeScript
import { DataShareResultSet, DataType } from '@kit.ArkData';
```

## 汇总

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DataShareResultSet](arkts-arkdata-data-datashareresultset-datashareresultset-i-sys.md) | 提供通过查询数据库生成的结果集的相关访问方法。<br> <br>列或键名称作为字符串数组返回，其中字符串的顺序与结果集中的列或键的顺序相同。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [DataType](arkts-arkdata-data-datashareresultset-datatype-e-sys.md) | 数据类型枚举。 |
<!--DelEnd-->
