# LifecycleData接口切换
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @xialiangwei-->
<!--Designer: @jsjzju-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->


| FA模型接口 | Stage模型接口对应d.ts文件 | Stage模型对应接口 | 
| -------- | -------- | -------- |
| update?(uri:&nbsp;string,&nbsp;valueBucket:&nbsp;rdb.ValuesBucket,&nbsp;predicates:&nbsp;dataAbility.DataAbilityPredicates,&nbsp;callback:&nbsp;AsyncCallback&lt;number&gt;):&nbsp;void; | \@ohos.application.DataShareExtensionAbility.d.ts | update?(uri:&nbsp;string,&nbsp;predicates:&nbsp;dataSharePredicates.DataSharePredicates,&nbsp;valueBucket:&nbsp;ValuesBucket,&nbsp;callback:&nbsp;AsyncCallback&lt;number&gt;):&nbsp;void; |
| query?(uri:&nbsp;string,&nbsp;columns:&nbsp;Array&lt;string&gt;,&nbsp;predicates:&nbsp;dataAbility.DataAbilityPredicates,&nbsp;callback:&nbsp;AsyncCallback&lt;ResultSet&gt;):&nbsp;void; | \@ohos.application.DataShareExtensionAbility.d.ts | query?(uri:&nbsp;string,&nbsp;predicates:&nbsp;dataSharePredicates.DataSharePredicates,&nbsp;columns:&nbsp;Array&lt;string&gt;,&nbsp;callback:&nbsp;AsyncCallback&lt;Object&gt;):&nbsp;void; |
| delete?(uri:&nbsp;string,&nbsp;predicates:&nbsp;dataAbility.DataAbilityPredicates,&nbsp;callback:&nbsp;AsyncCallback&lt;number&gt;):&nbsp;void; | \@ohos.application.DataShareExtensionAbility.d.ts | delete?(uri:&nbsp;string,&nbsp;predicates:&nbsp;dataSharePredicates.DataSharePredicates,&nbsp;callback:&nbsp;AsyncCallback&lt;number&gt;):&nbsp;void; |
| normalizeUri?(uri:&nbsp;string,&nbsp;callback:&nbsp;AsyncCallback&lt;string&gt;):&nbsp;void; | \@ohos.application.DataShareExtensionAbility.d.ts | normalizeUri?(uri:&nbsp;string,&nbsp;callback:&nbsp;AsyncCallback&lt;string&gt;):&nbsp;void; |
| batchInsert?(uri:&nbsp;string,&nbsp;valueBuckets:&nbsp;Array&lt;rdb.ValuesBucket&gt;,&nbsp;callback:&nbsp;AsyncCallback&lt;number&gt;):&nbsp;void; | \@ohos.application.DataShareExtensionAbility.d.ts | batchInsert?(uri:&nbsp;string,&nbsp;valueBuckets:&nbsp;Array&lt;ValuesBucket&gt;,&nbsp;callback:&nbsp;AsyncCallback&lt;number&gt;):&nbsp;void; |
| denormalizeUri?(uri:&nbsp;string,&nbsp;callback:&nbsp;AsyncCallback&lt;string&gt;):&nbsp;void; | \@ohos.application.DataShareExtensionAbility.d.ts | denormalizeUri?(uri:&nbsp;string,&nbsp;callback:&nbsp;AsyncCallback&lt;string&gt;):&nbsp;void; |
| insert?(uri:&nbsp;string,&nbsp;valueBucket:&nbsp;rdb.ValuesBucket,&nbsp;callback:&nbsp;AsyncCallback&lt;number&gt;):&nbsp;void; | \@ohos.application.DataShareExtensionAbility.d.ts | insert?(uri:&nbsp;string,&nbsp;valueBucket:&nbsp;ValuesBucket,&nbsp;callback:&nbsp;AsyncCallback&lt;number&gt;):&nbsp;void; |
| openFile?(uri:&nbsp;string,&nbsp;mode:&nbsp;string,&nbsp;callback:&nbsp;AsyncCallback&lt;number&gt;):&nbsp;void; | Stage模型无对应接口 | Stage模型不支持uri跨进程访问，建议通过Want携带fd和文件信息进行跨进程文件访问，参考通过startAbility拉起文件处理类应用。 |
| getFileTypes?(uri:&nbsp;string,&nbsp;mimeTypeFilter:&nbsp;string,&nbsp;callback:&nbsp;AsyncCallback&lt;Array&lt;string&gt;&gt;):&nbsp;void; | Stage模型无对应接口 | Stage模型不支持uri跨进程访问，建议通过Want携带fd和文件信息进行跨进程文件访问，参考通过startAbility拉起文件处理类应用。 |
| onInitialized?(info:&nbsp;AbilityInfo):&nbsp;void; | \@ohos.application.DataShareExtensionAbility.d.ts | onCreate?(want:&nbsp;Want,&nbsp;callback:&nbsp;AsyncCallback&lt;void&gt;):&nbsp;void; |
| getType?(uri:&nbsp;string,&nbsp;callback:&nbsp;AsyncCallback&lt;string&gt;):&nbsp;void; | Stage模型无对应接口 | Stage模型不支持uri跨进程访问，建议通过Want携带fd和文件信息进行跨进程文件访问，参考通过startAbility拉起文件处理类应用。 |
| executeBatch?(ops:&nbsp;Array&lt;DataAbilityOperation&gt;,&nbsp;callback:&nbsp;AsyncCallback&lt;Array&lt;DataAbilityResult&gt;&gt;):&nbsp;void; | Stage模型无对应接口 | 暂时未提供对应接口 |
| call?(method:&nbsp;string,&nbsp;arg:&nbsp;string,&nbsp;extras:&nbsp;PacMap,&nbsp;callback:&nbsp;AsyncCallback&lt;PacMap&gt;):&nbsp;void; | Stage模型无对应接口 | 暂时未提供对应接口 |
