
<br>




<br />


<br>

<br/>

# 前言


 衍生控件：录屏控件（也是作者写的^_^）（见底部）
若你想要使用，直接复制下列代码至文本文件改后缀为.js即可导入自定义控件
 

# 下载
 控件md5: 1b39843bbd9e9db24ec3ea7c24d38353;
您可以从[点鸭控件商城](https://shequ.pgaot.com/?mod=cocojs)下载本控件,
或者从此页面<a href="/widget/rJEspGJip.jsx" download="控件.jsx">直接下载</a>获取

# 1.0.3 修改
1. 增添特殊功能--滤镜;
2. 优化某些积木显示问题

# 1.0.2 修复
1. 修复文档地址
2. 修复永久链接错位问题
3. 修改样式,文字描述

# 1.0.1 版本更新

1. 增加可用性检测积木;
2. 允许后台播放(隐藏控件即可)不必一定使用播放器
3. 添加音量自动增益功能

# 功能指南
1. 利用本控件,您可以实时监测照相机,不必打开照相机软件!
2. 3种技术:噪音消除,消除回音,自动增益
3. 高级功能:视频闪光灯,防红眼,音频采样率


# 积木用法

## 滤镜积木

在"拍照滤镜参数"中,你可以选择一个滤镜进行拍照, 
再使用"使用滤镜拍照并获得图片(永久链接)"积木进行拍照,即可得到对应滤镜效果作用后的图片


## 初始化积木

![核心积木](block%20(1).png)

图1 核心积木-图片(注意:作者系统字体改为这样了)

方法说明:打开摄像头,启用视频流并实时监控
返回:空

|参数|说明|类型|
|---|----|---|
|视频流帧率|定义视频一秒多少帧|数值
|启用音频|修改是否可以使用音频|布尔
|截取视频宽/高|修改视频最佳需求的宽和高,建议值:1920,1080;|数值
|音频采样率|音频每一秒收集样本的速率(**范围:8000-96000Hz**)|数值
|自动减噪|最大程度上消除噪音的一种功能|布尔
|消除回音|最大程度上消除回音的一种功能,例如演唱会的回音是不利的,您可以使用本功能|布尔
|摄像头朝向|指示获取的摄像头应该是哪一个,(下拉菜单有"偏移"一词,其义是摄像头向用户的相对方向的平移,例如:向右偏移则可以稍微拍到右侧肩膀)**电脑端在此属性似乎无效**|下拉菜单(字符串)
|自动音频增益|由系统自动调节音频的增减幅度|布尔

!> 注意:**此处帧率远低于游戏'帧率'**!将此属性60FPS+可能会对手机造成不可逆的损伤!
<br>最佳值应为30~60FPS间

## 拍照积木

![拍照积木](block%20(2).png)

图2 拍照积木(2类型)

说明:顾名思义<br>

|参数|说明|类型|
|---|----|---|
|闪光灯|自动由系统自己决定,开启则可以使用,关闭反之,至今,尚无"常亮"值|下拉菜单(字符串)
|防"红眼"|红眼是拍照时由于反光而形成的,防止红眼可以使照片不那么阴森|布尔值

返回:<br>
字符串,下列两者之一:<br>
<mark>临时链接:blob:___ 在应用/页面未关闭均可使用!不能上传至云端!<br>
永久链接:data:image/png...___ 最多存储512MB数据,永久指向这张图片,但大文件数据冗长,不方便存储和加载<br></mark>

### 关闭摄像头

> 懒得加图片了()

作用:关闭视频流并关闭摄像头
参数:无,
返回:空

## 视频录制模块

> 此模块共有9积木,提供视频的录制,暂停,获取数据等功能

### 开始
参数解释(编解码方法):
* webm: 大部分浏览器支持的一种视频格式,[首页](https://www.webmproject.org/) (注意:似乎不fq,无法打开);
* H264: (最常用,另名AVC)MPEG-4 规范套件的高级视频编码（AVC）标准由相同的 ITU H.264 规范和 MPEG-4 Part 10 规范指定。它是一种基于运动补偿的编解码器
* vp8: Video Processor 8（VP8）编解码器最初由 On2 Technologies 创建。在Google收购 On2 之后，Google 发布了 VP8 作为一种开放且免版税的视频格式，并承诺不强制执行相关专利。
* vp9 VP9 是完全开放且免版税的。其编解码性能与 AVC 相当或略快，但质量更好。
* 音频 采用webm音频格式
* 自动 使用浏览器默认值

### 请求数据
说明:截取当前视频已录制片段并触发对应文件生成事件,<br>
不进行暂停,停止等操作,不会影响录制

### 获取录制时间
返回:数字<br>
返回一个浮点值数字(浮点值带有多位小数,建议取整使用)

### 是否在录制?
返回:布尔<br>
暂停或没有开始均会返回"否"

### 检查设备是否支持录制?
返回:布尔<br>
检测设备是否支持本控件所有功能



### 注意事项

1. 由于开发接口受限,无法使用MP4,MP3等格式,修改后缀名无效!
2. 在已经暂停后再暂停,则方法无作用;
3. 开始录制后再开始,录制将会重新开始!原先录制将被删除!


## 属性和事件

![大小](/block%20(3).png)

图3 大小设置积木

### 属性

以下类型均为数值:

大小:放大/缩小视频源;仅供预览,不能被照相获取<br>
默认:100<br>
单位:%<br>
<br>
角度:旋转视频流;仅供预览,不能被照相获取<br>
默认:0<br>
单位:角度(degree)<br>
<br>
圆角:4个角边缘圆状半径值<br>
默认:3<br>
单位:像素<br>
<br>

### 事件

![事件积木](block%20(4).png)
图4 接入/拔出设备

![生成录制文件](block%20(5).png)
图5 生成录制文件
<br>
点击:视频流显示框被点击的一瞬间触发,无参数<br>
接入/拔出设备:接入/拔出摄像头,麦克风等媒体设备时触发<br>

- 生成录制文件完毕:当录制完成时或请求数据时触发:


|参数名|描述|类型|
|---|---|---|
|永久链接|定义见[此处](#拍照积木)|字符串|
|临时链接|定义见[此处](#拍照积木)|字符串|
|文件大小|返回文件以兆字节(Megabytes)的大小,一般文件大于20MB不宜使用永久链接|数值|
|录制时长|时长,**单位为毫秒** |数值|

<br>

录制出错:
可能是以下原因之一:
* 控件的某些bug;
* 用户不允许录制;
* 硬件设备不支持;
* 没有可以支持的文件格式或没有对应接口


!> Windows 有"媒体设备"一说法,此义为U盘等存储设备,与本文档所述不一致!

# 控件兼容性
> 日期可以理解为最近手机更新日期减去3个月

系统需求:2017年9月之前更新的手机系统无法使用本控件
非Chromium内核浏览器调试时 无法进行拍照<br>
最低版本需求:<br>
Chrome 60+ Edge 79+ Opera 47+<br>


# 控件帮助

* Q:控件无法播放视频?
* A:请多点击屏幕,如果开始运行APP时无法显示,是因为受到权限限制,无法使用播放.
* Q:滤镜功能?
* A:请期待未来版本,但是使用滤镜不能同时使用闪光灯

!> 注意,如果在电脑端能够正常使用,而手机端(或模拟器)无法正常使用不属于此控件问题.








# 相关链接
[PICKDUCK](https://shequ.pgaot.com/)<br>
[本网站首页](https://reducedradius.netlify.app/home.html)<br>
[本控件开发参考页](https://developer.mozilla.org)

# 控件警告

v1.21.7 - 自定义控件安全性提升
2024年2月19日
近期个别用户使用自定义控件时带上恶意代码，为了确保编程猫社区成员账户安全，我们将限制导入“自定义控件”的作品进行分享及协作。
为此，我们建议各作者请先将控件提交审核 Coco控件商城-投稿，再由控件商城添加及使用。
这一措施旨在维护我们社区的健康与安全，感谢您的理解与支持 ❤️ ～4
<del>(附一句：就问多久看一眼控件审核表...)</del>

## 相关控件 

```js
 var navigator = this.window.parent.navigator;
var window = this.window
var document = this.document;
const types = {
    isInvisibleWidget: true,
    type: "RECORDER_SCREEN_WIDGET",
    icon: "https://waddle.coco-central.cn/static/img/logo/logo-white.svg",
    title: "录屏控件",
    version: "1.0.0",
    isGlobalWidget: true,
    platforms:"web",//仅仅电脑端
    properties: [{
        key:'w',
        label:"像宽",
        valueType:"number",
        defaultValue:"1920"
    },{
        key:'h',
        label:'像高',
        valueType:"number",
        defaultValue:1080
    },{
        key:"frameRate",
        label:"帧率",
        valueType:"number",
        defaultValue:24
    },{
        key:"audio",
        label:'录制音频',
        valueType:"boolean",
        defaultValue:true
    },{
        key:"bits",
        label:"录制比特率",
        valueType:"number",
        defaultValue:2500000
    },{
        key:"form",
        label:"录制为WEBM",
        valueType:"boolean",
        defaultValue:true
    }],
    methods: [{
        key:"getscreen",
        label:"开始录制",
         params:[],
        callbackLabel:false
    },{
        key:"isRecording",
        label:"是否在录制",
        params:[],
        valueType:"boolean"
    },{
        key:"stop",
        label:"停止录制",
        params:[]
    },{
        key:"resume",
        label:"继续录制",
        params:[]
    },{
        key:"pause",
        label:"暂停",
        params:[]
    },{
        key:"capture",
        label:"截取录制部分",
        params:[]
    },{
        key:'download',
        label:"尝试下载文件链接",
        params:[{
            key:"file",
            label:"链接",
            valueType:["string","object"],
            defaultValue:""
        },{
            key:'name',
            label:"名称",
            valueType:"string",
            defaultValue:new Date().toLocaleString("zh-CN").replaceAll("/","_").replaceAll(":","_")+"录制的视频.webm"
        }]
    }],
    events: [{
        key:"start",
        label:"录制开始",
        params:[]
    },{
        key:"stop",
        label:"录制结束",
        params:[]
    },{
        key:"file",
        label:"录制文件生成",
        params:[{
            key:'link',
            label:"文件链接(可播放)",
            valueType:"string"
        },{
            key:"by",
            label:"临时链接(可播放)",
            valueType:"string"
        },{
          key:'size',
          label:'文件大小',
          valueType:"number"
        }]
    },{
        key:"err",
        label:"出错",
        params:[]
    }],
};

class Widget extends InvisibleWidget {
    constructor(props) {
        super(props);
        console.log(InvisibleWidget);
        console.log(props)
        this.w = Number(props.w);
        this.h = Number(props.h);
        this.bits = props.bits
        this.frameRate = Number(props.frameRate);
        this.audio = new Boolean(props.audio);
        this.mediaRecorder = null;
        this.blob = null;
        this.form = props.form;
        var m = navigator.mediaDevices.getSupportedConstraints();
        if(!navigator.mediaDevices.getDisplayMedia){this.widgetError("由于您的浏览器版本太低，无法使用");return;}
        if(!(m.width&&m.height&&m.frameRate&&MediaRecorder)){
            this.widgetError("由于您的浏览器版本太低，无法使用");return;
        }
    }

    async getscreen(){
        var mmm;
        if(MediaRecorder.isTypeSupported("video/webm")&&this.form === true){
            mmm = "video/webm";
        }else if(this.form === false){
            mmm = undefined
        }else{
            mmm = undefined;
            this.widgetError("很抱歉,不支持webm格式")
        }
        if(this.mediaRecorder){
            if(this.mediaRecorder.state !== "inactive"){
                this.widgetError("还没有录制结束呢...怎么就开始了？")
                return;
            }
            this.mediaRecorder.start();
            return;
        }
      var a = await navigator.mediaDevices.getDisplayMedia({
        video:{
        width:this.w,
        height:this.h,
        frameRate:this.frameRate
        },
        audio:this.audio
      })
      this.mediaRecorder = new MediaRecorder(a,{
        bitsPerSecond:this.bits,
        mimeType:mmm
      })
      this.mediaRecorder.onstart = () =>this.emit("start");
      this.mediaRecorder.onstop = () =>this.emit("stop");
      this.mediaRecorder.onerror = () =>this.emit("err")
      this.mediaRecorder.ondataavailable = (e) =>{
        var reader = new FileReader();
        reader.onload = () =>this.emit("file",reader.result,window.URL.createObjectURL(e.data),e.data.size);
        reader.readAsDataURL(e.data)
      }
      this.mediaRecorder.start();
    }

  isRecording(){
    if(!this.mediaRecorder){return false}
    if(this.mediaRecorder.state ==="recording"){return true}
  }

  stop(){
    if(this.mediaRecorder&&this.mediaRecorder.state === "recording"){
        this.mediaRecorder.stop()
    }
  }

  resume(){
    if(this.mediaRecorder&&this.mediaRecorder.state === "paused"){
        this.mediaRecorder.resume()
    }else{
        this.widgetError("是否没有开始或进行暂停？")
    }
  }

  pause(){
    if(this.mediaRecorder&&this.mediaRecorder.state === "recording"){
        this.mediaRecorder.pause()
    }else{
        this.widgetError("是否没有开始或已经暂停了？")
    }
  }
  
  capture(){
    if(this.mediaRecorder&&this.mediaRecorder.state === "recording"){
        this.mediaRecorder.requestData()
    }
  }
  download(file,name){
    if(window.location.href.includes("editor-player.html")){
       var parent = window.parent.parent;
       var a =parent.document.createElement("a");
       a.href = file.toString()
       a.download = name;
       a.click()
    }else{
       var a =document.createElement("a");
       a.href = file.toString()
       a.click()
    }
  }
}

exports.types = types;
exports.widget = Widget;
 
 ```

-----------------------------------------------------

&copy; 2025.7.24 ReducedRadius