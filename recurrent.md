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

五、下载官方的 checkpoints<br>
> 新建checkpoints文件夹，然后下载预训练模型，并将其复制到 ./checkpoints 目录下<br>

六、运行test.py文件<br>
> 问题一:ImportError: cannot import name 'PILLOW_VERSION' from 'PIL'<br>
>> 原因是pillow版本太高<br>
>> 解决方法:打开functional.py文件，将from PIL import Image, ImageOps, ImageEnhance, PILLOW_VERSION 改为 from PIL import Image, ImageOps, ImageEnhance, __ version__<br>

> 问题二:ImportError: cannot import name 'imread' from 'scipy.misc' <br>
>> 原因是scipy库的版本太高，新版把imread删除了<br>
>> 解决方法:安装imageio库，并找到调用imread的地方，加入from imageio import imread<br>

> 问题三:OMP: Error #15: Initializing libiomp5md.dll, but found libiomp5md.dll already initialized.<br>
> OMP: Hint This means that multiple copies of the OpenMP runtime have been linked into the program. That is dangerous.....<br>
>> 解决方案:加入以下两行代码<br>
>> import os<br>
>> os.environ["KMP_DUPLICATE_LIB_OK"]="TRUE"<br>

> 问题四:self._dict = yaml.load(self._yaml)   TypeError: load() missing 1 required positional argument: 'Loader'<br>
>> 原因:YAML5.1弃用了yaml.load(file)这个用法,5.1版本之后就修改了需要指定Loader，通过默认加载器（FullLoader）禁止执行任意函数，该load函数也变得更加安全<br>
>> 解决方法:<br>
>>> 方法1:self._dict = yaml.load(self._yaml, Loader=yaml.FullLoader)<br>
>>> 方法2:self._dict = yaml.safe_load(self._yaml)<br>
>>> 方法3:self._dict = yaml.load(self._yaml, Loader=yaml.CLoader)<br>

> 问题五:Downloading: "https://download.pytorch.org/models/vgg19-dcbb9e9d.pth" to C:\Users\zhan/.cache\torch\hub\checkpoints\vgg19-dcbb9e9d.pth<br>
>> 下载速度过慢<br>
>> 直接下载vgg19-dcbb9e9d.pth到指定位置，然后重新执行即可。<br>

七、运行train.py文件<br>
> 加上import os 和 os.environ["KMP_DUPLICATE_LIB_OK"]="TRUE"<br>
> 问题二:如下所示<br>
>> ![](https://github.com/tree-sun/edgeconnect/blob/main/screenshot/1.png)<br>
>> 问题原因:shuffle的参数设置错误，因为已有batch_sample，不需要shuffle来进行随机的sample了，故shuffle设置为FALSE<br>
>> 解决方法:更改更改edge_connect.py文件，将shuffle设置为FALSE<br>

> 问题三:No training data was provided! Check 'TRAIN_FLIST' value in the configuration file.<br>
