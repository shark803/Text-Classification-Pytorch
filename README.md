# Text-Classification-Pytorch  参考 git项目 https://github.com/649453932/Chinese-Text-Classification-Pytorch.git 适配IMDB，修改成英文的标准处理流程，对于中文原来项目开箱即用，只需要对于
# 不同的显存，稍微修改hidden node的数目，以及适当减少batch，防止出现类似out_cuda的错误
# 之前写过一个版本基于torchtext的预处理，有一个小问题没有纠正，后期补偿   其实也可以直接用tensorflow.keras.preprocessing



TextCNN，TextRNN，FastText，TextRCNN，BiLSTM_Attention, DPCNN, Transformer, 基于pytorch。

  

预训练词向量使用 [GLove 200d]

## 环境
python 3.7  
pytorch 1.4 
tqdm  
sklearn  
tensorboardX

#数据集IMDB

数据集|数据量
--|--
训练集|2万
验证集|2500
测试集|2500





## 性能

模型|acc|备注
--|--|--
TextCNN|87.60%|Kim 2014 经典的CNN文本分类
TextRNN|84.44%|BiLSTM 
TextRNN_Att|86.88%|BiLSTM+Attention
TextRCNN|86.80%|BiLSTM+池化
FastText|84.80%| 原项目在中文新闻分类中bow+bigram+trigram， 效果出奇的好，但是在情感分析中则表现最差，可见同样的分类问题，情感分析对词序更依赖，感受野大的模型效果更好
DPCNN|87.24%|深层金字塔CNN
Transformer|86.08%|效果较差

bert|94.83%|bert + fc  
ERNIE|94.61%|比bert略差(说好的中文碾压bert呢)  

 

## 使用说明
```
# 训练并测试：

python run.py --model [model_name]



# FastText, embedding层是随机初始化的,且用到bigram 和 trigram
python run.py --model FastText --embedding random 



#致谢  十分感谢北京科技大学的胡文星同学 精简正确的中文文本分类项目，良好的代码结构和规范的预处理流程，极大的减少了我从tensorflow代码过度到pytorch的时间，再次感谢作者的扎实工作和分享精神   


## 对应论文
[1] Convolutional Neural Networks for Sentence Classification  
[2] Recurrent Neural Network for Text Classification with Multi-Task Learning  
[3] Attention-Based Bidirectional Long Short-Term Memory Networks for Relation Classification  
[4] Recurrent Convolutional Neural Networks for Text Classification  
[5] Bag of Tricks for Efficient Text Classification  
[6] Deep Pyramid Convolutional Neural Networks for Text Categorization  
[7] Attention Is All You Need  
