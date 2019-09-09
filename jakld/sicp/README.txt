Scheme System JAKLD with Picture Language (2008/10/09 by T.Yuasa)

How to install:and test

1. If no Java VM is installed on your machine, download Sun JDK and
   install it.

2. Put the Jar file in whatever directory you like.
   (e.g., /Users/taiichi/jakld for my Mac)

3. You can invoke JAKLD, at any directory, by:

     % java -jar /Users/taiichi/jakld/jakld.jar

   It is a good idea to define a handy commend (sometimes called an alias or
   a shortcut) to invoke JAKLD.  I myself put the following line in the file
   ".bashrc".

     alias jakld="java -jar ~/bin/mac/jakld/jakld/jakld.jar"

4. Try the following expression and see whether a new window, named
   "JAKLD Pictures", appears on your display.

     (start-picture)

   The window is the one on which pictures are drawn.

5. All the functions defined in SICP Section 2.2.4 ("Example: A Picture
   Language") will already be defined when you invoked "start-picture".
   Draw whatever pictures you want.  For example, if you have a picture
   file "rogers.gif", the following expression will define a "painter" for
   the picture.

     (define rogers (image->painter "rogers.gif"))

   You can find a sample program at the end of this document.

6. Here are some extended functions for drawing pictures.

   You can clear the drawing window by

     (clear-picture)

   You can change the color of the backgroud by

     (set-bg-color color)

   and the default color of lines, polygons, and points by

     (set-color color)

   where color may be one of the following symbols:

     black, blue, cyan, dark-gray, gray, green, light-gray,
     magenta, orange, pink, red, white, yellow

   or it may be a 24-bit integer composed of three 8-bit RGB values.
   For example,

     (set-color #xff0000) has the same effect as (set-color 'red) does. 

7. When you close the drawing window, it just hides itself.  In order to
   make it appear again, type

     (show-picture)

   You can also hide the drawing window from JAKLD by:

     (hide-picture)

8. If you want to save the picture, use the function "save-picture".
   For example, the following expression saves the picture into the
   specified jpg file.

     (save-picture "aaa.png")

   The file type in the specified file name determines the format of the
   saved picture.  The set of available formats depends on the machine
   environment, but the following formats are worth trying.

     bmp, jpeg, jpg, png, 

9. The following function saves the current picture in the drawing window
   as an image and creates a painter for the image.
   
     (picture->painter)

10. If you want to draw a picture by specifying the color of each pixcel,
   use the following function.
   
     (procedure->painter F V)

   F is a function with a single argument.  The argument must be a pair of
   x-y cordinates within the unit square (i.e., 0<=x<1, 0<=y<1).  F is
   expected to return the RGB value at the specified point.
   V is an optional argument which requests the "verbose" mode.
   If V is given, procedure->painter displays a "*" each time it finishes
   computing one column of the picture.  With the default settings, you may
   see about 512 starts while procedure->painter is computing the entire
   picture.  This mode is usefule when you specify a complex function for F.

11. To exit JAKLD, type Control-D.  

The following code may be useful.to enjoy first experience with 
the picture language.  The file "rogers.gif" can be downloaded from
the following web page:

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

That's it.  Good luck.
