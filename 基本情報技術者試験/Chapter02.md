# ソフトウェアとマルチメディア
## 2-01 ソフトウェア
### OS
オペレーションシステム。ハードやアプリを管理・制御するソフトウェア  
<例>　mac OS,Windows,UNIX,Linux,Android,iOS

### 制御プログラム
ハードウェア資源の状態を常に監視して、コンピュータの効率的な利用を実現する  
<主な機能> ジョブ管理、タスク管理、記憶管理、ファイル管理、その他  

#### ハードウェア > OS > ミドルウェア > アプリケーションソフトウェア といった仕組み
- ミドルウェアとは?　　 
  DBMSなど。
 
### API（アプリケーション　プログラム　インターフェース）
アプリケーションから、OSが用意する各機能を利用するための仕組み

### デバイスドライバ
PCに接続した周辺機器を制御するソフトウェア
<具体例>　プリンタを接続するために、ドライバをインストールする作業

### プラグアンドプレイ
プラグを挿す駄kで必要な設定をしてくれる機能

### OSS
オープンソースソフトウェア　　
| 分類 | OSS |
| ---- | ---- |
| OS | Linux |
| オフィスツール | OpenOffice.org |
| データベース | MySQL |
| 統合開発環境 | Eclipse |
など

### OSSのライセンス
- BSD
  - 無保証
  - 改変後のアップロードは元の著作権表示やライセンス条文を記す事
- GPL
  - BSDの条件に加え、コピーレフトがある。
    - コピーレフトとは、ソフトウェアを独占せずに、みんなで改良して共有の財産にするという考えのもと成り立っており、頒布先にコードの開示が必要となる。

## ソフトウェアの確認問題
### 問題
1. デバイスドライバとは  
    ア:PCに接続された周辺機器を制御するソフトウェア

1. OSSの取り扱いについて正しいものを選択  
    イ:OSSを改変して再配布する場合、元にソフトウェアと同じ配布条件となるように、同じライセンスを適用して配布する必要がある。

### 正解
1. ア　○
2. エ　×  
    イ:自由に再配布可能。GPLの場合はこの条件が適用される。  
    エ:社内での利用のようにOSSを改変しても再配布しない場合、改変部分のソースコードを公開しなくても良い。
---
## 2-02ジョブ管理とタスク管理
- ジョブ  
利用者から見た仕事の単位
- タスク(プロセス)  
OSから見た仕事の単位

> スプーリング  
> とくれば  
> 出力データを磁気ディスクに書き込んでから出力する

### タスク管理
- 実行可能状態（CPU）
    CPUの使用権が割り当てられるのを待っている状態
- 実行状態
    CPUの使用権が割り当てられ、実行している状態
- 待ち状態(I/O)
    他のタスクが入出力装置を使用しているので、完了するのを待っている状態

> マルチタスク  
> とくれば  
> 見かけ上、複数のタスクを並行処理する

### タスクの実行方式
- ノンプリエンプティブ方式  
OSがCPUを管理せずプログラムに任せる方式
- プリエンプティブ方式  
OSがCPUを管理する

> 現在はプリエンプティブが主流

- マルチスレッド  
１つのプログラムの中で並行処理が可能な部分を、複数の処理単位(スレッド)に分解して、それらを並行して処理するOSの機能　　
マルチコアCPUを使用したコンピュータの処理能力を有効活用できる

- I/Oとは？  
Input/Outputの略で「入出力」を意味

- 割込み  
実行中のプログラムを一時中断し、制御プログラムに制御を移して、必要とする別の処理に切り替えること
  - 内部割り込み  
    実行中のプログラムが原因で起こる
    - ゼロによる除算（プログラム割込み）
    - SVC割り込み
  - 外部割り込み
      実行中のプログラム以外が原因で起こる
      - 電源異常（機械チェック割込み）
      - 入出力完了（入出力割込み）
      - プログラムの実行時間が設定時間を超過したとき（タイマ割込み）
- ポーリング制御
    割り込みに似た処理。  
    CPUが状態レジスタやビジー信号などを読み出して、入出力装置の状態を監視する方法
---
## 2-03 記憶管理
- フラグメンテーション  
細切れの未使用領域が発生する現象  
- メモリコンパクション  
フラグメンテーションを解決する方法  
- メモリリーク  
OSやアプリのバグが原因で、動作中の確保した主記憶領域が解放されず、主記憶中の利用可能な領域が減少してしまう現象  
プログラム終了後のメモリの解放のし忘れ
- ガーベジコレクション  
メモリリークの解消方法
> 仮想記憶方式  
> とくれば  
> 補助記憶の一部を主記憶に見せかけて、大きな記憶空間を作る方式 
- ページング方式  
主記憶とプログラムを固定長に分割し、このページ単位で管理する方式  
ページング方式を理解するのは引き出しのイメージが良い  
[引き出しのイメージ参照](https://wa3.i-3-i.info/word13352.html)

---

## 2-04 ファイル管理

- カレントディレクトリ  
現在操作対象となっているディレクトリ

- 絶対パス  
ルートディレクトリを基点に、目的となるディレクトリやファイルまでの経路を指定する  
例　/next/child/page.html

- 相対パス  
カレントディレクトリを基点に、目的となるディレクトリやファイルまでの経路を指定する  
例　CD => next  
child/page.html

> 1階層上のディレクトリに移動する  
> とくれば  
> ..

---

## 2-05 マルチメディア

> JPEG  
> とくれば  
> 静止画の国際標準規格

> MPEG  
> とくれば  
> 動画の国際標準規格

- ラスタデータ  
写真のようなピクセルの集まりで画像を表現する  
色の種類や明るさがピクセルごとに調節できる
<例> BMP GIF PNG JPEG

- ベクタデータ  
座標の位置や線分の長さなどを演算で表現する  
拡大しても図形の縁にジャギーが生じない
<例>　アウトラインフォント  

- SVG(Scalable Vector Graphics)  
画像フォーマット
大きさを変えられるベクター画像

### マルチメディアの応用
- CG  
- VR
- AR

- H.264/MPEG-4AVC  
ワンセグ放送で使用されている動画圧縮技術

- アンチエイリアシング  
液晶ディスプレイなどの表示装置において、傾いた直線の境界を滑らかに表示する手法
