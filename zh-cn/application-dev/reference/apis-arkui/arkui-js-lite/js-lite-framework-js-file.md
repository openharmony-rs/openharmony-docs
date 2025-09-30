# app.js
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @HelloCrease-->

## 应用生命周期<sup>4+</sup>

每个应用可以在app.js自定义应用级生命周期的实现逻辑，包括：


- onCreate：在应用生成时被调用的生命周期函数。

- onDestroy：在应用销毁时被调用的生命周期函数。


以下示例仅在生命周期函数中打印对应日志：



```js
// app.js
export default {
  onCreate() {
    console.info('Application onCreate');
  },
  onDestroy() {
    console.info('Application onDestroy');
  },
}
```

## 应用对象<sup>10+</sup>

| 属性     | 类型       | 描述                                       |
| ------ | -------- | ---------------------------------------- |
| getApp | Function | 提供getApp()全局方法，可以在页面js文件中获取app.js中暴露的数据对象。 |

> **说明**：
>
> 应用对象是全局数据，其在整个应用消亡之前都会一直占用JS内存。尽管应用对象可为不同页面共享数据提供便利，但因为小型设备本身内存比较小，也应谨慎使用。如果过度使用，则容易造成应用在进入复杂page页面时，内存不够而出现异常。

示例如下：

在 app.js 中声明应用对象:

```javascript
// app.js
export default {
    data: {
        test: "by getApp"
    },
    onCreate() {
        console.info('Application onCreate');
    },
    onDestroy() {
        console.info('Application onDestroy');
    },
};
```

在具体的页面中访问应用对象：

```javascript
// index.js
export default {
    data: {
        title: ""
    },
    onInit() {
        if (typeof getApp !== 'undefined') {
            var appData = getApp().data;
            if (typeof appData !== 'undefined') {
                this.title = appData.name; // read from app data
            }
        }
    },
    clickHandler() {
        if (typeof getApp !== 'undefined') {
            var appData = getApp().data;
            if (typeof appData !== 'undefined') {
                appData.name = this.title; // write to app data
            }
        }
    }
}
```

> **说明**：
>
> 为了应用可在不支持getApp的低版本上正常运行，代码中应进行兼容性处理，即在使用getApp前先判断其是否可用。