---
layout: post
title: Introduction to Quadcopter Drone
author: [Richard Kuo]
category: [Lecture]
tags: [jekyll, ai]
---

簡介無人機產業, 無人機應用, 無人機種類, 飛行原理, 飛行器組成, 電機, 鋰電池, 組裝指南, 飛控板, 飛控軔體 , 飛行模式及飛行功能, 地面控制站 等.

---
## 無人機產業
[產業應用漸成形 無人機大聯盟促設分級指引](https://www.digitimes.com.tw/iot/article.asp?cat=158&cat2=80&ct=o&id=0000645107_KJU27JPHLAI9FO8V2UARA)<br>
目前無人機應用可分為3大類，即**軍事攻擊/供給**、**商務應用**、以及**娛樂展演**。軍事領域事涉敏感不便多談，商務應用則相當多元，例如橋樑和水庫等設施巡檢、農藥噴灑、偵查搜救、物流補給、國土測繪等，娛樂性的群飛展演也已相當成熟。<br>

![](https://img.digitimes.com/newsimg/2022/0919/645107-4-2uara.jpg)

### 台灣無人機大聯盟(Unmanned Aircraft Systems Team of Taiwan; UAS Taiwan)<br>
<iframe width="553" height="311" src="https://www.youtube.com/embed/XeSh5lLFass" title="2022智慧城市展xDrone遊國際•產業起飛─臺灣無人機大聯盟成立大會暨科技產業發展國際論壇" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### [台灣無人機應用發展協會](https://www.facebook.com/uastw/)

---
## 無人機應用

### 無人機投放砲彈
[台製無人機現蹤烏克蘭！投「6枚迫擊砲」毀俄軍　傳波蘭採購800架](https://www.ettoday.net/news/20220824/2323312.htm)<br>
![](https://cdn2.ettoday.net/images/6529/d6529313.jpg)
波蘭科技媒體《WP tech》則於18日報導稱，橙森國際所出產的800架「Revolver 860」已先出售給波蘭，再由波蘭政府轉手捐給烏克蘭軍隊

---
### 無人機群飛展演
[無人機群飛展演「重質不求量」　臺灣希望創新強化內容設計](https://www.digitimes.com.tw/iot/article.asp?cat=158&ct=o&id=0000645108_AN22VZY6LMRV1G96ZWGO7)
臺灣希望創新公司(Taiwan Drone 100)屢以群飛展演驚艷四座，執行長李志清指出，群飛技術著重精確定位及通訊技術，即時定位誤差可控制在10~15公分之內。2021年團隊在國際群飛競賽「1000架以下」組別奪得首獎。

![](https://img.digitimes.com/newsimg/2022/0920/645108-1-zwgo7.jpg)
臺灣希望創新公司執行長李志清(左)及技術長蔡博智

為提升定位精準度，團隊運用的是Real-time Kinematic (RTK)定位系統，每台無人機皆須裝設RTK接收器，地面則設有天線基地台。RTK接收器的成本曾經相當昂貴，一台要價新台幣40萬，不過近期基本款已降到4,000~5,000元左右。<br>
以展演用到的通訊技術而言，基地台得持續上傳修正訊號到每台無人機，才能持續將定位誤差維持在10~15公分左右，資料傳輸則用到4G LTE、5G、或工業級的Wi-Fi系統。同時，無人機也會回傳資料給操控電腦，地面的操控人員須隨時監控飛機的定位、路徑、電量等狀況，若有異常則須讓機台返航或降落。此外，團隊也開發出雲端監控平台，以利即時和遠端監控。<br>
<table>
<tr>
<td><img src="https://img.digitimes.com/newsimg/2022/0920/645108-2-zwgo7.jpg"></td>
<td><img src="https://img.digitimes.com/newsimg/2022/0920/645108-3-zwgo7.jpg"></td>
</tr>
</table>

---
### 無人機植樹
[日植4萬棵樹！AirSeed改良無人機種樹系統](https://www.digitimes.com.tw/iot/article.asp?cat=158&cat1=20&cat3=41&id=0000643512_6346LNFW0ZGASC3MD221U)<br>
![](https://img.digitimes.com/newsimg/2022/0913/643512-1-d221u.jpg)

---
### 無人機收水果
[Tevel Aerobotics](https://www.tevel-tech.com/)<br>
<iframe width="1031" height="580" src="https://www.youtube.com/embed/xzOf4-WaXzE" title="First Commercial Pilot of Tevel Aerobotics & Rivoira Group" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

---
### 無人機物流
[中華郵政於尖石鄉試辦遙控無人機物流服務](https://www.digitimes.com.tw/iot/article.asp?cat=158&cat1=20&cat2=&id=643497)<br>
中華郵政首度使用25公斤以上的無人機於新竹縣尖石鄉進行物流投遞試飛<br>
![](https://img.digitimes.com/newsimg/2022/0830/643497-1-6qh5r.jpg)

---
### 無人機外送
[可省70%外送人力成本　高軟無人送餐10月「上門」](https://www.digitimes.com.tw/iot/article.asp?cat=158&cat1=20&cat2=&id=643409)<br>
統一集團攜手中光電智能機器人，展開全新的無人機外送模式<br>
![](https://img.digitimes.com/newsimg/2022/0829/643409-1-8vil4.jpg)
7-Eleven串聯Foodomo外送平台，積極投入兩大無人外送測試計畫。一是攜手工研院，參與AMR無人智慧物流技術送餐服務行列，推動在地首創自主移動機器人直送門口(door to door)的無人外送服務；二是整合集團旗下四大品牌資源，攜手中光電智能機器人，展開全新的無人機外送模式。<br>

工研院南分院執行長曹芳海與統一超商協理吳輝振26日在高雄「2022 Meet Greater South亞灣創新×新創大南方」簽署合作備忘錄，雙方瞄準無人送餐市場，運用AMR無人智慧物流技術，打造全台首創可室外、室內配送、自動呼叫並搭乘電梯的無人送餐物流服務。<br>

---
### 城市無人機物流
[日將開放大城市無人機物流　爭取制定國際標準](https://www.digitimes.com.tw/iot/article.asp?cat=158&cat1=20&cat2=&id=642820)<br>
![](https://img.digitimes.com/newsimg/2022/0825/642820-1-so8o0.jpg)
日本從2012年引進美國軍方的的無人機，就開始研究以無人機當基地台的無人機無線通訊網技術，並分配920MHz與169MHz無線電波頻段，供無人機航管控制及影像轉播等用途應用<br>
據日經報導，2022年6月起，在日本重量超過0.1公斤的無人機，都要申請類似車牌的ID編號，確定無人機使用者身分，防範惡意使用者。<br>

---
### 中光電智能機器人
[Teledyne FLIR攜手中光電智能機器人 無人機4Q22美國銷售](https://www.digitimes.com.tw/iot/article.asp?cat=158&cat1=20&cat3=16&id=0000645052_LFD1QPLQ4FM3RU3Z8O7SJ)<br>
SIRAS無人機具備IP54防塵防水等級設計、31分鐘飛行時間、前雷達防撞系統，可1分鐘內快速起飛，長距離圖傳雙頻無線電(2.4/5.8 GHz)遙控器，電池熱插拔，可確保任務不中斷，同時為提高數據安全性，操作者不需建立在線帳戶即可立即飛行，圖像可全部儲存在SD卡，提高使用便利性及避免潛在資料外洩等風險功能。<br>
![](https://img.digitimes.com/newsimg/2022/0915/645052-1-8o7sj.jpg)

---
### 無人機監控水質
[環保署推無人機監控水質 更省時、省錢、低污染 2020/10/21](https://news.ltn.com.tw/news/life/breakingnews/3328102)<br>
![](https://img.ltn.com.tw/Upload/news/600/2020/10/21/3328102_2_1.jpg)

---
### 農業無人機
[佐翼科技](https://www.droxotech.com/) [以航太領域的無人機技術為傳統農工業打穩轉型的第一哩路](https://www.gvm.com.tw/article/85865)<br>
農業用智能無人機<br>
![](https://www.droxotech.com/uploads/1/2/9/5/129575120/1090615-droxo-web-01_orig.jpg)
特殊空拍應用專案<br>
![](https://www.droxotech.com/uploads/1/2/9/5/129575120/0615-droxo-web-orig_orig.jpg)
<table>
<tr>
<td>農用植保機 DX10-N1</td>
<td>農用植保機 DX20-E1</td>
</tr>
<tr>
<td><img src="https://www.droxotech.com/uploads/1/2/9/5/129575120/1100527-droxo-web-01_orig.jpg"></td>
<td><img src="https://www.droxotech.com/uploads/1/2/9/5/129575120/1100527-droxo-web-02_orig.jpg"></td>
</tr>
</table>

---
### 風機檢測
[金屬中心無停轉風機之無人機(UAV)巡檢系統 勇奪科技界奧斯卡2020 R&D100大獎](https://www.mirdc.org.tw/NewsView0.aspx?Cond=2203&Source=0)<br>
此外該技術具備「高空穩定性」，可於15kg~25kg的荷載下，7級陣風中穩定飛行。同時可於5分鐘以內完成單一風機檢測任務，風機檢測時間縮短，更能有效擴展到大規模巡檢。<br>
<iframe width="1031" height="580" src="https://www.youtube.com/embed/vW6TbXJ-cpw" title="無停轉風機無人機巡檢系統技術" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

---
### 全自動風機葉片表面瑕疵檢測
[開發AI檢測風機葉片瑕疵 要比人工更準更快](https://www.windtaiwan.com/ArticleView.aspx?ID=ART00632)<br>
![](https://www.windtaiwan.com/Upload/20220517/perceptual-robotics-and-the-university-of-bristol-announce-results-of-innovate-uk-data-analysis-project-image-11-1536x866.jpg?ID=ART00632)

---
### 工業巡檢
Flyability ELIOS2 工業巡檢無人機
![](https://i0.wp.com/www.esentra.com.tw/wp-content/uploads/2019/05/3e4899693c35ca47c8c6c6f27f159515-450x450.jpg)
Flyability ELIOS 3 無人機-局限空間檢查/數位建模
![](https://i0.wp.com/www.esentra.com.tw/wp-content/uploads/2022/05/24165f504bca70bac19d038be3ff5ead-450x450.jpg)

<iframe width="765" height="430" src="https://www.youtube.com/embed/JWkf8qMOcB4" title="風力發電機  Flyability室內無人機檢查" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

---
## Quadcopter (四軸無人機)
**VTOL (Vertical Take-Off and Landing)**<br>
**機動性高 :** 最高時速應該有超過 100 km/hr
<iframe width="500" height="282" src="https://www.youtube.com/embed/8p5uDf9i_Yc" title="minicp120 x2208 2000kv 6x4.5 hqprop kiss esc 18a nanowii 4s1800 40c" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
* Flying Santa Penta Copter
<iframe width="640" height="385" src="https://www.youtube.com/embed/48B_3AqRuW0" title="What is Santa doing when he's not at delivering presents to the kids | Santa penta drone" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### 掌上型/迷你型無人機
<table>
<tr>
<td><img src="https://a.rimg.com.tw/s0/d4c/820/popular2020/5/f3/0a/22011340470026_752.jpg"></td>
<td><img src="https://a.rimg.com.tw/s2/f/67/08/22208017372936_736.jpg"></td>
</tr>
</table>

### Q100 室內穿越機
<table>
<tr>
<td>Q100室內穿越機四軸機架</td>
<td>8520 航模小電機 空心杯</tD>
<td>室內穿越微型有刷馬達驅動板</td>
</tr>
<tr>
<td><img src="https://img.ruten.com.tw/s1/5/48/23/21649673459747_114.jpg"></td>
<td><img src="https://img.ruten.com.tw/s2/d/c0/18/21805650628632_901.jpg"></td>
<td><img src="https://img.ruten.com.tw/s2/2/a8/88/21637601301640_510.jpg"></td>
</tr>
</table>
<iframe width="498" height="280" src="https://www.youtube.com/embed/YhTbYbuW8KI" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

---
### Q200/250 穿越機
![](https://a.rimg.com.tw/s2/7/31/cc/21521520906700_786.jpg)
![](https://a.rimg.com.tw/s9/528/873/xihn0005/3/c9/22217724897225_497.jpg)
<iframe width="498" height="280" src="https://www.youtube.com/embed/jXG91unOZts" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

---
### F450空拍機
<table>
<tr>
<td><img src="https://img.ruten.com.tw/s2/3/34/bc/21607819441340_16.jpg"></td>
<td><img src="https://img.ruten.com.tw/s2/3/34/bc/21607819441340_500.jpg"></td>
</tr>
</table>

---
### 市售航拍機
<iframe width="712" height="359" src="https://www.youtube.com/embed/DjWONLRgvZ0" title="【新手入門級】S91折疊無人機 自動避障航拍機【8K雙攝像頭+30分鐘長續航" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
**<u>無人機功能</u>** :
1. 一鍵起飛
2. 三面避障
3. 前進避障
4. 左右避障
5. 前置鏡頭，底置鏡頭
6. 氣壓定高懸停
7. 實時圖傳 (鏡頭影像傳到手機顯示)
8. 手勢拍照/錄像
9. 軌跡飛行
10. 360度翻滾 
11. 無頭模式 (Headless)
12. 一鍵返航

---
### [DJI](https://www.dji.com/tw) 大疆無人機
* **Mavic 3** 是 DJI 新一代旗艦航拍無人機，配備 4/3 感光元件的 Hasselblad 相機，成就傳世佳作；支援全向避障，為你帶來暢快的飛行體驗；續航時間長可達 46 分鐘，圖傳距離可達 15 公里。它的每一項提升，都為航拍確立了全新標準。<br>
  <iframe width="640" height="360" src="https://www.youtube.com/embed/svrn0NMRmIg" title="開箱 史上最強空拍機DJI MAVIC 3 5K畫質來了 ft.VACS攝視度「Men's Game玩物誌」" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
  
* **DJI AIR 2S** 擁有一台強大航拍機所需：1 英吋感光元件、5.4K 影片、大師鏡頭智能拍攝功能、12 公里 1080p 圖傳、四向環境感知和高速飛行主動避障。<br>
  <iframe width="580" height="327" src="https://www.youtube.com/embed/o7qIAF00rYU" title="最適合Youtuber的空拍機!! DJI Mavic Air 2開箱!! 終於等到最完美的空拍機了?!【劉沛空拍機】" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

* **DJI Mini 2** 作為 DJI 航拍機入門首選，DJI Mini 2 便攜易用且安全可靠，極致輕巧，性能犀利，可拍攝 4K 影片，實現 4 倍變焦和 10 公里圖傳距離。支援一鍵短片、一鍵全景、相片畫質智慧優化、手機快傳、截選下載等功能。智慧易用，助你一鍵拍大片，輕鬆變身航拍大師。<br>
  <iframe width="640" height="360" src="https://www.youtube.com/embed/nFdWm_TsZrU" title="DJI MINI 2  開箱：僅249公克！免登記也有強大穩定4K攝錄影" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

* **DJI FPV** 沉浸式飛行體驗 - 飛臨其境<br>
  <iframe width="640" height="360" src="https://www.youtube.com/embed/hWknxsTrUY8" title="開箱 DJI FPV Combo穿越機 | 一次就上手 體驗開飛機的臨場感 比空拍機更爽「Men's Game玩物誌」@懷爸瘋科技" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

---
### Coaxial Quadcopter
[Design and Model Predictive Control of a Mars Coaxial Quadrotor](https://arxiv.org/pdf/2109.06810.pdf)
![](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQD5bTakTcz6Xhbpj-42NgByQgAIoZefXLrUw&usqp=CAU)

---
### DelftAcopter
<iframe width="459" height="258" src="https://www.youtube.com/embed/wj0gV08Hdr8" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

---
### Google Drone
<iframe width="640" height="360" src="https://www.youtube.com/embed/7wA8uYjgfoM" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

---
### LONG-RANGE TACTICAL VTOL UAS (長程戰術垂直起降無人飛機系統)
VTOL (Vertical Take-Off and Landing)
UAS (Unmanned Aircraft Systems)
<iframe width="560" height="315" src="https://www.youtube.com/embed/pV9iXIa6E9Y" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

---
### 雷虎科技
![](https://img.ltn.com.tw/Upload/business/page/800/2022/06/09/3955046_1.jpg)
[雷虎轉型生產無人機 獲空中基地台訂單](https://ec.ltn.com.tw/article/breakingnews/3955046)<br>
此次雷虎股東會中亦展示各式中大型無人載具產品，其空中基地台無人直升機去年開花結果，得標NCC及中華電信（2412）五千萬元「空中基地台」訂單，強調未來將持續開發新型無人機及無人潛艇產品。

---
### 經緯航太 
[ALIAS 保全巡檢無人機](https://www.geosat.com.tw/TW/product-uav-alias.aspx) - 多旋翼機(multirotor)<br>
![](https://www.geosat.com.tw/assets/images/products/uav/GEOSAT-UAV-ALIAS-1-W1920.jpg)
* 應用範例:
  - 夜間工廠空氣汙染及水汙染偵測
  - 建築物安全狀況監測
  - 無人機太陽能面板巡檢服務

<iframe width="640" height="360" src="https://www.youtube.com/embed/1MkrDliJzrw" title="1-2國內無人載具產業現況_羅正方創辦人(經緯航太科技股份有限公司)" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

---
## [飛行原理](https://hom-wang.gitbooks.io/quadcopter/content/02_Principles.html)
![](https://www.dronezon.com/wp-content/uploads/2017/11/How-A-Quadcopter-Flies-Using-Propeller-And-Motor-Direction-e1580563822230.jpg)
![](https://hom-wang.gitbooks.io/quadcopter/content/cw.png)

---
## 飛行器組成
系統圖
![](https://uav.jreyn.net/user/pages/04.quadcopter-design/step-7-electronics-selection/quad%20wiring.jpg)
![](https://hom-wang.gitbooks.io/quadcopter/content/qd.png)

---
### 機架 (Frame)
通常我們會用對角馬達的軸距（M2M）來敘述機身的大小，如果對角馬達的兩個轉軸相距 450mm 的距離，則稱為 F450
![](https://ph-test-11.slatic.net/p/c62efacb047a9e22bfdc30c09ff31eb0.jpg)
* **腳架 (Landing Gear)**
![](https://robu.in/wp-content/uploads/2017/05/F450-F550-Landing-skit-2.png)

---
### 螺旋槳（Propeller)
四軸中有兩對螺旋槳，一對螺旋槳順時針旋轉，另一對螺旋槳則是逆時針旋轉，並不是所有螺旋槳都一樣的<br>
通常會用像 1045 或 10x4.5 的方式來分別不同規格的螺旋槳，其意思為直徑10 inch，螺距 4.5 inch。<br>
在相同轉速下，螺旋槳越長，攻角越大，所提供的升力就越大，但所受到的阻力亦會越大，所以轉動大的槳需要扭力大的馬達。<br>
![](https://hom-wang.gitbooks.io/quadcopter/content/prop.jpg)

---
### 電子調速器（Electronic Speed Controller）ESC
通常市售的電調只需輸入 PWM，並透過調整 PWM 的占空比即可控制無刷馬達轉速
![](https://a.rimg.com.tw/s2/6/00/98/21202132148376_553_m.jpg)

---
###  飛控板
<table>
<tr>
<td><img src="https://a.rimg.com.tw/s1/9/af/39/21614442402617_341.jpg"></td>
<td><img width="50%" height="50%" src="http://docs.px4.io/main/assets/img/pixhawk4_hero_upright.74e8a52a.jpg"></td>
</tr>
<tr>
<td><img src="https://ardupilot.org/copter/_images/APM25encl1.jpg"></td>
<td><img src="https://my-test-11.slatic.net/p/8e9e17d4cc1b68afb51eb81e2db7b8a2.jpg"></td>
</tr>
<tr>
<td><img src="https://img.ruten.com.tw/s5/644/60e/tiko756/4/a2/69/22129953387113_536.jpg"></td>
<td><img src="https://a.rimg.com.tw/s1/5/30/05/21204112855045_627.jpg"></td>
</tr>
</table>

---
### 慣性感測器
慣性測量單元（Inertial Measurement Unit, IMU）捕捉物體運動的資訊、測量物體姿態的一種電子元件，又稱為慣性感測器，主要由陀螺儀（Gyroscope）與加速度計（Accelerometer）組成，部分的應用中有時也會加入磁力計（Magnetometer）與氣壓計（Barometer）來輔助估算相關訊息，經常使用在載具的導航上面。
四軸飛行器上面常會使用一些感測器做為回授，來取得飛行器的姿態、航向或是高度等資訊，常見有陀螺儀、加速度計、磁力計以及氣壓計這四種，
<table>
<tr>
<td><img src="https://github.com/rkuo2000/Robotics/blob/main/images/MPU9250_BMP280.jpg?raw=true"></td>
<td><img src="https://a.rimg.com.tw/s1/2/45/09/21721347568905_401.jpg"></td>
</tr>
</table>

---
### GPS 模組
[Ublox Neo-M8 series](https://www.u-blox.com/en/product/neo-m8-series)<br>
![](http://blog.rctoysky.com/wp-content/uploads/2019/08/2.8-withcompass.png)
![](https://m.media-amazon.com/images/I/61Xkn2keEoL.jpg)
![](https://els-jbs-prod-cdn.jbs.elsevierhealth.com/cms/asset/35ae42c5-9915-4e97-9d48-1fb86724e100/gr7_lrg.jpg)
![](https://ardupilot.org/copter/_images/pixhawk_connect_essential_peripherals.jpg)

---
### 遙控接收器 (RC receiver)
![](https://ae01.alicdn.com/kf/Hee0d4bbd93df4743961ef5233e5482c88.jpg)

---
## 鋰電池 (LiPo)
Lithium-ion polymer battery
<table>
<tr>
<td><img src="https://a.rimg.com.tw/s1/5/3a/a5/22209045359269_638.jpg"></td>
<td><img src="https://a.rimg.com.tw/s1/e/35/ab/22209043850667_916.jpg"></td>
</tr>
</table>
<iframe width="1061" height="597" src="https://www.youtube.com/embed/FhCqE8k54fE" title="《韓吉老師碎碎念》電池種類介紹與充電注意事項-新手教學" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### 放電能力
電池的放電能力是以倍數（C）來表示的，1C是指電池用1C放電可以持續工作1小時。
例：2200mAH容量的電池持續工作1小時(1C)，那么平均電流是2200mA,即2.2A.

### 航模鋰電
通常，**11.1V**的遙控航模鋰電池都由3片鋰電芯串聯而成(**3S1P**), 也就是說每片電芯的電壓為3.7V。

### 插頭型號:
![](https://a.rimg.com.tw/s2/a/e1/78/22030964354424_832.jpg)

### 圓桶型鋰電池型號
以最常見的**18650**電池為例，「18」為電池的直徑；「65」為電池長度；「0」則是指圓柱形的電池
![](https://github.com/rkuo2000/Robotics/blob/main/images/Li_Battey_table.png?raw=true)

[磷酸鐵鋰電池的六大優點和五大缺點解析](https://blog.xuite.net/boavista/blog/588986823#)<br>

---
## 無人機電機
[無人機的電機電調你都了解嗎](https://ppfocus.com/0/dieeca43e.html)<br>

### 電機的種類及區別
對於多旋翼無人機來說，小型無人機通常使用有刷電機，比如空心杯電機；而軸距較大，通常大於200mm左右的無人機都使用無刷電機。<br>
目前的無人機多以無刷電機 中的永磁同步電機爲主。<br>
無刷電機：可連續工作20000小時 左右，常規的使用壽命7-10年。<br>
有刷電機：可連續工作5000小時左右，常規的使用壽命2-3年。<br>

### 電機的基本參數
最大電流（A），最大電壓（V），KV值。<br>
KV值：指電機在單位電壓下的轉速。一般KV值越高，代表電機的轉速越快。<br>
比方說：KV值爲1000，意思是：此電機在1V電壓下，每分鐘轉速爲1000轉。<br>

###電機的命名
四位數字，前兩位是定子的直徑，後兩位是定子的高度。如4108規格的電機，定子的直徑是41mm，高度是8mm。

### 如何選配電機
多旋翼的電機最大拉力總和不應低於總重的1.5倍，最好是兩倍朝上。

### For 四軸F450/F350: **2212 950KV**
![](https://img.ruten.com.tw/s1/1/26/ab/21704181796523_243_m.jpg)

---
## 組裝指南
[新手DIY多軸飛行器——我的第一架450無人機](https://www.gushiciku.cn/dl/0pOfe/zh-tw)

### QA250 組裝指南
<iframe width="516" height="290" src="https://www.youtube.com/embed/u8VwOuuhMKM" title="翔大模型_新改款QAV250_更加方便組裝_維修_初學著最佳" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<iframe width="498" height="280" src="https://www.youtube.com/embed/BDjCUj14Iyc" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

---
### F450 組裝指南
<iframe width="498" height="280" src="https://www.youtube.com/embed/cg1-L9EYe1U" title="F450 安裝指南" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

---
## 飛控板

### APM2.6/2.8
![](https://content.instructables.com/ORIG/FIS/KM5R/J3YPUEXT/FISKM5RJ3YPUEXT.jpg?auto=webp) 
* Specification:<br>
  - Arduino Compatible!
  - Includes 3-axis gyro, accelerometer, along with a high-performance barometer
  - Onboard 4 MegaByte Dataflash chip for automatic datalogging
  - Optional off-board GPS, uBlox LEA-6H module with Compass.
  - One of the first open source autopilot systems to use Invensense’s 6 DoF Accelerometer/Gyro MPU-6000.
  - Barometric pressure sensor upgraded to MS5607, from Measurement Specialties.
  - Atmel’s ATMEGA2560 and ATMEGA32U-2 chips for processing and usb functions respectively.
  - Weight: 30g

---
### PixHawk 2.4.8
![](https://a.rimg.com.tw/s1/9/af/39/21614442402617_341.jpg)
* Specification:<br>
  - Processor
    - 32-bit ARM Cortex M4 core with FPU
    - 168 Mhz/256 KB RAM/2 MB Flash
    - 32-bit failsafe co-processor
  - Sensors
    - MPU6000 as main accel and gyro
    - ST Micro 16-bit gyroscope
    - ST Micro 14-bit accelerometer/compass (magnetometer)
    - MEAS barometer
  - Power
    - Ideal diode controller with automatic failover
    - Servo rail high-power (7 V) and high-current ready
    -  All peripheral outputs over-current protected, all inputs ESD protected
  - Interfaces
    - 5x UART serial ports, 1 high-power capable, 2 with HW flow control
    - Spektrum DSM/DSM2/DSM-X Satellite input
    - Futaba S.BUS input (output not yet implemented)
    - PPM sum signal
    - RSSI (PWM or voltage) input
    - I2C, SPI, 2x CAN, USB
    - 3.3V and 6.6V ADC inputs
  - Dimensions
    - Weight 38 g (1.3 oz)
    - Width 50 mm (2.0”)
    - Height 15.5 mm (.6”)
    - Length 81.5 mm (3.2”)

---
### Pixhawk 4 (PX4)
![](https://docs.px4.io/v1.9.0/assets/flight_controller/pixhawk4/pixhawk4_wiring_overview.png)
* Specification:<br>
  - **Main FMU Processor: STM32F765**<br>
    - 32 Bit Arm® Cortex®-M7, 216MHz, 2MB memory, 512KB RAM
    - IO Processor: STM32F100
    - 32 Bit Arm® Cortex®-M3, 24MHz, 8KB SRAM<br>
  - **On-board sensors:**<br>
    - Accel/Gyro: ICM-20689
    - Accel/Gyro: BMI055 or ICM20602
    - Magnetometer: IST8310
    - Barometer: MS5611
    - GPS: u-blox Neo-M8N GPS/GLONASS receiver; integrated magnetometer IST8310<br>
  - **Interfaces:**<br>
    - 8-16 PWM outputs (8 from IO, 8 from FMU)
    - 3 dedicated PWM/Capture inputs on FMU
    - Dedicated R/C input for CPPM
    - Dedicated R/C input for Spektrum / DSM and S.Bus with analog / PWM RSSI input
    - Dedicated S.Bus servo output
    - 5 general purpose serial ports
    - 3 I2C ports
    - 4 SPI buses
    - Up to 2 CANBuses for dual CAN with serial ESC
    - Analog inputs for voltage / current of 2 batteries
  - **Power System:**
    - Power module output: 4.9~5.5V
    - USB Power Input: 4.75~5.25V
    - Servo Rail Input: 0~36V
  - **Weight and Dimensions:**
    - Weight: 15.8g
    - Dimensions: 44x84x12mm
  - **Other Characteristics:**
    - Operating temperature: -40 ~ 85°c

---
### DIY飛控板: [ESP32copter](https://github.com/rkuo2000/arduino/tree/master/examples/Robot/Esp32Copter)
<table>
<tr>
<td><img src="https://github.com/rkuo2000/arduino/blob/master/examples/Robot/Esp32Copter/DSC02360.jpg?raw=true"></td>
<td><img src="https://github.com/rkuo2000/arduino/blob/master/examples/Robot/Esp32Copter/DSC02364.jpg?raw=true"></td>
</tr>
</table>

---
## 飛控韌體
### [PX4: Open Source Autopilot For Drone Developers](https://px4.io/)
![](https://docs.px4.io/main/assets/img/pixhawk4_wiring_overview.8cf16bfa.png)
![](https://docs.px4.io/v1.9.0/assets/flight_controller/pixhawk4/pixhawk4-connectors.jpg)
* **[PX4 Autopilot Software](https://github.com/PX4/PX4-Autopilot)**<br>
* **[PX4 Autopilot User Guide](https://docs.px4.io/v1.12/en/)**<br>

---
### [Ardupilot](https://ardupilot.org/)
ArduPilot is the most advanced, full-featured, and reliable open source autopilot software available.<br>

**Copter -- Plane -- Rover -- Sub -- Antenna Tracker**<br>
![](https://ardupilot.org/ardupilot/_images/firmware_types.jpg)
* **[code](https://github.com/ArduPilot/ardupilot)**<br>
  - [ArduCopter](https://github.com/ArduPilot/ardupilot/tree/master/ArduCopter)
  - [ArduPlane](https://github.com/ArduPilot/ardupilot/tree/master/ArduPlane)
  - [ArduSub](https://github.com/ArduPilot/ardupilot/tree/master/ArduSub)

---
### [Mission Planner](https://ardupilot.org/planner/)
Download the [latest Mission Planner installer from here](https://firmware.ardupilot.org/Tools/MissionPlanner/MissionPlanner-latest.msi).
[Loading Firmware](https://ardupilot.org/planner/docs/common-loading-firmware-onto-pixhawk.html)<br>

* [Loading Firmware onto flight-control board (first time only)](https://ardupilot.org/planner/docs/common-loading-firmware-onto-chibios-only-boards.html)

* APM飛控與調參<br>
  <iframe width="640" height="360" src="https://www.youtube.com/embed/zNaDJMqF5Yk" title="如何安裝APM飛控與調參「大鎚創作」" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

* Pixhawk飛控 設定重點 F450<br>
  <iframe width="640" height="366" src="https://www.youtube.com/embed/e0SWhm0MnSM" title="【天鷹遙控】PIXHAWK飛控 設定重點 F450 四軸無人機 APM PX4 開源飛控 Arduino 大學 研究所 專題 實驗 Mission Planner GCS 地面站 Autopilot" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

* Pixhawk4 刷 Ardupilot 千萬一定要注意的步驟<br>
  <iframe width="640" height="360" src="https://www.youtube.com/embed/9URmy0NiyqA" title="翔大模型_Holybro Pixhawk4 刷 Ardupilot 千萬一定要注意的步驟" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
  
---
## Flight Modes & Features
### Flight Modes (飛行模式)
**Recommended Flight Modes:**<br>
* [Stabilize (穩定模式)](https://ardupilot.org/copter/docs/stabilize-mode.html#stabilize-mode)
* [Altitude Hold (維持高度模式)](https://ardupilot.org/copter/docs/altholdmode.html#altholdmode)
* [Loiter (閒逛模式)](https://ardupilot.org/copter/docs/loiter-mode.html#loiter-mode)
<iframe width="697" height="422" src="https://www.youtube.com/embed/yVAnBQkNJdY" title="Ardupilot:Copter V3.6.0 Release" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
* [RTL (Return-to-Launch) (返回原點模式)](https://ardupilot.org/copter/docs/rtl-mode.html#rtl-mode)
![](https://ardupilot.org/copter/_images/RTL.jpg)
* [Auto](https://ardupilot.org/copter/docs/auto-mode.html#auto-mode)
![](https://ardupilot.org/copter/_images/auto.jpg)

**Additional Flight Modes:**<br>
* [Acro (競技模式)](https://ardupilot.org/copter/docs/acro-mode.html#acro-mode)
  - Release the sticks and the vehicle will maintain its current attitude and will not return to level (attitude hold).
* [AirMode](https://ardupilot.org/copter/docs/airmode.html#airmode)
* [Heli_Autorotate (自旋)](https://ardupilot.org/copter/docs/traditional-helicopter-autorotation-mode.html#traditional-helicopter-autorotation-mode) for traditional helicopters only.
* [AutoTune (自調)](https://ardupilot.org/copter/docs/autotune.html#autotune)
  - automatically tune the Stabilize P, Rate P and D, and maximum rotational acceleration
* [Brake (煞停)](https://ardupilot.org/copter/docs/brake-mode.html#brake-mode)
* [Circle (繞圈)](https://ardupilot.org/copter/docs/circle-mode.html#circle-mode)
* [Drift (漂移)](https://ardupilot.org/copter/docs/drift-mode.html#drift-mode)
* [Flip (翻滾)](https://ardupilot.org/copter/docs/flip-mode.html#flip-mode)
* [FlowHold (穩停)] (https://ardupilot.org/copter/docs/flowhold-mode.html#flowhold-mode)
  - FlowHold mode uses an [optical flow sensor](https://ardupilot.org/copter/docs/common-optical-flow-sensors-landingpage.html#common-optical-flow-sensors-landingpage) to hold position without the need for a GPS nor a downward facing Lidar.
* [Follow (跟隨)](https://ardupilot.org/copter/docs/follow-mode.html#follow-mode)
* [Guided](https://ardupilot.org/copter/docs/ac2_guidedmode.html#ac2-guidedmode) (and Guided_NoGPS)
* [Land (著陸)](https://ardupilot.org/copter/docs/land-mode.html#land-mode)
* [PosHold (維持位置)](https://ardupilot.org/copter/docs/poshold-mode.html#poshold-mode)
* [Sport](https://ardupilot.org/copter/docs/sport-mode.html#sport-mode)
* [Throw (拋飛)](https://ardupilot.org/copter/docs/throw-mode.html#throw-mode)
* [Follow Me (跟著我)](https://ardupilot.org/copter/docs/ac2_followme.html#ac2-followme)
* [Simple and Super Simple](https://ardupilot.org/copter/docs/simpleandsuper-simple-modes.html#simpleandsuper-simple-modes)
![](https://ardupilot.org/copter/_images/NormalControls.jpg)
![](https://ardupilot.org/copter/_images/SimpleModeControls.jpg)
![](https://ardupilot.org/copter/_images/SuperSimpleControls.jpg)
* [Smart RTL (Return-to-Launch) 回發射點](https://ardupilot.org/copter/docs/smartrtl-mode.html#smartrtl-mode)
* [SysID (System Identification) 系統識別](https://ardupilot.org/copter/docs/systemid-mode.html#systemid-mode)
* [Turtle](https://ardupilot.org/copter/docs/turtle-mode.html#turtle-mode)
* [ZigZag](https://ardupilot.org/copter/docs/zigzag-mode.html#zigzag-mode)
![](https://ardupilot.org/copter/_images/zigzag-auto.png)
* [Avoid_ADSB](https://ardupilot.org/copter/docs/common-ads-b-receiver.html#common-ads-b-receiver)
  - ADS-B (aka Automatic Dependent Surveillance Broadcast) (自動相關監視廣播)
 
---
### Flight Features (飛行功能)
For a full set of features see the [full parameter list](https://ardupilot.org/plane/docs/parameters.html) and the [MAVLink protocol definition](https://mavlink.io/en/).
* [Automatic Takeoff (自動起飛)](https://ardupilot.org/plane/docs/automatic-takeoff.html) 
  - Hand Launching (手拋發射)
  - Catapult Launching (發射器發射)
  - Bungee Launching (蹦極發射)
  - Runway Takeoffs (跑道起飛)
  - Testing Ground Takeoff in FBWA mode (Fly By Wire_A mode)
  - Speed Scaling Issues with no Airspeed Sensor 
* [Automatic Landing (自動降落)](https://ardupilot.org/plane/docs/automatic-landing.html) 
  - Setting Flare point (設定閃光點)
  - Controlling the glide slope (控制下滑坡道)
  - Landing Airspeed (降落空速)
  - Controlling the approach (控制著近)
  - Controlling the Flare (控制拉平)
  - After the Flare (拉平之後)
  - Using a rangefinder (使用測距儀)
* [Inverted Flight (顛倒飛行)](https://ardupilot.org/plane/docs/inverted-flight.html)
* [Stall Prevention (失速預防)](https://ardupilot.org/plane/docs/stall-prevention.html)
* [Geo-Fencing in Plane (地理圍欄)](https://ardupilot.org/plane/docs/common-geofencing-landing-page.html)
* [Terrain Following (地形跟隨)](https://ardupilot.org/plane/docs/common-terrain-following.html)
  - see Copter specific [terrain following instructions](https://ardupilot.org/copter/docs/terrain-following.html#terrain-following) here.
  - The ground station is normally responsible for providing the raw terrain data which is sent to the aircraft via MAVLink.
  - Terrain following works by maintaining a terrain database on the microSD card on the autopilot which gives the terrain height in meters above sea level for a grid of geographic locations.  
* [Soaring (翱翔)](https://ardupilot.org/plane/docs/soaring-4_1.html) 
![](https://ardupilot.org/plane/_images/thermalling.jpg)
* [Automated Aerobatics (自動化特技飛行)](https://ardupilot.org/plane/docs/common-scripting-aerobatics.html)
  - ArduPilot has the capability of executing aerobatics from a [LUA script](https://ardupilot.org/plane/docs/common-lua-scripts.html#common-lua-scripts)
* [Moving Vehicle/Ship Takeoff/Landing (移動載台之起飛與降落)](https://ardupilot.org/plane/docs/common-ship-landing.html) 
  - To use this feature you need a **beacon** setup on the landing platform.
  - The beacon will be broadcasting its position to allow the QuadPlane to track its moving HOME position, similar to Copter’s [Follow Mode (跟隨模式)](https://ardupilot.org/copter/docs/follow-mode.html#follow-mode).
* [dual GPS blending](https://ardupilot.org/copter/docs/common-gps-blending.html)
<iframe width="697" height="422" src="https://www.youtube.com/embed/ieUD6FlxM-I" title="Drone With Tree (testing Dual GPS, Lidar, Optical Flow)" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
  
--- 
## Ground Control Station (地面控制站)
### [Mission Planner](https://ardupilot.org/planner/)
Mission Planner is a full-featured ground station application for the ArduPilot open source autopilot project.
![](https://ardupilot.org/planner/_images/mission_planner_flight_data.jpg)
![](https://ardupilot.org/planner/_images/mission_planner_screen_flight_plan.jpg)

---
## MAVlink
[Communicating with Raspberry Pi via MAVLink](https://ardupilot.org/dev/docs/raspberry-pi-via-mavlink.html)<br>
* Connect the flight controller’s TELEM2 port to the RPi’s Ground, TX and RX pin
![](https://ardupilot.org/dev/_images/RaspberryPi_Pixhawk_wiring1.jpg)

---
## 先進技術

### Quadcopter flies in areas without GPS signals
<iframe width="826" height="465" src="https://www.youtube.com/embed/gWtrka2mK7U" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### 混合動力無人機
* [混合動力無人機的發展](http://www.cie.org.tw/cms/JournalFiles/10912_chapter04.pdf) - 長榮大學無人機中心
![](https://github.com/rkuo2000/Robotics/blob/main/images/%E6%A9%9F%E9%9B%BB%E4%B8%A6%E8%81%AF%E5%BC%8F%E6%B7%B7%E5%90%88%E5%8B%95%E5%8A%9B%E7%B3%BB%E7%B5%B1.png?raw=true)
![](https://github.com/rkuo2000/Robotics/blob/main/images/%E5%BC%95%E6%93%8E%E5%90%8C%E8%BB%B8%E7%99%BC%E9%9B%BB%E6%A9%9F%E7%B5%84%E8%A3%9D%E4%B8%89%E8%A6%96%E5%9C%96.png?raw=true)

<br />
<br />

*This site was last updated {{ site.time | date: "%B %d, %Y" }}.*

