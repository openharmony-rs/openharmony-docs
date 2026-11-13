# picker
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @luoying_ace_admin-->
<!--Designer: @weixin_52725220-->
<!--Tester: @xiong0104-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=bb8be30ac20777cbedde0933e1c8687834bf89bb translatedAt=2026-11-12T04:17:38.225Z pushedAt=2026-11-12T08:23:57.617Z nl=1 -->

>  **NOTE**
>  This component is supported since API version 4. Updates will be marked with a superscript to indicate their earliest API version.

The **\<picker>** component supports common, date, time, date and time, and multi-column text selectors.


## Required Permissions

None


## Child Components

Not supported


## Attributes

In addition to the [universal attributes](js-components-common-attributes.md), the following attributes are supported.

| Name   | Type     | Default Value  | Mandatory   | Description                                       |
| ---- | ------ | ---- | ---- | ---------------------------------------- |
| type | string | -    | No    | Picker type. Dynamic modification is not supported. The options are as follows:<br/>-&nbsp;**text**: text selector.<br/>-&nbsp;**date**: date selector.<br/>-&nbsp;**time**: time selector.<br/>-&nbsp;**datetime**: date and time selector.<br/>-&nbsp;**multi-text**: multi-column text selector. |


### Normal Picker

When the sliding picker type is set to text, it indicates a normal picker.

| Name       | Type     | Default Value  | Mandatory   | Description                                       |
| -------- | ------ | ---- | ---- | ---------------------------------------- |
| range    | Array  | -    | No    | Value range of the common selector, for example, **["15",&nbsp;"20",&nbsp;"25"]**.<br/>When using this attribute, use data binding in the form of `range ={{data}}`, and declare the corresponding variable `data:["15","20","25"]` in JavaScript. |
| selected | string | 0    | No    | Default value of the common selector. The value must be the index of &nbsp;**range**&nbsp;, and it indicates the default selected value on the pop-up window UI. |
| value    | string | -    | No    | Value of the common selector.                               |


### Date Selector

When **type** is set to **date**, a date selector is used.

| Name                 | Type           | Default Value        | Mandatory   | Description                                       |
| ------------------ | ------------ | ---------- | ---- | ---------------------------------------- |
| start              | &lt;time&gt; | 1970-1-1   | No    | Start date of the date selector, in the format of&nbsp;*YYYY-MM-DD*.        |
| end                | &lt;time&gt; | 2100-12-31 | No    | End date of the date selector, in the format of&nbsp;*YYYY-MM-DD*.        |
| selected           | string       | Current date       | No    | Default value of the date selector, in format of&nbsp;*YYYY-MM-DD*. This value indicates the default selected value on the pop-up window UI. |
| value              | string       | -          | Yes    | Value of the date selector.                               |
| lunar<sup>5+</sup> | boolean      | false      | No    | Whether the date selector displays the lunar calendar.<br/>Default value: **false**, indicating that the date selector displays the Gregorian calendar.                      |
| lunarswitch        | boolean      | false      | No    | Whether the date selector displays the lunar calendar switch, which is used to switch between the Gregorian calendar and lunar calendar. The value **true** means to display the lunar calendar switch for users to switch between the Gregorian calendar and lunar calendar. The value **false** means not to display the lunar calendar switch.<br/>When both **lunarswitch** and **lunar** are set to **true**, the switch is selected. |


### Time Selector

When **type** is set to **time**, a time selector is used.

| Name           | Type    | Default Value                        | Mandatory | Description                              |
| ------------- | ------- | ----------------------------------- | ---- | ---------------------------------------- |
| containsecond | boolean | false                               | No   | Whether seconds are contained. <br/>Default value: **false**, indicating that seconds are not contained.                           |
| selected      | string  | Current time                        | No   | Default value of the time selector, in format of&nbsp;*HH:mm*. If seconds are contained, the format is *HH:mm:ss*.<br/>This value indicates the default selected value on the pop-up window UI. |
| value         | string  | -                                   | No   | Value of the time selector.                               |
| hours         | number  | 24<sup>1-4</sup><br/>-<sup>5+</sup> | No   | Time format used by the time selector. Available values are as follows:<br/>-&nbsp;**12**: displayed in 12-hour format and distinguished by a.m. and p.m.<br/>-&nbsp;**24**: displayed in 24-hour format.<br/>Since API version 5, the default value is the most commonly-used hour format in the current locale. |


### Date and Time Selector

When **type** is set to **datetime**, a date and time selector is used.

| Name                | Type    | Default Value                        | Mandatory | Description                              |
| ------------------- | ------- | ------------------------------------ | -------- | ---------------------------------------- |
| selected            | string  | Current date and time                | No       | Default value of the date and time selector. The value can be in either of the following formats:<br/>-&nbsp;MM-DD-HH-mm<br/>-&nbsp;YYYY-MM-DD-HH-mm<br/>If the year is not set, the current year is used by default. This value indicates the default selected value on the pop-up window UI. |
| value               | string  | -                                    | Yes      | Value of the date and time selector.  |
| hours               | number  | 24<sup>1-4</sup><br/>-<sup>5+</sup>  | No       | Time format used by the date and time selector. Available values are as follows:<br/>-&nbsp;**12**: displayed in 12-hour format and distinguished by a.m. and p.m.<br/>-&nbsp;**24**: displayed in 24-hour format.<br/>Since API version 5, the default value is the most commonly-used hour format in the current locale. |
| lunar<sup>5+</sup>  | boolean | false                                | No       | Whether the date and time selector displays the lunar calendar.<br/>Default value: **false**, indicating that the date and time selector displays the Gregorian calendar. |
| lunarswitch         | boolean | false                                | No       | Whether the date and time selector displays the lunar calendar switch, which is used to switch between the Gregorian calendar and lunar calendar. The value **true** means to display the lunar calendar switch for users to switch between the Gregorian calendar and lunar calendar. The value **false** means not to display the lunar calendar switch.<br/>When both **lunarswitch** and **lunar** are set to **true**, the switch is selected. |


### Multi-column Text Selector

When **type** is set to **multi-text**, a multi-column text selector is used.

| Name      | Type      | Default Value | Mandatory | Description                                      |
| -------- | ------- | --------- | ---- | ---------------------------------------- |
| columns  | number  | -         | Yes   | Number of columns in the multi-column text selector.                            |
| range    | 2-dimensional array | -         | No    | Items of the multi-column text selector. **range** is a two-dimensional array that indicates the number of columns. Each item in the array indicates the data of each column, for example,&nbsp;**[["a","b"],&nbsp;["c","d"]]**.<br/>When using this attribute, use data binding in the form of `range ={{data}}`, and declare the corresponding variable `data:[["a","b"], ["c","d"]]` in JavaScript. |
| selected | Array   | [0,0,0,...] | No    | Default value of the multi-column text selector. This value is an array of the indexes of the selected items in each column, and it indicates the default selected value on the pop-up window UI. |
| value    | Array   | -         | No    | Value of the multi-column text selector. It is an array of the values of the selected items in each column.            |


## Styles

In addition to the [universal styles](js-components-common-styles.md), the following styles are supported.

| Name                        | Type                       | Default Value | Mandatory | Description                                |
| -------------------------- | -------------------------- | ---------- | ---- | ---------------------------------------- |
| text-color                 | &lt;color&gt;              | -          | No    | Text color of the selector.                                |
| font-size                  | &lt;length&gt;             | -          | No    | Font size of the selector.                                |
| allow-scale                | boolean                    | true       | No    | Whether the font size changes with the system's font size settings.<br/>If the **config-changes** tag of **fontSize** is configured for abilities in the **config.json** file, the setting takes effect without application restart.<br/>Default value: **true**, indicating that the font size changes with the system's font size settings. |
| letter-spacing             | &lt;length&gt;             | 0          | No    | Letter spacing of the selector. For details, see **letter-spacing** in the **[\<text>](js-components-basic-text.md#styles)** component. |
| text-decoration            | string                     | -          | No    | Text decoration of the selector. For details, see **text-decoration** in the **[\<text>](js-components-basic-text.md#styles)** component. |
| font-style                 | string                     | normal     | No    | Font style of the selector. For details, see **font-style** in the **[\<text>](js-components-basic-text.md#styles)** component. |
| font-weight                | number&nbsp;\|&nbsp;string | normal     | No    | Font weight of the selector. For details, see **font-weight** in the **[\<text>](js-components-basic-text.md#styles)** component. |
| font-family                | string                     | sans-serif | No    | Font family of the selector, in which fonts are separated by commas (,). Each font is set using a font name or font family name. The first font in the family or the specified [custom fonts](js-components-common-customizing-font.md) is used for the text. |
| line-height                | &lt;length&gt;             | 0px        | No    | Text line height of the selector.                                |
| column-height<sup>5+</sup> | &lt;length&gt;             | -          | No    | Height of the selector option list.                             |


## Events

In addition to the [universal events](js-components-common-events.md), the following events are supported.


### Common Selector

| Name     | Parameter                                       | Description                                       |
| ------ | ---------------------------------------- | ---------------------------------------- |
| change | {&nbsp;newValue:&nbsp;newValue,&nbsp;newSelected:&nbsp;newSelected&nbsp;} | Triggered when an item is selected and the OK button is clicked in the displayed pop-up window. **newSelected** is the index. |
| cancel | -                                        | Triggered when the cancel button is clicked.                      |


### Date Selector

| Name     | Parameter                                       | Description                                       |
| ------ | ---------------------------------------- | ---------------------------------------- |
| change | {&nbsp;year:&nbsp;year,&nbsp;month:&nbsp;month,&nbsp;day:&nbsp;day&nbsp;} | Triggered when an item is selected and the OK button is clicked in the displayed pop-up window.<br/>The value of **month** ranges from **0** (January) to **11** (December) since API version 5. |
| cancel | -                                        | Triggered when the cancel button is clicked.                     |


### Date and Time Selector

| Name     | Parameter                                       | Description                           |
| ------ | ---------------------------------------- | ---------------------------- |
| change | {&nbsp;year:&nbsp;year,&nbsp;month:&nbsp;month,&nbsp;day:&nbsp;day,&nbsp;&nbsp;hour:&nbsp;hour,&nbsp;minute:&nbsp;minute} | Triggered when an item is selected and the OK button is clicked in the displayed pop-up window. |
| cancel | -                                        | Triggered when the cancel button is clicked.          |


### Time Selector

| Name     | Parameter                                       | Description                                       |
| ------ | ---------------------------------------- | ---------------------------------------- |
| change | {&nbsp;hour:&nbsp;hour,&nbsp;minute:&nbsp;minute,&nbsp;[second:&nbsp;second]&nbsp;} | Triggered when an item is selected and the OK button is clicked in the displayed pop-up window. If **containsecond** is set to true, value contains seconds. |
| cancel | -                                        | Triggered when the cancel button is clicked.                      |


### Multi-column Text Selector

| Name           | Parameters                                       | Description                                       |
| ------------ | ---------------------------------------- | ---------------------------------------- |
| change       | {&nbsp;newValue:&nbsp;[newValue1,&nbsp;newValue2,&nbsp;newValue3,&nbsp;...],&nbsp;newSelected:[newSelected1,&nbsp;newSelected2,&nbsp;newSelected3,&nbsp;...]&nbsp;} | Triggered when an item is selected and the OK button is clicked in the displayed pop-up window.<br/>-&nbsp;**newValue** is an array consisting of the values of the selected items.<br/>-&nbsp;**newSelected** is an array consisting of the indexes of the selected items. The lengths of **newValue** and **newSelected** are the same as the length of **range**. |
| columnchange | {&nbsp;column:&nbsp;column,&nbsp;newValue:&nbsp;newValue,&nbsp;newSelected:&nbsp;newSelected&nbsp;} | Triggered when the value of a column in the multi-column selector changes.<br/>-&nbsp;**column**: column whose value has changed.<br/>-&nbsp;**newValue**: selected value.<br/>-&nbsp;**newSelected**: index of the selected value. |
| cancel       | -                                        | Triggered when the cancel button is clicked.                      |


## Methods

In addition to the [universal methods](js-components-common-methods.md), the following methods are supported.

| Name | Parameter | Description |
| ---- | ---- | --------------- |
| show | - | Shows the&nbsp;selector. |


## Example

```html
<!-- xxx.hml -->
<div class="container">
    <select @change="selectChange">
        <option value="{{ item }}" for="item in selectList">
            {{ item }}
        </option>
    </select>
    <picker id="picker0" type="text" value="{{ textvalue }}" selected="{{ textselect }}" range="{{ rangetext }}"
            onchange="textonchange"
            oncancel="textoncancel" class="pickertext" show="false"></picker>

    <picker id="picker1" type="date" value="{{ datevalue }}" start="2002-2-5" end="2030-6-5" selected="{{ dateselect }}"
            lunarswitch="true"
            onchange="dateonchange" oncancel="dateoncancel" class="pickerdate" show="false"></picker>

    <picker id="picker2" type="time" value="{{ timevalue }}" containsecond="{{ containsecond }}"
            selected="{{ timeselect }}" hours="12"
            onchange="timeonchange" oncancel="timeoncancel" class="pickertime" show="false"></picker>

    <picker id="picker3" type="datetime" value="{{ datetimevalue }}" selected="{{ datetimeselect }}" hours="24"
            lunarswitch="true"
            onchange="datetimeonchange" oncancel="datetimeoncancel" class="pickerdatetime" show="false"></picker>

    <picker id="picker4" type="multi-text" value="{{ multitextvalue }}" columns="3" range="{{ multitext }}"
            selected="{{ multitextselect }}"
            onchange="multitextonchange" oncancel="multitextoncancel" class="pickermuitl" show="false"></picker>
</div>
```

```css
/* xxx.css */
.container {
    flex-direction: column;
    justify-content: center;
    align-items: center;
}

picker {
    width: 60%;
    height: 80px;
    border-radius: 20px;
    text-color: white;
    font-size: 15px;
    background-color: #4747e3;
    margin-left: 20%;
}

select {
    background-color: #efecec;
    height: 50px;
    width: 60%;
    margin-left: 20%;
    margin-top: 300px;
    margin-bottom: 50px;
    font-size: 22px;
}
```

```js
// xxx.js
import promptAction from '@ohos.promptAction';

export default {
    data: {
        selectList: ["text", "date", "time", "datetime", "multitext"],
        rangetext: ['15', "20", "25"],
        multitext: [["a", "b", "c"], ["e", "f", "g"], ["h", "i"], ["k", "l", "m"]],
        textvalue: 'default textvalue',
        datevalue: 'default datevalue',
        timevalue: 'default timevalue',
        datetimevalue: 'default datetimevalue',
        multitextvalue: 'default multitextvalue',
        containsecond: true,
        multitextselect: [1, 2, 0],
        datetimeselect: '2012-5-6-11-25',
        timeselect: '11:22:30',
        dateselect: '2021-3-2',
        textselect: '2'
    },
    selectChange(e) {
        for (let i = 0;i < this.selectList.length; i++) {
            if (e.newValue == this.selectList[i]) {
                this.$element("picker" + i).show();
            }
        }
    },
    textonchange(e) {
        this.textvalue = e.newValue;
        promptAction.showToast({
            message: "text:" + e.newValue + ",newSelected:" + e.newSelected
        })
    },
    textoncancel(e) {
        promptAction.showToast({
            message: "text: textoncancel"
        })
    },
    dateonchange(e) {
        this.datevalue = e.year + "-" + (e.month + 1) + "-" + e.day;
        promptAction.showToast({
            message: "date:" + e.year + "-" + (e.month + 1) + "-" + e.day
        })
    },
    dateoncancel() {
        promptAction.showToast({
            message: "date: dateoncancel"
        })
    },
    timeonchange(e) {
        if (this.containsecond) {
            this.timevalue = e.hour + ":" + e.minute + ":" + e.second;
            promptAction.showToast({
                message: "Time:" + e.hour + ":" + e.minute + ":" + e.second
            })
        } else {
            this.timevalue = e.hour + ":" + e.minute;
            promptAction.showToast({
                message: "Time:" + e.hour + ":" + e.minute
            })
        }
    },
    timeoncancel() {
        promptAction.showToast({
            message: "timeoncancel"
        })
    },
    datetimeonchange(e) {
        this.datetimevalue = e.year + "-" + (e.month + 1) + "-" + e.day + " " + e.hour + ":" + e.minute;
        promptAction.showToast({
            message: "Time:" + (e.month + 1) + "-" + e.day + " " + e.hour + ":" + e.minute
        })
    },
    datetimeoncancel() {
        promptAction.showToast({
            message: "datetimeoncancel"
        })
    },
    multitextonchange(e) {
        this.multitextvalue = e.newValue;
        promptAction.showToast({
            message: "Multi-column text change" + e.newValue
        })
    },
    multitextoncancel() {
        promptAction.showToast({
            message: "multitextoncancel"
        })
    },
    popup_picker() {
        this.$element("picker0").show();
    },
}
```


