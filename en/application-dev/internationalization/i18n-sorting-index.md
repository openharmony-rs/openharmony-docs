# Sorting by Indexes

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @yliupy-->
<!--Designer: @sunyaozu-->
<!--Tester: @lpw_work-->
<!--Adviser: @Brilliantry_Rui-->

## When to Use

When there are many options in a list, users need to slide the window to search for the target option. Sorting by indexes is here to help them quickly find the target option by way of creating an index for each option. It is actually a kind of labeling. For example, labels A, B, C, and D on the right of the contact page correspond to the initial letters of contact names. If you want to find John, clicking J will direct you to a list of names starting with J. Such labels are called indexes, which help to quickly navigate to the corresponding range and find the target option.

## How to Develop

For details about how to use related APIs, see [IndexUtil](../reference/apis-localization-kit/js-apis-i18n.md#indexutil8).

**Development Example**

```ts
// Import the i18n module.
import { i18n } from '@kit.LocalizationKit';

// Create indexes in a single language.
let indexUtil: i18n.IndexUtil = i18n.getInstance('zh-CN');
let indexList: Array<string> = indexUtil.getIndexList(); // indexList = ['...', 'A', 'B', 'C', ... 'X', 'Y', 'Z', '...']

// Create indexes in multiple languages.
indexUtil.addLocale('ru-RU');
// indexList = ['...', 'A', 'B', 'C', ... 'X', 'Y', 'Z', '...', 'А', 'Б', 'В', ... 'Э', 'Ю', 'Я', '...']
indexList = indexUtil.getIndexList();

// Obtain the index of the string.
let index: string = indexUtil.getIndex('Nihao'); // index = 'N'
```
