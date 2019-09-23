# musicPlayer
实现简易的音乐播放器

1. 写简单的静态界面布局
2. 使用AJAX获取数据列表
3. 使用获取歌曲的数据设置歌词和作者
4. 进度条随着音乐的进度和实时变更
5. 暂停播放上一首下一首的功能
6. 点击进度条调节歌曲进度的功能
##audioObj属性
1. 创建或者获取audio对象
```
    var audio=new Audio
```
2. audioObject.play()开始播放
3. audioObject.pause()暂停播放
4. audioObject.autoPlay设置或者获取自动播放状态
5. audioObject.duration获取音乐长度
6. audioObjetc.currentTime 设置获取播放时间
7. audioObject.ended 判断音乐是否播放完毕
8. audio.paused 判断音乐是否为暂停状态,设置暂停按钮
###功能的实现
1. 设置progress-now的宽度随着播放时间变化而变化
```
audio.ontimeupdate=function(e){
    $('.progress-now').style.width=(this.currentTime/this.duration)*100+'%'
}
```
2. 两种方式设置歌曲时间随进度进行变化
```
audio.ontimeupdate=function(e){
   $('.progress-now').style.width = (this.currentTime/this.duration)*100 + '%'
   var min=Math.floor(this.currentTime/60)
   var sec= Math.floor(this.currentTime %60)>9?(Math.floor(this.currentTime%60)):('0'+Math.floor(this.currentTime%60))
   $('.time').innerText=''+min+':'+sec
 }//使用ontimeupdate来进行设置,每秒触发4-66次会导致时间变化不均匀
 udio.onplay=function(){
       clock =setInterval(function(){
       var min=Math.floor(audio.currentTime/60)
       var sec= Math.floor(audio.currentTime %60)>9?(Math.floor(audio.currentTime%60)):('0'+Math.floor(audio.currentTime%60))
       $('.time').innerText=''+min+':'+sec
 
         })
     }
audio.onpause=function(){
        clearInterval(clock)
    }//通过setInterval来设置，每秒一次，时间变化均匀



```