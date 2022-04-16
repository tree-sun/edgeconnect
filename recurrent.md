### 参考网址
(网页教程)https://benpaodewoniu.github.io/2020/06/02/edge0/<br>
(视频教程)https://www.bilibili.com/video/BV15o4y127Rt/?spm_id_from=333.788.recommend_more_video.0<br>
### 项目代码
https://github.com/knazeri/edge-connect<br>
### 复现过程
一、创建虚拟环境  conda create -n edge python=3.8<br>
二、激活虚拟环境  activate edge<br>
三、安装pytorch<br>
> pip install torch==1.10.1 -i https://pypi.tuna.tsinghua.edu.cn/simple<br>
> pip install torchvision==0.2.1 -i https://pypi.tuna.tsinghua.edu.cn/simple<br>
> 如何验证pytorch安装完成呢？<br>
>> 打开python  输入import torch 如果出现 >>> 说明安装成功<br>

四、安装requirements.txt<br>
> 安装python依赖包时出现了错误:ValueError: check_hostname requires server_hostname,如下图所示<br>

![](https://github.com/tree-sun/edgeconnect/blob/main/screenshot/error_1.jpg)<br>
> 解决方法:关掉VPN<br>

安装requirements.txt最好是在pycharm中进行安装。方法:在pycharm中打开requirements.txt文件，它会自动询问是否安装。<br>
在pycharm中安装包时，可能会遇到以下问题<br>
> 问题一:<br>
> ![](https://github.com/tree-sun/edgeconnect/blob/main/screenshot/error_2.png)<br>
> 解决方法:关闭VPN<br>
> 问题二:<br>
> ![](https://github.com/tree-sun/edgeconnect/blob/main/screenshot/error_3.png)<br>
> 解决方法:安装其他版本的包，如果找不到的话，在cmd中激活虚拟环境，采用pip install 名称  进行安装<br>
