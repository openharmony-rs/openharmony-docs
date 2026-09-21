# @ohos.arkui.advanced.Filter

## Modules to Import

```TypeScript
import { Filter, FilterParams, FilterResult, FilterType } from '@kit.ArkUI';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [FilterParams](arkts-arkui-arkui-advanced-filter-filterparams-c.md) | This parameter is used to define the input of each filtering dimension. |
| [FilterResult](arkts-arkui-arkui-advanced-filter-filterresult-c.md) | This parameter specifies the selection result of a filtering dimension. The index starts from 0. |

### Structs

| Name | Description |
| --- | --- |
| [Filter](arkts-arkui-arkui-advanced-filter-filter-s.md) | Declare Filter.The Filter is used in scenarios where multi-dimensional filtering is required. |

### Enums

| Name | Description |
| --- | --- |
| [FilterType](arkts-arkui-arkui-advanced-filter-filtertype-e.md) | Declare FilterType @enum { FilterType } |

## Examples

This example shows how to implement a multi-line collapsible filter by setting FilterType to MULTI_LINE_FILTER.

```TypeScript
import { Filter, FilterParams, FilterResult, FilterType } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  private filterParam: Array<FilterParams> = [{
    name: 'Month',
    options: ['All', 'Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'],
  },
    {
      name: 'Year',
      options: ['All', '2023', '2022', '2021', '2020', '2019', '2018', '2017', '2016', '2015', '2014', '2013', '2012',
        '2011', '2010', '2009', '2008'],
    },
    {
      name: 'Day',
      options: ['All', '1', '2', '3', '4', '5',' 6', '7','8', '9','10', '11', '12',
        '13','14', '15', '16', '17', '18','19','20','21','22', '23', '24'],
    }];
  // Addition filter parameter. The name of the filter dimension must be specified. Otherwise, the entire filter dimension is not displayed.
  private additionParam: FilterParams =
    { name: 'Suggestions', options: ['Category 1', 'Category 2', 'Category 3', 'Category 4', 'Category 5', 'Category 6'] };
  private arr: number[] = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

  build() {
    Column() {
      Filter({
        multiFilters: this.filterParam,
        additionFilters: this.additionParam,
        filterType: FilterType.MULTI_LINE_FILTER,
        onFilterChanged: (select: Array<FilterResult>) => {
          console.info('rec filter change');
          for (let filter of select) {
            console.info('name:' + filter.name + ',index:' + filter.index + ',value:' + filter.value);
          }
        }
      }) {
        List({ initialIndex: 0 }) {
          ForEach(this.arr, (item: string, index: number) => {
            ListItem() {
              Text(item.toString())
                .width('100%')
                .height(100)
                .fontSize(16)
                .textAlign(TextAlign.Center)
                .borderRadius(10)
                .backgroundColor(Color.White)
                .margin({ top: 10, bottom: 10 })
            }
          })
        }.backgroundColor(Color.Gray)
        .padding({ left: 20, right: 20 })
      }
    }
    .height('100%')
    .width('100%')
  }
}
```
