## Chapter 2

### Installing GHC on Mac

```
brew install haskell-stack
stack setup
stack ghci
```

### Comprehension Check

1. `let half x = x / 2`


### Exercises: A Head Code

1. `let x = 5 in x` -> 5
2. `let x = 5 in x * x` -> 25
3. `let x = 5; y = 6 in x * y` -> 30
4. `let x = 3; y = 1000 in x + 3` -> 6

### Exercises with `let` and `where`

Rewrite the following `let` expressions into declarations with `where` clauses:

`let x = 3; y = 1000 in x * 3 + y` ->  

```
answer = x * 3 + y 
	where x = 3
	 	  y = 1000
```




`let y = 10; x = 10 * 5 + y in x * 5` ->
```
answer = x * 5
	where y = 10
	      x = 10 * 5 + y
```

`let x = 7; y = negate x; z = y * 10 in z / x + y` ->
```
answer = z / x + y
	where x = 7
		   y = negate x
		   z = y * 10
```

