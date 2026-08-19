# WaterFlowSections

瀑布流分组信息。 > **说明：** > > 使用splice、push、update修改分组信息后需要保证所有分组子节点总数与瀑布流实际子节点总数一致，否则会出现瀑布流因为不能正常布局而无法滑动的问题。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class WaterFlowSections--><!--Device-unnamed-export declare class WaterFlowSections-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor()
```

创建一个瀑布流分组。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WaterFlowSections-constructor()--><!--Device-WaterFlowSections-constructor()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## length

```TypeScript
length(): int
```

获取瀑布流中分组数量。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WaterFlowSections-length(): int--><!--Device-WaterFlowSections-length(): int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 瀑布流中分组数量。 |

## push

```TypeScript
push(section: SectionOptions): boolean
```

将指定分组添加到瀑布流末尾。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WaterFlowSections-push(section: SectionOptions): boolean--><!--Device-WaterFlowSections-push(section: SectionOptions): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| section | [SectionOptions](arkts-na-waterflow-sectionoptions-c.md) | 是 | 添加到瀑布流末尾的分组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 分组添加成功返回true，添加失败（新分组的itemsCount不是非负数）返回false。 |

## splice

```TypeScript
splice(start: int, deleteCount?: int, sections?: Array<SectionOptions>): boolean
```

移除或者替换已存在的分组和/或添加新分组。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WaterFlowSections-splice(start: int, deleteCount?: int, sections?: Array<SectionOptions>): boolean--><!--Device-WaterFlowSections-splice(start: int, deleteCount?: int, sections?: Array<SectionOptions>): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| start | int | 是 | 从0开始计算的索引，会转换为整数，表示要开始改变分组的位置。<br/>**说明：** <br/>1. 如果索引是负数，则从末尾开始计算，使用 `start + WaterFlowSections.length()`。<br/>2. 如果 `start &lt; -WaterFlowSections.length()`，则使用0。<br/>3. 如果 `start &gt;= WaterFlowSections.length()`，则在最后添加新分组。 <br>取值限定为整数。 |
| deleteCount | int | 否 | 从0开始计算的索引，会转换为整数，表示要开始改变分组的位置。<br/>**说明：** <br/>1. 如果索引是负数，则从末尾开始计算，使用 `start + WaterFlowSections.length()`。<br/>2. 如果 `start &lt; -WaterFlowSections.length()`，则使用0。<br/>3. 如果 `start &gt;= WaterFlowSections.length()`，则在最后添加新分组。 <br>取值限定为整数。 |
| sections | Array&lt;[SectionOptions](arkts-na-waterflow-sectionoptions-c.md)&gt; | 否 | 表示要从start开始加入的分组。如果不指定，`splice()`将只从瀑布流中删除分组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 分组修改成功返回true；修改失败（要加入的分组中有任意分组的itemsCount不是非负数）返回false。 |

## update

```TypeScript
update(sectionIndex: int, section: SectionOptions): boolean
```

修改指定索引分组的配置信息。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WaterFlowSections-update(sectionIndex: int, section: SectionOptions): boolean--><!--Device-WaterFlowSections-update(sectionIndex: int, section: SectionOptions): boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sectionIndex | int | 是 | 从0开始计算的索引，会转换为整数，表示要修改的分组的位置。<br/>**说明：** <br/>1. 如果索引是负数，则从末尾开始计算，使用 `sectionIndex + WaterFlowSections.length()`。<br/>2. 如果`sectionIndex &lt; -WaterFlowSections.length()`，则使用0。<br/> 3. 如果`sectionIndex &gt;= WaterFlowSections.length()`，则在最后添加新分组。 <br>取值限定为整数。 |
| section | [SectionOptions](arkts-na-waterflow-sectionoptions-c.md) | 是 | 新的分组信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 分组是否更新成功。true：分组更新成功，false：新分组的itemsCount不是非负数。 |

## values

```TypeScript
values(): Array<SectionOptions>
```

获取瀑布流中所有分组配置信息。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WaterFlowSections-values(): Array<SectionOptions>--><!--Device-WaterFlowSections-values(): Array<SectionOptions>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[SectionOptions](arkts-na-waterflow-sectionoptions-c.md)&gt; | 瀑布流中所有分组配置信息。 |

