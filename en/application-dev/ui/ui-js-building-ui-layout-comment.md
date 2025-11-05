# Adding a Comment Area
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @fenglinbailu-->
<!--Designer: @lanshouren-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->

The comment component allows users to input messages and submit them by clicking the confirm button. Submitted comments are displayed in the comment area, where users can delete individual comments by clicking the delete button and then enter new messages.


This implementation combines **\<div>**, **\<text>**, and **\<input>** components with click event handling. The **\<input>** component handles message entry, while the **\<text>** components manage comment submission and deletion. The **commentText** state variable controls component visibility through conditional rendering (using the **if** attribute). Click events on the submission and deletion buttons update both the **commentText** state and **inputValue** content. The implementation example is as follows:


```html
<!-- xxx.hml -->
<div class="container">
  <text class="comment-title">Comment</text>
  <div if="{{!commentText}}">
    <input class="comment" value="{{inputValue}}" onchange="updateValue()"></input>
    <text class="comment-key" onclick="update" focusable="true">Done</text>
  </div>
  <div if="{{commentText}}">
    <text class="comment-text" focusable="true">{{inputValue}}</text>
    <text class="comment-key" onclick="update" focusable="true">Delete</text>
  </div>
</div>
```


```css
/* xxx.css */
.container {
  margin-top: 24px;
  background-color: #ffffff;
}
.comment-title {
  font-size: 40px;
  color: #1a1a1a;
  font-weight: bold;
  margin-top: 40px;
  margin-bottom: 10px;
}
.comment {
  width: 550px;
  height: 100px;
  background-color: lightgrey;
}
.comment-key {
  width: 150px;
  height: 100px;
  margin-left: 20px;
  font-size: 32px;
  color: #1a1a1a;
  font-weight: bold;
}
.comment-key:focus {
  color: #007dff;
}
.comment-text {
  width: 550px;
  height: 100px;
  text-align: left;
  line-height: 35px;
  font-size: 30px;
  color: #000000;
  border-bottom-color: #bcbcbc;
  border-bottom-width: 0.5px;
}
```


```js
// xxx.js
export default {
  data: {
    inputValue: '',
    commentText: false,
  },
  update() {
    this.commentText = !this.commentText;
  },
  updateValue(e) {
    this.inputValue = e.text;
  },
}
```
