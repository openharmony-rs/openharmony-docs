# Storage Switching

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @wkljy-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

  | API in the [FA Model](ability-terminology.md#fa-model)| Corresponding .d.ts File in the [Stage Model](ability-terminology.md#stage-model)| Corresponding API in the Stage Model| 
| -------- | -------- | -------- |
| GetStorageOptions | There is no corresponding API in the stage model.| The stage model uses **Preferences** to replace **Storage** and has redesigned the input parameters.| 
| SetStorageOptions | There is no corresponding API in the stage model.| The stage model uses **Preferences** to replace **Storage** and has redesigned the input parameters.| 
| ClearStorageOptions | There is no corresponding API in the stage model.| The stage model uses **Preferences** to replace **Storage** and has redesigned the input parameters.| 
| DeleteStorageOptions | There is no corresponding API in the stage model.| The stage model uses **Preferences** to replace **Storage** and has redesigned the input parameters.| 
| [static&nbsp;get(options:&nbsp;GetStorageOptions):&nbsp;void;](../reference/apis-arkdata/js-apis-system-storage.md#storageget) | \@ohos.data.preferences.d.ts | [get(key:&nbsp;string,&nbsp;defValue:&nbsp;ValueType,&nbsp;callback:&nbsp;AsyncCallback&lt;ValueType&gt;):&nbsp;void;](../reference/apis-arkdata/js-apis-data-preferences.md#get)<br>[get(key:&nbsp;string,&nbsp;defValue:&nbsp;ValueType):&nbsp;Promise&lt;ValueType&gt;;](../reference/apis-arkdata/js-apis-data-preferences.md#get-1) |
| [static&nbsp;set(options:&nbsp;SetStorageOptions):&nbsp;void;](../reference/apis-arkdata/js-apis-system-storage.md#storageset) | \@ohos.data.preferences.d.ts | [put(key:&nbsp;string,&nbsp;value:&nbsp;ValueType,&nbsp;callback:&nbsp;AsyncCallback&lt;void&gt;):&nbsp;void;](../reference/apis-arkdata/js-apis-data-preferences.md#put)<br>[put(key:&nbsp;string,&nbsp;value:&nbsp;ValueType):&nbsp;Promise&lt;void&gt;;](../reference/apis-arkdata/js-apis-data-preferences.md#put-1) |
| [static&nbsp;clear(options?:&nbsp;ClearStorageOptions):&nbsp;void;](../reference/apis-arkdata/js-apis-system-storage.md#storageclear) | \@ohos.data.preferences.d.ts | [clear(callback:&nbsp;AsyncCallback&lt;void&gt;):&nbsp;void;](../reference/apis-arkdata/js-apis-data-preferences.md#clear)<br>[clear():&nbsp;Promise&lt;void&gt;;](../reference/apis-arkdata/js-apis-data-preferences.md#clear-1) |
| [static&nbsp;delete(options:&nbsp;DeleteStorageOptions):&nbsp;void;](../reference/apis-arkdata/js-apis-system-storage.md#storagedelete) | \@ohos.data.preferences.d.ts | [delete(key:&nbsp;string,&nbsp;callback:&nbsp;AsyncCallback&lt;void&gt;):&nbsp;void;](../reference/apis-arkdata/js-apis-data-preferences.md#delete)<br>[delete(key:&nbsp;string):&nbsp;Promise&lt;void&gt;;](../reference/apis-arkdata/js-apis-data-preferences.md#delete-1) |
