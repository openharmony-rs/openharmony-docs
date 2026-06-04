# 数据类型说明
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @seaside_wu1-->
<!--Designer: @shiyu_huang-->
<!--Tester: @TerryTsao-->
<!--Adviser: @Brilliantry_Rui-->

## 长度类型

| 名称         | 类型定义                       | 描述                                       |
| ---------- | -------------------------- | ---------------------------------------- |
| length     | string&nbsp;\|&nbsp;number | 用于描述尺寸单位，输入为number类型时，使用px单位；输入为string类型时，需要显式指定像素单位，当前支持的像素单位有：<br/>-&nbsp;px：逻辑尺寸单位。<br/>-&nbsp;fp<sup>6+</sup>：字体尺寸单位，会随系统字体大小设置发生变化，仅支持文本类组件设置相应的字体大小。 |
| percentage | string                     | 百分比尺寸单位，如“50%”。                          |


## 颜色类型

| 名称    | 类型定义                        | 描述                                       |
| ----- | --------------------------- | ---------------------------------------- |
| color | string&nbsp;\|&nbsp;颜色枚举字符串 | 用于描述颜色信息，JS脚本中不支持颜色枚举格式。<br/>字符串格式如下：<br/>-&nbsp;'rgb(255,&nbsp;255,&nbsp;255)'<br/>-&nbsp;'rgba(255,&nbsp;255,&nbsp;255,&nbsp;1.0)'<br/>-&nbsp;HEX格式：'\#rrggbb'、'\#aarrggbb'。<br/>-&nbsp;枚举格式：'black'、'white'。 |

**表1** 当前支持的颜色枚举

| 枚举名称                 | 对应颜色     | 颜色                                       |
| -------------------- | -------- | ---------------------------------------- |
| aliceblue            | \#f0f8ff | ![zh-cn_image_0000001173324803](figures/zh-cn_image_0000001173324803.png) |
| antiquewhite         | \#faebd7 | ![antiquewhite](figures/antiquewhite.png) |
| aqua                 | \#00ffff | ![zh-cn_image_0000001127285050](figures/zh-cn_image_0000001127285050.png) |
| aquamarine           | \#7fffd4 | ![zh-cn_image_0000001173324729](figures/zh-cn_image_0000001173324729.png) |
| azure                | \#f0ffff | ![azure](figures/azure.png) |
| beige                | \#f5f5dc | ![zh-cn_image_0000001173324773](figures/zh-cn_image_0000001173324773.png) |
| bisque               | \#ffe4c4 | ![zh-cn_image_0000001173164895](figures/zh-cn_image_0000001173164895.png) |
| black                | \#000000 | ![zh-cn_image_0000001173324735](figures/zh-cn_image_0000001173324735.png) |
| blanchedalmond       | \#ffebcd | ![zh-cn_image_0000001173164889](figures/zh-cn_image_0000001173164889.png) |
| blue                 | \#0000ff | ![zh-cn_image_0000001127125194](figures/zh-cn_image_0000001127125194.png) |
| blueviolet           | \#8a2be2 | ![blueviolet](figures/blueviolet.png) |
| brown                | \#a52a2a | ![zh-cn_image_0000001173324833](figures/zh-cn_image_0000001173324833.png) |
| burlywood            | \#deb887 | ![burlywood](figures/burlywood.png) |
| cadetblue            | \#5f9ea0 | ![zh-cn_image_0000001127125210](figures/zh-cn_image_0000001127125210.png) |
| chartreuse           | \#7fff00 | ![zh-cn_image_0000001173324811](figures/zh-cn_image_0000001173324811.png) |
| chocolate            | \#d2691e | ![chocolate](figures/chocolate.png) |
| coral                | \#ff7f50 | ![zh-cn_image_0000001173164877](figures/zh-cn_image_0000001173164877.png) |
| cornflowerblue       | \#6495ed | ![zh-cn_image_0000001173324781](figures/zh-cn_image_0000001173324781.png) |
| cornsilk             | \#fff8dc | ![cornsilk](figures/cornsilk.png) |
| crimson              | \#dc143c | ![zh-cn_image_0000001127285066](figures/zh-cn_image_0000001127285066.png) |
| cyan                 | \#00ffff | ![zh-cn_image_0000001173324789](figures/zh-cn_image_0000001173324789.png) |
| darkblue             | \#00008b | ![zh-cn_image_0000001173164841](figures/zh-cn_image_0000001173164841.png) |
| darkcyan             | \#008b8b | ![zh-cn_image_0000001173324745](figures/zh-cn_image_0000001173324745.png) |
| darkgoldenrod        | \#b8860b | ![zh-cn_image_0000001173324835](figures/zh-cn_image_0000001173324835.png) |
| darkgray             | \#a9a9a9 | ![darkgray](figures/darkgray.png) |
| darkgreen            | \#006400 | ![darkgreen](figures/darkgreen.png) |
| darkgrey             | \#a9a9a9 | ![zh-cn_image_0000001127125174](figures/zh-cn_image_0000001127125174.png) |
| darkkhaki            | \#bdb76b | ![zh-cn_image_0000001127285070](figures/zh-cn_image_0000001127285070.png) |
| darkmagenta          | \#8b008b | ![zh-cn_image_0000001173164875](figures/zh-cn_image_0000001173164875.png) |
| darkolivegreen       | \#556b2f | ![zh-cn_image_0000001173164835](figures/zh-cn_image_0000001173164835.png) |
| darkorange           | \#ff8c00 | ![zh-cn_image_0000001127125178](figures/zh-cn_image_0000001127125178.png) |
| darkorchid           | \#9932cc | ![zh-cn_image_0000001173324829](figures/zh-cn_image_0000001173324829.png) |
| darkred              | \#8b0000 | ![zh-cn_image_0000001173164851](figures/zh-cn_image_0000001173164851.png) |
| darksalmon           | \#e9967a | ![darksalmon](figures/darksalmon.png) |
| darkseagreen         | \#8fbc8f | ![zh-cn_image_0000001173324755](figures/zh-cn_image_0000001173324755.png) |
| darkslateblue        | \#483d8b | ![darkslateblue](figures/darkslateblue.png) |
| darkslategray        | \#2f4f4f | ![zh-cn_image_0000001127125190](figures/zh-cn_image_0000001127125190.png) |
| darkslategrey        | \#2f4f4f | ![zh-cn_image_0000001173324759](figures/zh-cn_image_0000001173324759.png) |
| darkturquoise        | \#00ced1 | ![darkturquoise](figures/darkturquoise.png) |
| darkviolet           | \#9400d3 | ![zh-cn_image_0000001127285058](figures/zh-cn_image_0000001127285058.png) |
| deeppink             | \#ff1493 | ![zh-cn_image_0000001173324767](figures/zh-cn_image_0000001173324767.png) |
| deepskyblue          | \#00bfff | ![zh-cn_image_0000001173164897](figures/zh-cn_image_0000001173164897.png) |
| dimgray              | \#696969 | ![dimgray](figures/dimgray.png) |
| dimgrey              | \#696969 | ![zh-cn_image_0000001173164911](figures/zh-cn_image_0000001173164911.png) |
| dodgerblue           | \#1e90ff | ![zh-cn_image_0000001173164855](figures/zh-cn_image_0000001173164855.png) |
| firebrick            | \#b22222 | ![firebrick](figures/firebrick.png) |
| floralwhite          | \#fffaf0 | ![zh-cn_image_0000001173324771](figures/zh-cn_image_0000001173324771.png) |
| forestgreen          | \#228b22 | ![zh-cn_image_0000001173324825](figures/zh-cn_image_0000001173324825.png) |
| fuchsia              | \#ff00ff | ![zh-cn_image_0000001127285052](figures/zh-cn_image_0000001127285052.png) |
| gainsboro            | \#dcdcdc | ![zh-cn_image_0000001173164901](figures/zh-cn_image_0000001173164901.png) |
| ghostwhite           | \#f8f8ff | ![ghostwhite](figures/ghostwhite.png) |
| gold                 | \#ffd700 | ![zh-cn_image_0000001173324761](figures/zh-cn_image_0000001173324761.png) |
| goldenrod            | \#daa520 | ![zh-cn_image_0000001173324817](figures/zh-cn_image_0000001173324817.png) |
| gray                 | \#808080 | ![gray](figures/gray.png) |
| green                | \#008000 | ![zh-cn_image_0000001173164865](figures/zh-cn_image_0000001173164865.png) |
| greenyellow          | \#adff2f | ![greenyellow](figures/greenyellow.png) |
| grey                 | \#808080 | ![zh-cn_image_0000001127285054](figures/zh-cn_image_0000001127285054.png) |
| honeydew             | \#f0fff0 | ![zh-cn_image_0000001173324813](figures/zh-cn_image_0000001173324813.png) |
| hotpink              | \#ff69b4 | ![hotpink](figures/hotpink.png) |
| indianred            | \#cd5c5c | ![zh-cn_image_0000001173164849](figures/zh-cn_image_0000001173164849.png) |
| indigo               | \#4b0082 | ![zh-cn_image_0000001173324821](figures/zh-cn_image_0000001173324821.png) |
| ivory                | \#fffff0 | ![zh-cn_image_0000001173164887](figures/zh-cn_image_0000001173164887.png) |
| khaki                | \#f0e68c | ![zh-cn_image_0000001173324801](figures/zh-cn_image_0000001173324801.png) |
| lavender             | \#e6e6fa | ![zh-cn_image_0000001127125188](figures/zh-cn_image_0000001127125188.png) |
| lavenderblush        | \#fff0f5 | ![zh-cn_image_0000001173324809](figures/zh-cn_image_0000001173324809.png) |
| lawngreen            | \#7cfc00 | ![zh-cn_image_0000001127125224](figures/zh-cn_image_0000001127125224.png) |
| lemonchiffon         | \#fffacd | ![zh-cn_image_0000001173164879](figures/zh-cn_image_0000001173164879.png) |
| lightblue            | \#add8e6 | ![zh-cn_image_0000001127125180](figures/zh-cn_image_0000001127125180.png) |
| lightcoral           | \#f08080 | ![zh-cn_image_0000001127125228](figures/zh-cn_image_0000001127125228.png) |
| lightcyan            | \#e0ffff | ![zh-cn_image_0000001173324799](figures/zh-cn_image_0000001173324799.png) |
| lightgoldenrodyellow | \#fafad2 | ![zh-cn_image_0000001127125218](figures/zh-cn_image_0000001127125218.png) |
| lightgray            | \#d3d3d3 | ![lightgray](figures/lightgray.png) |
| lightgreen           | \#90ee90 | ![zh-cn_image_0000001173324805](figures/zh-cn_image_0000001173324805.png) |
| lightpink            | \#ffb6c1 | ![lightpink](figures/lightpink.png) |
| lightsalmon          | \#ffa07a | ![zh-cn_image_0000001173324795](figures/zh-cn_image_0000001173324795.png) |
| lightseagreen        | \#20b2aa | ![zh-cn_image_0000001173324737](figures/zh-cn_image_0000001173324737.png) |
| lightskyblue         | \#87cefa | ![lightskyblue](figures/lightskyblue.png) |
| lightslategray       | \#778899 | ![zh-cn_image_0000001127125226](figures/zh-cn_image_0000001127125226.png) |
| lightslategrey       | \#778899 | ![zh-cn_image_0000001127125222](figures/zh-cn_image_0000001127125222.png) |
| lightsteelblue       | \#b0c4de | ![lightsteelblue](figures/lightsteelblue.png) |
| lightyellow          | \#ffffe0 | ![zh-cn_image_0000001173324807](figures/zh-cn_image_0000001173324807.png) |
| lime                 | \#00ff00 | ![lime](figures/lime.png) |
| limegreen            | \#32cd32 | ![limegreen](figures/limegreen.png) |
| linen                | \#faf0e6 | ![zh-cn_image_0000001173324739](figures/zh-cn_image_0000001173324739.png) |
| magenta              | \#ff00ff | ![magenta](figures/magenta.png) |
| maroon               | \#800000 | ![maroon](figures/maroon.png) |
| mediumaquamarine     | \#66cdaa | ![zh-cn_image_0000001173164899](figures/zh-cn_image_0000001173164899.png) |
| mediumblue           | \#0000cd | ![mediumblue](figures/mediumblue.png) |
| mediumorchid         | \#ba55d3 | ![zh-cn_image_0000001127125216](figures/zh-cn_image_0000001127125216.png) |
| mediumpurple         | \#9370db | ![zh-cn_image_0000001173324779](figures/zh-cn_image_0000001173324779.png) |
| mediumseagreen       | \#3cb371 | ![zh-cn_image_0000001127125230](figures/zh-cn_image_0000001127125230.png) |
| mediumslateblue      | \#7b68ee | ![zh-cn_image_0000001173164921](figures/zh-cn_image_0000001173164921.png) |
| mediumspringgreen    | \#00fa9a | ![zh-cn_image_0000001173324793](figures/zh-cn_image_0000001173324793.png) |
| mediumturquoise      | \#48d1cc | ![zh-cn_image_0000001127125214](figures/zh-cn_image_0000001127125214.png) |
| mediumvioletred      | \#c71585 | ![zh-cn_image_0000001173164893](figures/zh-cn_image_0000001173164893.png) |
| midnightblue         | \#191970 | ![midnightblue](figures/midnightblue.png) |
| mintcream            | \#f5fffa | ![mintcream](figures/mintcream.png) |
| mistyrose            | \#ffe4e1 | ![zh-cn_image_0000001173324785](figures/zh-cn_image_0000001173324785.png) |
| moccasin             | \#ffe4b5 | ![moccasin](figures/moccasin.png) |
| navajowhite          | \#ffdead | ![zh-cn_image_0000001173164925](figures/zh-cn_image_0000001173164925.png) |
| navy                 | \#000080 | ![navy](figures/navy.png) |
| oldlace              | \#fdf5e6 | ![zh-cn_image_0000001127125184](figures/zh-cn_image_0000001127125184.png) |
| olive                | \#808000 | ![olive](figures/olive.png) |
| olivedrab            | \#6b8e23 | ![zh-cn_image_0000001173324839](figures/zh-cn_image_0000001173324839.png) |
| orange               | \#ffa500 | ![zh-cn_image_0000001173164885](figures/zh-cn_image_0000001173164885.png) |
| orangered            | \#ff4500 | ![orangered](figures/orangered.png) |
| orchid               | \#da70d6 | ![zh-cn_image_0000001127285056](figures/zh-cn_image_0000001127285056.png) |
| palegoldenrod        | \#eee8aa | ![palegoldenrod](figures/palegoldenrod.png) |
| palegreen            | \#98fb98 | ![palegreen](figures/palegreen.png) |
| paleturquoise        | \#afeeee | ![zh-cn_image_0000001173324757](figures/zh-cn_image_0000001173324757.png) |
| palevioletred        | \#db7093 | ![zh-cn_image_0000001173164905](figures/zh-cn_image_0000001173164905.png) |
| papayawhip           | \#ffefd5 | ![papayawhip](figures/papayawhip.png) |
| peachpuff            | \#ffdab9 | ![zh-cn_image_0000001173324769](figures/zh-cn_image_0000001173324769.png) |
| peru                 | \#cd853f | ![zh-cn_image_0000001173164843](figures/zh-cn_image_0000001173164843.png) |
| pink                 | \#ffc0cb | ![pink](figures/pink.png) |
| plum                 | \#dda0dd | ![zh-cn_image_0000001173324831](figures/zh-cn_image_0000001173324831.png) |
| powderblue           | \#b0e0e6 | ![powderblue](figures/powderblue.png) |
| purple               | \#800080 | ![purple](figures/purple.png) |
| rebeccapurple        | \#663399 | ![zh-cn_image_0000001173164907](figures/zh-cn_image_0000001173164907.png) |
| red                  | \#ff0000 | ![red](figures/red.png) |
| rosybrown            | \#bc8f8f | ![zh-cn_image_0000001173324775](figures/zh-cn_image_0000001173324775.png) |
| royalblue            | \#4169e1 | ![royalblue](figures/royalblue.png) |
| saddlebrown          | \#8b4513 | ![saddlebrown](figures/saddlebrown.png) |
| salmon               | \#fa8072 | ![zh-cn_image_0000001127285064](figures/zh-cn_image_0000001127285064.png) |
| sandybrown           | \#f4a460 | ![zh-cn_image_0000001173324777](figures/zh-cn_image_0000001173324777.png) |
| seagreen             | \#2e8b57 | ![zh-cn_image_0000001173324733](figures/zh-cn_image_0000001173324733.png) |
| seashell             | \#fff5ee | ![zh-cn_image_0000001127285062](figures/zh-cn_image_0000001127285062.png) |
| sienna               | \#a0522d | ![zh-cn_image_0000001173164917](figures/zh-cn_image_0000001173164917.png) |
| silver               | \#c0c0c0 | ![zh-cn_image_0000001173324743](figures/zh-cn_image_0000001173324743.png) |
| skyblue              | \#87ceeb | ![skyblue](figures/skyblue.png) |
| slateblue            | \#6a5acd | ![zh-cn_image_0000001173164915](figures/zh-cn_image_0000001173164915.png) |
| slategray            | \#708090 | ![zh-cn_image_0000001173324815](figures/zh-cn_image_0000001173324815.png) |
| slategrey            | \#708090 | ![slategrey](figures/slategrey.png) |
| snow                 | \#fffafa | ![zh-cn_image_0000001173324731](figures/zh-cn_image_0000001173324731.png) |
| springgreen          | \#00ff7f | ![zh-cn_image_0000001127285060](figures/zh-cn_image_0000001127285060.png) |
| steelblue            | \#4682b4 | ![steelblue](figures/steelblue.png) |
| tan                  | \#d2b48c | ![zh-cn_image_0000001173324747](figures/zh-cn_image_0000001173324747.png) |
| teal                 | \#008080 | ![zh-cn_image_0000001173324741](figures/zh-cn_image_0000001173324741.png) |
| thistle              | \#d8bfd8 | ![zh-cn_image_0000001173164913](figures/zh-cn_image_0000001173164913.png) |
| tomato               | \#ff6347 | ![zh-cn_image_0000001173164909](figures/zh-cn_image_0000001173164909.png) |
| turquoise            | \#40e0d0 | ![zh-cn_image_0000001173164837](figures/zh-cn_image_0000001173164837.png) |
| violet               | \#ee82ee | ![violet](figures/violet.png) |
| wheat                | \#f5deb3 | ![zh-cn_image_0000001127285068](figures/zh-cn_image_0000001127285068.png) |
| white                | \#ffffff | ![zh-cn_image_0000001173324823](figures/zh-cn_image_0000001173324823.png) |
| whitesmoke           | \#f5f5f5 | ![whitesmoke](figures/whitesmoke.png) |
| yellow               | \#ffff00 | ![zh-cn_image_0000001173324837](figures/zh-cn_image_0000001173324837.png) |
| yellowgreen          | \#9acd32 | ![zh-cn_image_0000001173164923](figures/zh-cn_image_0000001173164923.png) |
