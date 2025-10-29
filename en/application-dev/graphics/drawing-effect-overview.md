# Overview of Drawing Effects

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @hangmengxin-->
<!--Designer: @wangyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->

After a canvas is created, it has a default fill effect and stroke effect. You can directly draw graphical elements. However, the default effects cannot meet the requirements in most cases. For example, the default color is black, and only black shapes can be drawn. No blur or gradient effect is available by default. If more drawing effects are required, for example, drawing a red shape, adding a blur effect, or gradient effect, you need to set a custom brush or pen for the canvas.


A brush is used to implement the fill effect, which is applicable to the internal area of a shape. The basic effects include the fill color and anti-aliasing.


A pen is used to implement the stroke effect, which is applicable to the outline of a shape. The basic effects include the stroke color, width, line connection mode, and line endpoint style.


In addition, brushes and pens can implement more complex effects, such as:


- Blend mode.

- Path effect (dashed line effect)

- Shader effect (linear gradient and radial gradient)

- Filtering effect (blur effect)


You can select either a brush or a pen as required, or set both or neither. If neither is set, the default black brush is used.
