# Kaggle_Practice_Dogs_vs._Cats
Image Classification影象分類練習，分辨狗(Dogs)與貓(Cats)的圖片
https://www.kaggle.com/competitions/dogs-vs-cats/

# 使用工具
* Python 3
* Tensorflow
* Numpy
* OpenCV
* Matplotlib


# 流程
1.   讀取數據
2.   資料預處理(Preprocessing).
      * 調整大小(Resize)
      * 重新縮放(Rescale to (0,1))
      * 調整色彩
          >全彩或灰階(Grayscale)
      * 將資料分為訓練集(training)及與驗證集(Validation)
4.   構建分類器模型(build the classifer model)
      * 使用Tensorflow.Keras
5.   訓練(Training)
6.   分析結果

# 數據(Dataset)
使用kaggle數據集
URL：https ://www.kaggle.com/c/dogs-vs-cats/data
包含25,000張狗與貓的圖片，標記為1 = 狗，0 = 貓
## 預處理(Preprocessing)
使用ImageDataGenerator對圖片進行旋轉放大平移來增強資料避免過擬合，以及Rescale。
也用使用OpenCV將圖片轉成灰階，可以減少運算時間，但是結果不佳

# Model
## CNN(Convolutional Neural Network)
主要由卷積層(Convolutional)和池化層(Maxpool)所組成，ReLU作為activation
三組層後接上全連接層，以及使用Dropout防止過擬合(Overfitting)
最後用Sigmoid函數輸出預測結果
![image](https://user-images.githubusercontent.com/103236841/164624127-b77cfd23-e2c8-411f-938c-45072bc32ff6.png)
## ResNet(Deep residual network)
使用ResNet-50V2預訓練模型，捨棄頂層的fully connected layers，最後增加Dense layer，以Sigmoid函數輸出預測結果。
![image](https://user-images.githubusercontent.com/103236841/164936655-e19818c9-9002-4966-a42e-bf4a142fcb5e.png)

# 結果
## CNN
單純使用CNN結果，預測準確度落在80%左右
![image](https://user-images.githubusercontent.com/103236841/164628715-d3219918-e109-4c50-8380-3626cbfaa75d.png)
## ResNet
使用ImageDataGenerator增強資料與ResNet預訓練模型準確度可來到98以上
![image](https://user-images.githubusercontent.com/103236841/164936755-ebc9533f-989f-4827-9702-3b30f2c4ca38.png)

