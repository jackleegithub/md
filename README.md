ffmpeg
-i 设定输入流 
-f 设定输出格式 
-ss 开始时间 

-b 设定视频流量(码率)，默认为200Kbit/s 
-r 设定帧速率，默认为25 
-s 设定画面的宽与高 
-aspect 设定画面的比例 
-vn 不处理视频 
-vcodec 设定视频编解码器，未设定时则使用与输入流相同的编解码器 

-ar 设定采样率 
-ac 设定声音的Channel数 
-acodec 设定声音编解码器，未设定时则使用与输入流相同的编解码器 
-an 不处理音频


ffmpeg-修改分辨率: ffmpeg -i 1.mp4 -strict -2 -s 640x480 4.mp4
