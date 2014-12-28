---
layout: post
title: "An Algebra of Boxing Footwork"
category: Development
tags: ['personal', 'boxing', 'functional-programming']
---
{% include JB/setup %}

Back/Forward/Left/Right -> Motion
Back/Forward/Left/Right -> Orientation

t A
Fwd < A
Back < A

t B
Left < B
Right < B

t C
Right Foot Forward < C
Left Foot Forward < C


Fwd(A) && Right(B)
Back(A) && Left(B)

Fwd(A) && Left(B)
Back(A) && Right(B)

***AB/BA/C where A -> [Fwd/Back], B -> [Left/Right], 
  C -> [Right Foot Forward/Left Foot Forward]

Fwd, Back, Left, Right = F, B, L, R
Right Foot Fwd, Left Food Fwd = RFF, LFF

F/L/RFF
B/R/RFF

F/L/LFF
B/R/LFF

F/R/RFF
B/L/RFF

F/R/LFF
B/L/LFF

0/L/RFF
0/R/RFF

0/L/LFF
0/R/LFF

B/0/RFF
F/0/RFF

B/0/LFF
F/0/LFF
