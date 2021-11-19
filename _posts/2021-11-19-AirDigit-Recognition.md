---
layout: post
title: 空中手寫數字辨識
author: [Richard Kuo]
category: [Lecture]
tags: [jekyll, ai]
---

運用智慧型手機, 利用紀錄手機之三軸加速器可將空中手寫數字或其他手勢動作儲存加速器之資料, 透過Kaggle平台訓練AI模型,
再安裝於電腦執行辨識, 由手機應用程式紀錄動作傳送至PC進行辨識。

---
## AirDigit 手機應用程式

### App Inventor 2 雲端平台設計手機應用程式
使用個人電腦或筆電進行以下步驟：<br />
以Google Chrome打開網址 **[https://ai2.appinventor.mit.edu](https://ai2.appinventor.mit.edu)**, 即可使用App Inventor 2 開發環境

* 使用 iOS 手機者, 請參考 [https://youtu.be/z9YmWY8FeII](https://youtu.be/z9YmWY8FeII)<br />
  步驟如下:
 - iPhone 安裝MIT App Inventor, 啟動後產生QR碼
 - PC Chrome開啟ai2.appinventor.mit.edu之計畫，上方選單選Connect，後選AI companion ，產生QR碼及文字碼
 - iPhone執行MIT App Inventor掃描QR碼或輸入文字碼，AI2計畫會傳送應用程式至iPhone執行
<iframe width="811" height="456" src="https://www.youtube.com/embed/z9YmWY8FeII" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

---
### 開發 AirDigit 手機應用程式
1. 先下載 [AirDigit.aia](https://drive.google.com/file/d/1bKW38dGtjk3XkeMbiFFcalfw-CyR1rTM/view?usp=sharing)於電腦<br />
2. 於Chrome 中之App Inventor 2頁面, 上方選 **import project(.aia) from my computer**<br />
![](https://github.com/rkuo2000/Robotics/blob/gh-pages/images/AI2_import_aia.png?raw=true)

3. App設計畫面如下
![](https://github.com/rkuo2000/Robotics/blob/gh-pages/images/AI2_AirDigit_design.png?raw=true)

4. App程式畫面如下
![](https://github.com/rkuo2000/Robotics/blob/gh-pages/images/AI2_AirDigit_block.png?raw=true)

5. 按上方選單Build可產生一QR碼, 可用手機掃描取得應用程式.apk來安裝
6. 於手機上點選AirDigit.apk檔案, 可完成AirDigit之App安裝

---
### 使用AirDigit App 紀錄手勢動作以建立資料集
#### 手勢動作順序
![](https://github.com/rkuo2000/Robotics/blob/gh-pages/images/AirDigit_dataset.png?raw=true)
*手寫數字需按筆劃動作進行, 可有效提昇辨識率！*<br />

#### 資料集之檔案
* 錄取三軸加速器之資料檔案如下：<br />
> **Train: 0~9 各20筆訓練資料**<br />
> 0_000.csv, 0_001.csv, …, 0_019.csv<br />
> 1_000.csv, 1_001.csv, …, 1_019.csv<br />
> …<br />
> 9_000.csv, 9_001.csv, …, 9_019.csv<br />
> <br />
> **Test: 0~9 各2筆訓練資料**<br />
> 0_000.csv, 0_001.csv, 1_000.csv, 1_001.csv, …, 9_000.csv, 9_001.csv<br />

#### 使用AirDigit App進行以下資料集取樣步驟：
1. 輸入Filename 取樣資料之檔案名 (0_000，將取樣儲存至/Download/0_000.csv)
 (Android手機會存到內建儲存空間之Download檔案夾，請查看手機之[檔案管理])
 (iPhone手機會存到AppInventor底下的Download檔案夾，請查看手機之[檔案])
2. 輸入[取樣速度] (50，為設定每50ms取樣一次)
3. 輸入[感測時間] (1500，為設定取樣時間長度1500ms = 1.5秒，如動作較大較長，可設至２或３秒）
4. 按下[開始取樣] 開始取樣（接著馬上搖動手機做出手勢動作）
5. 每個空中手寫數字動作儲存成不同檔案名，需做至少20次以上，
6. 尋找存有 0_000.csv, ... 0_019.csv, 1_000.csv ...之檔案夾, 將其壓縮成.zip
7. 上傳至Kaggle Datasets以建立你的AirDigit資料集: https://kaggle.com/your_name/airdigit

**Note:** 請注意手寫數字之筆畫順序，需固定筆畫順序進行

---
### 於Kaggle平台使用資料集訓練AI模型
**[airdigit-cnn](https://kaggle.com/rkuo2000/airdigt-cnn)** : https://kaggle.com/your_name/airdigit-cnn
使用CNN神經網路模型訓練辨識空中手寫數字0~9:
1. 於電腦上打開kaggle.com網頁
2. 於Kaggle上執行AirDigit-CNN進行模型訓練（點選上方Run-All來執行所有程式）
3. 執行程式後會產生一模型檔 airdigit_cnn.h5 (點選下載至電腦）

---
### 使用電腦啟動 AI辨識服務器

#### 安裝環境
* 於電腦終端機(Windows使用GitBash或Anaconda之Command, MAC/Linux PC使用Terminal）執行以下命令<br />
`$conda create -n tensor`<br />
`$conda activate tensor`<br />
`$conda install matplotlib pillow`<br />
`$pip install pandas requests`<br />
`$pip install opencv-python`<br />
`$python -c 'import tensorflow as tf; print(tf.__version__)'`<br />
`$pip install tensorflow`(==2.6.0 to match kaggle version)<br />

* 取得程式範例<br />
`!git clone https://github.com/rkuo2000/tf`<br />

* 將airdigit_cnn.h5至於~/tf/models

* 執行服務器程式 [airdigit_server.py](https://github.com/rkuo2000/tf/blob/master/airdigit_server.py)<br />
`$ cd ~/tf`<br />
`$ python airdigit_server.py`<br />

---
### 使用手機AirDigit App進行手勢動作辨識
<p align="center"><img src="https://github.com/rkuo2000/Robotics/blob/gh-pages/images/AirDigit_app.png?raw=true"></p>

* 須設定PC服務器之IP位址（並須與手機同一個網路,可由手機開熱點分享給跑AI辨識服務器的PC)

* 按下**[開始取樣]**收錄動作資料

* 完成後再按下**[傳送資料]**即可由服務器傳回辨識之答案




*This site was last updated {{ site.time | date: "%B %d, %Y" }}.*

