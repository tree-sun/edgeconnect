### model.train()   model.eval()
在使用PyTorch构建神经网络的时候，训练过程中会在程序上方添加一句model.train(), 作用是启用 batch normalization 和 drop out<br>
测试过程中会使用model.eval(), 此时神经网络会沿用batch normalization的值, 并不使用drop out<br>

### 模型中的forward()
教程: https://blog.csdn.net/hxxjxw/article/details/107707471<br>
forward()函数是自动调用的<br>
神经网络的典型结构为 __ init__() 和 forward()<br>
> model = MyNet()<br>
> y = model(x)<br>
> 注意: 上述调用的即是forward()函数<br>

### torch.load()
torch.load() 从文件中加载用 torch.save() 保存的对象<br>
> 直接加载模型: model.load_state_dict(torch.load('./data/my_model.pkl'))<br>
> GPU训练的模型加载到CPU上: model.load_state_dict(torch.load('./data/my_model.pkl', map_location=lambda storage, loc: storage))<br>
> 加载到GPU1上: model.load_state_dict(torch.load('./data/my_model.pkl', map_location=lambda storage, loc: storage.cuda(1)))<br>
> 从GPU1 移动到 GPU0: model.load_state_dict(torch.load('./data/my_model.pkl', map_location={'cuda:1':'cuda:0'}))<br>

### PyTorch中模型的保存与加载
官方网址: https://pytorch.org/tutorials/beginner/basics/saveloadrun_tutorial.html<br>
教学网址: https://blog.csdn.net/weixin_40522801/article/details/106563354<br>
