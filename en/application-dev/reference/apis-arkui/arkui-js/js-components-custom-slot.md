# slot
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @seaside_wu1-->
<!--Designer: @shiyu_huang-->
<!--Tester: @TerryTsao-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=214e29279f37b00be7bd8f1096b2e4dc3af96177 translatedAt=2026-11-12T04:40:43.372Z pushedAt=2026-11-18T04:04:03.684Z nl=1 -->

>  **NOTE**
>
>  This component is supported since API version 7. Updates will be marked with a superscript to indicate their earliest API version.


## Default Slot

You can use the **\<slot>** tag in a custom component to carry the content defined in the parent component. Using the **\<slot>** tag allows more flexible control over the content elements of a custom component. The usage is as follows:

```html
<!-- comp.hml -->
<div class="item">  
   <text class="text-style">The following uses the content defined in the parent component.</text> 
   <slot></slot> 
</div>
```

The following references the custom component:
```html
<!-- xxx.hml --> 
 <element name='comp' src='../common/component/comp.hml'></element>  
 <div class="container">  
   <comp>
     <text class="text-style">Content defined in the parent component</text> 
   </comp>  
 </div>
```


## Named Slot

When multiple slots are needed inside a custom component, you can name them, so that you can specify the slot in which you want to fill content by setting the **\<name>** attribute.

```html
<!-- comp.hml -->
<div class="item">  
   <text class="text-style">The following uses the content defined in the parent component.</text> 
   <slot name="first"></slot>
   <slot name="second"></slot> 
</div>
```

The following references the custom component:
```html
<!-- xxx.hml --> 
 <element name='comp' src='../common/component/comp.hml'></element>  
 <div class="container">  
   <comp>
     <text class="text-style" slot="second">Fill in the second slot.</text> 
     <text class="text-style" slot="first">Fill in the first slot.</text>
   </comp>  
 </div>
```

>  **NOTE**
>
>  **\<name>** and **\<slot>** do not support dynamic data binding.
