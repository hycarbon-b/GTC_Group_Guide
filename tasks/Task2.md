# Task1

## 软件环境
- Kaggle平台账号注册
- 安装python
- 安装VSCODE
- VSCODE安装插件：Python \ Jupyter \ SSH Remote  

## 掌握DL基础概念
1. 何为Deep Learning
2. FCN执行前向计算的过程
3. （反向传播）梯度下降的过程
4. 卷积核的计算方式，CNN的前向计算过程，CNN与FCN的差异

## Pytorch介绍
1. 何为Pytorch
2. Pytorch官网介绍 [官网](pytorch.org)
3. 学习官网的的Tutorial(太难的话可以跳到第四条)
4. Pytorch速学视频[b站视频链接](https://www.bilibili.com/video/BV1CT411q7Sw)  （运行pyotorch代码在kaggle/notebook上面运行，因为pytorch在本地的安装比较麻烦）
- nnModule
- Dataset 和 Dataloader
- Optimzer
- Loss function
### Pytorch
Tensor  
img text audio video ... -> tensor  
img:   
    二维tensor： pixel intensity 
    三维tensor： channel [[width,height] [width,height] [width,height]]  
    img (3,224,224)  

1. Forward/Backpropagation
    $$f(\vec{x};a) = \vec{y}$$
   
    loss : pred label 的差异  ground truth
   
    $$loss(a;\vec{y}, \vec{gt})$$
   
    loss ： MSE $(y - gt)^2$、RMSE、L1 、CrossEntropy    
    label: vector[], 向量的每一位对应一个logit，值的大小视作该类别的概率    
    Update a 梯度下降（自动实现），a是整个nn Module计算时的参数（网络权重）
    
3. nn module
    抽象的计算结构 $\vec{y} = nnModule(\vec{x})$  
    nn module 可以作为基础神经计算单元、网络层、网络结构、多个网络的复合体等一切在Pytorch中的计算结构
    

4. Process  
    Data Preprocessing: png jpg nii ...... -> tensor  
    Foward  
    Backp  
    Repeat  

    Data Preprocessing: png jpg nii ...... -> tensor  
    Data stack & Data load   
    Foward  
    Backp  
    Repeat  
### One-hot/logits
车的型号：A B C D E F G   
1. [1~7] 先验  
2. [0000001] [0000010] [0000100] 无先验  
a b c  
pred=[0.2 0.3 0.9]  
gt = [0 0 1]  

```
class net1(nn.Module):
    def __init__(self):
        super().__init__()
        self.flatten = nn.Flatten()
        self.linear_relu_stack = nn.Sequential(
            nn.Linear(28*28, 512),
            nn.ReLU(),
            nn.Linear(512, 512),
            nn.ReLU(),
            nn.Linear(512, 10),
        )

    def forward(self, x):
        x = self.flatten(x)
        logits = self.linear_relu_stack(x)
        return logits


class myDataset():
    def __init__(self):
        pass
    def __getitem__(self, idx):
        pass
        return tensor, label
# getitem ：编号 返回样本和GT

dataloader = DataLoader(myDataset, batch_size=32, shuffle=True)
# batch_size =32 , 32个sample叠到一个tensor，label叠到一个tensor
# tensor1 tensor2 tensor3 ... tensor32
# label1 label2 label3 ... label32
# new_tensor [tensor1,tensor2,tensor3,...,tensor32] new_label [label1,label2,label3,...,label32]
# new tesnor[0]= tensor[0] 
# new_tensor  (32,28,28) label(32,1)                        (28,28) (1)

#dataloader = [(new_tensor, new_label) , (new_tensor, new_label) , (new_tensor, new_label) , ...]

def train_loop(dataloader, model, loss_fn, optimizer):
    # Set the model to training mode - important for batch normalization and dropout layers
    # Unnecessary in this situation but added for best practices
    model.train()
    for batch, (X, y) in enumerate(dataloader):
        # Compute prediction and loss
        pred = model(X)
        loss_fn = nn.CrossEntropyLoss()
        loss = loss_fn(pred, y) + nn.MSELoss(pred, y)

        # Backpropagation
        loss.backward()
        optimizer.step()
        optimizer.zero_grad()

        if batch % 100 == 0:
            print(loss)
```

## Unet
阅读知乎文章https://zhuanlan.zhihu.com/p/313283141
- 图像分割Task是什么
- Unet基础内容
