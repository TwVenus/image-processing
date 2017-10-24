# image processing
##### 本程式為基本數位影像處理之方法，其中幫包含：
- Gray(彩圖轉灰階)
- Gamma Correction: 0.5 、 1 、 2
- Invert(負片)
- Otus(二值化)
- Salt and Pepper(胡椒鹽炸雜訊)
- Mean filter
- Median filter
- Sobel
---
#### 原圖影像
&emsp; &emsp; ![original](https://i.imgur.com/KakCeTm.jpg)

#### (一)、Gray
``` 
原理：彩色轉灰階的過程應該是灰階 = (紅+綠+藍)/3。但實際上人眼對綠色的亮度感最大，而對藍色最小，於是Gray = 0.299 * Red + 0.587 * Green + 0.114 * Blue才能得到比較適合人類眼睛的灰階影像。
```
##### 執行結果：
&emsp; &emsp; ![gray](https://i.imgur.com/QrbwrTm.jpg)

#### (二)、Gamma Correction
``` 
公式：(((pixels-min(pixels))/(man(pixels)-min(pixels)))^gamma)*255
Gamma取大：凸顯亮，圖變暗
Gamma取小：凸顯暗，圖變亮
```
##### 執行結果一： (Gamma:0.5)
 &emsp; &emsp; ![gamma0.5](https://i.imgur.com/Jeaqdio.jpg)

##### 執行結果二： (Gamma:2)
&emsp; &emsp; ![Gamma:2](https://i.imgur.com/Ux0sDQE.jpg)

#### (三)、Invert
``` 
原理：255 – 原本的灰階度。
```
##### 執行結果：
&emsp; &emsp; ![invert](https://i.imgur.com/V8PNirs.jpg)

#### (四)、Otus
``` 
原理：整張圖的平均值作為門檻值，大於該值測該灰階度設為 255，小於門檻值設為 0。
```
##### 執行結果：
&emsp; &emsp; ![oyus](https://i.imgur.com/sy0O4Gm.jpg)

#### (五)、Salt and Pepper
``` 
原理：對所有 pixel 做 random(0~9) ， 如果是 9 給黑色的雜訊，如果是 0 給白色的雜訊。
```
##### 執行結果：
&emsp; &emsp; ![salt and pepper](https://i.imgur.com/Y8wKDWp.jpg)

#### (六)、Mean filter
``` 
原理：取(3 x 3) windows 並對整張 Salt and Pepper圖 做處理，將 windows 中所有數字平均取代中間的 pixel。 (會出現模糊問題)
```
##### 執行結果：
&emsp; &emsp; ![mean filter](https://i.imgur.com/FwBi5GE.jpg)

#### (七)、Median filter
``` 
原理：取(3 x 3) windows 並對整張 Salt and Pepper圖 做處理，將 windows 第四大的值數字取代中間 pixel。 (去 salt and pepper 的問題連良好)
```
##### 執行結果：
&emsp; &emsp; ![median](https://i.imgur.com/1dgbGlb.jpg)

#### (八)、Sobel
``` 
原理：該算子包含兩組3x3的矩陣，分別為橫向及縱向，將之與圖像作平面卷積，即可分別得出橫向及縱向的亮度差分近似值。其矩陣如下：
```
&emsp; &emsp; &emsp; &emsp; &emsp; ![](https://i.imgur.com/dD6bDol.png)
```
圖像的每一個像素的橫向及縱向梯度近似值可用以下的公式結合，來計算梯度的大小。
```
&emsp; &emsp; &emsp; &emsp; &emsp; ![](https://i.imgur.com/SZodhQ6.png)
```
然後可用以下公式計算梯度方向。
```
&emsp; &emsp; &emsp; &emsp; &emsp; ![](https://i.imgur.com/DPwqyLm.png)

##### 執行結果：
&emsp; &emsp; ![sobel](https://i.imgur.com/lzQrDzp.jpg)




