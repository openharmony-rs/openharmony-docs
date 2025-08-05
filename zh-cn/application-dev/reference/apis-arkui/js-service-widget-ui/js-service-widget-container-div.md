# div
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @lanshouren-->
<!--SE: @lanshouren-->
<!--TSE: @liuli0427-->


基础容器，用作页面结构的根节点或将内容进行分组。

>  **说明：**
>
> 从API Version 8 开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。

## 子组件

支持。


## 属性

支持[通用属性](js-service-widget-common-attributes.md)。


## 样式

除支持[通用样式](js-service-widget-common-styles.md)外，还支持如下样式：

| 名称 | 类型 | 默认值 | 必填 | 描述 |
| -------- | -------- | -------- | -------- | -------- |
| flex-direction | string | row | 否 | flex容器主轴方向。可选项有：<br/>-&nbsp;column：垂直方向从上到下。<br/>-&nbsp;row：水平方向从左到右。 |
| flex-wrap | string | nowrap | 否 | flex容器是单行还是多行显示，该值暂不支持动态修改。可选项有：<br/>-&nbsp;nowrap：不换行，单行显示。<br/>-&nbsp;wrap：换行，多行显示。 |
| justify-content | string | flex-start | 否 | flex容器当前行的主轴对齐格式。可选项有：<br/>-&nbsp;flex-start：项目位于容器的开头。<br/>-&nbsp;flex-end：项目位于容器的结尾。<br/>-&nbsp;center：项目位于容器的中心。<br/>-&nbsp;space-between：项目位于各行之间留有空白的容器内。<br/>-&nbsp;space-around：项目位于各行之前、之间、之后都留有空白的容器内。<br/>-&nbsp;space-evenly<sup>5+</sup>:&nbsp;&nbsp;均匀排列每个元素，每个元素之间的间隔相等。 |
| align-items | string | stretch | 否 | flex容器当前行的交叉轴对齐格式，可选值为：<br/>-&nbsp;stretch：弹性元素在交叉轴方向被拉伸到与容器相同的高度或宽度。<br/>-&nbsp;flex-start：元素向交叉轴起点对齐。<br/>-&nbsp;flex-end：元素向交叉轴终点对齐。<br/>-&nbsp;center：元素在交叉轴居中。 |
| align-content | string | flex-start | 否 | 交叉轴中有额外的空间时，多行内容对齐格式，可选值为：<br/>-&nbsp;flex-start：所有行从交叉轴起点开始填充。第一行的交叉轴起点边和容器的交叉轴起点边对齐。接下来的每一行紧跟前一行。<br/>-&nbsp;flex-end：所有行从交叉轴末尾开始填充。最后一行的交叉轴终点和容器的交叉轴终点对齐。同时所有后续行与前一个对齐。<br/>-&nbsp;center：所有行朝向容器的中心填充。每行互相紧挨，相对于容器居中对齐。容器的交叉轴起点边和第一行的距离相等于容器的交叉轴终点边和最后一行的距离。<br/>-&nbsp;space-between：所有行在容器中平均分布。相邻两行间距相等。容器的交叉轴起点边和终点边分别与第一行和最后一行的边对齐。<br/>-&nbsp;space-around：所有行在容器中平均分布，相邻两行间距相等。容器的交叉轴起点边和终点边分别与第一行和最后一行的距离是相邻两行间距的一半。 |
| display | string | flex | 否 | 确定该元素视图框的类型，该值暂不支持动态修改。可选值为：<br/>-&nbsp;flex：弹性布局<br/>-&nbsp;none：不渲染此元素 |
| grid-template-[columns\|rows] | string | 1行1列 | 否 | 用于设置当前网格布局行和列的数量，不设置时默认1行1列，仅当display为grid时生效。<br/>示例：如设置grid-template-columns为：<br/>-&nbsp;50px&nbsp;100px&nbsp;60px：分三列，第一列50px，第二列100px，第三列60px。<br/>-&nbsp;1fr&nbsp;1fr&nbsp;2fr：分三列，将父组件允许的宽分为4等份，第一列占1份，第二列占1份，第三列占2份。<br/>-&nbsp;30%&nbsp;20%&nbsp;50%：分三列，将父组件允许的宽为基准，第一列占30%，第二列占20%，第三列占50%。<br/>-&nbsp;repeat(2,100px)：分两列，第一列100px，第二列100px。<br/>-&nbsp;repeat(auto-fill,100px)<sup>5+</sup>：按照每列100px的大小和交叉轴大小计算最大正整数重复次数，按照该重复次数布满交叉轴。<br/>-&nbsp;auto&nbsp;1fr&nbsp;1fr：分三列，第一列自适应内部子组件所需宽度，剩余空间分为两等份，第二列占一份，第三列占一份。 |
| grid-[columns\|rows]-gap | &lt;length&gt; | 0 | 否 | 用于设置行与行的间距或者列与列的间距，也可以支持通过grid-gap设置相同的行列间距，仅当display为grid时生效。 |
| grid-row-[start\|end] | number | - | 否 | 用于设置当前元素在网格布局中的起止行号，仅当父组件display样式为grid时生效（仅div支持display样式设置为grid）。 |
| grid-column-[start\|end] | number | - | 否 | 用于设置当前元素在网格布局中的起止列号，仅当父组件display样式为grid时生效（仅div支持display样式设置为grid）。 |
| grid-auto-flow | string | - | 否 | 使用框架自动布局算法进行网格的布局，可选值为：<br/>-&nbsp;row：逐行填充元素，如果行空间不够，则新增行。<br/>-&nbsp;column：逐列填充元素，如果列空间不够，则新增列。 |
| align-items | string | - | 否 | 设置容器中元素交叉轴上的对齐方式：<br/>-&nbsp;stretch：Flex容器内容在交叉轴方向被拉伸到与容器相同的高度或宽度。<br/>-&nbsp;flex-start：Flex布局容器内元素向交叉轴起点对齐。<br/>-&nbsp;flex-end：Flex布局容器内元素向交叉轴终点对齐。<br/>-&nbsp;center：Flex布局容器内元素在交叉轴居中对齐。<br/>-&nbsp;baseline：如Flex布局纵向排列，则该值与'flex-start'等效。横向布局时，内容元素存在文本时按照文本基线对齐，否则底部对齐。 |


## 事件

支持[通用事件](js-service-widget-common-events.md)。


## 示例

1. Flex样式
  
   ```html
   <!-- xxx.hml -->
   <div class="container">
     <div class="flex-box">
       <div class="flex-item color-primary"></div>
       <div class="flex-item color-warning"></div>
       <div class="flex-item color-success"></div>
     </div>
   </div>
   ```

   
   ```css
   /* xxx.css */
   .container {
     flex-direction: column;
     justify-content: center;
     align-items: center;
     width: 454px;
     height: 454px;
   }
   .flex-box {
     justify-content: space-around;
     align-items: center;
     width: 400px;
     height: 140px;
     background-color: #ffffff;
   }
   .flex-item {
     width: 120px;
     height: 120px;
     border-radius: 16px;
   }
   .color-primary {
     background-color: #007dff;
   }
   .color-warning {
     background-color: #ff7500;
   }
   .color-success {
     background-color: #41ba41;
   }
   ```
    **2*4卡片**

    ![zh-cn_image_0000001231610863](figures/zh-cn_image_0000001231610863.png)

2. Flex Wrap样式
  
   ```html
   <!-- xxx.hml -->
   <div class="container">
     <div class="flex-box">
       <div class="flex-item color-primary"></div>
       <div class="flex-item color-warning"></div>
       <div class="flex-item color-success"></div>
     </div>
   </div>
   ```

   
   ```css
   /* xxx.css */
   .container {
     flex-direction: column;
     justify-content: center;
     align-items: center;
     width: 454px;
     height: 454px;
   }
   .flex-box {
     justify-content: space-around;
     align-items: center;
     flex-wrap: wrap;
     width: 300px;
     height: 250px;
     background-color: #ffffff;
   }
   .flex-item {
     width: 120px;
     height: 120px;
     border-radius: 16px;
   }
   .color-primary {
     background-color: #007dff;
   }
   .color-warning {
     background-color: #ff7500;
   }
   .color-success {
     background-color: #41ba41;
   }
   ```
   **4*4卡片**

   ![zh-cn_image_0000001186131150](figures/zh-cn_image_0000001186131150.png)

