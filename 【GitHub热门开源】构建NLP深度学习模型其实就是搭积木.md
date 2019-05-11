## 【GitHub热门开源】构建NLP深度学习模型其实就是搭积木

STCA NLP Group [新智元](javascript:void(0);) *今天*

![img](https://mmbiz.qpic.cn/mmbiz_png/UicQ7HgWiaUb266KFGOBP4s6F1vibKs6qKicvfrkMAFr8K20VnPx5hgL9ze7SiblnnSQzAHNXyfrx1RWfQphgT0vLibg/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

###    **新智元推荐**  

来源：PaperWeekly(ID：paperweekly)

整理编辑：三石

##### **【新智元导读】**近日，为了提高NLP深度学习模型过程中的效率，微软亚洲互联网工程院NLP团队重磅推出开源项目NeuronBlocks，使得上述复杂的任务像搭积木一样简单！



其实，构建NLP深度学习模型就是搭积木。



在构建自然语言理解深度学习模型过程中，研究人员或者工程师们经常需要在编程细节和代码调试上花费大量精力，而不是专注于模型架构设计与参数调整。



为了提升构建深度模型的效率，微软亚洲互联网工程院自然语言理解团队 (STCA NLP Group, Microsoft) 推出了开源项目**NeuronBlocks**——**自然语言处理任务的模块化深度学习建模工具包**。



![img](https://mmbiz.qpic.cn/mmbiz_png/UicQ7HgWiaUb266KFGOBP4s6F1vibKs6qKicw0bDjKOZvZOMlK58sL9wbqIYMf4MDJP0eiaI5HtNwImtBTDK2drXicAg/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

论文地址：https://arxiv.org/abs/1904.09535

项目地址：https://github.com/Microsoft/NeuronBlocks



NeuronBlocks将常用的神经网络层封装为标准模块，通过配置简单的配置文件，就可以轻松构建复杂的深度神经网络模型。与此同时，工具包还提供了一系列针对常见NLP 任务的经典模型。NeuronBlocks能使工程师们在几秒钟内快速构建和训练各种自然语言处理模型。工具包的可扩展性很强，支持快速加入新的神经元模块用于新的网络模型的构建，最大程度地避免重复的代码工作。



目前工具包支持的任务包括：**句子分类（二/多分类）**，**文本匹配**，**序列标注**，**阅读理解**，**基于知识蒸馏的模型压缩**，等等。



NeuronBlocks设计



NeuronBlocks是基于PyTorch的NLP深度学习建模工具包，可以帮助研究员或者工程师们快速构建自然语言理解任务的深度神经网络模型。该工具包的主要目标是将NLP深度神经网络模型构建的开发成本降到最低，包括模型训练阶段和推断阶段。NeuronBlocks整体框架如下图所示，包括**Block Zoo**和**Model Zoo**两个重要组件。



![img](https://mmbiz.qpic.cn/mmbiz_png/UicQ7HgWiaUb266KFGOBP4s6F1vibKs6qKic9tVoLLpj47XfLKiaqiaXViayGia5QBhJ4Rs6jhyKWVqkaxA8ppwJ813Rfw/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)



**Block Zoo**将常用的神经网络层抽象并封装为可重用的标准模块。这些模块将被用于构建各种针对不同自然语言理解任务的深度学习模型。工具包目前支持的标准神经网络模块包括：词嵌入、CNN、LSTM/GPU、Transformer和各种Attention等。



**Model Zoo**提供大量预构建好的深度神经网络模型，涵盖了常见的NLP任务。这些模型以JSON配置文件的形式呈现，用户可以通过简单修改Model Zoo中的示例模型配置，即可将其应用于自己的任务中。此外，工具包支持Linux和Windows操作系统、CPU与GPU处理器、以及PAI等GPU调度平台。



快速开始



NeuronBlocks目前支持：Python 3.6, PyTorch 0.4.1，Linux/Windows，GPU/CPU。



**1、获取源码：**

```
git clone https://github.com/Microsoft/NeuronBlocks
```



**2、安装依赖包：**

```
pip install -r requirements.txt
pip install torch==0.4.1
```



**3、运行示例模型：**

```
# 训练
cd PROJECT_ROOT
python train.py --conf_path=model_zoo/demo/conf.json

# 测试
python test.py --conf_path=model_zoo/demo/conf.json

# 预测
python predict.py --conf_path=model_zoo/demo/conf.json 
```



NeuronBlocks工作流程



用户可以选择Model Zoo中的示例模型（JSON配置文件）开启模型训练，或者利用Block Zoo中的标准神经网络模块自由构建新的模型架构，就像玩乐高积木一样。



![img](https://mmbiz.qpic.cn/mmbiz_png/UicQ7HgWiaUb266KFGOBP4s6F1vibKs6qKicH50YFtf9FB4flDThADSua9eGywNia2WolPDU5NHRy4FXzF7Sc5tFpCQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)



模型可视化工具



NeuronBlocks提供了一个模型可视化工具，可以快速绘制模型架构图，如下图所示。



![img](https://mmbiz.qpic.cn/mmbiz_png/UicQ7HgWiaUb266KFGOBP4s6F1vibKs6qKicLIciccbMfCQrhHuV1LEvRU4qfWXq174RC0o2k0ea7Lr7ibCTOC9c6UicQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)



NeuronBlocks优势



- **模型构建**：用户只需要配置简单的JSON文件，就能够构建模型和调整参数，大大减少了模型实现的工作量；
- **模型分享**：可以通过分享JSON配置文件来分享模型，使模型共享变得非常容易。对于不同的任务或模型，用户只需维护一个通用的源码库；
- **代码重用**：可以在各任务与模型间共享神经网络模块，减少重复的编程工作；
- **平台灵活性**：可以在Linux和Windows机器上运行，支持CPU和GPU，也支持像Open PAI这样的GPU管理平台；
- **模型可视化**：提供了一个模型可视化工具，用于观察模型结构及检查JSON配置的正确性；
- **可扩展性**：支持用户贡献新的神经网络模块或者新的模型。





当然，有兴趣的读者可以加入NeuronBlocks开源项目，一起贡献代码!



参考链接：

https://arxiv.org/pdf/1904.09535.pdf

https://github.com/Microsoft/NeuronBlocks

------

**新智元春季招聘开启，****一起弄潮 AI 之巅！**

**岗位详情请戳：**

[![解决AI技术落地难题，“解耦”是关键 (3).png](https://mmbiz.qpic.cn/mmbiz_png/UicQ7HgWiaUb2M4h9tkuarGklADG9cjGMsf8bicLRzt5cibWevRjGhqg5Nr6MNwCbbSmV2WE1PdyLqytGrKJms8R0w/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)](http://mp.weixin.qq.com/s?__biz=MzI3MTA0MTk1MA==&mid=2652040487&idx=5&sn=4d39d27bf481f4651c17aa58f8e08436&chksm=f12199d6c65610c006f6640fccf6c28ace29138a132b8f6b60daa53329894dd006aaa751ea15&scene=21#wechat_redirect)



**【加入社群】**



新智元 AI 技术 + 产业社群招募中，欢迎对 AI 技术 + 产业落地感兴趣的同学，加小助手微信号：aiera2015_2   入群；通过审核后我们将邀请进群，加入社群后务必修改群备注（姓名 - 公司 - 职位；专业群审核较严，敬请谅解）。

![img](https://mmbiz.qpic.cn/mmbiz_gif/UicQ7HgWiaUb1KTwONTiaO3FZYUSGxl8ibiaHPViaYfsE4hOOOHrmyQ7r5CwkByn6oHdGmwBA6Q1I6r4eCn9gVhJQ3nA/640?wx_fmt=gif&tp=webp&wxfrom=5&wx_lazy=1)

文章转载自公众号

![PaperWeekly](http://wx.qlogo.cn/mmhead/Q3auHgzwzM4XfZEiaIxTZFPcSMe0laHNlkWJfvNVMcFY7PrIPmKrQjg/0) **PaperWeekly** 

阅读原文

阅读 1134

 在看9



精选留言

[写留言](javascript:;)

-  4

  **Teng.**![img](http://wx.qlogo.cn/mmopen/aa9fn9j4Z8XjADicIJYkobDeKBI9xvahx4Xju2UWufibRLzcSQTDzvTiaMibsMY7N54B32CicZJWgyseZHwiaNOiciaeLXkypHYWQscR/96)

  

  有點厲害哦~