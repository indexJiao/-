### 1  路由后退一步

```js
this.$router.go(-1)
```

### 2  路由跳转

```js
this.$router.push({
    path: 'addArticle',
    query:{
    	status: 'create'
    }
})
```

### 3  获取路由跳转传参

```js
let id = this.$route.query.status
```

### 4  路由跳转，文件加载阻塞

```js
<link rel="icon" href="data:;base64,=">
```

### 5  媒体查询

```css
/* iPhone X XS */
@media only screen and (device-width: 375px) and (device-height: 812px) and (-webkit-device-pixel-ratio: 3) {

}

/* iPhone XR */
@media only screen and (device-width: 414px) and (device-height: 896px) and (-webkit-device-pixel-ratio: 2) {

}

/* iPhone XS Max */
@media only screen and (device-width: 414px) and (device-height: 896px) and (-webkit-device-pixel-ratio: 3) {

}
```

### 6 去掉获取焦点的样式

```css
input {
    -webkit-appearance: none;
    -webkit-tap-highlight-color: rgba(255, 255, 255, 0); 
    outline: none;/*去掉鼠标点击的默认黄色边框*/
}

*:focus {
    outline: none;
}
```

### 7  页面初始化输入框获取焦点

```js
<input type="text" autofocus="autofocus">
```

同时需要设置页面不能放大，在html里面设置

```html
<meta content="width=device-width,initial-scale=1.0,maximum-scale=1.0,user-scalable=no" name="viewport" />
```

### 8  ios软键盘回弹，输入框的点击事件不返回位置

具体百度

### 9  动态样式 :class

```html
<!-- 第一种方式:对象的形式 -->
<!-- 第一个参数 类名， 第二个参数：boolean值 -->
<!-- 对象的形式: 用花括号包裹起来，类名用引号， -->
<!-- 优点: 以对象的形式可以写多个，用逗号分开 -->
<p :class="{'sm' : true}">对象的形式</p>
<p :class="{'sm' : false, 'lg': true}">对象的形式</p>

<!-- 第二种方式:三元表达式 注意点：放在数组中，类名要用引号-->
<p :class="[ controller.summary? 'sm' : 'lg' ]" >三元表示式</p>

<!-- 第三种方式: 数组的形式 -->
<p :class="[isTrue, isFalse]">数组的形式</p>

<!-- 数组中用对象 -->
<p :class="[{'sm': false}, isFalse]">数组中使用对象</p>
 
<!--补充:  class中还可以传方法，在方法中返回类名-->
<p :class="setClass">通过方法设置class类名</p>
```

### 10  动态样式 :style

```vue
<div class="controller" :style="{paddingTop:controller.summary?'20px':'10px'}">
```

### 11  单位 rem  vh  vw  vmax  ex  ch

**rem**

rem中的"r"代表"root"；这等同于font-size基于根元素进行设置；在大多数情况下根元素为html元素。

```css
html {
	font-size: 14px;
}

div {
	font-size: 1.2rem;
}
```

**vh 和 vw**

vh等于viewport高度的1/100.例如，如果浏览器的高是900px,1vh求得的值为9px。同理，如果显示窗口宽度为750px,1vw求得的值为7.5px

**vmin 和 vmax**

vmin和vmax是与宽度和高度的最大值或最小值有关，取决于哪个更大和更小。

例如，如果浏览器设置为1100px宽、700px高，1vmin会是7px,1vmax为11px。然而，如果宽度设置为800px，高度设置为1080px，1vmin将会等于8px而1vmax将会是10.8px。

**ex 和 ch**

以上详见 

[https://www.w3cplus.com/css/7-css-units-you-might-not-know-about.html]: 

### 12  隐藏滚动条

```css
.xs-ul::-webkit-scrollbar { display: none; }
```

### 13 js获取上传视频的时长、大小、后缀名

```js
var value = document.getElementById("upload-video");
var video_file = e.target.files[0];
if (!video_file) return;

// 获取文件路径并限制上传文件的格式
var fileName = $("#sectionfileUpload").val(); //C:\fakepath\3.jpeg
var exts = fileName.split('.');
var ext = "";
if (exts != undefined) {
    if (exts.length <= 1 && fileName.indexOf('=')>-1) {//直接输入上传到azure之后生成的文件地址
        console.log(exts.length);
    } else {
        ext = exts[exts.length - 1];
        ext = ext.toLowerCase();
        if (ext != 'ppt' && ext != 'pptx' && ext != 'doc' && ext != 'docx' && ext != 'xls' 
            && ext != 'xlsx' && ext != 'pdf' && ext != 'mp4') {
            toaster.pop('error', "上传失败，文件格式限制为office文件、pdf、mp4视频文件");
            return;
        }                    
    }
}

//获取视频或者音频时长
var fileurl = URL.createObjectURL(video_file);
//经测试，发现audio也可获取视频的时长
var audioElement = new Audio(fileurl);
var duration;
audioElement.addEventListener("loadedmetadata", function (_event) {
    duration = audioElement.duration;
    console.log( "duration");
    console.log(duration);//单位：秒
});

//获取文件大小
var size = file.size;//单位：字节(byte)
```

