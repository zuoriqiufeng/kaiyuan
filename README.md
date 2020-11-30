## INSTALL

配置、编译和安装该项目的说明信息

1. 安装Anaconda 3.0(进入anaconda官方网址,点击对应的Python 版本以及电脑位数，选择只有当前用户，加入PATH目录，设为默认python 版本)

2. 安装Pycharm

3. 配置需要的python 环境
4. 下载合适的CUDA及其对应的CUDNN本项目CUDA为9.0和其对应的CUDNN版本

（1）模型训练

需要安装的包（版本仅供参考，可适当升级或降低版本）：

Python 3.6.8

tensorflow-gpu  1.10.0  （1.15以前的版本，cpu版和gpu版是分开的，之后的版本直接安装tensorflow即可，具体见官网）

keras 2.2.4  （keras包含在tensorflow中，应该不用安装，直接from tensorflow import keras即可调用，但我单独安装了，所以程序中代码直接from keras了）

 numpy 1.16.6		
		scikit-learn 0.21.2
		matplotlib 3.2.1
		pandas  0.24.2
		opencv-python  4.1.0.25
		Pillow 7.0.0  （第4步需要）

实现步骤：

1. 将FER2013数据集（fer2013.csv）下载到Emotion_Recognition\fer2013文件夹中。该文件夹中的fer2013_clean2.csv为我在fer2013数据集的基础上处理的数据集，可直接用来训练，具体处理方式见论文。FER2013数据集可在参考程序链接中找到。

2. load_and_process.py中可设置要训练的数据集。

3. 运行train_emotion_classifier.py 进行模型训练，并生成混淆矩阵。训练完的模型储存在models文件夹下。

4. 数据集为csv格式，想要转换成图片运行parse fer2013.py即可。（代码中的file 和directory分别代表要转换的csv文件和储存到的文件位置，根据需要进行设置）

5. 代码中存在的问题：train_emotion_classifier.py中使用train_test_split随机划分数据集和测试集，但感觉在多次训练比较算法时这样不严谨，应该固定使用一样的训练和测试集来比较不同算法的准确率高低。可根据keras官方文档修改代码。

（2）模型算法测试

程序名称：Emotion_Recognition

需要安装的包：
		PyQt5 5.13.2
		imutils 0.5.2

实现步骤:

	1. 运行FER_test.py 做简单的表情识别测试，从摄像头获取人脸并识别表情。模型路径在代码中设置
	2. 运行runMain.py 可在功能更全的界面进行测试，可从界面选择模型和测试图片及摄像头。

（3）NAO机器人利用训练好的模型进行表情识别

程序名称：nao_Facial_expression_recognition （Python2.7.18） 和nao_Fer_server（Python3.6.8）

参考链接：http://doc.aldebaran.com/2-8/index_dev_guide.html

需要安装的包：
	pynaoqi-python2.7-2.8.6.23-win64-vs2015-20191127_152649将其解压到复制到Anaconda下的python2.7的环境目录

实现步骤：

1. 在nao_Fer_server中的Fer_server_2.py设置主机IP地址。

2. 在nao_Facial_expression_recognition中的facial_expression_recognition.py中安装pillow包，并设置NAO机器人IP地址及主机地址。

3. 先运行Fer_server_2.py进行监听端口，再运行facial_expression_recognition.py机器人即可进行人脸识别。

## HISTORY

国外：2012年后，随着深度学习和卷积神经网（CNNConvolutionalNeuralNetworks）的兴起，深度神经网络逐渐应用于表情识别领域。Tran等人【2】提出了一种简单有效的时空特征学习方法，即在

大规模监督视频数据集上使用深度3维卷积网络（3DConvNets），它们在概念上非常简单，且易于训练和使用。Lopes等人【3】在2016年提出了一个简单的面部表情识别解决方案，它结合了卷积神经网络和特定的图像预处理步骤。该方案与其他面部表情识别方法相比具有竞争优势（CK+数据库中准确率达到96.76％），训练速度快，并且可以使用标准计算机进行实时面部表情识别。Jeong等人【4】在2019年提出了基于深度外观和几何神经网络的有效深度联合时空特征，用于面部表情识别。该方案在CK+，MMI和FERA数据集的识别准确率分别为99.21％，87.88％和91.83％，通过比较分析表明，至少能够将识别精度提高4％。

近些年，东南大学的唐传高等人【5】在FG2017表情识别与分析竞赛荣获冠军。北京大学陈颖婕等人【6】比较了使用传统机器学习模型或深度学习模型的不同面部表情识别方法，并为情感智能机器人提出了一种快速、准确的多模型面部表情识别方法，以完成实时和高精度的面部表情识别任务。张桐等人【7】提出了一种新颖的深度学习框架，称为时空递归神经网络（STRNN，spatial-temporalrecurrentneuralnetwork），从而将对两个不同信号源的学习统一为时空依赖模型。所提出的STRNN方法在脑电图和面部表情的公共情感数据集上比其他最新方法更具竞争力。