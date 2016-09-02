# 文字与字体 #
## 1、使用自定义字体@font-face ##
如果是英文网站，建议使用`@font-face`，如果是中文网站，建议使用图片代替特殊字体。因为英文的字体文件很小，而中文的字体文件太大。  
语法：
```css
/*定义*/
@font-face {
  font-family: <YourWebFontName>;
  src: <source> [<format>][,<source> [<format>]]*;
  [font-weight: <weight>];
  [font-style: <style>];
}
/*使用*/
div{ font-family: YourWebFontName;}
```
`source`可以使用相对路径或者绝对路径，一般会将字体文件单独放在`fonts`文件夹中；  
`format`是自定义字体的格式，主要用来帮助浏览器识别，其取值有truetype，opentype，truetype-aat，embedded-opentype，svg

兼容各浏览器的写法
```css
@font-face {
  font-family: 'YourWebFontName';
  src: url('YourWebFontName.eot?') format('eot');/*IE*/
  src: url('YourWebFontName.woff') format('woff'), url('YourWebFontName.ttf') format('truetype');/*non-IE*/
}
```
更多的兼容
```css
 @font-face {
  font-family: 'YourWebFontName';
  src: url('YourWebFontName.eot'); /* IE9 Compat Modes */
  src: url('YourWebFontName.eot?#iefix') format('embedded-opentype'), /* IE6-IE8 */
       url('YourWebFontName.woff') format('woff'), /* Modern Browsers */
       url('YourWebFontName.ttf')  format('truetype'), /* Safari, Android, iOS */
       url('YourWebFontName.svg#YourWebFontName') format('svg'); /* Legacy iOS */
   }
```

## 2、自定义被选中时样式 ##
```css
::selection{
  color: #9400D3;
  background-color: #a9a9a9;
}
/*兼容Firefox*/
::-moz-selection {
  color: #9400D3;
  background-color: #a9a9a9;
}
```

## 3、文字与字符的间距 ##
```css
p{
  word-spacing: 20px;/*单词之间的间隔，因为因为单词以空格间断，所以对于中文，体现于汉字之间空格的距离*/
  letter-spacing: 10px;/*单个字符之间的间隔，中文同样效果，无需空格*/
  line-height: 1.5;/*行间距，可能值为normal(默认)，inherit(继承)，数值(当前字体尺寸的倍数)，像素，百分比(当前字体尺寸)*/
  white-space: normal;/*默认值，忽略多个空格为一个，忽略回车符*/
  white-space: pre;/*保留多个空格*/
  white-space: nowrap;/*忽略回车符，禁止换行，直到遇到<br>*/
  white-space: pre-wrap;/*保留所有的空格与回车符*/
  white-space: pre-line;/*忽略多个空格为一个，保留回车*/
}
```

## 4、文本装饰--划线，粗体，斜体 ##
```css
p{
  text-decoration: overline;/*上划线*/
  text-decoration: line-through;/*穿过线*/
  text-decoration: underline;/*下划线*/
  text-decoration: none;/*无，常用于去除a标签的默认下划线*/
}
p{
  font-weight: bold;/*也可使用bolder，虽然<strong>也有字体加粗的显示效果，但<strong>有一种强调的语义在里面*/
  font-style: italic;/*斜体字*/
  font-style: oblique;/*倾斜的文字*/
}
```

## 5、文字阴影 ##
text-shadow是CSS3新增的内容，IE10+及所有现代浏览器都支持，[http://caniuse.com/#search=text-shadow](http://caniuse.com/#search=text-shadow)，IE9及以下hack请参考张鑫旭文章[http://www.zhangxinxu.com/wordpress/tag/text-shadow/](http://caniuse.com/#search=text-shadow)
```css
p{
  text-shadow: 5px 5px 5px #ccc;
  text-shadow: h-shadow v-shadow blur color;
  /*h-shadow为水平阴影的位置，必选，允许负值；v-shadow为垂直阴影位置，必选，允许负值；
  blur为模糊的距离，可选，非负值，越大越模糊；color为阴影的颜色，可选，默认为当前文字颜色
  可添加多个阴影效果，中间用逗号隔开*/
}
```

## 6、文本溢出处理 ##
```css
p{
  overflow: hidden;/*直接隐藏*/
}
p{
  overflow: scroll;/*显示滚动条，不管是否溢出*/
}
```
单行文字超出使用省略号，还可以使用自定义字符串(经测试Edge，Chrome，Firefox中仅Firefox支持)
```css
p{
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
  text-overflow: "---";/*自定义字符*/
}
```
单行文字超出裁切
```css
p{
  overflow: hidden;
  white-space: nowrap;
  text-overflow: clip;/*clip为默认值*/
}
```
多行文字超出使用省略号  
对于Chrome，Safari，Opera等现代浏览器以及iOS Safari，Android Browser，UC Browser for Android等大部分移动端浏览器可以使用`-webkit-line-clamp:N;`进行设置，N代表行数。
```css
p{
  display: -webkit-box;
  overflow: hidden;
  text-overflow: ellipsis;
  -webkit-line-clamp: 3;
  -webkit-box-orient: vertical;
}
```
兼容IE，Firefox，Chrome的方法
```html
<!-- html -->
<div class="overflow-wrapper" >
   <div class="overflow-content" >测试多行文本，文字超出使用省略号，后面的</div>
   <div class="overflow-dotted" >…</div>
</div>
```
```css
/*css*/
.overflow-wrapper{
  font-size: 16px;
  line-height: 18px;
  width: 64px;
  height: 54px;
  overflow: hidden;
  zoom: 1;
}
.overflow-content{
  float:left;
  height:54px;
}
.overflow-dotted{
  width: 18px;
  height: 18px;
  float: right;
  margin-top: -18px;
  background-color: #fff;
}
```
另外还可以使用jQuery.dotdotdot插件。PS:未验证兼容性。
