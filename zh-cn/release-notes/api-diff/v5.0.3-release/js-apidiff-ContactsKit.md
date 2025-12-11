| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增API|NA|类名：contact；<br>API声明：function addContactViaUI(context: Context, contact: Contact): Promise\<number>;<br>差异内容：function addContactViaUI(context: Context, contact: Contact): Promise\<number>;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：function saveToExistingContactViaUI(context: Context, contact: Contact): Promise\<number>;<br>差异内容：function saveToExistingContactViaUI(context: Context, contact: Contact): Promise\<number>;|api/@ohos.contact.d.ts|
|新增API|NA|类名：ContactSelectionOptions；<br>API声明：maxSelectable?: number;<br>差异内容：maxSelectable?: number;|api/@ohos.contact.d.ts|
|新增API|NA|类名：ContactSelectionOptions；<br>API声明：isDisplayedByName?: boolean;<br>差异内容：isDisplayedByName?: boolean;|api/@ohos.contact.d.ts|
|新增API|NA|类名：ContactSelectionOptions；<br>API声明：filter?: ContactSelectionFilter;<br>差异内容：filter?: ContactSelectionFilter;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：interface ContactSelectionFilter<br>差异内容：interface ContactSelectionFilter|api/@ohos.contact.d.ts|
|新增API|NA|类名：ContactSelectionFilter；<br>API声明：filterClause: FilterClause;<br>差异内容：filterClause: FilterClause;|api/@ohos.contact.d.ts|
|新增API|NA|类名：ContactSelectionFilter；<br>API声明：filterType: FilterType;<br>差异内容：filterType: FilterType;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：enum FilterType<br>差异内容：enum FilterType|api/@ohos.contact.d.ts|
|新增API|NA|类名：FilterType；<br>API声明：SHOW_FILTER<br>差异内容：SHOW_FILTER|api/@ohos.contact.d.ts|
|新增API|NA|类名：FilterType；<br>API声明：DEFAULT_SELECT<br>差异内容：DEFAULT_SELECT|api/@ohos.contact.d.ts|
|新增API|NA|类名：FilterType；<br>API声明：SHOW_FILTER_AND_DEFAULT_SELECT<br>差异内容：SHOW_FILTER_AND_DEFAULT_SELECT|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：interface FilterClause<br>差异内容：interface FilterClause|api/@ohos.contact.d.ts|
|新增API|NA|类名：FilterClause；<br>API声明：id?: Array\<FilterOptions>;<br>差异内容：id?: Array\<FilterOptions>;|api/@ohos.contact.d.ts|
|新增API|NA|类名：FilterClause；<br>API声明：name?: Array\<FilterOptions>;<br>差异内容：name?: Array\<FilterOptions>;|api/@ohos.contact.d.ts|
|新增API|NA|类名：FilterClause；<br>API声明：dataItem?: DataFilter;<br>差异内容：dataItem?: DataFilter;|api/@ohos.contact.d.ts|
|新增API|NA|类名：FilterClause；<br>API声明：focusModeList?: Array\<FilterOptions>;<br>差异内容：focusModeList?: Array\<FilterOptions>;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：interface FilterOptions<br>差异内容：interface FilterOptions|api/@ohos.contact.d.ts|
|新增API|NA|类名：FilterOptions；<br>API声明：filterCondition: FilterCondition;<br>差异内容：filterCondition: FilterCondition;|api/@ohos.contact.d.ts|
|新增API|NA|类名：FilterOptions；<br>API声明：value?: string \| ValueType[];<br>差异内容：value?: string \| ValueType[];|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：enum FilterCondition<br>差异内容：enum FilterCondition|api/@ohos.contact.d.ts|
|新增API|NA|类名：FilterCondition；<br>API声明：IS_NOT_NULL<br>差异内容：IS_NOT_NULL|api/@ohos.contact.d.ts|
|新增API|NA|类名：FilterCondition；<br>API声明：EQUAL_TO<br>差异内容：EQUAL_TO|api/@ohos.contact.d.ts|
|新增API|NA|类名：FilterCondition；<br>API声明：NOT_EQUAL_TO<br>差异内容：NOT_EQUAL_TO|api/@ohos.contact.d.ts|
|新增API|NA|类名：FilterCondition；<br>API声明：IN<br>差异内容：IN|api/@ohos.contact.d.ts|
|新增API|NA|类名：FilterCondition；<br>API声明：NOT_IN<br>差异内容：NOT_IN|api/@ohos.contact.d.ts|
|新增API|NA|类名：FilterCondition；<br>API声明：CONTAINS<br>差异内容：CONTAINS|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：interface DataFilter<br>差异内容：interface DataFilter|api/@ohos.contact.d.ts|
|新增API|NA|类名：DataFilter；<br>API声明：field: DataField;<br>差异内容：field: DataField;|api/@ohos.contact.d.ts|
|新增API|NA|类名：DataFilter；<br>API声明：options: Array\<FilterOptions>;<br>差异内容：options: Array\<FilterOptions>;|api/@ohos.contact.d.ts|
|新增API|NA|类名：contact；<br>API声明：enum DataField<br>差异内容：enum DataField|api/@ohos.contact.d.ts|
|新增API|NA|类名：DataField；<br>API声明：EMAIL<br>差异内容：EMAIL|api/@ohos.contact.d.ts|
|新增API|NA|类名：DataField；<br>API声明：PHONE<br>差异内容：PHONE|api/@ohos.contact.d.ts|
|新增API|NA|类名：DataField；<br>API声明：ORGANIZATION<br>差异内容：ORGANIZATION|api/@ohos.contact.d.ts|
