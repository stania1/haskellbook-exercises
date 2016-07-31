
## Chapter 1

### Intermission: Equivalence Exercises

1. 𝜆𝑥𝑦.𝑥𝑧 - Answer: b) 𝜆𝑚𝑛.𝑚𝑧
2. 𝜆𝑥𝑦.𝑥𝑥𝑦 - Answer: c) 𝜆𝑎(𝜆𝑏.𝑎𝑎𝑏)
3. 𝜆𝑥𝑦𝑧.𝑧𝑥 - Answer: b) 𝜆𝑡𝑜𝑠.𝑠𝑡

### Chapter Exercises

#### Combinators

1. 𝜆𝑥.𝑥𝑥𝑥 - Answer: combinator2. 𝜆𝑥𝑦.𝑧𝑥 - Answer: not a combinator (z is a free variable)3. 𝜆𝑥𝑦𝑧.𝑥𝑦(𝑧𝑥) - Answer: combinator4. 𝜆𝑥𝑦𝑧.𝑥𝑦(𝑧𝑥𝑦) - Answer: combinator5. 𝜆𝑥𝑦.𝑥𝑦(𝑧𝑥𝑦) - Answer: not a combinator (z is a free variable)#### Normal form or diverge?Normal form: it's been beta-reduced to the simplest form possible.  
Divergence: when the reduction process never terminates.  

These are two ends of the spectrum, but there's more: there are also lambda expressions that are still reducible, i.e. not normal form, but not a divergence either.1. 𝜆𝑥.𝑥𝑥𝑥 - Answer: normal form2. (𝜆𝑧.𝑧𝑧)(𝜆𝑦.𝑦𝑦). Answer: diverge3. (𝜆𝑥.𝑥𝑥𝑥)𝑧. Answer: normal form

#### Beta reduce 

Evaluate (that is, beta reduce) each of the followingexpressions to normal form. We strongly recommend writing outthe steps on paper with a pencil or pen.

##### Problem 1

```
(𝜆𝑎𝑏𝑐.𝑐𝑏𝑎)𝑧𝑧(𝜆𝑤𝑣.𝑤)   
(𝜆𝑎(𝜆𝑏(𝜆𝑐.𝑐𝑏𝑎)))𝑧𝑧(𝜆𝑤(𝜆𝑣.𝑤))   // just making the currying explicit
[a := z]
(𝜆𝑏(𝜆𝑐.𝑐𝑏𝑧))𝑧(𝜆𝑤(𝜆𝑣.𝑤))
[b := z]
(𝜆𝑐.𝑐𝑧𝑧)(𝜆𝑤(𝜆𝑣.𝑤))
[c := (𝜆𝑤(𝜆𝑣.𝑤))]
(𝜆𝑤(𝜆𝑣.𝑤))𝑧𝑧
[w := z]
(𝜆𝑣.𝑧)𝑧
[v := z] // no effect, v not used in the body
𝑧
```

##### Problem 2

```
(𝜆𝑥.𝜆𝑦.𝑥𝑦𝑦)(𝜆𝑎.𝑎)𝑏
[ x := (𝜆𝑎.𝑎) ]
(𝜆𝑦.(𝜆𝑎.𝑎)𝑦𝑦)𝑏
[ y := b ]
(𝜆𝑎.𝑎)𝑏𝑏
[ a := b ]
𝑏𝑏
```

##### Problem 3

```
(𝜆𝑦.𝑦)(𝜆𝑥.𝑥𝑥)(𝜆𝑧.𝑧𝑞)
[ y := (𝜆𝑥.𝑥𝑥) ] // the first lambda is an identity function
(𝜆𝑥.𝑥𝑥)(𝜆𝑧.𝑧𝑞)
[ x := (𝜆𝑧.𝑧𝑞) ]
(𝜆𝑧.𝑧𝑞)(𝜆𝑧.𝑧𝑞)
[ z := (𝜆𝑧.𝑧𝑞) ]
(𝜆𝑧.𝑧𝑞)𝑞
[ z := q ]
𝑞𝑞
```

##### Problem 4

```
(𝜆𝑧.𝑧)(𝜆𝑧.𝑧𝑧)(𝜆𝑧.𝑧𝑦) // Hint: alpha equivalence.
[ z := (𝜆𝑧.𝑧𝑧) ] // the first lambda is an identity function
(𝜆𝑧.𝑧𝑧)(𝜆𝑧.𝑧𝑦)
[ z := (𝜆𝑧.𝑧𝑦) ]
(𝜆𝑧.𝑧𝑦)(𝜆𝑧.𝑧𝑦)
[ z := (𝜆𝑧.𝑧𝑦) ]
(𝜆𝑧.𝑧𝑦)𝑦
[ z := y ]
𝑦𝑦
```

##### Problem 5

```
(𝜆𝑥.𝜆𝑦.𝑥𝑦𝑦)(𝜆𝑦.𝑦)𝑦
[ x := (𝜆𝑦.𝑦) ]
(𝜆𝑦.(𝜆𝑦.𝑦)𝑦𝑦)𝑦
[ y := y ]
(𝜆𝑦.𝑦)𝑦𝑦
[ y := y ]
𝑦𝑦
```

##### Problem 6

```
(𝜆𝑎.𝑎𝑎)(𝜆𝑏.𝑏𝑎)𝑐
[ a := (𝜆𝑏.𝑏𝑎) ]
(𝜆𝑏.𝑏𝑎)(𝜆𝑏.𝑏𝑎)𝑐 
[ b := (𝜆𝑏.𝑏𝑎) ]
(𝜆𝑏.𝑏𝑎)𝑎𝑐 
[ b := a] 
𝑎𝑎𝑐 
```

##### Problem 7

```
(𝜆𝑥𝑦𝑧.𝑥𝑧(𝑦𝑧))(𝜆𝑥.𝑧)(𝜆𝑥.𝑎)
[ x := (𝜆𝑥.𝑧) ]
(𝜆𝑦𝑧1.(𝜆𝑥.𝑧)𝑧1(𝑦𝑧1))(𝜆𝑥.𝑎)
[ y := (𝜆𝑥.𝑎) ]
(𝜆𝑧1.(𝜆𝑥.𝑧)𝑧1((𝜆𝑥.𝑎)𝑧1)
[ x := z1 ]
(𝜆𝑧1.(𝑧((𝜆𝑥.𝑎)𝑧1)
[ x := z]
(𝜆𝑧1.𝑧𝑎)
```
