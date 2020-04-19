# Monkey Banana Problem

In this reality monkeys use fruits as money.Values:1 banana for 2 apples or 4 oranges or 10 peaches or 20 grapes.How many combination of fruit can a monkey get if it has x bananas at start?

ANSWER:

(define banana  '((apples 2) (oranges 4) (peaches 10) (grapes 20)))<br/>
(define apples  '((oranges 2) (peaches 4)))<br/>
(define peaches '((grapes 2)))<br/>

(define (monkey-calc n)<br/>
&emsp;(let* ((b (map (lambda (x)<br/>
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;(list (car x) (* n (cadr x))))<br/>
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;  banana))<br/>
&emsp;&emsp;&emsp;&emsp;(an (cadr (assoc 'apples b)))<br/>
&emsp;&emsp;&emsp;&emsp;(a  (map (lambda (x)<br/>
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; (list (car x) (* an (cadr x))))<br/>
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;    apples))<br/>
&emsp;&emsp;&emsp;&emsp;(pn (cadr (assoc 'peaches a)))<br/>
&emsp;&emsp;&emsp;&emsp;(p  (map (lambda (x)<br/>
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; (list (car x) (* pn (cadr x))))<br/>
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;    peaches)))<br/>
&emsp;   (displayln b)<br/>
&emsp;   (displayln a)<br/>
&emsp;   (displayln p)))<br/>


(monkey-calc 10)<br/>
;((apples 20) (oranges 40) (peaches 100) (grapes 200))<br/>
;((oranges 40) (peaches 80))<br/>
;((grapes 160))<br/>

(monkey-calc 50)<br/>
;((apples 100) (oranges 200) (peaches 500) (grapes 1000))<br/>
;((oranges 200) (peaches 400))<br/>
;((grapes 800))<br/>

(monkey-calc 100)<br/>
;((apples 200) (oranges 400) (peaches 1000) (grapes 2000))<br/>
;((oranges 400) (peaches 800))<br/>
;((grapes 1600))<br/>