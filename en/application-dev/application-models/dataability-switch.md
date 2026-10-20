# DataAbility Switching

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @wkljy-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=e6693c7e3467fc83da37592065a3dc8118ac09a4 translatedAt=2026-10-13T07:16:14.795Z pushedAt=2026-10-14T03:14:33.452Z -->

The DataAbility component in the [FA model](ability-terminology.md#fa-model) corresponds to the DataShareExtensionAbility component in the [stage model](ability-terminology.md#stage-model).


The DataShareExtensionAbility class provides system APIs. Only system applications can create DataShareExtensionAbility instances. Therefore, DataAbility switching adopts different policies for system applications and third-party applications.


## Switching a DataAbility for a System Application

The procedure for switching a DataAbility for a system application is similar to the procedure of PageAbility switching.

1. Create a DataShareExtensionAbility in the stage model.

2. Migrate the DataAbility code to the DataShareExtensionAbility.

   The table below describes the lifecycle comparison of the DataAbility and DataShareExtensionAbility.
   | DataAbility| DataShareExtensionAbility| Comparison Description|
   | -------- | -------- | -------- |
   | onInitialized?(info:&nbsp;AbilityInfo):&nbsp;void | onCreate?(want:&nbsp;Want,&nbsp;callback:<br/>AsyncCallback&lt;void&gt;):&nbsp;void | The two are invoked at the same time, but the function names and input parameters differ. In the Stage model, the input parameter `want` is added so that developers can obtain parameters during creation. |
   | update?(uri: string, valueBucket: rdb.ValuesBucket, predicates: dataAbility.DataAbilityPredicates, callback: AsyncCallback&lt;number&gt;): void | update?(uri: string, predicates: dataSharePredicates.DataSharePredicates, value: ValuesBucket, callback: AsyncCallback&lt;number&gt;): void | The two methods have the same meaning and invoking time, but slightly different parameter sequence and parameter type. A simple reconstruction is required.|
   | query?(uri: string, columns: Array&lt;string&gt;, predicates: dataAbility.DataAbilityPredicates, callback: AsyncCallback&lt;ResultSet&gt;): void | query?(uri:&nbsp;string,&nbsp;predicates:&nbsp;dataSharePredicates.DataSharePredicates,&nbsp;columns:&nbsp;Array&lt;string&gt;,&nbsp;callback:&nbsp;AsyncCallback&lt;Object&gt;):&nbsp;void | The two methods have the same meaning and invoking time, but slightly different parameter sequence and parameter type. A simple reconstruction is required.|
   | delete?(uri: string, predicates: dataAbility.DataAbilityPredicates, callback: AsyncCallback&lt;number&gt;): void | delete?(uri:&nbsp;string,&nbsp;predicates:&nbsp;dataSharePredicates.DataSharePredicates,&nbsp;callback:&nbsp;AsyncCallback&lt;number&gt;):&nbsp;void | The two methods have the same meaning and invoking time, but slightly different parameter type. A simple reconstruction is required.|
   | normalizeUri?(uri: string, callback: AsyncCallback&lt;string&gt;): void| normalizeUri?(uri: string, callback: AsyncCallback&lt;string&gt;): void| The two methods have the same meaning, invoking time, and parameters.|
   | batchInsert?(uri: string, valueBuckets: Array&lt;rdb.ValuesBucket&gt;, callback: AsyncCallback&lt;number&gt;): void | batchInsert?(uri: string, values: Array&lt;ValuesBucket&gt;, callback: AsyncCallback&lt;number&gt;): void| The two methods have the same meaning and invoking time, but slightly different parameter type. A simple reconstruction is required.|
   | denormalizeUri?(uri: string, callback: AsyncCallback&lt;string&gt;): void | denormalizeUri?(uri: string, callback: AsyncCallback&lt;string&gt;): void | The two methods have the same meaning, invoking time, and parameters.|
   | insert?(uri: string, valueBucket: rdb.ValuesBucket, callback: AsyncCallback&lt;number&gt;): void | insert?(uri: string, value: ValuesBucket, callback: AsyncCallback&lt;number&gt;): void | The two methods have the same meaning and invoking time, but slightly different parameter type. A simple reconstruction is required.|
   | openFile?(uri:&nbsp;string,&nbsp;mode:&nbsp;string,&nbsp;callback:&nbsp;AsyncCallback&lt;number&gt;):&nbsp;void | NA | The Stage model does not support URI cross-process access. It is recommended to perform cross-process file access by [carrying the FD and file information in Want](file-processing-apps-startup.md). |
   | getFileTypes?(uri:&nbsp;string,&nbsp;mimeTypeFilter:&nbsp;string,&nbsp;callback:&nbsp;AsyncCallback&lt;Array&lt;string&gt;&gt;):&nbsp;void | NA | The Stage model does not support URI cross-process access. It is recommended to perform cross-process file access by [carrying the FD and file information in Want](file-processing-apps-startup.md). |
   | getType?(uri:&nbsp;string,&nbsp;callback:&nbsp;AsyncCallback&lt;string&gt;):&nbsp;void | NA | The Stage model does not support URI cross-process access. It is recommended to perform cross-process file access by [carrying the FD and file information in Want](file-processing-apps-startup.md). |
   | executeBatch?(ops: Array&lt;DataAbilityOperation&gt;, callback: AsyncCallback&lt;Array&lt;DataAbilityResult&gt;&gt;): void | NA | DataShareExtensionAbility does not provide this API. You need to reimplement it based on service functions.|
   | call?(method: string, arg: string, extras: PacMap, callback: AsyncCallback&lt;PacMap&gt;): void | NA | DataShareExtensionAbility does not provide this API. You need to reimplement it based on service functions.|


## Switching a DataAbility for a Third-Party Application

In the stage model, third-party applications cannot provide data services for other third-party applications. You can select a switching solution based on your service requirements.

| Service Type| Switching Solution|
| -------- | -------- |
| Providing data for third-party applications| Match a scenario-specific [ExtensionAbility](../reference/apis-ability-kit/js-apis-bundleManager.md#extensionabilitytype).|
| Providing data within the application| Extract the component code as a common module for other components to use.|
