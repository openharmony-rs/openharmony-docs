# Sorting by Indexes

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @yliupy-->
<!--Designer: @sunyaozu-->
<!--Tester: @lpw_work-->
<!--Adviser: @Brilliantry_Rui-->

## Use Cases

When there are many options in a list, users need to slide the window to search for the target option. Sorting by indexes is here to help them quickly find the target option by way of creating an index for each option. It is actually a kind of labeling. For example, labels A, B, C, and D on the right of the contact page correspond to the initial letters of contact names. If you want to find John, clicking J will direct you to a list of names starting with J. Such labels are called indexes, which help to quickly navigate to the corresponding range and find the target option.

## How to Develop

For details about how to use related APIs, see [IndexUtil](../reference/apis-localization-kit/js-apis-i18n.md#indexutil8).

1. Import the related modules.

   <!-- @[import_module](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/International/Internationalization/entry/src/main/ets/i18napplication/MultilingualSorting.ets) -->
   
   ``` TypeScript
   import { i18n } from '@kit.LocalizationKit';
   ```

2. Obtain the index list and index values.

   <!-- @[create_index](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/International/Internationalization/entry/src/main/ets/i18napplication/MultilingualSorting.ets) -->
   
   ``` TypeScript
   // Create indexes in a single language.
   let indexUtil: i18n.IndexUtil = i18n.getInstance('zh-CN');
   let indexList = indexUtil.getIndexList(); // indexList = ['…', 'A', 'B', 'C', ... 'X', 'Y', 'Z', '…']
   
   // Create indexes in multiple languages.
   indexUtil.addLocale('ru-RU');
   // indexList = ['...', 'A', 'B', 'C', ... 'X', 'Y', 'Z', '...', 'А', 'Б', 'В', ... 'Э', 'Ю', 'Я', '...']
   indexList = indexUtil.getIndexList();
   
   // Obtain the index of the string.
   let index = indexUtil.getIndex('Hello'); // index = 'N'
   ```
   
