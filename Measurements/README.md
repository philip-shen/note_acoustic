Table of Contents
=================

   * [Table of Contents](#table-of-contents)
   * [Purpose](#purpose)
   * [Application Note: ヘッドホンの電気音響測定](#application-note-ヘッドホンの電気音響測定)
   * [Headphone, Earphone Frequency Response Measurements](#headphone-earphone-frequency-response-measurements)
      * [Sound Pressure Level Measurement System](#sound-pressure-level-measurement-system)
      * [Impedance Measurement System](#impedance-measurement-system)
      * [Noise Canceling Performance Measurement System](#noise-canceling-performance-measurement-system)
   * [ヘッドフォンの性能をチェックできるウェブサイト｢Audiocheck｣](#ヘッドフォンの性能をチェックできるウェブサイトaudiocheck)
      * [Frequency Response](#frequency-response)
      * [Spectral Flatness and Earbud Insert Test](#spectral-flatness-and-earbud-insert-test)
      * [Dynamic Range](#dynamic-range)
      * [Quality](#quality)
      * [Driver Matching](#driver-matching)
      * [Wiring](#wiring)
      * [Binaural Test](#binaural-test)
      * [Ultimately, listen to your favorite music...](#ultimately-listen-to-your-favorite-music)
   * [Frequency Response (周波数情報)](#frequency-response-周波数情報)
      * [背景](#背景)
      * [resampleの落とし穴](#resampleの落とし穴)
      * [fft内挿アルゴリズムinterpft](#fft内挿アルゴリズムinterpft)
   * [任意の周波数特性を持ったFIRフィルタの設計](#任意の周波数特性を持ったfirフィルタの設計)
   * [h1 size](#h1-size)
      * [h2 size](#h2-size)
         * [h3 size](#h3-size)
            * [h4 size](#h4-size)
               * [h5 size](#h5-size)
   * [Table of Contents](#table-of-contents-1)

Created by [gh-md-toc](https://github.com/ekalinin/github-markdown-toc)

# Purpose  
Take note Measurments of acoustic stuffs


# Application Note: ヘッドホンの電気音響測定  
[Application Note: ヘッドホンの電気音響測定](https://www.cornestech.co.jp/tech/wp-content/uploads/sites/2/2017/03/Audio-Precision-AppNote-Headphone-EA-Measurements-0617-JP.pdf)  

# Headphone, Earphone Frequency Response Measurements   
[ヘッドホン・イヤホン 周波数特性 測定結果 ](http://www.sam.hi-ho.ne.jp/t-suzuki/audio_headphones/measurement_system_201702.html)  
## Sound Pressure Level Measurement System
![alt tag](http://www.sam.hi-ho.ne.jp/t-suzuki/audio_headphones/img/headphone_spl_measurment_system_201805_w620.png)  

## Impedance Measurement System  
![alt tag](http://www.sam.hi-ho.ne.jp/t-suzuki/audio_headphones/img/headphone_imp_measurment_system_201405_w620.png)  

## Noise Canceling Performance Measurement System  
![alt tag](http://www.sam.hi-ho.ne.jp/t-suzuki/audio_headphones/img/headphone_nc_measurement_system_20170204.png)  

'''
測定は以下の4パターン行います。

(1) ノイズを止めた状態でヘッドホンを装着せず測定（ノイズフロアを確認）  
(2) ノイズ発生を発生させヘッドホンを装着せず測定（ノイズ量を測定）  
(3) ヘッドホンを装着しノイズキャンセリング機能オフで測定（遮音性能を測定）  
(4) さらにノイズキャンセリング機能オンで測定（アクティブ性能を測定）  
'''
[ノイズキャンセリングヘッドホンの性能測定を試みる 2017/02/08](https://dominant7th.blog.fc2.com/blog-entry-1372.html)
![alt tag](https://blog-imgs-100-origin.fc2.com/d/o/m/dominant7th/bose_quietcomfort35_nc_performance_lch.png)  

![alt tag](https://blog-imgs-100-origin.fc2.com/d/o/m/dominant7th/bose_quietcomfort35_nc_performance_rch.png)  



# ヘッドフォンの性能をチェックできるウェブサイト｢Audiocheck｣  
[ヘッドフォンの性能をチェックできるウェブサイト｢Audiocheck｣ 2017.09.18](https://www.lifehacker.jp/2017/09/170918-audiocheck-for-testing-your-headphones.html)  

[The Ultimate Headphones (and Earphones) Test](https://www.audiocheck.net/soundtests_headphones.php)
## Frequency Response  
## Spectral Flatness and Earbud Insert Test  
## Dynamic Range  
## Quality  
## Driver Matching  
## Wiring  
## Binaural Test  
## Ultimately, listen to your favorite music...  

# Frequency Response (周波数情報)  
[周波数情報を変化させないまま信号を補間する．updated at 2018-02-27](https://qiita.com/Y_F_Acoustics/items/bcf6d6705038dca9975f)  
## 背景  
'''
「あっ，いけね・・・この収録した信号，再生する際のサンプリング周波数が違う・・・」
「異なるサンプリング周波数でちゃんと再生するために補間したいな・・・」

「えいっ！！resample！！」

ちょい待って！！
'''
[resample](https://jp.mathworks.com/help/signal/ref/resample.html)  

## resampleの落とし穴

## fft内挿アルゴリズムinterpft  
'''
そこで，信号の周波数成分を壊さずに補間できるアルゴリズムとして，interpftをオススメします．

以下，引用
「interpft コマンドは FFT 法を使用します。元のベクトル x は、fft を使ってフーリエ領域に変換され、より多くのサンプル点を使って逆変換されます。」

つまり，「サンプルをフーリエ変換して周波数情報を取得し，サンプル間の信号を予測して内挿しますよ」ということです．
こちらも適用後の周波数特性を見ればわかるかと思いますが，本来ない周波数成分は平坦になるかと思います．
'''
[interpft/1 次元内挿 (FFT 法)](https://jp.mathworks.com/help/matlab/ref/interpft.html)  

# 任意の周波数特性を持ったFIRフィルタの設計  
'''
マイクで収録した音にFIRフィルタで周波数補正をかけたくなりました。FIRフィルタというとscipy.signal.firwinなどがありますが、今回は単純なローパスフィルタやハイパスフィルタではなく、複雑な周波数特性の実現を目指します。私はFIRフィルタの理論を深く理解しているわけではないので、間違っている箇所があると思います。そのときはコメントで教えていただけるとありがたいです。
'''
[やる夫で学ぶディジタル信号処理](http://www.ic.is.tohoku.ac.jp/%7Eswk/lecture/yaruodsp/main.html)


* []()  
![alt tag]()  

# h1 size

## h2 size

### h3 size

#### h4 size

##### h5 size

*strong*strong  
**strong**strong  

> quote  
> quote

- [ ] checklist1
- [x] checklist2

* 1
* 2
* 3

- 1
- 2
- 3
