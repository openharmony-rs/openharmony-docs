# Adding Interactions
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @jiangtao92-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->

You can make the UI interactive by binding events to components. This topic describes how to associate a click event with **\<div>**, **\<text>**, and **\<image>** components to build a like button, as shown below.

![en-us_image_0000001064068638](figures/en-us_image_0000001064068638.gif)


The like button is implemented by binding a click event to a **\<div>** component, which contains an **\<image>** component and a **\<text>** component.


- The **\<image>** component displays the liked or unliked state. The click event handler toggles the image source between the liked and unliked versions.

- The **\<text>** component displays the number of likes, which is updated synchronously in the click event handler.


The click event calls the **likeClick()** function defined in the .js file. This function toggles the value of **isPressed**, which controls the image display. If the value of **isPressed** is **true**, the like count is incremented by 1. The function updates the corresponding **\<div>** component in the .hml file. The styles for the like button and its child components are defined in the .css file. Below is a complete example:


```html
<!-- xxx.hml -->
<!-- Like button -->
<div>
  <div class="like" onclick="likeClick">
    <image class="like-img" src="{{likeImage}}" focusable="true"></image>
    <text class="like-num" focusable="true">{{total}}</text>
  </div>
</div>
```


```css
/* xxx.css */
.like {
  width: 104px;
  height: 54px;
  border: 2px solid #bcbcbc;
  justify-content: space-between;
  align-items: center;
  margin-left: 72px;
  border-radius: 8px;
}
.like-img {
  width: 33px;
  height: 33px;
  margin-left: 14px;
}
.like-num {
  color: #bcbcbc;
  font-size: 20px;
  margin-right: 17px;
}
```


```js
// xxx.js
export default {
  data: {
    likeImage: '/common/unLike.png',
    isPressed: false,
    total: 20,
  },
  likeClick() {
    var temp;
    if (!this.isPressed) {
      temp = this.total + 1;
      this.likeImage = '/common/like.png';
    } else {
      temp = this.total - 1;
      this.likeImage = '/common/unLike.png';
    }
    this.total = temp;
    this.isPressed = !this.isPressed;
  },
}
```


In addition, a variety of form components, such as switches, tags, and pickers, are available to help you create flexible and engaging interactions in your layouts.
