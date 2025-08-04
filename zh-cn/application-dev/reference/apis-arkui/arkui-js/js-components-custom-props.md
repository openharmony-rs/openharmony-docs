# 数据传递与处理
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @seaside_wu1-->
<!--SE: @shiyu_huang-->
<!--TSE: @TerryTsao-->


## Props

自定义组件可以通过props声明属性，父组件通过设置属性向子组件传递参数，props支持类型包括：String，Number，Boolean，Array，Object，Function。camelCase (驼峰命名法) 的 prop 名，在外部父组件传递参数时需要使用 kebab-case (短横线分隔命名) 形式，即当属性compProp在父组件引用时需要转换为comp-prop。给自定义组件添加props，通过父组件向下传递参数的示例如下：

```html
<!-- comp.hml -->
<div class="item"> 
   <text class="title-style">{{compProp}}</text> 
</div>
```

```js
// comp.js 
export default { 
  props: ['compProp'],
}
```

```html
<!-- xxx.hml -->
<element name='comp' src='../common/component/comp/comp.hml'></element>
<div class="container"> 
   <comp comp-prop="{{title}}"></comp> 
</div>
```

>  **说明：**
>
>  自定义属性命名时禁止以on、@、on:、grab: 等保留关键字为开头。

### 添加默认值

子组件可以通过固定值default设置默认值，当父组件没有设置该属性时，将使用其默认值。此情况下props属性必须为对象形式，不能用数组形式，示例如下：

```html
<!-- comp.hml -->
<div class="item"> 
   <text class="title-style">{{title}}</text> 
</div>
```

```js
// comp.js
export default { 
  props: {
    title: {
      default: 'title',
    },
  },
}
```

本示例中加入了一个text组件显示标题，标题的内容是一个自定义属性，显示用户设置的标题内容，当用户没有设置时显示默认值title。在引用该组件时添加该属性的设置：

```html
<!-- xxx.hml -->
<element name='comp' src='../common/component/comp/comp.hml'></element>
<div class="container"> 
   <comp title="自定义组件"></comp> 
</div>
```

### 数据单向性

父子组件之间数据的传递是单向的，只能从父组件传递给子组件，子组件不能直接修改父组件传递下来的值，可以将props传入的值用data接收后作为默认值，再对data的值进行修改。

```js
// comp.js
export default { 
  props: ['defaultCount'],
  data() {
    return {
      count: this.defaultCount,
    };
  },
  onClick() {
    this.count = this.count + 1;
  },
}
```

### $watch感知数据改变

如果需要观察组件中属性变化，可以通过$watch方法增加属性变化回调。使用方法如下：

```js
// comp.js
export default { 
  props: ['title'],
  onInit() {
    this.$watch('title', 'onPropertyChange');
  },
  onPropertyChange(newV, oldV) {
    console.info('title 属性变化 ' + newV + ' ' + oldV);
  },
}
```


## computed

自定义组件中经常需要在读取或设置某个属性时进行预先处理，提高开发效率，此种情况就需要使用computed计算属性。computed字段中可通过设置属性的getter和setter方法在属性读写的时候进行触发，使用方式如下：

```js
// comp.js
export default { 
  props: ['title'],
  data() {
    return {
      objTitle: this.title,
      time: 'Today',
    };
  },
  computed: {
    message() {
      return this.time + ' ' + this.objTitle;
    },
    notice: {
      get() {
        return this.time;
      },
      set(newValue) {
        this.time = newValue;
      },
    },
  },
  onClick() {
    console.info('get click event ' + this.message);
    this.notice = 'Tomorrow';
  },
}
```

这里声明的第一个计算属性message默认只有getter函数，message的值会取决于objTitle的值的变化。getter函数只能读取不能改变参数值，例如data中初始化定义的time，当需要赋值给计算属性的时候可以提供一个setter函数，如示例中的notice。