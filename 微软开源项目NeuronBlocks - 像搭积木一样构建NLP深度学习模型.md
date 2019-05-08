## 微软开源项目NeuronBlocks - 像搭积木一样构建NLP深度学习模型

原创： STCA NLP Group [PaperWeekly](javascript:void(0);) *昨天*

![img](https://mmbiz.qpic.cn/mmbiz_gif/VBcD02jFhgm9RFr5icmiaj0bibJxUeIGdAFHNM4G6PJEiccw293RuVnOiadQ4zcdibdJa5FFfn0ZMgpbKib4AAKD8dm2w/640?tp=webp&wxfrom=5&wx_lazy=1)



在构建自然语言理解深度学习模型过程中，研究人员或者工程师们经常需要在编程细节和代码调试上花费大量精力，而不是专注于模型架构设计与参数调整。为了提升构建深度模型的效率，**微软亚洲互联网工程院自然语言理解团队 (STCA NLP Group, Microsoft) 推出了开源项目 NeuronBlocks** - 自然语言处理任务的模块化深度学习建模工具包。



NeuronBlocks 将常用的神经网络层封装为标准模块，通过配置简单的配置文件，就可以轻松构建复杂的深度神经网络模型。与此同时，工具包还提供了一系列针对常见 NLP 任务的经典模型。



**NeuronBlocks 能使工程师们在几秒钟内快速构建和训练各种自然语言处理模型。**工具包的可扩展性很强，支持快速加入新的神经元模块用于新的网络模型的构建，最大程度地避免重复的代码工作。



目前工具包支持的任务包括：**句子分类（二/多分类），文本匹配，序列标注，阅读理解，基于知识蒸馏的模型压缩**，等等。欢迎来自学术界和工业界的朋友加入 NeuronBlocks 开源项目：



![img](https://mmbiz.qpic.cn/mmbiz_png/VBcD02jFhgnmPfiaYjxY6czQhicNQoJLr0PDJQVDic90PzSKKJ4CGTXQkyHwic21pkUD3AWJmWxyCtcvRqmj8dHkmw/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)



**项目地址：**https://github.com/Microsoft/NeuronBlocks

**论文地址：**https://arxiv.org/abs/1904.09535



# NeuronBlocks设计



NeuronBlocks 是基于 PyTorch 的 NLP 深度学习建模工具包，可以帮助研究员或者工程师们快速构建自然语言理解任务的深度神经网络模型。该工具包的主要目标是**将 NLP 深度神经网络模型构建的开发成本降到最低**，包括模型训练阶段和推断阶段。



NeuronBlocks 整体框架如下图所示，包括 **Block Zoo** 和 **Model Zoo** 两个重要组件。



![img](https://mmbiz.qpic.cn/mmbiz_png/VBcD02jFhgnmPfiaYjxY6czQhicNQoJLr0yUeheAxbqeGH2FU8OgYKe9qvqaC9Ux4gbskPxQFWUCYtaKhuUkmeZg/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)



**Block Zoo** 将常用的神经网络层抽象并封装为可重用的标准模块。这些模块将被用于构建各种针对不同自然语言理解任务的深度学习模型。工具包目前支持的标准神经网络模块包括：词嵌入、CNN、LSTM/GPU、Transformer 和各种 Attention 等。 



**Model Zoo** 提供大量预构建好的深度神经网络模型，涵盖了常见的 NLP 任务。这些模型以 JSON 配置文件的形式呈现，用户可以通过简单修改 Model Zoo 中的示例模型配置，即可将其应用于自己的任务中。此外，工具包支持 Linux 和 Windows 操作系统、CPU 与 GPU 处理器、以及 PAI 等 GPU 调度平台。



# 快速开始



NeuronBlocks 目前支持：Python 3.6, PyTorch 0.4.1，Linux/Windows，GPU/CPU。



**1. 获取源码**



```
git clone https://github.com/Microsoft/NeuronBlocks
```



**2. 安装依赖包**



```
pip install -r requirements.txt
pip install torch==0.4.1
```



**3. 运行示例模型**



```
# 训练
cd PROJECT_ROOT
python train.py --conf_path=model_zoo/demo/conf.json

# 测试
python test.py --conf_path=model_zoo/demo/conf.json

# 预测
python predict.py --conf_path=model_zoo/demo/conf.json
```



# NeuronBlocks工作流程



用户可以选择 Model Zoo 中的示例模型（JSON 配置文件）开启模型训练，或者利用 Block Zoo 中的标准神经网络模块自由构建新的模型架构，就像玩乐高积木一样。



![img](https://mmbiz.qpic.cn/mmbiz_png/VBcD02jFhgnmPfiaYjxY6czQhicNQoJLr0dl07R9hLzLfTXyqBsPcfSXJhh0b1HV2PNKuAatibhEBWROibkbE8jcCA/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)



# 模型可视化工具



NeuronBlocks 提供了一个模型可视化工具，可以快速绘制模型架构图，如下图所示。



![img](https://mmbiz.qpic.cn/mmbiz_png/VBcD02jFhgnmPfiaYjxY6czQhicNQoJLr0W5FHhl3pGP8CINjxH18LJBJtluriahv7mqKa8HVqbL3aV8NBo8tdxWw/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)



# NeuronBlocks优势



**• 模型构建：**用户只需要配置简单的 JSON 文件，就能够构建模型和调整参数，大大减少了模型实现的工作量； 



**• 模型分享：**可以通过分享 JSON 配置文件来分享模型，使模型共享变得非常容易。对于不同的任务或模型，用户只需维护一个通用的源码库； 



**• 代码重用：**可以在各任务与模型间共享神经网络模块，减少重复的编程工作； 



**• 平台灵活性：**可以在 Linux 和 Windows 机器上运行，支持 CPU 和 GPU，也支持像 Open PAI 这样的 GPU 管理平台； 



**• 模型可视化：**提供了一个模型可视化工具，用于观察模型结构及检查 JSON 配置的正确性； 



**• 可扩展性：**支持用户贡献新的神经网络模块或者新的模型。



# 联系我们



欢迎来自学术界和工业界的朋友加入 NeuronBlocks 开源项目，一起贡献代码！



如有任何问题，请联系：

NeuronBlocks@microsoft.com



![img](https://mmbiz.qpic.cn/mmbiz_png/VBcD02jFhgmPEF4lW0pL5weJia5y4xhJbog2pIZZ3ZCgVUDynvus6rCzNKGAAAI6R8jaXTpYPISCMicpFegVdG0g/640?tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)





**点击以下标题查看更多往期内容：** 



- [目标检测小tricks之样本不均衡处理](http://mp.weixin.qq.com/s?__biz=MzIwMTc4ODE0Mw==&mid=2247496155&idx=1&sn=b720e982a8e99a5db93a48c59ecad8d5&chksm=96ea2e5ba19da74dff62f9e57043423e9dd4ac4109933aad530b96fed279d80e5f7ad516eb50&scene=21#wechat_redirect)

- [图神经网络综述：模型与应用](http://mp.weixin.qq.com/s?__biz=MzIwMTc4ODE0Mw==&mid=2247493906&idx=1&sn=15c9f18a1ce6baa15dc85ecb52e799f6&chksm=96ea3692a19dbf847c1711e6e194ad60d80d11138daf0938f90489a054d77cfd523bee2dc1d2&scene=21#wechat_redirect)

- [DRr-Net：基于动态重读机制的句子语义匹配方法](http://mp.weixin.qq.com/s?__biz=MzIwMTc4ODE0Mw==&mid=2247496112&idx=1&sn=923701d6be5204d2bf22f723df448531&chksm=96ea2e30a19da726e2475d38f8bdf2f9f891a388eb231bec4a343d3ed8f6052925643735cd68&scene=21#wechat_redirect)

- [小样本学习（Few-shot Learning）综述](http://mp.weixin.qq.com/s?__biz=MzIwMTc4ODE0Mw==&mid=2247496040&idx=1&sn=ebea875571ccc80a70a3166f62b9640b&chksm=96ea2ee8a19da7fe9bf3d9cbf15c3a2fc6e3ca898e48a2d01207a7cdc2cd046c4087eda27637&scene=21#wechat_redirect)

- [万字综述之生成对抗网络（GAN）](http://mp.weixin.qq.com/s?__biz=MzIwMTc4ODE0Mw==&mid=2247495668&idx=1&sn=e7e959b2bdd7b2763b9207ccb80fa6bc&chksm=96ea3074a19db96208a51d26f7b5b4ef9c3a37a7799ec270becc77203de4294235041ede7206&scene=21#wechat_redirect)

- [可逆ResNet：极致的暴力美学](http://mp.weixin.qq.com/s?__biz=MzIwMTc4ODE0Mw==&mid=2247495880&idx=1&sn=e3a960836797c7dd4eb2dbb9b9a0b9e7&chksm=96ea2f48a19da65eea9cc157f2110a6856985d322d872c6679a8dd0807c9bb10f85c4d3c3f7d&scene=21#wechat_redirect)

- [基于多任务学习的可解释推荐系统](http://mp.weixin.qq.com/s?__biz=MzIwMTc4ODE0Mw==&mid=2247495957&idx=1&sn=2e614a271d9ba5c6391987c16455deff&chksm=96ea2e95a19da783b7470a9d66753644eab6a0fe0441e795a400f6c888a96692770e177ed1fb&scene=21#wechat_redirect)

- [AAAI 2019 | 基于分层强化学习的关系抽取](http://mp.weixin.qq.com/s?__biz=MzIwMTc4ODE0Mw==&mid=2247495926&idx=1&sn=a59ffa7b3639497e68617e1ea40d8cd2&chksm=96ea2f76a19da660508b0d149101cbc9591c3203622eea1545a26181f86a26404723101c9baf&scene=21#wechat_redirect)

  







**![img](https://mmbiz.qpic.cn/mmbiz_gif/xuKyIMVqtF2cO2WSmiccOqL8YlIwp5Xv2cqdDp6ANbUt8yibCc1cgQQrPHLKhf73icQGHves57M2XMZLJxIhF0e7g/640?tp=webp&wxfrom=5&wx_lazy=1)****#****投 稿 通 道#**

 **让你的论文被更多人看到** 





如何才能让更多的优质内容以更短路径到达读者群体，缩短读者寻找优质内容的成本呢？**答案就是：你不认识的人。**



总有一些你不认识的人，知道你想知道的东西。PaperWeekly 或许可以成为一座桥梁，促使不同背景、不同方向的学者和学术灵感相互碰撞，迸发出更多的可能性。



PaperWeekly 鼓励高校实验室或个人，在我们的平台上分享各类优质内容，可以是**最新论文解读**，也可以是**学习心得**或**技术干货**。我们的目的只有一个，让知识真正流动起来。



📝 **来稿标准：**

• 稿件确系个人**原创作品**，来稿需注明作者个人信息（姓名+学校/工作单位+学历/职位+研究方向） 

• 如果文章并非首发，请在投稿时提醒并附上所有已发布链接 

• PaperWeekly 默认每篇文章都是首发，均会添加“原创”标志



**📬 投稿邮箱：**

• 投稿邮箱：hr@paperweekly.site 

• 所有文章配图，请单独在附件中发送 

• 请留下即时联系方式（微信或手机），以便我们在编辑发布时和作者沟通







🔍



现在，在**「知乎」**也能找到我们了

进入知乎首页搜索**「PaperWeekly」**

点击**「关注」**订阅我们的专栏吧





**关于PaperWeekly**



PaperWeekly 是一个推荐、解读、讨论、报道人工智能前沿论文成果的学术平台。如果你研究或从事 AI 领域，欢迎在公众号后台点击**「交流群」**，小助手将把你带入 PaperWeekly 的交流群里。



![img](https://mmbiz.qpic.cn/mmbiz_gif/VBcD02jFhgkXb8A1kiafKxib8NXiaPMU8mQvRWVBtFNic4G5b5GDD7YdwrsCAicOc8kp5tdEOU3x7ufnleSbKkiaj5Dg/640?tp=webp&wxfrom=5&wx_lazy=1)

▽ 点击 | 阅读原文 | 获取最新论文推荐

阅读原文

阅读 6798

 在看67



精选留言

[写留言](javascript:;)

-  1

  **Winston**![img](http://wx.qlogo.cn/mmopen/nFNzd9xjFeBF0OichvibJXAvdWfLFv0w1uYEfib2L4PLCKiccicm31eUc4vVbMVncOoRFRgDIvoLxeZsmRibTzbYmhwichujrpvs3Z7/96)

  

  这个好短