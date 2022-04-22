### model.train()   model.eval()
在使用PyTorch构建神经网络的时候，训练过程中会在程序上方添加一句model.train(), 作用是启用 batch normalization 和 drop out<br>
测试过程中会使用model.eval(), 此时神经网络会沿用batch normalization的值, 并不使用drop out<br>

### 模型中的forward()
教程: https://blog.csdn.net/hxxjxw/article/details/107707471
forward()函数是自动调用的<br>
神经网络的典型结构为 __ init__() 和 forward()<br>
> model = MyNet()<br>
> y = model(x)<br>
> 注意: 上述调用的即是forward()函数<br>

