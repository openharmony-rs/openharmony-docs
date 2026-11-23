# Animation Styles
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hehongyang3-->
<!--Designer: @hehongyang3-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=8dd2d5cdf88acdc31ee17ec2006247a008c91d7c translatedAt=2026-11-12T04:21:22.542Z pushedAt=2026-11-17T11:16:31.435Z nl=1 -->

>  **NOTE**
>
>  Supported since API version 4. Updates will be marked with a superscript to indicate their earliest API version.

Components support dynamic rotation, translation, and scaling effects. These effects can be set in the **style** attribute or CSS files.

## Attributes

| Name                               | Type                                      | Description                                      |
| --------------------------------- | ---------------------------------------- | ---------------------------------------- |
| transform-origin                  | string<sup>6+</sup>&nbsp;\|<br>&nbsp;&lt;percentage&gt;&nbsp;\|<br>&nbsp;&lt;length&gt;&nbsp;string<sup>6+</sup>&nbsp;\|<br>&nbsp;&lt;percentage&gt;&nbsp;\|&nbsp;&lt;length&gt; | Origin position of the transformed element. The unit can be px or a percentage (relative to the animation target component). If only one value is specified, the other one is **50%**. The available values for the first string are **left**, **center**, and **right**. The available values for the second string are **top**, **center**, and **bottom**.<br>Example:<br>transform-origin: 200px 30%<br>transform-origin: 100px top<br>transform-origin: center center<br>Default value: **center center**|
| transform                         | string                                   | Translation, rotation, and scaling attributes.<br>For details, see Table 1 transform.|
| animation<sup>6+</sup>            | string                                   | Animation attributes in the format of **duration \| timing-function \| delay \| iteration-count \| direction \| fill-mode \| play-state \| name**. The order of the parameters is not specified, but the **duration** and **delay** parameters are parsed based on where they are placed.<br>Default value: **0s ease 0s 1 normal none running none**|
| animation-name                    | string                                   | @keyframes. For details, see Table 2 @keyframes.       |
| animation-delay                   | &lt;time&gt;                             | Delay for playing the animation, in s or ms (default), for example, **1000 ms** or **1s**.<br>Default value: **0**|
| animation-duration                | &lt;time&gt;                             | Animation duration, in s or ms (default), for example, **1000 ms** or **1s**.<br>**animation-duration** must be specified. Otherwise, the duration is **0**, which means the animation will not be played.<br>Default value: **0**|
| animation-iteration-count         | number&nbsp;\|&nbsp;infinite             | Number of times that an animation is played. The animation is played once by default. You can set the value to **infinite** to play the animation infinitely.<br>Default value: **1**|
| animation-timing-function         | string                                   | Speed curve of animation execution, which is used to make the animation smoother.<br/>Available values are as follows:<br/>-&nbsp;**linear**: The animation speed is the same from start to finish.<br/>-&nbsp;**ease**: The animation starts at a low speed, then speeds up, and slows down before the end. cubic-bezier(0.25,&nbsp;0.1,&nbsp;0.25,&nbsp;1.0).<br/>-&nbsp;**ease-in**: The animation starts at a low speed. cubic-bezier(0.42,&nbsp;0.0,&nbsp;1.0,&nbsp;1.0).<br/>-&nbsp;**ease-out**: The animation ends at a low speed. cubic-bezier(0.0,&nbsp;0.0,&nbsp;0.58,&nbsp;1.0).<br/>-&nbsp;**ease-in-out**: The animation starts and ends at a low speed. cubic-bezier(0.42,&nbsp;0.0,&nbsp;0.58,&nbsp;1.0).<br/>-&nbsp;**friction**: damping curve. cubic-bezier(0.2,&nbsp;0.0,&nbsp;0.2,&nbsp;1.0).<br/>-&nbsp;**extreme-deceleration**: extremely slow curve. cubic-bezier(0.0,&nbsp;0.0,&nbsp;0.0,&nbsp;1.0).<br/>-&nbsp;**sharp**: sharp curve. cubic-bezier(0.33,&nbsp;0.0,&nbsp;0.67,&nbsp;1.0).<br/>-&nbsp;**rhythm**: rhythm curve. cubic-bezier(0.7,&nbsp;0.0,&nbsp;0.2,&nbsp;1.0).<br/>-&nbsp;**smooth**: smooth curve. cubic-bezier(0.4,&nbsp;0.0,&nbsp;0.4,&nbsp;1.0).<br/>-&nbsp;**cubic-bezier**: animation change process in a cubic Bezier function. The x and y values of the input parameters must be from 0 to 1.<br/>-&nbsp;**steps**:&nbsp;step curve<sup>6+</sup>.  **Syntax**: steps(number[,&nbsp;end\|start]); **number** must be set, and the supported type is a positive integer. The second parameter is optional and indicates whether the step change occurs at the start or end of each interval. It supports **end** or **start**, and the default value is **end**.<br>Default value: **ease** |
| animation-direction<sup>6+</sup>  | string                                   | Mode of playing the animation.<br>- **normal**: Plays the animation in forward loop mode.<br>- **reverse**: Plays the animation in reverse loop mode.<br>- **alternate**: Plays the animation in alternating loop mode. When the animation is played for an odd number of times, the playback is in forward direction. When the animation is played for an even number of times, the playback is in reverse direction.<br>- **alternate-reverse**: Plays the animation in reverse alternating loop mode. When the animation is played for an odd number of times, the playback is in reverse direction. When the animation is played for an even number of times, the playback is in forward direction.<br>Default value: **normal**|
| animation-fill-mode               | string                                   | Start and end styles of the animation.<br>- **none**: No style is applied to the target before or after the animation is executed.<br>- **forwards**: The target keeps the state at the end of the animation (defined in the last key frame) after the animation is executed.<br>- **backwards**<sup>6+</sup>: The animation uses the value defined in the first key frame during the **animation-delay**. When **animation-direction** is set to **normal** or **alternate**, the value in the **from** key frame is used. When **animation-direction** is set to **reverse** or **alternate-reverse**, the value in the **to** key frame is used.<br>- **both**<sup>6+</sup>: The animation follows the **forwards** and **backwards** rules.<br>Default value: **none**|
| animation-play-state<sup>6+</sup> | string                                   | Current state of the animation.<br>- **paused**: The animation is paused.<br>- **running**: The animation is playing.<br>Default value: **running**|
| transition<sup>6+</sup>           | string                                   | Transition effect when the component status is switched. The following four attributes can be set through the **transition** attribute:<br>- **transition-property**: name of the CSS property for setting the transition effect. Currently, the width, height, and background color are supported.<br>- **transition-duration**: duration required for completing the transition effect, in seconds.<br>- **transition-timing-function**: time curve of the transition effect. The curve provided by the style animation is supported.<br>- **transition-delay**: delay for starting the transition effect, in seconds.<br>Default value: **all 0 ease 0**|


**Table 1** transform

| Name                      | Type                                      | Description                                      |
| ------------------------ | ---------------------------------------- | ---------------------------------------- |
| none<sup>6+</sup>        | -                                        | Does not perform any transformation.                                |
| matrix<sup>6+</sup>      | &lt;number&gt;                           | Defines a matrix of six values, which represent scaleX, skewY, skewX, scaleY, translateX, translateY.|
| matrix3d<sup>6+</sup>    | &lt;number&gt;                           | Defines a 4 x 4 matrix of 16 values.                          |
| translate                | &lt;length&gt;&nbsp;\|&nbsp;&lt;percent&gt; | Moves an element in 2D space. You can set the element to move along its x-axis or y-axis.              |
| translate3d<sup>6+</sup> | &lt;length&gt;&nbsp;\|&nbsp;&lt;percent&gt; | Moves an element in 3D space. There are three input parameters, indicating the translation distance of the x-axis, y-axis, and z-axis, respectively.                 |
| translateX               | &lt;length&gt;&nbsp;\|&nbsp;&lt;percent&gt; | Moves an element along the x-axis.                             |
| translateY               | &lt;length&gt;&nbsp;\|&nbsp;&lt;percent&gt; | Moves an element along the y-axis.                             |
| translateZ<sup>6+</sup>  | &lt;length&gt;&nbsp;\|&nbsp;&lt;percent&gt; | Moves an element along the z-axis.                                |
| scale                    | &lt;number&gt;                           | Resizes an element in 2D space. You can set the element to resize along its x-axis or y-axis.              |
| scale3d<sup>6+</sup>     | &lt;number&gt;                           | Resizes an element in 3D space. There are three input parameters, indicating the scale ratio of the x-axis, y-axis, and z-axis, respectively.                 |
| scaleX                   | &lt;number&gt;                           | Resizes an element along the x-axis.                             |
| scaleY                   | &lt;number&gt;                           | Resizes an element along the y-axis.                             |
| scaleZ<sup>6+</sup>      | &lt;number&gt;                           | Resizes an element along the z-axis.                                |
| rotate                   | &lt;deg&gt;&nbsp;\|&nbsp;&lt;rad&gt;&nbsp;\|&nbsp;&lt;grad&gt;<sup>6+</sup>&nbsp;\|&nbsp;&lt;turn&gt;<sup>6+</sup> | Rotates an animation. It supports setting rotation parameters in two dimensions: the x-axis and the y-axis.                              |
| rotate3d<sup>6+</sup>    | &lt;deg&gt;&nbsp;\|&nbsp;&lt;rad&gt;&nbsp;\|&nbsp;&lt;grad&gt;&nbsp;\|&nbsp;&lt;turn&gt; | Rotates an element in 3D space. There are four input parameters: The first three parameters are the rotation vectors of the x-axis, y-axis, and z-axis, and the fourth parameter is the rotation angle.      |
| rotateX                  | &lt;deg&gt;&nbsp;\|&nbsp;&lt;rad&gt;&nbsp;\|&nbsp;&lt;grad&gt;<sup>6+</sup>&nbsp;\|&nbsp;&lt;turn&gt;<sup>6+</sup> | Rotates an element around the x-axis.                             |
| rotateY                  | &lt;deg&gt;&nbsp;\|&nbsp;&lt;rad&gt;&nbsp;\|&nbsp;&lt;grad&gt;<sup>6+</sup>&nbsp;\|&nbsp;&lt;turn&gt;<sup>6+</sup> | Rotates an element around the y-axis.                             |
| rotateZ<sup>6+</sup>     | &lt;deg&gt;&nbsp;\|&nbsp;&lt;rad&gt;&nbsp;\|&nbsp;&lt;grad&gt;&nbsp;\|&nbsp;&lt;turn&gt; | Rotates an element around the z-axis.                              |
| skew<sup>6+</sup>        | &lt;deg&gt;&nbsp;\|&nbsp;&lt;rad&gt;&nbsp;\|&nbsp;&lt;grad&gt;&nbsp;\|&nbsp;&lt;turn&gt; | Skews an element in 2D space. There are two input parameters, indicating the 2D skew angle of the x-axis and y-axis, respectively.                   |
| skewX<sup>6+</sup>       | &lt;deg&gt;&nbsp;\|&nbsp;&lt;rad&gt;&nbsp;\|&nbsp;&lt;grad&gt;&nbsp;\|&nbsp;&lt;turn&gt; | Skews an element along the x-axis in 2D space.                              |
| skewY<sup>6+</sup>       | &lt;deg&gt;&nbsp;\|&nbsp;&lt;rad&gt;&nbsp;\|&nbsp;&lt;grad&gt;&nbsp;\|&nbsp;&lt;turn&gt; | Skews an element along the y-axis in 2D space.                              |
| perspective<sup>6+</sup> | &lt;number&gt;                           | Sets the distance from the lens to the element's surface in the 3D perspective scenario.                     |

**Table 2** @keyframes

| Name                              | Type                                      | Default Value         | Description                                      |
| -------------------------------- | ---------------------------------------- | ------------ | ---------------------------------------- |
| background-color                 | &lt;color&gt;                            | -            | Background color applied to the component after the animation is played.                       |
| opacity                          | number                                   | 1            | Opacity value applied to the component after the animation is played. The value ranges from **0** to **1**. The default value is **1**.      |
| width                            | &lt;length&gt;                           | -            | Width value applied to the component after the animation is played.                        |
| height                           | &lt;length&gt;                           | -            | Height value applied to the component after the animation is played.                        |
| transform                        | string                                   | -            | Transform type applied to the component. For details, see Table 1 transform.         |
| background-position<sup>6+</sup> | string&nbsp;\|&nbsp;&lt;percentage&gt;&nbsp;\|&nbsp;&lt;length&gt;&nbsp;string&nbsp;\|<br>&nbsp;&lt;percentage&gt;&nbsp;\|&nbsp;&lt;length&gt; | 50%&nbsp;50% | Position of the background image. The unit can be a percentage or px. The first value indicates the horizontal position, and the second value indicates the vertical position. If only one value is specified, the other one is **50%**. The available values for the first string are **left**, **center**, and **right**. The available values for the second string are **top**, **center**, and **bottom**.<br>Example:<br>-&nbsp;background-position:&nbsp;200px&nbsp;30%<br>-&nbsp;background-position:&nbsp;100px&nbsp;top<br>-&nbsp;background-position:&nbsp;center&nbsp;center |


If there is no default value for when an animation will start or end, you can explicitly specify the start and end using **from** and **to**. You can use a percentage value to specify an intermediate state of the animation<sup>6+</sup>. The following is an example:

```html
<!-- xxx.hml -->
<div class="container">
  <div class="rect">
  </div>
</div>
```

```css
/* xxx.css */
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 150px;
}
.rect{
  width: 200px;
  height: 200px;
  background-color: #f76160;
  animation: Go 3s infinite;
}
@keyframes Go
{
  from {
    background-color: #f76160;
    transform:translate(100px) rotate(0deg) scale(1.0);
  }
  /* Specify the intermediate state of the animation by a percentage value. */
  50% {    
  background-color: #f76160;    
  transform:translate(100px) rotate(60deg) scale(1.3);  
  }  
  to {
    background-color: #09ba07;
    transform:translate(100px) rotate(180deg) scale(2.0);
  }
}
```


![Animation-Styles02](figures/Animation-Styles02.gif)

```html
<!-- xxx.hml -->
<div class="container">
  <div class="simpleAnimation simpleSize" style="animation-play-state: {{playState}}"></div>
  <text onclick="toggleState">animation-play-state: {{playState}}</text>
</div>
```

```css
/* xxx.css */
.container {
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.simpleSize {
  background-color: blue;
  width: 100px;
  height: 100px;
}
.simpleAnimation {
  animation: simpleFrames 9s;
}
@keyframes simpleFrames {
  from { transform: translateX(0px); }
  to { transform: translateX(100px); }
}
```

```js
// xxx.js
export default {
  data: {
    title: "",
    playState: "running"
  },
  toggleState() {
    if (this.playState === "running") {
      this.playState = "paused";
    } else {
      this.playState = "running";
    }
  }
}
```


![animation-styles](figures/animation-styles.gif)

```html
<!-- xxx.hml -->
<div id='img' class="img"></div>
```

```css
/* xxx.css */
.img {
  width: 294px;
  height: 233px;
  background-image: url('common/heartBeat.jpg');
  background-repeat: no-repeat;
  background-position: 0% 0%;
  background-size: 900%;
  animation-name: heartBeating;
  animation-duration: 1s;
  animation-delay: 0s;
  animation-fill-mode: forwards;
  animation-iteration-count: -1;
  animation-timing-function: steps(8, end);
}

@keyframes heartBeating {
  from { background-position: 0% 0%;}
  to { background-position: 100% 0%;}
}
```

```html
<!-- xxx.hml -->
<div class="container">
  <div class="content"></div>
</div>
```

```css
/* xxx.css */
.container {
    flex-direction: column;
    justify-content: center;
    align-items: center;
}
.content { /* Component state 1 */
    height: 200px;
    width: 200px;
    background-color: red;
    transition: all 5s ease 0s;
}
.content:active { /* Component state 2 */
    height: 400px;
    width: 400px;
    background-color: blue;
    transition: all 5s linear 0s;
}
```


![animation-styles01](figures/animation-styles01.gif)


>  **NOTE**
>  The @keyframes rule with **from** and **to** defined cannot be dynamically bound to an element.
>
>  The following figure shows the meanings of **end** and **start** in the **steps** function.
>
>  ![steps](figures/steps.png)
