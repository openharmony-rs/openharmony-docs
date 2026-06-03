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
| aliceblue            | \#f0f8ff | ![aliceblue](figures/aliceblue.png) |
| antiquewhite         | \#faebd7 | ![zh-cn_image_0000001127285014](figures/zh-cn_image_0000001127285014.png) |
| aqua                 | \#00ffff | ![aqua](figures/aqua.png) |
| aquamarine           | \#7fffd4 | ![aquamarine](figures/aquamarine.png) |
| azure                | \#f0ffff | ![zh-cn_image_0000001127285040](figures/zh-cn_image_0000001127285040.png) |
| beige                | \#f5f5dc | ![beige](figures/beige.png) |
| bisque               | \#ffe4c4 | ![bisque](figures/bisque.png) |
| black                | \#000000 | ![black](figures/black.png) |
| blanchedalmond       | \#ffebcd | ![blanchedalmond](figures/blanchedalmond.png) |
| blue                 | \#0000ff | ![zh-cn_image_0000001127125194](figures/zh-cn_image_0000001127125194.png) |
| blueviolet           | \#8a2be2 | ![zh-cn_image_0000001127285046](figures/zh-cn_image_0000001127285046.png) |
| brown                | \#a52a2a | ![brown](figures/brown.png) |
| burlywood            | \#deb887 | ![zh-cn_image_0000001127285026](figures/zh-cn_image_0000001127285026.png) |
| cadetblue            | \#5f9ea0 | ![zh-cn_image_0000001127125210](figures/zh-cn_image_0000001127125210.png) |
| chartreuse           | \#7fff00 | ![chartreuse](figures/chartreuse.png) |
| chocolate            | \#d2691e | ![zh-cn_image_0000001127125256](figures/zh-cn_image_0000001127125256.png) |
| coral                | \#ff7f50 | ![coral](figures/coral.png) |
| cornflowerblue       | \#6495ed | ![cornflowerblue](figures/cornflowerblue.png) |
| cornsilk             | \#fff8dc | ![zh-cn_image_0000001127285048](figures/zh-cn_image_0000001127285048.png) |
| crimson              | \#dc143c | ![crimson](figures/crimson.png) |
| cyan                 | \#00ffff | ![cyan](figures/cyan.png) |
| darkblue             | \#00008b | ![darkblue](figures/darkblue.png) |
| darkcyan             | \#008b8b | ![darkcyan](figures/darkcyan.png) |
| darkgoldenrod        | \#b8860b | ![darkgoldenrod](figures/darkgoldenrod.png) |
| darkgray             | \#a9a9a9 | ![zh-cn_image_0000001127285028](figures/zh-cn_image_0000001127285028.png) |
| darkgreen            | \#006400 | ![zh-cn_image_0000001127284990](figures/zh-cn_image_0000001127284990.png) |
| darkgrey             | \#a9a9a9 | ![zh-cn_image_0000001127125174](figures/zh-cn_image_0000001127125174.png) |
| darkkhaki            | \#bdb76b | ![darkkhaki](figures/darkkhaki.png) |
| darkmagenta          | \#8b008b | ![darkmagenta](figures/darkmagenta.png) |
| darkolivegreen       | \#556b2f | ![darkolivegreen](figures/darkolivegreen.png) |
| darkorange           | \#ff8c00 | ![zh-cn_image_0000001127125178](figures/zh-cn_image_0000001127125178.png) |
| darkorchid           | \#9932cc | ![darkorchid](figures/darkorchid.png) |
| darkred              | \#8b0000 | ![darkred](figures/darkred.png) |
| darksalmon           | \#e9967a | ![zh-cn_image_0000001127284998](figures/zh-cn_image_0000001127284998.png) |
| darkseagreen         | \#8fbc8f | ![darkseagreen](figures/darkseagreen.png) |
| darkslateblue        | \#483d8b | ![zh-cn_image_0000001127125246](figures/zh-cn_image_0000001127125246.png) |
| darkslategray        | \#2f4f4f | ![zh-cn_image_0000001127125190](figures/zh-cn_image_0000001127125190.png) |
| darkslategrey        | \#2f4f4f | ![darkslategrey](figures/darkslategrey.png) |
| darkturquoise        | \#00ced1 | ![zh-cn_image_0000001127284980](figures/zh-cn_image_0000001127284980.png) |
| darkviolet           | \#9400d3 | ![darkviolet](figures/darkviolet.png) |
| deeppink             | \#ff1493 | ![deeppink](figures/deeppink.png) |
| deepskyblue          | \#00bfff | ![deepskyblue](figures/deepskyblue.png) |
| dimgray              | \#696969 | ![zh-cn_image_0000001127285022](figures/zh-cn_image_0000001127285022.png) |
| dimgrey              | \#696969 | ![dimgrey](figures/dimgrey.png) |
| dodgerblue           | \#1e90ff | ![dodgerblue](figures/dodgerblue.png) |
| firebrick            | \#b22222 | ![zh-cn_image_0000001127125234](figures/zh-cn_image_0000001127125234.png) |
| floralwhite          | \#fffaf0 | ![floralwhite](figures/floralwhite.png) |
| forestgreen          | \#228b22 | ![forestgreen](figures/forestgreen.png) |
| fuchsia              | \#ff00ff | ![fuchsia](figures/fuchsia.png) |
| gainsboro            | \#dcdcdc | ![gainsboro](figures/gainsboro.png) |
| ghostwhite           | \#f8f8ff | ![zh-cn_image_0000001127285012](figures/zh-cn_image_0000001127285012.png) |
| gold                 | \#ffd700 | ![gold](figures/gold.png) |
| goldenrod            | \#daa520 | ![goldenrod](figures/goldenrod.png) |
| gray                 | \#808080 | ![zh-cn_image_0000001127125238](figures/zh-cn_image_0000001127125238.png) |
| green                | \#008000 | ![green](figures/green.png) |
| greenyellow          | \#adff2f | ![zh-cn_image_0000001127285000](figures/zh-cn_image_0000001127285000.png) |
| grey                 | \#808080 | ![grey](figures/grey.png) |
| honeydew             | \#f0fff0 | ![honeydew](figures/honeydew.png) |
| hotpink              | \#ff69b4 | ![zh-cn_image_0000001127285016](figures/zh-cn_image_0000001127285016.png) |
| indianred            | \#cd5c5c | ![indianred](figures/indianred.png) |
| indigo               | \#4b0082 | ![indigo](figures/indigo.png) |
| ivory                | \#fffff0 | ![ivory](figures/ivory.png) |
| khaki                | \#f0e68c | ![khaki](figures/khaki.png) |
| lavender             | \#e6e6fa | ![zh-cn_image_0000001127125188](figures/zh-cn_image_0000001127125188.png) |
| lavenderblush        | \#fff0f5 | ![lavenderblush](figures/lavenderblush.png) |
| lawngreen            | \#7cfc00 | ![zh-cn_image_0000001127125224](figures/zh-cn_image_0000001127125224.png) |
| lemonchiffon         | \#fffacd | ![lemonchiffon](figures/lemonchiffon.png) |
| lightblue            | \#add8e6 | ![zh-cn_image_0000001127125180](figures/zh-cn_image_0000001127125180.png) |
| lightcoral           | \#f08080 | ![zh-cn_image_0000001127125228](figures/zh-cn_image_0000001127125228.png) |
| lightcyan            | \#e0ffff | ![lightcyan](figures/lightcyan.png) |
| lightgoldenrodyellow | \#fafad2 | ![zh-cn_image_0000001127125218](figures/zh-cn_image_0000001127125218.png) |
| lightgray            | \#d3d3d3 | ![zh-cn_image_0000001127284974](figures/zh-cn_image_0000001127284974.png) |
| lightgreen           | \#90ee90 | ![lightgreen](figures/lightgreen.png) |
| lightpink            | \#ffb6c1 | ![zh-cn_image_0000001127285038](figures/zh-cn_image_0000001127285038.png) |
| lightsalmon          | \#ffa07a | ![lightsalmon](figures/lightsalmon.png) |
| lightseagreen        | \#20b2aa | ![lightseagreen](figures/lightseagreen.png) |
| lightskyblue         | \#87cefa | ![zh-cn_image_0000001127285042](figures/zh-cn_image_0000001127285042.png) |
| lightslategray       | \#778899 | ![zh-cn_image_0000001127125226](figures/zh-cn_image_0000001127125226.png) |
| lightslategrey       | \#778899 | ![zh-cn_image_0000001127125222](figures/zh-cn_image_0000001127125222.png) |
| lightsteelblue       | \#b0c4de | ![zh-cn_image_0000001127284976](figures/zh-cn_image_0000001127284976.png) |
| lightyellow          | \#ffffe0 | ![lightyellow](figures/lightyellow.png) |
| lime                 | \#00ff00 | ![zh-cn_image_0000001127285020](figures/zh-cn_image_0000001127285020.png) |
| limegreen            | \#32cd32 | ![zh-cn_image_0000001127125236](figures/zh-cn_image_0000001127125236.png) |
| linen                | \#faf0e6 | ![linen](figures/linen.png) |
| magenta              | \#ff00ff | ![zh-cn_image_0000001127285044](figures/zh-cn_image_0000001127285044.png) |
| maroon               | \#800000 | ![zh-cn_image_0000001127285018](figures/zh-cn_image_0000001127285018.png) |
| mediumaquamarine     | \#66cdaa | ![mediumaquamarine](figures/mediumaquamarine.png) |
| mediumblue           | \#0000cd | ![zh-cn_image_0000001127284968](figures/zh-cn_image_0000001127284968.png) |
| mediumorchid         | \#ba55d3 | ![zh-cn_image_0000001127125216](figures/zh-cn_image_0000001127125216.png) |
| mediumpurple         | \#9370db | ![mediumpurple](figures/mediumpurple.png) |
| mediumseagreen       | \#3cb371 | ![zh-cn_image_0000001127125230](figures/zh-cn_image_0000001127125230.png) |
| mediumslateblue      | \#7b68ee | ![mediumslateblue](figures/mediumslateblue.png) |
| mediumspringgreen    | \#00fa9a | ![mediumspringgreen](figures/mediumspringgreen.png) |
| mediumturquoise      | \#48d1cc | ![zh-cn_image_0000001127125214](figures/zh-cn_image_0000001127125214.png) |
| mediumvioletred      | \#c71585 | ![mediumvioletred](figures/mediumvioletred.png) |
| midnightblue         | \#191970 | ![zh-cn_image_0000001127125260](figures/zh-cn_image_0000001127125260.png) |
| mintcream            | \#f5fffa | ![zh-cn_image_0000001127285030](figures/zh-cn_image_0000001127285030.png) |
| mistyrose            | \#ffe4e1 | ![mistyrose](figures/mistyrose.png) |
| moccasin             | \#ffe4b5 | ![zh-cn_image_0000001127125232](figures/zh-cn_image_0000001127125232.png) |
| navajowhite          | \#ffdead | ![navajowhite](figures/navajowhite.png) |
| navy                 | \#000080 | ![zh-cn_image_0000001127285032](figures/zh-cn_image_0000001127285032.png) |
| oldlace              | \#fdf5e6 | ![zh-cn_image_0000001127125184](figures/zh-cn_image_0000001127125184.png) |
| olive                | \#808000 | ![zh-cn_image_0000001127125244](figures/zh-cn_image_0000001127125244.png) |
| olivedrab            | \#6b8e23 | ![olivedrab](figures/olivedrab.png) |
| orange               | \#ffa500 | ![orange](figures/orange.png) |
| orangered            | \#ff4500 | ![zh-cn_image_0000001127284996](figures/zh-cn_image_0000001127284996.png) |
| orchid               | \#da70d6 | ![orchid](figures/orchid.png) |
| palegoldenrod        | \#eee8aa | ![zh-cn_image_0000001127125262](figures/zh-cn_image_0000001127125262.png) |
| palegreen            | \#98fb98 | ![zh-cn_image_0000001127285006](figures/zh-cn_image_0000001127285006.png) |
| paleturquoise        | \#afeeee | ![paleturquoise](figures/paleturquoise.png) |
| palevioletred        | \#db7093 | ![palevioletred](figures/palevioletred.png) |
| papayawhip           | \#ffefd5 | ![zh-cn_image_0000001127125248](figures/zh-cn_image_0000001127125248.png) |
| peachpuff            | \#ffdab9 | ![peachpuff](figures/peachpuff.png) |
| peru                 | \#cd853f | ![peru](figures/peru.png) |
| pink                 | \#ffc0cb | ![zh-cn_image_0000001127125242](figures/zh-cn_image_0000001127125242.png) |
| plum                 | \#dda0dd | ![plum](figures/plum.png) |
| powderblue           | \#b0e0e6 | ![zh-cn_image_0000001127285010](figures/zh-cn_image_0000001127285010.png) |
| purple               | \#800080 | ![zh-cn_image_0000001127285002](figures/zh-cn_image_0000001127285002.png) |
| rebeccapurple        | \#663399 | ![rebeccapurple](figures/rebeccapurple.png) |
| red                  | \#ff0000 | ![zh-cn_image_0000001127125254](figures/zh-cn_image_0000001127125254.png) |
| rosybrown            | \#bc8f8f | ![rosybrown](figures/rosybrown.png) |
| royalblue            | \#4169e1 | ![zh-cn_image_0000001127284972](figures/zh-cn_image_0000001127284972.png) |
| saddlebrown          | \#8b4513 | ![zh-cn_image_0000001127125250](figures/zh-cn_image_0000001127125250.png) |
| salmon               | \#fa8072 | ![salmon](figures/salmon.png) |
| sandybrown           | \#f4a460 | ![sandybrown](figures/sandybrown.png) |
| seagreen             | \#2e8b57 | ![seagreen](figures/seagreen.png) |
| seashell             | \#fff5ee | ![seashell](figures/seashell.png) |
| sienna               | \#a0522d | ![sienna](figures/sienna.png) |
| silver               | \#c0c0c0 | ![silver](figures/silver.png) |
| skyblue              | \#87ceeb | ![zh-cn_image_0000001127284970](figures/zh-cn_image_0000001127284970.png) |
| slateblue            | \#6a5acd | ![slateblue](figures/slateblue.png) |
| slategray            | \#708090 | ![slategray](figures/slategray.png) |
| slategrey            | \#708090 | ![zh-cn_image_0000001127284982](figures/zh-cn_image_0000001127284982.png) |
| snow                 | \#fffafa | ![snow](figures/snow.png) |
| springgreen          | \#00ff7f | ![springgreen](figures/springgreen.png) |
| steelblue            | \#4682b4 | ![zh-cn_image_0000001127125240](figures/zh-cn_image_0000001127125240.png) |
| tan                  | \#d2b48c | ![tan](figures/tan.png) |
| teal                 | \#008080 | ![teal](figures/teal.png) |
| thistle              | \#d8bfd8 | ![thistle](figures/thistle.png) |
| tomato               | \#ff6347 | ![tomato](figures/tomato.png) |
| turquoise            | \#40e0d0 | ![turquoise](figures/turquoise.png) |
| violet               | \#ee82ee | ![zh-cn_image_0000001127125258](figures/zh-cn_image_0000001127125258.png) |
| wheat                | \#f5deb3 | ![wheat](figures/wheat.png) |
| white                | \#ffffff | ![white](figures/white.png) |
| whitesmoke           | \#f5f5f5 | ![zh-cn_image_0000001127284992](figures/zh-cn_image_0000001127284992.png) |
| yellow               | \#ffff00 | ![yellow](figures/yellow.png) |
| yellowgreen          | \#9acd32 | ![yellowgreen](figures/yellowgreen.png) |
