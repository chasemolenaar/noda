# Noda
An Array-Oriented, OOP, FP, and Logical Programming Language for Concise Pseudocode-like Scalability

'Noda' is the faux-pluralization of the Latin word 'nodum', meaning 'knot'. It was named after the topological subfield of Knot Theory. Though many introduced to the language seem convinced it means "No duh!", which is equally accurate. ~~where I have conducted heavy research into devising an algorithm to solve the infamous Unknotting Problem. Neither Python nor Julia were up to the task, so I devised a new language.~~

Noda is ambitious. It seeks to bring the concision and power of array languages like APL to the readability and friendliness of Python. To make so accessible functional programming constructs like map-filter-reduce they seem trivial to kindergarteners. To popularize Prolog-like logical deduction for an evermore AI-driven world. To devise a language that is fun to write, quick to type, cool to look at, and pleases beginners and experts alike.

It is a language designed by Data Scientists, for Data Scientists.

Hook the reader in with some twist, some draw to Noda's design. Why it's different, better than Python or other languages. Why it's powerful, terse, scalable. Something they can grasp quickly, without thinking.

Feature correspondent/equivalent Python code shown everywhere along the way, so the user is never confused as to what your syntax does.

Why does terseness matter? Why it isn't everything.

Features/Ambitions—
[](#table-of-contents)
|                |  |
| --------------------- | ----------------------------------------------------------------------------------------------------------------- |
| **Out-of-the-Box:**	|Makes commonplace Python packages like Pandas, Numpy, PyTorch, and regex *first-class*
| **4 Paradigms in 1:**	|Evolves Python by stealing from Array (APL), Logical (Prolog), OOP (Smalltalk), and Functional (Haskell) paradigms
| **ML Oriented:**	|Prioritizes linear algebra, rank polymorphism, and tabular data manipulation (including JSONs/dataframes)
| **Logic Oriented:**|Has Prolog-inspired capabilities like unification, backtracking, and recursion
| **Functional Support:** |Supports functional constructs like maps, filters, pipes, predicates, structs, and functors
| **Object Oriented:**  |Shamelessly adopts Smalltalk's OOP, control-flow mechanisms, and custom keyword creation
| **Pattern Matching:**	|Expands regex-like pattern matching to the language at large (for every data structure)
| **SQL Databasing:**	|Interfaces with SQL seamlessly and makes relational operations first-class
| **Writable:**	      |Takes 1/3 the strokes and 1/3 the time to script with compared to Python
| **Readable:**	      |Inspired by APLs but still feels largely like Python/Numpy
| **Metaprogramming:**	|Enables LISP-like macros and metaprogramming
| **Optionally Typed:**	|Optionally typed, to satisfy both dynamic and static programmers alike
| **Quick Runtimes:**	|Lightning fast, with multiple dispatch baked into every calculation



Explanation of awesome, terse examples, with equivalent Python and APL code to match.

We need a showcase of every operator's usages :)

Expectations— 
Let `°` represent any operator, `//` and `/* */` enclose comments, code comparisons to Python will be written in tandem (to be completed).

OPERATOR OVERVIEW—

[](#table-of-contents)
| Family | Operators |
| ------ | --------- |
| Arithmetic | `+ - * / \ ^ % ^/ /\ \/ +*`
| Assignment | `= °= := ::= :=: =< =>`
| Comparison | `> < >= <= == != === !== %%` 
| Conditional | `: ><: ?: :: ; ;;`
| String | `-< +< >-< ~= !~`
| Array | `++ -- ** ^^ ,, \\ << >>`
| Modifiers | `~ % ^ * ** \ . +- -+`
| Membership | `# @ $ >-> <-<`
| Boolean | `! !! ? ?? && \|\|`
| Logic | `! & \| >< -> <->`
| Pattern | `: _ * + ? ?= ?! +- -+` 
| Combinator | `!° ~° .° <>° °: °&° °\|° ?°`
| Relational | `~< ~> >=< >=> <=< <=>`
| Keywords | `for while in of if elif then else`

\*The degree symbol `°` is used to indicate \[*insert any operator*\].

RANK POLYMORPHISM

#### Core Ideas
1. Noda

Noda targets both a Python audience. Noda is heavily inspired by Python, so it's safe to assume that constructs will look like Python if unspecified.
This tutorial assumes you know some Python....

#### Ground Rules
1. Noda indexes by 0, which is the superior choice
2. Noda is indentation sensitive, like Python
3. 

#### Basic Data Structures

[](#table-of-contents)
| empty | type | instance | notes |
| ----- | ---- | -------- | ----- |
| `()` | tuple | `(1,2,3,4)` | immutable list
| `{}` | set | `{1,2,3,4}` | unordered
| `[)` | ring | `[1,2,3,4,5)` | loops on itself
| `[]` | array | `[1,2,3,4,5]` | n-dimensional array
| `:` | slice | `1:4` | like range(1,4)
| `{}` | dict | `{"a": 1, "b": 2}` | dict and dataframe

Sets `{}` and tuples `()` behave similarly to Python——sets are unordered, tuples are immutable. Rings `[)` are like lists, but loop back on themselves and can be indexed anywhere: `[0,1,2,3)[4] == [0,1,2,3)[0] == 0`. Slices are denoted with `a:b` and are inclusive by default: `1:4 == 1,2,3,4`. To enforce exclusivity, use brackets `[]` for inclusive, parens `()` for exclusive: 
```csharp
[1:4] == [1,2,3,4]   // inclusive / inclusive
[1:4) == [1,2,3]     // inclusive / exclusive
(1:4] == [2,3,4]     // exclusive / inclusive
(1:4) == [2,3]       // exclusive / exclusive
[:3] == [0,1,2,3]    // slices start at 0
(:3] == [1,2,3]      // exclusive of 0
[0:] == [0,1,2..]    // infinite slice
[1:2:7] == [1,3,5,7] // start:step:end
[1:2:] == [1,3,5..]  // odd numbers
[:2:] == [0,2,4..]   // even numbers
```

```csharp
[


```
All arrays/lists `[]` are n-dimensional arrays, and mimic the conventions of Numpy/Pytorch/Tensorflow. Likewise, all dicts are dataframes and mimic many of the conventions of Pandas. Both may be indexed along each dimension:
```
X = [[1,2,3],[4,5,6]]
X[1]                     // 2nd row
>>>      [4,5,6]           
X[:,0]                   // 1st column
>>>      [[1],[4]]      
X[:,0:1]                 // 1st & 2nd column
>>>      [[1,2],[4,5]]  

df = {"team":    ["A","A","A","A","B","B","B","B"]
      "points":  [ 5,  7,  7,  9,  12, 9,  9,  4 ]
      "assists": [ 11, 8,  10, 6,  6,  5,  9,  12]}

df[:,:3]    
      {"team":    ["A","A","A","A"]
      "points":   [ 5,  7,  7,  9 ]
      "assists":  [ 11, 8,  10, 6 ]}
```

#### Arithmetic

[](#table-of-contents)
| op  | name | instance | notes |
| --- | ----- | ------- | ----- |
| `+` | plus  | `2 + 3 == 5` | addition
| `-` | minus | `2 - 3 == -1` | subtraction
| `*` | times | `2 * 3 == 6` | multiplication
| ` ` | coef  | `9n == 9 * n` | literal numeric coefficients
| `/` | divide | `3 / 6 == 0.5` | division
| `\` | floordiv | `11 \ 5 == 2` | floor division
| `%` | modulo | `11 % 5 == 1` | modulo remainder
| `^` | power | `2 ^ 3 == 8` | exponent
| `^/`| root | `3^/125 == 5` | nth root of number
| `!!`| choose | `4 !! 2 == 6` | n-choose-k
| `/\`| max | `4 /\ 5 == 5` | maximum value
| `\/`| min | `4 \/ 5 == 4` | minimum value

* Times `*`, division `/`, and power `^` are matrix operations on arrays
* Floordiv `\` becomes left divide on arrays (linear solution to `Ax = B` using `x = A\B`)
* Reciprocal `/` returns the inverse of a square matrix 

-----------------------------------------------------------------------------------------------

[](#table-of-contents)
| op  | name | instance | notes |
| --- | ----- | ------- | ----- |
| `+` | plus  | `+4 == 4` | positive
| `-` | minus | `-4 == -4` | negative
| `/` | divide | `/5 == 1/5 == 0.2` | reciprocal
| `^/`| root | `^/36 == 6` | square root
| `!!`| choose | `!!4 == 24` | factorial
| `/\`| max | `/\[0,2,1] == 2` | maximum value
| `\/`| min | `\/[0,2,1] == 0` | minimum value

* Plus `+` and minus `-` convert strings into ints/floats: `+"123" == 123`
* Juxtaposition multiplies functions: `f(x)g(x) == f(x)*g(x)`
* Factorials of floats return Gamma function values `Γ(n-1)`
* Max and min return the lexically greater/less string: `"apple" /\ "banana" == "banana"`

#### Comparison

[](#table-of-contents)
| op  | name | instance | notes |
| --- | ----- | ------- | ----- |
| `>` | greater | `3 > 2` | greater than
| `<` | less | `2 < 3` | less than
| `>=` | greater/equal | `3 >= 2` | greater or equal
| `<=` | less/equal  | `2 <= 3` | less or equal
| `==` | equal | `1 == 1.0` | equality (of value)
| `!=` | unequal | `1 != 1.5` | inequality (of value)
| `%%` | divisible | `20 %% 5` | remainder is 0
| `!%` | indivisible | `23 !% 5` | remainder is !0
| `===`| equivalence | `1.0 === 1.0` | same objects
| `!==`| inequivalence | `1 !== 1.0` | different objects

* Strings do lexical value comparison: `"apple" < "banana"`
* All equality comparisons are elementwise on arrays: `[1,2,3] == [1,0,3]` is `[true,false,true]`
* Equivalence `===` compares object equality *as a whole*: `[1,2,3] === [1,0,3]` is `false`

#### Strings
[](#table-of-contents)
| empty | type | instance | notes |
| ----- | ---- | -------- | ----- |
| `""` | string | `"Hi {name}!"` | All strings are fstrings
| `''` | regex | `'\d+'` | Matches "42069"
| ``` `` ``` | raw | ``` `"wow!"\\''` ``` | No escape sequences

* All strings are fstrings by default
* Escape braces using `\{` and `\}`
* Raw strings contain no escape sequences: ```filepath = `C:\Documents\Scripts\Test.py` ```
* Regexes patterns follow the PRCE standard (same as Python and C)
* Multiline strings can be written without using triple quotes. Use `\` to escape newline
* Use triple quotes `"""` to easily escape `"` from text

[](#table-of-contents)
| op | name | instance | notes |
| -- | ----- | ------- | ----- |
| `*`  | concat    |`"wind" * "mill" == "windmill"`         | concatenates strings
| `^`  | repeat    |`"no" ^ 4 == "nononono"`                | repeats string
| `/`  | remove    |`"workmanship" / "kman" == "worship"`   | removes substring everywhere
| `\`  | before    |`"try-method-x" \ "method" == "try-"`   | retains text before 1st substring
| `%`  | remainder |`"try-method-x" % "method" == "-x"`     | retains text after 1st substring
| `-<` | split     |`"2/14/23" -< "/" == ["2","14","23"]`   | splits on pattern (remove delimiter)
| `+<` | snip      |`"2/14/23" +< "/" == ["2/","14/","23"]` | snips on pattern (keep delimiter)
| `>-<`| join      |`["a","b","c"] >-< ":" == "a:b:c"`      | joins strings by delimiter
| `~=` | match     |`'\d+\.\d+' ~= "420.69"`                | checks if regex matches string
| `!~` | unmatch   |`'\d+\.\d+' !~ "1_000"`                 | checks if regex doesn't match string

* Literal concatenation of strings is valid: `"wind""mill" == "windmill"`
* Right argument tuples limit to n-times: `"split, me, up" -< (", ", 1) == ["split", "me, up"]`
* Unary `-<` splits on whitespace: `-<"Jane\n S Smith" == ["Jane", "S", "Smith"]`
* Unary `>-<` joins without space: `>-<["a","b","c"] == "abc"`
* Binary `>-<` lists together too: `["Okay", "but", "why"] >-< [", ", " ", "?"] == "Okay, but why?"`

Match operators `~=` and `!~` check whether a regex pattern matches a string. 

#### Assignment
[](#table-of-contents)
| op | name | instance | notes |
| -- | ----- | ------- | ----- |
| `=` | assign | `x = 1` | stores value of 1 for x
| `?=` | initialize | `count ?= 0` | assigns count to 0 if null or nonexistent
| `°=` | reassign | `x += 1` | adds 1 to current value of x
| `=<` | vacuum | `a =< b[:2]` | pops slice from b and assigns it to a
| `:=:` | swap | `a :=: b` | swaps the values of a and b ((a,b) = (b,a))
| `:=` | define | `add(x,y):= x + y` | function definition
| `::=` | class | `Person::= ...` | class definition

* Unary vacuum `=<` deletes a slice of a collection: `=<dict["names"]` deletes the key `"names"` from `dict`
* Define `:=` can be used on variables (not just functions), thereby creating dependent variables / properties; in `y := x^2 -2`, y is linked to x, and if x changes, y will be updated with the current value. In a broader sense, define `:=` is used like Prolog's logical implcation `:-` operator (as you will see). The last expression in a function returns.

(show examples of classes using `::=`)

#### Array/Setwise

[](#table-of-contents)
| op | name | instance | notes |
| -- | ----- | ------- | ----- |
| `++` | union | `[1,2] ++ [3,4] == [1,2,3,4]` | concatenates 2 arrays
| `--` | difference | `[1,2,3,4] -- [2,4] == [1,3]` | removes each item from 1st array
| `**` | intersection | `[1,2,3,4] ** [3,4,5,6] == [3,4]` | returns shared items
| `^^` | symmetric difference | `[1,2,3,4] ^^ [3,4,5,6] == [1,2,5,6]` | returns unshared items
| `\\` | remove | `[1,2,3,4] \\ 1 == [2,3,4]` | removes single item
| `<<` | append | `[1,2,3] << 4 == [1,2,3,4]` | appends single item
| `>>` | juxtapose | `[1,2,3] >> [0,1] == [1,2,3][0,1]` | affixes right argument
| `,,` | zip | `[1,2,3] ,, [4,5,6] == [[1,4],[2,5],[3,5]]` | zips arrays into nested arrays
| `::` | rank | `sum(matrix::1)` | sums matrix according to axis = 1

* Union `++` performs an rbind by default (axis = 0)
* Difference `--` removes elements by matching values
* Intersection `**` populates an empty list/set for every item shared. Duplicates are possible.
`12>>34 == 1234`
Should `,;` be used here?

#### Modifiers

[](#table-of-contents)
| op | name | instance | notes |
| -- | ----- | ------- | ----- |
| `~` | complement | `~[3:] == [:3)` | complement slice / regex
| `<~>` | rotate | `[1,2,3,4] <~> 1 == [2,3,4,1]` | rotates array n-times
| `->>` | reshape | `[1:4] ->> [2,2] == [[1,2],[3,4]]` | reshapes array by dimensions
| `+>` | repeat | `[0,1] +> 3 == [0,1,0,1,0,1]` | concats array to itself n-times

Unary rotate `<~>` reverses an array/string: `<~>[1,2,3] == [3,2,1]; <~>"live" == "evil"`. Rank `::` is identical to it's usage in other array languages like APL and J. 

#### Membership

[](#table-of-contents)
| op | name | instance | notes |
| -- | ----- | ------- | ----- |
| `#` | length | `#[1,2,3,4] == 4` | length along first axis 
| `%` | shape | `%[[1,2,3],[4,5,6]] == [2,3]` | shape of matrix/dataframe
| `@` | in | `1 @ [[1,2],[3,4]]` | checks if scalar exists in collection
| `$` | subset | `[2,3] $ [1,2,3,4]` | checks if subsequence/subset exists
| `>->` | starts | `[1,2] >-> [1,2,3,4]` | checks if subsequence is at the start
| `<-<` | ends | `[3,4] <-< [1,2,3,4]` | checks if subsequence is at the end

#### Maps & Filters

[](#table-of-contents)
| op | name | instance | notes |
| -- | ----- | ------- | ----- |
| `[]` | map | `[4,5,6,7][_+2] == [6,7,8,9]` | maps values + 2
| `{}` | filter | `[4,5,6,7]{_%%2} == [4,6]` | filter even values (%% 2)
| `()` | index | `[4,5,6,7](_>=6) == [2,3]` | indices of values (>= 6)
| `=>` | arrow | `[1,2,3][x => x*2] == [2,4,6]` | mapping with named variable x
| `:`  | colon | `[1,2,3,4]{_%%2: _*10} == [1,20,3,40]` | 10x even numbers
| `?:` | cond  | `[1,2,3,4]{_%%2?: _*10} == [20,40]` | remove unmatched values

#### Conditional

[](#table-of-contents)
| op | name | instance | notes |
| -- | ----- | ------- | ----- |
| `?` | truthy | `?0 == ?[] == false` | returns truthy/falsy values
| `??` | existence | `??null == false` | false if null or nonexistent
| `&&` | and | `false && true == false` | short-circuit and
| `\|\|` | or | `false \|\| true == true` | short-circuit or

* Truthy/Falsy rules follow the conventions of Python
* Existence `??` returns `false` if an error occurs (like a failed key-value reference)
* Use `T`, `F`, `U` shorthands for `true`,`false`,`null`
// ?? is also the coalesce operator, and ?= is the initialize operator
//1_000 T F U I o oo O 

[](#table-of-contents)
| op | name | instance | notes |
| -- | ----- | ------- | ----- |
| `?:` | ternary | `if_true ? do_this : otherwise` | ternary conditional
| `??` | coalesce | `if_not_null ?? otherwise` | returns left argument if not null
| `:` | elif chain | `conditional: do_this` | obviates if/elif keyword
| `><:` | else | `false \|\| true == true` | replaces else keyword
| `==:` | switch | `variable ==: case1: do_x` | switch statement

* `?:` and `??` work like they're known to in C#
* Keywords `if`, `elif`, and `else` are all valid like in Python
* Successive colon conditionals `:` create an if-elif chain ending with else `><:`
```csharp
//Keyword chain of if-elif-else
if conditional1:     do_thing1
elif conditional2:   do_thing2
elif conditional3:   do_thing3
else:                do_thing4

//Implicit elif-chain semantics
conditional1:     do_thing1
conditional2:     do_thing2
conditional3:     do_thing3
><:               do_thing4
```

#### Logex

[](#table-of-contents)
| op | name | instance | notes |
| -- | ----- | ------- | ----- |
| `!` | not | `!2 == 3` | logically negates value/object
| `&` | and | `1&2 @ [1,2,3,4]` | both 1 and 2 in array
| `\|` | or | `0\|1 @ [1,2,3,4]` | either 0 or 1 in array
| `!&` | nand | `0!&1 @ [1,2,3,4]` | not both 0 and 1 in array
| `!\|` | nor | `0!\|5 @ [1,2,3,4]` | neither 0 nor 5 in array
| `><` | xor  | `0><1 @ [1,2,3,4]` | either 0 or 1 in array, but not both
| `->` | imply | `1->2 @ [1,2,3,4]` | 1 in array implies 2 also in array
| `<->` | iff | `1<->2 @ [1,2,3,4]` | both 1 and 2, or neither (xnor)

#### Metalogic

[](#table-of-contents)
| op | name | instance | notes |
| -- | ----- | ------- | ----- |
| `<=>` | equivalence | `!1\|!2 <=> 1!&2` | DeMorgan's Law
| `==>` | implication | `1&2 ==> 1\|2` | if both, then either is also true
| `>=<` | inequivalence | `1&2 >=< 3\ |4` | different logical universes

#### Forks

[](#table-of-contents)
| op | name | instance | notes |
| -- | ----- | ------- | ----- |
| `+-` | plus-minus | `2+-3 == 5,-1` | expands into 2 values
| `-+` | implication | `2-+3 == -1,5` | reverse order
| `°,°` | comma fork | `2+,*3 == 2+3,2*3 == 5,6` | branches along operator choices
| `°&°` | and fork | `2+&*3 == (2+3)&(2*3) == 5&6` | branches along operator choices
| `°\|°` | or fork | `2+\|*3 == (2+3)\|(2*3) == 5\|6` | branches along operator choices
| `^` | identity | `+|^"123" == 123|"123"` | returns self
| `?` | optional | `"word" ?|* "s" == "word"|"words"` | returns left argument

#### Combinators

[](#table-of-contents)
| op | name | instance | notes |
| -- | ----- | ------- | ----- |
| `!°` | not | `0 !@ [1,2,3,4]` | negates membership
| `.°` | inner | `[1,2] .* [3,4] == [3,8]` | inner product
| `<>°` | outer | `[1,2] <>+ [0,10] == [[1,2],[11,12]]` | outer sum
| `~°` | swap | `a ~* b == b * a` | swaps operator order / associativity
| `[°]` | scan | `[+][1,2,3,4] == [1,3,6,10]` | scans along axis applying operator
| `°:` | increment | `[1+:2] == [1:3]` | increments length by difference

Unary `.°` does reductions. So `.+` is a sum: `.+[1,2,3] == 6`. `.==` checks whether every element is equal: `.==[1,1,1,1] == true`. 


### Examples
#### Entitle String
Task: Capitalize each word in a lowercase string.
```csharp
entitle(str):=
      words = str -< " "
      words >>= [upper(_[0])_[1:)]
      words >-< " "
   
entitle("world records book")
>>>   "World Records Book"
```
1. Entitle function ingests a string as its only argument
2. Split string along space `" "`, and assign to `words`
3. The map `[upper(_[0])_[1:)]` capitalizes 1st character, concats rest of the unaltered word
- `"world" => upper("w")"orld" => "W""orld" => "World"`
4. Apply map `>>` to each element of `words`, giving all capitalized words
5. Join list of strings `words` with space `" "`
6. Last expression of function/branch returns
`"world records book" => ["world","records","book"] => ["World","Records","Book"] => "World Records Book"`

Python (longer and messier):
```
def entitle(str):
      words = str.split(" ")
      words = [upper(w[0])+w[1:] for w in words]
      return " ".join(words)
```

#### Leap Year
Task: Check if year is leap year.
Rules: A leap year is divisible by 4, not divisible by 100 unless divisible by 400. 
```
leap_year(yr):= yr %% 4&(!100|400)

leap_year(2024)   //true
leap_year(1900)   //false
leap_year(2000)   //true
```

Python (clunky):
```
def leap_year(yr):
      if yr % 4 == 0:
            if yr % 400 == 0:
                  return True
            elif yr % 100 == 0:
                  return False
            else:
                  return True
      else:
            return False
```
#### Number of Factors
Task: Given a positive integer n, return the number of factors
```csharp
num_factors(n):= .+(n %% [1:n])

num_factors(10)   //4 factors
```
Calculation for n == 10:
```
.+(10 %% [1:10])
.+(10 %% [1,2,3,4,5,6,7,8,9,10])
.+[T,T,F,F,T,F,F,F,F,T] == 4
```

Python:
```python
def num_factors(n):
      return sum(n % i == 0 for i in range(1,n+1))
```
#### Day Number (Switch Case)
Task: Convert number 0-6 to day of the week (string).
```csharp
day(num):=
      num ==:
            0:  "Monday"
            1:  "Tuesday"
            2:  "Wednesday"
            3:  "Thursday"
            4:  "Friday"
            5:  "Saturday"
            6:  "Sunday"
            
day(3)      //"Thursday"
```

#### Prime Divisibility

#### Check If Run of Cards
Task: Verify sequence of cards makes a valid run
```csharp
is_run(run):= (#run >= 4 && .==run.suit && run.card$DECK)
```


#### Average
```python
avg(xs):= .+xs/#xs                    //Noda
def avg(xs): return sum(xs)/len(xs)   #Python
```

```
progress_dots(percent):= "🔵"^10percent * "⚪"^10(1-percent)
   
progress_dots(0.8)
>>>   "🔵🔵🔵🔵🔵🔵🔵🔵⚪⚪"

prime_counter(P):= #[2:P]{.!|(_%%[2:_))}

pascal_triangle(n):= [:n]!![:[:n]]

diff(g):= .+(2g-1)::0 <>+ .+(2g-1)::1

pluralize(word):= word * ("ch"|"sh"|"s"|"x"|"z"<-<word ? "es" : "s")

liebniz_pi = .+-4/[1:2:]
e = .+/!![0:]

npv = .+(costs./(1+r)^[0:])

norm(X):= ^/.+X.^2
softmax(X):= e^X/.+e^X

checkMatrix(m):= (1\/m)==(I(m)/\<~>I(m))

[][1,2,3,4] == [[1],[1,2],[1,2,3],[1,2,3,4]]
{}[1,2,3,4]

(-*4.:strs)(%_==4)[0]	# New algorithm?
(-*4.:strs)(#_==4)[0]	// Old algorithm?
str(:,4)(-*_==_)[0]

//for scans—
(scan_type, window)
(:,window)          is a slicing scan with window size
(scan_type, :)      is a ____ scan with increasing window size
(:,:)               empty scan

str = "chicky"
str(:,:) == ["c","ch","chi","chic","chick","chicky"]
str(:,4) == ["chic","hick","icky"]

nums = [1,2,3,4,5]
nums(:,:) == [[1],[1,2],[1,2,3],[1,2,3,4],[1,2,3,4,5]]
nums(:,2) == [[1,2],[2,3],[3,4],[4,5]]
nums(*,:) == [1,2,6,24,120]
nums(*,2) == [2,6,12,20]


.:max([1,5,0,7,2]) === [1,5,5,7,7]  # max scan
max([1,5,0,7,2]) == 7
max([1,5,0,7,2],:) == [1,5,5,7,7]  
avg([1,5,0,7,2]) === 15/5 == 3
avg([1,5,0,7,2],:3) === [6/3,12/3,9/3] == [2,4,3]
3.:+[1,5,0,7,2] === 
[1,5,0,7,2](3,+) === [6,12,9]
[1,5,0,7,2](+,3) === 

[1,5,0,7,2](:) === [[1],[1,5],[1,5,0],[1,5,0,7],[1,5,0,7,2]]
[1,5,0,7,2](/\) === [1,5,5,7,7]
[1,5,0,7,2](avg) === [1,3,2,3.25,3]
[1,5,0,7,2](avg,3) === [2,4,3]
[1,5,0,7,2](3) === [[1,5,0],[5,0,7],[0,7,2]]
[1,5,0,7,2](:,3) === [[1,5,0],[5,0,7],[0,7,2]]

[1,5,0,7,2](==3) === []       //no indices where == 0
[1,5,0,7,2][>=3] === 

1 # 4 == 1,1,1,1
[0#10] === [0,0,0,0,0,0,0,0,0,0]

//idioms
#[0#n] === n

4.:"chicky" => ["chic","hick","icky"]
2.:*[1,3,5,7] => [3,15,35]	//pairwise multiplication (this looks terrible)

"chicky"(:,4) == ["chic","hick","icky"]


avg(X):= .+X/#X				//define average function
moving_avg(X,size):= size.:avg(X)	//moving average with window size
moving_avg(X,size):= X(avg,size)    //avg scan with window size

num_factors(N):= .+(N %% [1:N])

```


//Literal Multiplication  f()g()


![image](https://user-images.githubusercontent.com/84992695/200396390-b1cc877c-803d-45de-864b-5d8a91acc4f0.png)
![image](https://user-images.githubusercontent.com/84992695/200396524-b24a112d-ccd1-400c-a872-55775bbea1fe.png)

<img src="https://user-images.githubusercontent.com/84992695/200396390-b1cc877c-803d-45de-864b-5d8a91acc4f0.png" width="1000">

MORE OF THIS PRESENTATION NEEDS TO BE IMAGES FRANKLY, THEY'RE CLEANER



Sections to be added—
1. Lists, rings, and sets
2. Ranges and Intervals

1. Explain lists, sets, and tuples. Same as Python
2. Rings (and why they are useful, including endless indexing, circular buffers, mathematics, card games, etc.)
3. Ranges and intervals, and how to combine them
4. Indexing with ranges and intervals, indexing with lists too
5. Dictionaries (ordered rules, and much more) (when will elementwise zip dictionaries be shown??)
6. Matrices and Dataframes. How to index them too!!
7. Strings and regexes, fstrings and fregexes
8. Empty
9. Note to address logexes, patterns, and maps LATER

#### Numeric Types, Constants, Built-ins
```
+     nat         0           // unsigned positive integer (natural number)
-     int         -8          // signed integer
.     flo         1.0         // floating point number
i     com         3+2i        // complex number
(:)   datetime    (8:35:42)   // 8 hours, 35 minutes, 42 seconds ​

I     identity    [1 0; 0 1]  // identity matrix; takes shape of operand
e     Euler's     2.71828...  // constant


(||)  round
[||]  floor/lowercase
{||}  absolute value/uppercase
```





1. Introduce obvious operator usage, ^ for exponent instead of **. Mention unary / for reciprocal.
2. ^/ for root
3. ldivide (ala Julia)
4. \ also used to escape newlines in long statements chaining stuff (although trailing dot is fine?)

#### String Arithmetic
String arithmetic is partly inspired by Julia, with many other features. All operations here apply to regexes too.
```csharp
+   space      "hi" + "there" == "hi there"         // concats with space between
*   concat     "match" * "box" == "matchbox"        // concats strings
°   literal    "ship""yard" == "shipyard"           // literally concats strings
/   remove     "walla walla" / "all" == "wa wa"
^   repeat     "na" ^ 4 == "nananana"     
-   modulus    "try-my-lang" - "-" == "my-lang"     // everything after first split
%   modulus    "try-my-lang" % "-" == "try"         // everything before first split
^/  strip      ^/"   str   " == "str"
```
^Though frankly there should be a little section showing how these are used in unary fashion
1. Explain why * and ^ are chosen (in the Julia way) and remark that + is used quite often to avoid pesky "hello " scenarios
2. Compare ++|* --|/ and %|-<  although these should be all at the same time
3. Literal concatenation on variables with strings: mon"/"day"/"year
4. Modulus?
5. Strip using root.
6. All can be used literally as string methods...
7. Why * was chosen instead of ++? (to be possibly addressed later)
8. Use \\ to remove characters, ** to keep only certain ones (addressed in the regex case)

Note: Join is omitted here, perhaps we should introduce reduction (and scan) sooner. It's all about order. Maybe after .& as forall and .| as there exists.

Pattern Operations

```csharp
-<  split     "2/14/23"-<"/" == ["2","14","23"]     -<"Jane Smith" == ["Jade","Smith]   // can also be used on regexes
+<  snip      "2/14/23"+<"/" == ["2/","14/","23"]
<>  findall   "123def56"<>'\d+' == ["123","56"]
%   remainder "try-method" % "-" == "method"
```

1. Scissors (-<), flamethrower (+<), nanobot (<>)
2. Unary uses of -< and less commonly +<
3. Using -< and +< on lists instead of strings
4. Convenient remainder shortcut and why it's useful. Compare to / usage.
5. Awesome bag `{+*-<.+words}` example (likely shown much, much later) WHERE IS UNPACKING IN THIS?

At some point, the discussion of how strings differ from lists by being treated as scalars unless explicitly split up :)
Scalars vs Collections (group,set,etc.)

#### Comparators

```csharp
==  equal
!=  inequal
<   less
<=  less or equal
>   greater
>=  greater or equal
%%  divisible
!%  indivisible
=== equivalent
!== nonequivalent       'str' !== "str"
~=  match               
!~  no match
```

1. Introduce familiar == != < <= > >= operators as perfectly normal
2. Divisibility shortcuts, almost exclusively used numerically to replace n%m==0 as n%%m.
3. Make clear that == checks the value and can differ across structures where `'' == ""` and `0x1f == 31` and `[1:5] == [1,2,3,4,5]`
4. Equivalence === checks the object identify, so '' !== "" for instance. (differently ordered dicts fall in this category, `^"" !== ""`)
5. Matching operator ~= used to compare likeness. The following matches matter most
   `[} != [}, "" ~= '', {}|""|'' ~= <>, 0 ~= false, 5 ~= true`
6. 




all(1nation !% + liberty&justice)

#### Assignment, Functions, & Classes
```js
=   assign
°=  reassign
:=  func​tion   // does this still do immute or are we gone now? Should :=: do that? Or =:?
::= cl​ass      // Consider BNF uses
=<  vacuum      // unary =< to delete vars
??  coalesce    // was this replaced by binary ?:
```

1. Intro = and °= typical uses. Any user-defined operator not ending in equals is assumed to benefit from °= syntax. .= and -*= too
2. Talk about functions and the difference between := and = (for inline assignments)
3. Introduce Classes/Structs, how they are written, o.name shortcuts, etc. Compare to Python :D
4. Vacuum operator, although this is best addressed in conjunction with << and >>, otherwise it seems pointless
5. Coalescence, and their usages in C# and JS

#### Setwise Operators
```csharp
,   comma           1,2 => (1,2)                 // commas make tuples by default
<<  append          [1,2] << 3 == [1,2,3]        // << appends into structure
>>  pop             [1,2,3] >> 2 == [1,3]        // pops value from list
++  concat          [1,2] ++ [3,4] == [1,2,3,4]  // concatenates structures
--  difference      [1,2,3,4] -- [2,3] == [1,4]  // removes subsequence (if found)
\\  set minus       [1,2,3,4] \\ [1,3] == [2,4]  // removes each element          
**  intersect       [1,2,3] ** [2,3,4] == [2,3]  // retrieves shared elements
^^  symdiff         [1,2,3] ^^ [2,3,4] == [1,4]  // retrieves unshared elements
.°  dot             [[1],[2,3]] .++ [[4,5],[6]] == [[1,4,5],[2,3,6]]
```



1. Comma's creating tuples, trailing commas, unnecessary commas (dicts/lists/etc.)
2. Append << and Pop >> 
3. Extend/Union ++ (all DS)
4. -- vs \\ usage
5. ** intersect
6. ^^ symdiff
7. Go into bag uses with ++ ** and ^^ later (otherpage ideas)
8. Difference between setwise and elementwise operations
9. Talk about how list combinations terminate at the shortest list and why this is useful
10. Usage of the binary dot operator .++ examples
11. >> vs ++ for dataframes

#### Membership Operators
```csharp
#   length
@   in/at
$   subset/subsequence
>-> starts
<-< ends
```

1. Explain intuition behind # (length) @ (in/at) $ (subset/subsequence). $ is not strict subset
2. Intuition between <<|<-< and >>|>->. Both are sub-operators of $

#### Special Set Operators
```csharp
%   reverse
~   complement
`   transpose  
~<  tulip         ascend
~>  umbrella      descend
<~> hotdog        rotate mustache
->> pine          reshape
,,  zip           zip
+*  cosmos        dot-product
```

1. Show examples for % (simple)
2. Complement needs a whole intro. Show every data structure as complement (range, interval, regex, probability)
3. Wondering if:  ~<> == (::)  // udderly unbounded
4. Transpose needs a similar intro. Show each data structure (matrix, vector, nested list, dataframe, dictionary (cool part))
5. Tulip & Umbrella (sorting) made simple. Also show usage in dataframes `Users{~<"length"}` `Users{"last"=='Wu'|'Kim'}`
   Make cool parallel with .<=(~<X) and .>=(~>X) and monotonicity (hence scans & reductions need to come first)
7. Usage of hotdog for rotation <~>. Unary <~>X rotates rightward once.
8. Using ->> to shape objects (lists->>lists, matrices->>matrices, str->>list, dict->>dict)
9. Zip examples shown simply, alongside Python. Recall that it deletes unmatched pairs/triplets/etc.
10. Using cosmos for dot-product and polynomial operations. Possibility of `.+*L` for indefinitely flattening lists (diff from .++)


WHERE IS INDEXING RULES IN ALL OF THIS??? INDEXING BY INTERVALS TOO?? `list[*indices] == list[indices]` as well and `list{**map} == list{map}`
COLLECT QUOTES FROM EVERYTHING AND REFERENCE THEM

#### Relational Operators
```csharp
>==<  inner join
>==>  right join
<==<  left join
<==>  outer join
<<>>  disjoint
```
1. Introduce main cast of relational operators
2. Compare directly to SQL but using Nodan code examples
3. Explore using specialized joining operators like >>=> <<=< >><< (crossjoin) and so on.
4. ???

#### Functional Operators
```csharp
:=  map
=:  filter
_   placeholder
:   ifmap 
=>  domap/default/sword
[)  indices
[]  keys
{}  values
[}  indices from values
#   compose
-*  wand
:=: dogbone
.:  grapevine
```



1. Outline the purpose of map-filter-reduce and why it's a powerful construct
2. Show examples using explicit map (:=) and filter (=:) examples
3. Show underscore examples and implicit K{<0} like examples
4. Show K{+=1} examples for maps (and how := or = can be used in maps)
5. Show the difference between if-maps (:) and do-maps (=>) with `str{'\w+'=>" "}` example. Maybe also show ?: example
6. Explain how `{}` filter on values, `[]` filter on keys/indices, and `[}` gets indices/keys from values. 
7. At some point explain all the `[), [], {}` shortcuts.
8. Use the compose operator in a few examples (dot included?)
9. Explain the wand operator, and how it's used for `-*=` and to evade precedence rules.
10. Dogbone `:=:` for complex dictionary mapping scenarios (harderts to write)
11. Using grapevine for groupby `.:` similar to uses for ~< and ~>. Explain string literal shortcuts for filtering values.
^^ Perhaps this should go before ~< and ~> for this very reason, since filtering wasn't covered yet

This section is a great segway into map and filter objects, which should be addressed next.

LINK +=> it's dangerous to go alone (logos in there?) Perhaps a meme!

## LOGIC

#### Coercive Logic Operators
```csharp
?   bool
&&  and
||  or
```
Each of these coerce non-booleans into boolean values. `?3 === true` 
Not much else to see here. Maybe precedence levels?

#### Logex Operators
```csharp
!   not
&   and
|   or
!!  nor
><  xor
->  then
<-> iff
```

Since !° is a combinator, you can use it on other operators...

1. Using ! for logical negation. The object is negated, which leads to interesting scenarios like !2 == 3  same as 2 != 3
2. !° is a combinator so can be used on !@ or !$ to negate evaluations
3. Introduce & and | (obvious). Show examples of what logexes do. Emphasize no coercion of booleans.
4. Nor !! (mention that !| and !& are valid, but to be avoided due to bugs caused by &! and |! permutations)
5. xor >< and iff <-> (xnor) use cases
6. Then -> interesting uses
7. Leap Year example. Show how it reduces. bools reduce, but nothing else.
8. Logexes reducing against one another... Explain the elementwise concerns

#### Metalogic Operators
```csharp
<=> equivalent
==> entail/imply
>=< nonequivalent
```
1. Explain what metalogic means and why these are necessary
2. DeMorgan's Law and 1&2 ==> 1|2 examples
3. How candybar A >=< B differs from spaceship A <=> !B

#### Bitwise Operators
```js
~~  complement
/\  and
\/  or
>-< xor
>>> rshift
<<< lshift
```

1. Note that bitwise is the most different from other languages
2. /\ and \/ like logical symbols, >-< to mirror ><
3. Shifts have 1 extra character


#### Procedural Operators
```csharp
:   if/elif       (|:  double-if)
><: else
::  loop
;   semicolon     (;; for break?)
?:  ternary       (?: !: try except)
```

1. Explain how ifs don't use keywords, |: does double if (and why)
2. ><: else symtax
3. for loop (both @:: and $:: types), while loop, infinite loop (::)
4. Semicolon ;
5. Pass/break/continue
6. ?: ternary operator, coalesce too?

#### Combinators
```csharp
!°  not
°:  switch        (but also +: and -: should be mentioned)
~°  swaperator
.°  reduce/elementwise
[°] scan
```

1. !° combinators !@ and !$
2. ==: @: >=:
3. =:
4. +:
5. 

#### Alternators
```csharp
+-  plus-minus
-+  minus-plus
°,° commafy
°|° either
°&° both
°!!° neither
```

#### Shortcuts
```csharp
{+}   {>=0}
{-}   {<0}
{*}   {*L}
{:}   {L[0]:  L[1]}
{::}  {L[0}:: L[1]}
{++}  full-flatten
```



