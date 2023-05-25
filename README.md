# 神经网络加速拓扑优化灵敏度分析
## 项目结构

拓扑优化部分主要使用了一个国外研究者分享的[github项目](https://github.com/google-research/neural-structural-optimization)。
本项目中使用了其项目中有关于SIMP方法的主体部分，包括：
- problems.ipynb：使用`Problem`类来定义不同种类的结构。
- topo_physic.ipynb：用python重写了经典的SIMP88行Matlab代码，主要包括了有限元求解和拓扑优化求解两部分。
- caching.ipynb：用于加速numpy对象计算的缓存方法，这里照搬过来，可以忽略。
- autograd.ipynb：[autograd](https://github.com/HIPS/autograd)是一个实现自动求导的包，基于autograd对拓扑优化中涉及到的一些求梯度过程进行了自定义实现，可以忽略。

神经网络部分包括数据生成和模型训练两部分。
- data_generation.ipynb：用于生成随机方形结构的全尺度和缩减尺度数据。
- model_training.ipynb：
  1. 将生成的数据处理成合适的训练数据集格式；
  2. 定义神经网络的架构；
  3. 定义神经网络的训练过程。
- model_test.ipynb：读取训练好的模型文件，将其嵌入拓扑优化过程中，测试其加速效果、预测准确度。

---
## 样例使用
### 版本
- keras-gpu                 2.6.0         
- matplotlib                3.5.3       
- numpy                     1.21.5  
- python                    3.9.15    
- scikit-image              0.19.2   
- scipy                     1.7.3           
- tensorflow-gpu            2.6.0

### 样例notebooks
依次运行：
- example_data.ipynb：使用SIMP方法生成数据并保存；
- example_model.ipynb：读取数据、训练模型并保存；
- example_test.ipynb：测试训练后的模型的预测效果。
