# 图片 #
## 1、“拍立得”效果 ##
![效果](https://github.com/yuzhantian/css-library/raw/master/library-imgs/polaroid.png)
```css
/*单独图片*/
img.polaroid{width: 200px; height: 200px; box-shadow: 1px 1px 5px #333; border: solid #fff; border-width: 5px 5px 20px;}
/*图片下方有文字*/
div.polaroid{width: 200px; text-align: center; padding: 10px; border: 1px solid #ccc; line-height: 1.5; box-shadow: 1px 1px 5px #333;}
```
## 2、黑白图片 ##
浏览器支持：Chrome，Safari，Opera，Edge，Firefox，IE6~9  
![效果](https://github.com/yuzhantian/css-library/raw/master/library-imgs/img-gray.png)
```css
.gray{
  -webkit-filter: grayscale(100%);/* Chrome,Safari,Opera */
  filter: grayscale(100%); /* Edge,Firefox */
  filter: gray;/* IE6~9 */
}
```
## 3、固定列瀑布流 ##
![效果](https://github.com/yuzhantian/css-library/raw/master/library-imgs/img-waterfall.png)