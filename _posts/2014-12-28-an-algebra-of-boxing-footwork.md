---
layout: post
title: "An Algebra of Boxing Footwork"
category: Development
tags: ['personal', 'boxing', 'functional-programming']
---
{% include JB/setup %}

Been studying Scala algebras lately. Let this inform my workouts.

Back/Forward/Left/Right -> Motion
Back/Forward/Left/Right -> Orientation

t A
Fwd < A
Back < A

t B
Left < B
Right < B


Fwd(A) && Right(B)
Back(A) && Left(B)

Fwd(A) && Left(B)
Back(A) && Right(B)

**==**==** AB/BA where A -> [Fwd/Back], B -> [Left/Right] **==**==**

Fwd, Back, Left, Right = F, B, L, R

F/L
B/R

F/R
B/L

0/L
0/R

B/0
F/0
