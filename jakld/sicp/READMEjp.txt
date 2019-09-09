Scheme処理系JAKLDの図形言語搭載版について（2008/10/09 by T.Yuasa）

インストールとテストの方法

1. もしJava処理系が手元のマシンにインストールされていなければ，
　SunのJDKをダウンロードしてきてインストールする．

2. Jarファイルを適当なディレクトリに置く．
  （例えば，僕のMacなら /Users/taiichi/jakld とか）

3. 任意のディレクトリで

    % java -jar /Users/taiichi/jakld/jakld.jar

  としてJAKLDを起動する（Jar ファイルのパスは適当に）．
　もっと簡単にJAKLDを呼び出せるように，コマンド（aliasとかshortcutとか呼ばれる
　ことがあります）を定義しておくとよいです．僕自身は，次の１行を.bashrcに
　追加しています．

　  alias jakld="java -jar ~/bin/mac/jakld/jakld/jakld.jar"

4. 次の式を入力して，JAKLD Picture という名前の新しいウインドウが現れることを
　確認する．

    (start-picture)

　この描画ウインドウに図形が描画されます．

5. SICP 2.2.4 節で定義されているすべての関数は，上で start-picture を
　呼び出したときに定義されます．
　自分の好きな絵を描いてみてください．例えば，rogers.gif という画像ファイルを
　お持ちでしたら，次のようにすれば，その画像のための painter が生成されます．

　　(define rogers (image->painter "rogers.gif"))

　このドキュメントの末尾に役に立ちそうな参考プログラムを掲載しておきます．

6. 図形言語のための拡張機能のいくつかを簡単に紹介します．

　描画ウインドウを白紙に戻すには，(clear-picture)とします．
　描画ウインドウの背景色を変更するには，(set-bg-color 色指定)とし，
　線や多角形や点のデフォルト色を変更するには，(set-color 色指定)とします．
　ここで，色指定は，次のいずれかの記号

　　black, blue, cyan, dark-gray, gray, green, light-gray,
　　magenta, orange, pink, red, white, yellow

　または，三つの8ビットRGB値から構成される24ビット整数，例えば，

　　(set-color #xff0000)は，(set-color 'red)と同値です．

7. 描画ウインドウを閉じても，ウインドウが見えなくなるだけです．
　ウインドウを再度表示するには次の式を使います．

　  (show-picture)

　次の式を入力すれば，JAKLDの側からウインドウを隠すこともできます．

　  (hide-picture)

8. 描画した図形をファイルに保存するには，save-pictureという関数を使います．
　例えば，次の式は，指定したjpgファイルに図形を保存します．

     (save-picture "aaa.png")

　指定したファイル名のファイル・タイプが，図形を保存する形式を決定します．
　利用可能な保存形式は計算機環境に依存しますが，次の形式は試してみる価値が
　あります．

     bmp, jpeg, jpg, png

9. 次の関数は，描画ウインドウに現在表示されている図形を画像として保存し，
   その画像のための painter を生成します．
   
     (picture->painter)

10. 各ピクセルの色を指定して図形を描きたいときは，次の関数を使ってください．

     (procedure->painter F V)
     
   ここで，Fは１引数の関数です．引数は単位正方形内のx-y座標のペアでなければ
   なりません．つまり，0<=x<1，0<=y<1です．Fの返す値は，指定された点における
   RGB値として利用されます．
   Vは省略可能です．この引数が与えられた場合，procedure->painterは
   実行の進捗が分かるよう，１カラムの処理が終わるたびに星印（*）を表示します．
   標準の設定では，図形全体の処理が終わるまでに，512個の星印が表示される
   ことになります．計算に時間のかかる関数をFとして指定した場合に便利です．

11. JAKLDを終了するには，Control-Dを押します．

以下に，図形言語を初めて使う場合に役に立ちそうなコードを添付します．
rogers.gif というファイルは，次の web ページからダウンロードできます．

    http://mitpress.mit.edu/sicp/full-text/book/ch2-Z-G-30.gif

*********

(define rogers (image->painter "rogers.gif"))

;; The following code for wave was borrowed from
;; http://oss.timedia.co.jp/index.cgi/kahua-web/show/SICP/ex-2.49

(define wave
  (let ((p01 (make-vect 0.40 1.00))
        (p02 (make-vect 0.60 1.00))
        (p03 (make-vect 0.00 0.80))
        (p04 (make-vect 0.35 0.80))
        (p05 (make-vect 0.65 0.80))
        (p06 (make-vect 0.00 0.60))
        (p07 (make-vect 0.30 0.60))
        (p08 (make-vect 0.40 0.60))
        (p09 (make-vect 0.60 0.60))
        (p10 (make-vect 0.70 0.60))
        (p11 (make-vect 0.20 0.55))
        (p12 (make-vect 0.30 0.55))
        (p13 (make-vect 0.35 0.50))
        (p14 (make-vect 0.65 0.50))
        (p15 (make-vect 0.20 0.45))
        (p16 (make-vect 1.00 0.40))
        (p17 (make-vect 0.50 0.20))
        (p18 (make-vect 1.00 0.20))
        (p19 (make-vect 0.25 0.00))
        (p20 (make-vect 0.40 0.00))
        (p21 (make-vect 0.60 0.00))
        (p22 (make-vect 0.75 0.00)))
    (segments->painter
      (list (make-segment p01 p04)
            (make-segment p04 p08)
            (make-segment p08 p07)
            (make-segment p07 p11)
            (make-segment p11 p03)
            (make-segment p06 p15)
            (make-segment p15 p12)
            (make-segment p12 p13)
            (make-segment p13 p19)
            (make-segment p20 p17)
            (make-segment p17 p21)
            (make-segment p22 p14)
            (make-segment p14 p18)
            (make-segment p16 p10)
            (make-segment p10 p09)
            (make-segment p09 p05)
            (make-segment p05 p02)))))

(define letterlambda
  (vertexes->painter
    (list (make-vect .45 .6)
          (make-vect .25 .2)
          (make-vect .2 .2)
          (make-vect .2 .1)
          (make-vect .3 .1)
          (make-vect .5 .5)
          (make-vect .7 .1)
          (make-vect .8 .1)
          (make-vect .8 .2)
          (make-vect .75 .2)
          (make-vect .4 .9)
          (make-vect .3 .9)
          (make-vect .3 .8)
          (make-vect .35 .8))
    #t ;; fill inside the polygon?
    ))


(define (procedure-draw proc frame)
 (if (not (procedure? proc))
     (error "Argument not a procedure--PROCEDURE->PAINTER" proc) )
 (let ((step (/ 1.0 512.0)))
   (do ((i 0 (+ i 1)))
       ((> i 511))
     (do ((j 0 (+ j 1)))
         ((> j 511))
       (let ((x (* i step))
             (y (* j step)) )
         (if (proc x y)
             ((point->painter x y) frame )))))))

(define (circle frame)
  (procedure-draw
    (lambda (x y)
      (let ((r (+ (expt (- x 0.5) 2) (expt (- y 0.5) 2))))
        (and (>= r 0.249) (< r 0.251)) ))
    frame ))

(define (circle1 frame)
  (procedure-draw
    (lambda (x y)
      (let ((r (+ (* x x) (* y y))))
        (and (>= r 0.995) (< r 1.005)) ))
    frame ))



;; Standard frame
(define frm1 (make-frame (make-vect 0.0 0.0)
                         (make-vect 1.0 0.0)
                         (make-vect 0.0 1.0)))

;; Shearing frame
(define frm2 (make-frame (make-vect 0.0 0.0)
                         (make-vect 0.66 0.33)
                         (make-vect 0.33 0.66)))

;; Compress to left
(define frm3 (make-frame (make-vect 0.0 0.0)
                         (make-vect 0.5 0.0)
                         (make-vect 0.0 1.0)))

;; Compress to bottom
(define frm4 (make-frame (make-vect 0.0 0.0)
                         (make-vect 1.0 0.0)
                         (make-vect 0.0 0.5)))

(define (show painter . frame)
  (clear-picture)
  (painter (if (null? frame) frm1 (car frame))))

;; Figure 2.9

; (show (square-limit wave 4))
; (show (square-limit rogers 4))

;; Figure 2.10

; (show wave)
; (show wave frm2)
; (show wave frm3)
; (show wave frm4)

;; Figure 2.11

; (show rogers)
; (show rogers frm2)
; (show rogers frm3)
; (show rogers frm4)

;; Figure 2.12

; (define wave2 (beside wave (flip-vert wave)))
; (show wave2)
; (define wave4 (below wave2 wave2))
; (show wave4)

;; Figure 2.14

; (show (right-split wave 4))
; (show (right-split rogers 4))
; (show (corner-split wave 4))
; (show (corner-split rogers 4))

; (show letterlambda)
; (show letterlambda frm2)
; (show letterlambda frm3)
; (show letterlambda frm4)
; (show (right-split letterlambda 4))
; (show (corner-split letterlambda 4))

*********

以上です．健闘を祈ります．
