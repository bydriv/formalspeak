```
NOUN ::= {I, me, we, us, you}
VERB ::= {am, are}

sentence ::= NOUN VERB
```

```sml
(* 人称 *)
type first
type second
type third

(* 単複 *)
type singular
type plural

(* 格 *)
type nominative
type objective

(* (人称, 単複, 格) noun *)
type ('a, 'b, 'c) noun

val I : (first, singular, nominative) noun
val me : (first, singular, objective) noun
val we : (first, plural, nominative) noun
val us : (first, plural, objective) noun

(* T & U で交叉型 *)
(* T & U <: T     *)
(* T & U <: U     *)
val you :
  (second, singular, nominative) noun
& (second, singular, objective) noun
& (second, plural, nominative) noun
& (second, plural, objective) noun

(* 文 *)
type sentence

(* 動詞 (自動詞) *)
type ('a, 'b, 'c) intransitive_verb = ('a, 'b, 'c) noun -> sentence

val am : (first, singular, nominative) intransitive_verb

val are :
  (first, plural, nominative) intransitive_verb
| (second, plural, nominative) intransitive_verb
```
