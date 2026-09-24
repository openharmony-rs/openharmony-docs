# @ohos.arkui.advanced.Filter

多条件筛选，帮助用户在大量信息中找到所需内容，应结合具体场景选择合适筛选方式。多条件筛选控件由筛选器与悬浮条构成，悬浮条可下拉展示悬浮筛选器。筛选器样式可分为多行可折叠类型与多行列表类型，并可以在筛选器最后一行附加快捷筛选器。

> **说明：**
 >
 > - 该组件从API version 10开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
 >
 > - 该组件仅可在Stage模型下使用。
 >
 > - 如果Filter设置通用属性和通用事件，编译工具链会额外生
 > 成节点__Common__，并将通用属性或通用事件挂载在__Common__上，而不是直接应用到Filter本身。这可能导致开发者设置的通用属性或通用事件不生效或不符合预期，因此，不建议Filter设置通用属性和通用事件。

## 子组件

无

## 事件

不支持通用事件。

## 导入模块

```TypeScript
import { Filter, FilterParams, FilterResult, FilterType } from '@kit.ArkUI';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [FilterParams](arkts-arkui-arkui-advanced-filter-filterparams-c.md) | This parameter is used to define the input of each filtering dimension. |
| [FilterResult](arkts-arkui-arkui-advanced-filter-filterresult-c.md) | This parameter specifies the selection result of a filtering dimension. The index starts from 0. |

### 结构体

| 名称 | 说明 |
| --- | --- |
| [Filter](arkts-arkui-arkui-advanced-filter-filter-s.md) |  |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [FilterType](arkts-arkui-arkui-advanced-filter-filtertype-e.md) | 声明筛选器类型 |

## 示例

该示例设置FilterType属性为MULTI_LINE_FILTER，实现多行可折叠类型筛选器。

```TypeScript
import { Filter, FilterParams, FilterResult, FilterType } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  private filterParam: Array<FilterParams> = [{
    name: '月份',
    options: ['全部', '1月', '2月', '3月', '4月', '5月', '6月', '7月', '8月', '9月', '10月', '11月', '12月'],
  },
    {
      name: '年份',
      options: ['全部', '2023', '2022', '2021', '2020', '2019', '2018', '2017', '2016', '2015', '2014', '2013', '2012',
        '2011', '2010', '2009', '2008'],
    },
    {
      name: '节气',
      options: ['全部', '立春', '雨水', '惊蛰', '春分', '清明', '谷雨', '立夏', '小满', '芒种', '夏至', '小暑', '大暑',
        '立秋', '处暑', '白露', '秋分', '寒露', '霜降', '立冬', '小雪', '大雪', '冬至', '小寒', '大寒'],
    }];
  // additionFilters筛选行name必传，不可为空，否则整行不显示
  private additionParam: FilterParams =
    { name: '您还可以搜', options: ['运营栏目1', '运营栏目2', '运营栏目3', '运营栏目4', '运营栏目5', '运营栏目6'] };
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
          ForEach(this.arr, (item: number, index: number) => {
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
