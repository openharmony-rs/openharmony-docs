| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|New API |NA|Class name: contact;<br>API declaration: function addContactViaUI(context: Context, contact: Contact): Promise\<number>;<br>DIfferences: function addContactViaUI(context: Context, contact: Contact): Promise\<number>;|api/@ohos.contact.d.ts|
|New API |NA|Class name: contact;<br>API declaration: function saveToExistingContactViaUI(context: Context, contact: Contact): Promise\<number>;<br>DIfferences: function saveToExistingContactViaUI(context: Context, contact: Contact): Promise\<number>;|api/@ohos.contact.d.ts|
|New API |NA|Class name: ContactSelectionOptions;<br>API declaration: maxSelectable?: number;<br>DIfferences: maxSelectable?: number;|api/@ohos.contact.d.ts|
|New API |NA|Class name: ContactSelectionOptions;<br>API declaration: isDisplayedByName?: boolean;<br>DIfferences: isDisplayedByName?: boolean;|api/@ohos.contact.d.ts|
|New API |NA|Class name: ContactSelectionOptions;<br>API declaration: filter?: ContactSelectionFilter;<br>DIfferences: filter?: ContactSelectionFilter;|api/@ohos.contact.d.ts|
|New API |NA|Class name: contact;<br>API declaration: interface ContactSelectionFilter<br>DIfferences: interface ContactSelectionFilter|api/@ohos.contact.d.ts|
|New API |NA|Class name: ContactSelectionFilter;<br>API declaration: filterClause: FilterClause;<br>DIfferences: filterClause: FilterClause;|api/@ohos.contact.d.ts|
|New API |NA|Class name: ContactSelectionFilter;<br>API declaration: filterType: FilterType;<br>DIfferences: filterType: FilterType;|api/@ohos.contact.d.ts|
|New API |NA|Class name: contact;<br>API declaration: enum FilterType<br>DIfferences: enum FilterType|api/@ohos.contact.d.ts|
|New API |NA|Class name: FilterType;<br>API declaration: SHOW_FILTER<br>DIfferences: SHOW_FILTER|api/@ohos.contact.d.ts|
|New API |NA|Class name: FilterType;<br>API declaration: DEFAULT_SELECT<br>DIfferences: DEFAULT_SELECT|api/@ohos.contact.d.ts|
|New API |NA|Class name: FilterType;<br>API declaration: SHOW_FILTER_AND_DEFAULT_SELECT<br>DIfferences: SHOW_FILTER_AND_DEFAULT_SELECT|api/@ohos.contact.d.ts|
|New API |NA|Class name: contact;<br>API declaration: interface FilterClause<br>DIfferences: interface FilterClause|api/@ohos.contact.d.ts|
|New API |NA|Class name: FilterClause;<br>API declaration: id?: Array\<FilterOptions>;<br>DIfferences: id?: Array\<FilterOptions>;|api/@ohos.contact.d.ts|
|New API |NA|Class name: FilterClause;<br>API declaration: name?: Array\<FilterOptions>;<br>DIfferences: name?: Array\<FilterOptions>;|api/@ohos.contact.d.ts|
|New API |NA|Class name: FilterClause;<br>API declaration: dataItem?: DataFilter;<br>DIfferences: dataItem?: DataFilter;|api/@ohos.contact.d.ts|
|New API |NA|Class name: FilterClause;<br>API declaration: focusModeList?: Array\<FilterOptions>;<br>DIfferences: focusModeList?: Array\<FilterOptions>;|api/@ohos.contact.d.ts|
|New API |NA|Class name: contact;<br>API declaration: interface FilterOptions<br>DIfferences: interface FilterOptions|api/@ohos.contact.d.ts|
|New API |NA|Class name: FilterOptions;<br>API declaration: filterCondition: FilterCondition;<br>DIfferences: filterCondition: FilterCondition;|api/@ohos.contact.d.ts|
|New API |NA|Class name: FilterOptions;<br>API declaration: value?: string \| ValueType[];<br>DIfferences: value?: string \| ValueType[];|api/@ohos.contact.d.ts|
|New API |NA|Class name: contact;<br>API declaration: enum FilterCondition<br>DIfferences: enum FilterCondition|api/@ohos.contact.d.ts|
|New API |NA|Class name: FilterCondition;<br>API declaration: IS_NOT_NULL<br>DIfferences: IS_NOT_NULL|api/@ohos.contact.d.ts|
|New API |NA|Class name: FilterCondition;<br>API declaration: EQUAL_TO<br>DIfferences: EQUAL_TO|api/@ohos.contact.d.ts|
|New API |NA|Class name: FilterCondition;<br>API declaration: NOT_EQUAL_TO<br>DIfferences: NOT_EQUAL_TO|api/@ohos.contact.d.ts|
|New API |NA|Class name: FilterCondition;<br>API declaration: IN<br>DIfferences: IN|api/@ohos.contact.d.ts|
|New API |NA|Class name: FilterCondition;<br>API declaration: NOT_IN<br>DIfferences: NOT_IN|api/@ohos.contact.d.ts|
|New API |NA|Class name: FilterCondition;<br>API declaration: CONTAINS<br>DIfferences: CONTAINS|api/@ohos.contact.d.ts|
|New API |NA|Class name: contact;<br>API declaration: interface DataFilter<br>DIfferences: interface DataFilter|api/@ohos.contact.d.ts|
|New API |NA|Class name: DataFilter;<br>API declaration: field: DataField;<br>DIfferences: field: DataField;|api/@ohos.contact.d.ts|
|New API |NA|Class name: DataFilter;<br>API declaration: options: Array\<FilterOptions>;<br>DIfferences: options: Array\<FilterOptions>;|api/@ohos.contact.d.ts|
|New API |NA|Class name: contact;<br>API declaration: enum DataField<br>DIfferences: enum DataField|api/@ohos.contact.d.ts|
|New API |NA|Class name: DataField;<br>API declaration: EMAIL<br>DIfferences: EMAIL|api/@ohos.contact.d.ts|
|New API |NA|Class name: DataField;<br>API declaration: PHONE<br>DIfferences: PHONE|api/@ohos.contact.d.ts|
|New API |NA|Class name: DataField;<br>API declaration: ORGANIZATION<br>DIfferences: ORGANIZATION|api/@ohos.contact.d.ts|
