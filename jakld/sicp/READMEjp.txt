Scheme$B=hM}7O(JJAKLD$B$N?^7A8@8lEk:\HG$K$D$$$F!J(J2008/10/09 by T.Yuasa$B!K(J

$B%$%s%9%H!<%k$H%F%9%H$NJ}K!(J

1. $B$b$7(JJava$B=hM}7O$,<j85$N%^%7%s$K%$%s%9%H!<%k$5$l$F$$$J$1$l$P!$(J
$B!!(JSun$B$N(JJDK$B$r%@%&%s%m!<%I$7$F$-$F%$%s%9%H!<%k$9$k!%(J

2. Jar$B%U%!%$%k$rE,Ev$J%G%#%l%/%H%j$KCV$/!%(J
  $B!JNc$($P!$KM$N(JMac$B$J$i(J /Users/taiichi/jakld $B$H$+!K(J

3. $BG$0U$N%G%#%l%/%H%j$G(J

    % java -jar /Users/taiichi/jakld/jakld.jar

  $B$H$7$F(JJAKLD$B$r5/F0$9$k!J(JJar $B%U%!%$%k$N%Q%9$OE,Ev$K!K!%(J
$B!!$b$C$H4JC1$K(JJAKLD$B$r8F$S=P$;$k$h$&$K!$%3%^%s%I!J(Jalias$B$H$+(Jshortcut$B$H$+8F$P$l$k(J
$B!!$3$H$,$"$j$^$9!K$rDj5A$7$F$*$/$H$h$$$G$9!%KM<+?H$O!$<!$N#19T$r(J.bashrc$B$K(J
$B!!DI2C$7$F$$$^$9!%(J

$B!!(J  alias jakld="java -jar ~/bin/mac/jakld/jakld/jakld.jar"

4. $B<!$N<0$rF~NO$7$F!$(JJAKLD Picture $B$H$$$&L>A0$N?7$7$$%&%$%s%I%&$,8=$l$k$3$H$r(J
$B!!3NG'$9$k!%(J

    (start-picture)

$B!!$3$NIA2h%&%$%s%I%&$K?^7A$,IA2h$5$l$^$9!%(J

5. SICP 2.2.4 $B@a$GDj5A$5$l$F$$$k$9$Y$F$N4X?t$O!$>e$G(J start-picture $B$r(J
$B!!8F$S=P$7$?$H$-$KDj5A$5$l$^$9!%(J
$B!!<+J,$N9%$-$J3($rIA$$$F$_$F$/$@$5$$!%Nc$($P!$(Jrogers.gif $B$H$$$&2hA|%U%!%$%k$r(J
$B!!$*;}$A$G$7$?$i!$<!$N$h$&$K$9$l$P!$$=$N2hA|$N$?$a$N(J painter $B$,@8@.$5$l$^$9!%(J

$B!!!!(J(define rogers (image->painter "rogers.gif"))

$B!!$3$N%I%-%e%a%s%H$NKvHx$KLr$KN)$A$=$&$J;29M%W%m%0%i%`$r7G:\$7$F$*$-$^$9!%(J

6. $B?^7A8@8l$N$?$a$N3HD%5!G=$N$$$/$D$+$r4JC1$K>R2p$7$^$9!%(J

$B!!IA2h%&%$%s%I%&$rGr;f$KLa$9$K$O!$(J(clear-picture)$B$H$7$^$9!%(J
$B!!IA2h%&%$%s%I%&$NGX7J?'$rJQ99$9$k$K$O!$(J(set-bg-color $B?';XDj(J)$B$H$7!$(J
$B!!@~$dB?3Q7A$dE@$N%G%U%)%k%H?'$rJQ99$9$k$K$O!$(J(set-color $B?';XDj(J)$B$H$7$^$9!%(J
$B!!$3$3$G!$?';XDj$O!$<!$N$$$:$l$+$N5-9f(J

$B!!!!(Jblack, blue, cyan, dark-gray, gray, green, light-gray,
$B!!!!(Jmagenta, orange, pink, red, white, yellow

$B!!$^$?$O!$;0$D$N(J8$B%S%C%H(JRGB$BCM$+$i9=@.$5$l$k(J24$B%S%C%H@0?t!$Nc$($P!$(J

$B!!!!(J(set-color #xff0000)$B$O!$(J(set-color 'red)$B$HF1CM$G$9!%(J

7. $BIA2h%&%$%s%I%&$rJD$8$F$b!$%&%$%s%I%&$,8+$($J$/$J$k$@$1$G$9!%(J
$B!!%&%$%s%I%&$r:FEYI=<($9$k$K$O<!$N<0$r;H$$$^$9!%(J

$B!!(J  (show-picture)

$B!!<!$N<0$rF~NO$9$l$P!$(JJAKLD$B$NB&$+$i%&%$%s%I%&$r1#$9$3$H$b$G$-$^$9!%(J

$B!!(J  (hide-picture)

8. $BIA2h$7$??^7A$r%U%!%$%k$KJ]B8$9$k$K$O!$(Jsave-picture$B$H$$$&4X?t$r;H$$$^$9!%(J
$B!!Nc$($P!$<!$N<0$O!$;XDj$7$?(Jjpg$B%U%!%$%k$K?^7A$rJ]B8$7$^$9!%(J

     (save-picture "aaa.png")

$B!!;XDj$7$?%U%!%$%kL>$N%U%!%$%k!&%?%$%W$,!$?^7A$rJ]B8$9$k7A<0$r7hDj$7$^$9!%(J
$B!!MxMQ2DG=$JJ]B87A<0$O7W;;5!4D6-$K0MB8$7$^$9$,!$<!$N7A<0$O;n$7$F$_$k2ACM$,(J
$B!!$"$j$^$9!%(J

     bmp, jpeg, jpg, png

9. $B<!$N4X?t$O!$IA2h%&%$%s%I%&$K8=:_I=<($5$l$F$$$k?^7A$r2hA|$H$7$FJ]B8$7!$(J
   $B$=$N2hA|$N$?$a$N(J painter $B$r@8@.$7$^$9!%(J
   
     (picture->painter)

10. $B3F%T%/%;%k$N?'$r;XDj$7$F?^7A$rIA$-$?$$$H$-$O!$<!$N4X?t$r;H$C$F$/$@$5$$!%(J

     (procedure->painter F V)
     
   $B$3$3$G!$(JF$B$O#10z?t$N4X?t$G$9!%0z?t$OC10L@5J}7AFb$N(Jx-y$B:BI8$N%Z%"$G$J$1$l$P(J
   $B$J$j$^$;$s!%$D$^$j!$(J0<=x<1$B!$(J0<=y<1$B$G$9!%(JF$B$NJV$9CM$O!$;XDj$5$l$?E@$K$*$1$k(J
   RGB$BCM$H$7$FMxMQ$5$l$^$9!%(J
   V$B$O>JN,2DG=$G$9!%$3$N0z?t$,M?$($i$l$?>l9g!$(Jprocedure->painter$B$O(J
   $B<B9T$N?JD=$,J,$+$k$h$&!$#1%+%i%`$N=hM}$,=*$o$k$?$S$K@10u!J(J*$B!K$rI=<($7$^$9!%(J
   $BI8=`$N@_Dj$G$O!$?^7AA4BN$N=hM}$,=*$o$k$^$G$K!$(J512$B8D$N@10u$,I=<($5$l$k(J
   $B$3$H$K$J$j$^$9!%7W;;$K;~4V$N$+$+$k4X?t$r(JF$B$H$7$F;XDj$7$?>l9g$KJXMx$G$9!%(J

11. JAKLD$B$r=*N;$9$k$K$O!$(JControl-D$B$r2!$7$^$9!%(J

$B0J2<$K!$?^7A8@8l$r=i$a$F;H$&>l9g$KLr$KN)$A$=$&$J%3!<%I$rE:IU$7$^$9!%(J
rogers.gif $B$H$$$&%U%!%$%k$O!$<!$N(J web $B%Z!<%8$+$i%@%&%s%m!<%I$G$-$^$9!%(J

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

$B0J>e$G$9!%7rF.$r5'$j$^$9!%(J
