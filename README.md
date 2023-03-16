# Noda
![image](https://user-images.githubusercontent.com/84992695/221333492-bfdd39e5-1867-4f54-9155-23a60934cdf7.png)

**Ambitions—**
![image](https://user-images.githubusercontent.com/84992695/221332921-04c9609c-f982-4f8e-a1b7-9d1e7f22e6d3.png)

**Special Features—**
![image](https://user-images.githubusercontent.com/84992695/221332861-7fbc0e09-b3bb-4843-a971-853bc8aa1d2f.png)

OPERATOR OVERVIEW—

[](#table-of-contents)
| Family | Operators |
| ------ | --------- |
| Indexing | `: +: -:`
| Arithmetic | `+ - * / \ % ^ ^/ /\ \/ +* +- -+`
| Comparison | `> < >= <= == != %% === !==` 
| String | `-< +< >-<`
| Assignment | `= °= =< := ::= => ->`
| Conditional | `: ><: _: ?: ?? !! :: :=: ; ;;`
| Array | `++ -- ** ^^ \\ << >> <>`
| Relational | `/\ \/ ~< ~>`
| Membership | `# @ $`
| Morphers | `~ % ^ * ** \ .`
| Boolean | `! ? && \|\|`
| Logic | `! & \| >< <=> >=<`
| Pattern | `: _ * + ? ?= ?!`
| Combinator | `!° ~° .° (°)`
| Keywords | `for while in of if elif then else`

\*The degree symbol `°` is used to indicate \[*insert any operator*\]. `//` and `/* */` enclose comments like in C++.

RANK POLYMORPHISM

## Core Ideas
Noda is a supercharged Numpy/Pandas/PyTorch hybrid, with synactic inspirations everywhere. We target a Python audience, sharing many ideas and constructs. Here's how it compares to Python:

#### Similarites To Python
1. Indices start at 0
2. Slices `start:stop` include `start`, exclude `stop`
3. Indentation sensitivity (ifs, loops, classes, etc.)
4. Pythonic keywords and built-ins are valid
5. Operations are elementwise on arrays/dataframes
6. Dict, set, dataframe, tuple, and array syntax
7. Embeddable, can import Python libraries
8. Similar OOP, dataclass support, decorators

#### Differences From Python
1. Comments use `//` and `/* */`
2. Exponentiation is `^`, floor division is `\`
3. Stride indexing follows `start:step:stop`
4. Function `:=` and class `::=` definition operators
5. Strings use quotes `""`, regexes use apostrophes `''`
6. Lists are arrays `[]`, dicts are dataframes `{}`
7. Expanded suite of array, string, and logic operators
8. C# operators like `??`, `?:`, `?.`, and lambdas `=>`
9. Asserts `!!` and unit testing semantics
10. Simplified OOP syntax, function/method composition `.`
11. Predicates `(>0)`, maps `[_+2]`, reductions `.+X`, functors
12. Implicit conditionals / returns, switch statements `:=:`
13. Enforced type hints, refinement/gradual typing `::`
14. Advanced pattern matching + logical expressions
15. Uniform function call syntax
16. Everything is a function / is a callable

## Basic Data Structures

[](#table-of-contents)
| empty | type | instance | notes |
| ----- | ---- | -------- | ----- |
| `()` | tuple | `(1,2,3,4)` | immutable list
| `{}` | set | `{1,2,3,4}` | unordered
| `[)` | ring | `[1,2,3,4,5)` | loops on itself
| `[]` | array | `[1,2,3,4,5]` | n-dimensional array
| `[:]`| slice | `[1:5]` | iterable
| `{}` | dict | `{"a": 1, "b": 2}` | dict and dataframe

Sets `{}` and tuples `()` behave similarly to Python—sets are unordered, tuples are immutable. Rings `[)` are like lists, but loop back on themselves and are indexable anywhere: `[0,1,2,3)[4] => [0,1,2,3)[0] => 0`. Like Numpy, arrays are n-dimensional and can be used for matrix operations. However, they may contain multiple datatypes at once, and not be rectangular (e.g. differing lengths of rows). Slices are iterables like `start:stop`, includes `start` but excludes `stop`. Strides are similar, but the `step` size is in the middle: `start:step:stop`. Use `+:` and `-:` to set forward and backward slicing windows—
[](#table-of-contents)
| slice | equivalent        | notes |
| ----- | ----------------- | ----- |
| `[:5]` | `[0,1,2,3,4]`    | 0-5 exclusive
| `[1:2:9]` | `[1,3,5,7]`   | 1-9, stepwise 2
| `[-4:]` | `[-4,-3,-2,-1]` | -4-0 exclusive
| `[:2:]` | `[0,2,4,6,8..]` | unbounded, stepwise 2
| `[3:]`  | `[3,4,5,6,7..]` | numbers 3+
| `[2+:4]` | `[2,3,4,5]`    | 2 with 4 indices ahead
| `[6-:3]` | `[4,5,6]`      | 6 with 3 indices behind

Dictionaries use Pythonic syntax `{key: value}`, but can double as Pandas dataframes. Dicts and arrays benefit from dimensional Numpy indexing:
`matrix[:10,:10] === matrix[:10][:10]`
`dict["key","field"] === dict["key"]["field"]`

All arrays/lists `[]` are n-dimensional arrays, and mimic the conventions of Numpy/Pytorch/Tensorflow. Likewise, all dicts are dataframes and mimic many of the conventions of Pandas. Both may be indexed along each dimension:
```
X = [[1,2,3],[4,5,6]]
X[1]      [4,5,6]         // 2nd row              
X[:,0]    [[1],[4]]       // 1st column        
X[:,0:2]  [[1,2],[4,5]]   // 1st & 2nd column        
```
Arrays of 2+ dimensions can use `;` to delimit columns instead of nested arrays: `[[1,2],[4,5]] === [1,2; 4,5]`

```
df = {"team":    ["A","A","A","A","B","B","B","B"]
      "points":  [ 5,  7,  7,  9,  12, 9,  9,  4 ]
      "assists": [ 11, 8,  10, 6,  6,  5,  9,  12]}
```
```
df[:,:4]  or  df.[:4]
      {"team":    ["A","A","A","A"]
       "points":  [ 5,  7,  7,  9 ]
       "assists": [ 11, 8,  10, 6 ]}
```
Here, `df.[:4]` is equivalent to `df.iloc[:4]` in Pandas, which grabs the first 4 rows of the dataframe.

## Operators

Noda parses operators from right-to-left in a longest-match clumping pattern: `++->-<<>^^/` is parsed as `(+)(+-)(>-<)(<>)(^)(^/)`

### Arithmetic

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
| `/\`| min | `3 /\ 5 == 5` | minimum value
| `\/`| max | `3 \/ 5 == 3` | maximum value
| `+*`| dot | `u +* v == 0` | matrix multiplication
| `+-`| plus-minus | `2+-3 == 5,-1` | returns 2 results
| `-+`| minus-plus | `2-+3 == -1,5` | returns 2 results

* Times `*`, division `/`, and power `^` are elementwise on arrays/matrices like Numpy
* Juxtaposition multiplies functions: `f(x)g(x) == f(x)*g(x)`
* Plus times `+*` computes matrix multiplication / dot product on arrays
* Max/min return the lexically greater/less string: `"apple" \/ "banana" == "banana"`

-----------------------------------------------------------------------------------------------

[](#table-of-contents)
| op  | name | instance | notes |
| --- | ----- | ------- | ----- |
| `+` | plus  | `+4 == 4` | positive
| `-` | minus | `-4 == -4` | negative
| `/` | divide | `/5 == 1/5 == 0.2` | reciprocal
| `^/`| root | `^/36 == 6` | square root
| `+-`| plus-minus | `+-2 == +2,-2` | splats + and -
| `-+`| minus-plus | `-+2 == -2,+2` | splats - and +

* Plus `+` and minus `-` convert strings into ints/floats: `+"123" == 123`
* Unary floordiv `\` returns the inverse of a square matrix, or the pseudoinverse 

### Comparison

[](#table-of-contents)
| op  | name | instance | notes |
| --- | ----- | ------- | ----- |
| `>` | greater | `3 > 2` | greater than
| `<` | less | `2 < 3` | less than
| `>=` | greater/equal | `3 >= 2` | greater or equal
| `<=` | less/equal  | `2 <= 3` | less or equal
| `==` | equal | `1 == 1.0` | equality (of value)
| `!=` | unequal | `1 != 1.5` | inequality (of value)
| `%%` | divisible | `20 %% 5` | true if remainder is 0
| `===`| equivalence | `1.0 === 1.0` | same objects
| `!==`| inequivalence | `1 !== 1.0` | different objects

* Strings do lexical value comparison: `"apple" < "banana"`
* All equality comparisons are elementwise on arrays: `[1,2,3] == [1,0,3]` is `[true,false,true]`
* Equivalence `===` compares object equality *as a whole*: `[1,2,3] === [1,0,3]` is `false`

## Strings
[](#table-of-contents)
| empty | type | instance | notes |
| ----- | ---- | -------- | ----- |
| `""` | string | `"Hi {name}!"` | strings are fstrings
| `''` | regex | `'\d+'` | matches "42069"
| ``` `` ``` | raw | ``` `"wow!"\\''` ``` | no escape sequences

* All strings `""` are fstrings by default
* Escape braces using `\{` and `\}`
* Raw strings contain no escape sequences: ```filepath = `C:\Documents\Scripts\Test.py` ```
* Regexes patterns follow the PRCE standard (same as Python and C++)
* Multiline strings can be written without using triple quotes. Use `\` to escape newlines (like Python)
* Use triple quotes `"""` to easily escape `"` from text (same for `'''` on regexes)

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
| `>-<`| join      |`["a","b","c"] >-< "::" == "a::b::c"`   | joins strings by delimiter
| `==` | match     |`'\d+\.\d+' == "420.69"`                | checks if regex matches string
| `!=` | unmatch   |`'\d+\.\d+' != "1_000"`                 | checks if regex doesn't match string

* Literal concatenation of strings works: `"wind""mill" == "windmill"` (no space between)
* Right argument tuples limit to n-times: `"split, me, up" -< (", ", 1) == ["split", "me, up"]`
* Unary `-<` splits on whitespace: `-<"Jane\n S Smith" == ["Jane", "S", "Smith"]`
* Unary `>-<` joins without space: `>-<["a","b","c"] == "abc"`
* Binary `>-<` joins lists too: `["Okay", "but", "why"] >-< [", ", " ", "?"] == "Okay, but why?"`
* Regex matching uses `==` and `!=` (match on value, not type), similar to how `1.0 == 1` despite `float` vs `int`

Strings/Regexes are treated as scalars, and not split up in array calculations (unless explicitly forced to). They're like numbers in this sense:
```
[1_000, 2_000, 3_000] * 3 === [3_000, 6_000, 9_000]
["lens", "box", "wish"] * "es" === ["lenses", "boxes", "wishes"]
```
Noda is weakly typed when it comes to strings (scalar + string -> string): `3 * "str" == "3str"`
Regexes dominate strings (string + regex -> regex): `'\d+' * " input" == '\d+input'`

## Assignment
[](#table-of-contents)
| op | name | instance | notes |
| -- | ----- | ------- | ----- |
| `=` | assign | `x = 1` | stores value of 1 for x
| `°=` | reassign | `x += 1` | adds 1 to current value of x
| `=<` | vacuum | `a =< b[:2]` | pops slice from b and assigns it to a
| `:=` | define | `add(x,y):= x + y` | function definition
| `::=` | class | `Person::= ...` | class definition

* Reassignment mechanics are available for custom operator
* Unary vacuum `=<` deletes a slice of a collection: `=<dict["names"]` deletes the key `"names"` from `dict`
* Define `:=` can be used on variables (not just functions), thereby creating dependent variables / properties; in `y := x^2 - 2`, y is linked to x, and if x changes, y will be updated with the current value (akin to a nullary function `y()`). In a broader sense, define `:=` is used like Prolog's logical implcation `:-` operator for unification.
* The last expression in a function is returned (`return` keyword is generally omitted). You can mute this by appending `;`.

Custom operators/keywords are defined similarly to functions, but wrapped in parentheses:
```
(⋃)(A,B):= Union(A,B)                                  // A ⋃ B
(send,to)(message,address):= sendoff(message,address)  // send message to address
```

Classes are best explained by example:
```
Rectangle(Shape)::=
    __(o,height,width):=
        o.height = height
        o.width = width
        o.og_dimensions = (height, width)

    resize(o,factor):=
        o.height *= ^/factor
        o.width *= ^/factor

    lengthen(o,factor):= o.width  *= factor
    heighten(o,factor):= o.height *= factor
    o.circumference := 2(o.height + o.width)
    o.area := o.height * o.width
    o.diagonal := ^/(height^2 + width^2)
```

Inheritance works like Python, so `Rectangle(Shape)` inherits properties from `Shape`. The constructor is written with a double underscore `__`, and the `self` keyword is replaced with `o`. In the example, the constructor ingests a `height` and `width`, assigns them to class variables, and keeps a record of the original dimensions. The `resize`, `lengthen`, and `heighten` methods mutate the `Rectangle`'s dimensions by a sizing factor. Meanwhile, `circumference`, `area`, and `diagonal` are all properties of the `Rectangle` which change depending on the current `height` and `width`. 

Class `::=` defintions can be repurposed to structs, dataclasses, traits, and custom types. Class composition (using traits) is encouraged.

## Conditional
[](#table-of-contents)
| op | name | instance | notes |
| -- | ----- | ------- | ----- |
| `:` | if/elif | `conditional: do_this` | obviates if/elif keyword
| `><:` | else | `><: do_default` | replaces else keyword
| `?:` | ternary | `if_true ? do_this : otherwise` | ternary conditional (if-then-else)
| `??` | coalesce | `if_not_null ?? otherwise` | returns left argument if not null
| `!!` | assert | `cond === true !! "condition violated"` | triggers assert if false
| `:=:` | switch | `variable :=: case1: do_x` | switch statement
| `::` | loop | `name in names::` | for/while loop
| `;`  | inline | `x = 2; y = 3` | execute multiple statements inline
| `;;` | break | `loop:: if_this: ;;` | break operator

* `?:` and `??` work like they're known to in C#/JavaScript
* Unary `!!` triggers a generic assert error if the condition is unmet
* Keywords `if`, `elif`, and `else` are all valid like in Python (but generally omitted)
* Successive colon conditionals `:` create an if-elif chain ending with else/default `><:`
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
* Switch case `:=:` creates nested conditionals matching against the variable given:
```
lang = input("What's the programming language you want to learn? ")

lang :=:
    "JavaScript"|"JS":  print("Become a web developer")
    "Python":           print("Become a Data Scientist")
    "C++"|"Go":         print("Become a backend developer")
    "Solidity":         print("Become a Blockchain developer")
    "Java":             print("Become a mobile app developer")
    ><:                 print("The language doesn't matter, what matters is solving problems")
```
* Loops `::` do a for loop or while loop depending on the condition supplied. If membership is checked (like `in`), it's a for loop. If a condition if checked (`error > 0.00001`), it's a while loop. Use triple colon `:::` to make a do-while loop that runs once without checking.
```
name in names::
   key, value in dict::
       key != name:  key[value] = name

error > 0.00001::
    prev = curr
    curr = gradient_descent(curr)
    error = curr - prev
```
The `for` and `while` keywords are optional for Pythonic-style programming, but not necessary. For loops are generally frowned upon, as there's almost always a vectorized (and thereby optimized) way of handling calculations. The number of semicolons in the break operator `;;` indicates how many nested levels it can break from, which can be handy.

## Functional

[](#table-of-contents)
| op | name | instance | notes |
| -- | ----- | ------- | ----- |
| `=>` | lambda | `x => x + 1` | obviates if/elif keyword
| `>>` | pipe | `list >> map` | list piped to map operation
| `.` | compose | `composition = funct1 . funct2` | composes 2 functions together
| `::` | type | `funct(x::int, y::int)` | explicit typing + multiple dispatch
| `->` | output | `response(input) -> str` | specifies return type `str`

* Lambda `=>` can be used to create anonymous functions like in JavaScript, but this is discouraged since inline function declarations `:=` are clearer
* Dispatch `::` executes a multiple dispatch version of the function depending on type supplied
* Similar to `:`, enforced output types are available

[](#table-of-contents)
| object | name | instance | notes |
| -- | ----- | ------- | ----- |
| `()` | filter | `list(>0)` | filters positive list values
| `[]` | map | `list[_+1]` | adds 1 to each item in list
| `{}` | replace | `list{"(": 1, ")": -1}` | find and replace parentheses with numbers

* Filters can omit underscore `_` if a comparator appears first; the above can be expanded into `list(_>0)`
* Filters must evaluate to `true/false`, if not they are coerced into truthy/falsy values
* Maps and filters can use the arrow `=>` for named lambdas: `options(opt => !opt.assigned)`
* Both can be assigned as their own data structures: `half_map = [_/2]; filter_even = (_%%2)`
* 2 versions of replace exist: dict `{}` replacements keep all unmatched values unchanged
* Whereas filtermaps `()` only keep the matched values, discarding all others

Pipe `>>` behaviors differs based on the argument supplied:

[](#table-of-contents)
| combination | example | output | 
| ----------- | ------- | ------ |
| `array >> map` | `[1,2,3] >> [_+1] === [2,3,4]` | map array values
| `array >> filter` | `[1,2,3] >> (>1) === [2,3]` | filter array
| `array >> dict`  | `[1,2,3] >> {1: "one"} === ["one",2,3]` | apply filtermap / find and replace
| `array >> array` | `[1,2,3,4] >> [_,3|4] === [[2,3],[3,4]]` | find matching subarrays
| `string >> string` | `"canadian" >> "an" === ["an","an"]` | find matching substrings
| `string >> regex` | `"123def456" >> '\d+' === ["123","456"]` | find matching substrings
| `function >> function` | `order_words = split >> sort` | compose functions
| `object >> function` | `str >> capitalize` | apply function to object (like a method would)
| `class >> class` | `RubberDuck >> Quack` | implement trait for a class

### Array/Setwise

[](#table-of-contents)
| op | name | instance | notes |
| -- | ----- | ------- | ----- |
| `++` | union | `[1,2] ++ [3,4] == [1,2,3,4]` | concatenates 2 arrays
| `--` | difference | `[1,2,3,4] -- [2,4] == [1,3]` | removes each matching item from 1st array
| `**` | intersection | `[1,2,3,4] ** [3,4,5,6] == [3,4]` | returns shared items
| `^^` | symmetric difference | `[1,2,3,4] ^^ [3,4,5,6] == [1,2,5,6]` | returns unshared items
| `\\` | remove | `[1,2,3,4] \\ 1 == [2,3,4]` | removes first occurence of item
| `<<` | append | `[1,2,3] << 4 == [1,2,3,4]` | appends single item to the end

* Union `++` performs an rbind by default (axis = 0)
* Difference `--` removes elements by matching values
* Intersection `**` populates an empty array/set for every item shared. Duplicates are possible with array intersection.
* On higher dimensional arrays, append `<<` affixes on the 1st dimension (always rows)
* Meanwhile, union `++` affixes on the last dimension (columns for 2D matrices)

### Sorting

[](#table-of-contents)
| op | name | instance | notes |
| -- | ----- | ------- | ----- |
| `/\` | sort up | `/\[5,3,1,4,2] === [1,2,3,4,5]` | sorts ascending
| `\/` | sort down | `\/[5,3,1,4,2] === [5,4,3,2,1]` | sorts descending
| `~<` | grade up | `~<[5,3,1,4,2] === [4,2,0,3,1]` | indices of ascending positions
| `~>` | grade down | `~>[5,3,1,4,2] === [0,2,4,1,3]` | indices of ascending positions

* Sorting operators sort strings and arrays of strings alphabetically `/\["banana","coconut","apple"] === ["apple","banana","coconut"]`

### Morphers

[](#table-of-contents)
| op | name | instance | notes |
| -- | ----- | ------- | ----- |
| `^` | reverse | `^[1,2,3] === [3,2,1]` | reverses order of items
| `%` | unique | `%[1,2,1,4,2,8] === [1,2,4,8]` | removes duplicates
| `~` | complement | `~[0,3,7] === [1:3,4:7,8:]` | retrieves complement object
| `*` | unpack | `*[1,2,3] === 1,2,3` | unpacks values
| `**` | unpack | `**dict === k1: v1, k2: v2` | unpacks key-value pairs
| `.` | each | `.[[1,2],[0,0]] << 3 === [[1,2,3],[0,0,3]]` | applies operation to each element

* Caret `^` reverses along rows (0th dimension) on matrices by default 
* Unique `%` retains the order of 1st unique occurence
* Complement `~` has special behaviors depending on the object complemented
+ Integer array — complement indices `~[0,3,7] === [1:3,4:7,8:]` and `~[-5,-3] === [:-5,-4,-2:]`
+ Boolean — flips boolean values `~T === F` and `~[T,F,T] === [F,T,F]`
+ Regex — retrieves everything *not* matching regex `~'^.*substring.*$' == '^(?:(?!substring).)*$'`
+ Float — gets complement percentage 1-n `~0.6 == 0.4`
* Each `.` only goes 1 dimension deep; if more dimensions are desired, use rank parameters (addressed in later sections)

#### Membership

[](#table-of-contents)
| op | name | instance | notes |
| -- | ----- | ------- | ----- |
| `#` | length | `#[1,2,3,4] === 4` | length along first axis
| `#` | replicate | `[1,2] # 3 === [1,2,1,2,1,2]` | replicates list 3x
| `@` | in | `1 @ [[1,2],[3,4]]` | checks if scalar exists in collection
| `$` | sub | `[2,3] $ [1,2,3,4]` | checks if subarray/set/string exists

* For tensors/matrices, length `#` checks along the first dimension (rows)
* Postfix `[]` to get shape: `[[1,2,3],[4,5,6]][] === [2,3]`
* Postfix `()` to get values: `dict() === dict.values`
* Postfix `{}` to get indices/keys: `dict{} === dict.keys`

Sub `$` checks subarrays, subsets, and substrings. It can do this along multiple axes at once:
```
[[1,2]   $   [[1,2,3]
 [4,5]]       [4,5,6]
              [7,8,9]]
              
"++" $ ["x++", "x--", "x++"]
```
The 1st example checks the submatrix, even though it is not a direct sequence of elements like `[1,2,3]`. Same goes for the 2nd example, which is checking a nested substring `"++"` within a list of strings.

## Boolean

[](#table-of-contents)
| op | name | instance | notes |
| -- | ----- | ------- | ----- |
| `?` | truthy | `?0 == ?[] == false` | returns truthy/falsy values
| `??` | existence | `??null == false` | false if null or nonexistent
| `&&` | and | `false && true == false` | short-circuit and
| `\|\|` | or | `false \|\| true == true` | short-circuit or

* Use `T`, `F`, `U` shorthands for `true`,`false`,`null`
* Truthy/Falsy rules mimic Python — empty == falsy, 0 is falsy, etc.
* Conditionals coerce to truthy values if not already boolean
* Combine truthy into `?.` to apply elementwise on lists: `?.[-1,0,1,2,0] === [T,F,T,T,F]`
* Existence `??` returns `false` if null, `true` otherwise
* Short-circuit and `&&` returns `false` if its first argument is `false`
* Short-circuit or `||` returns `true` if its first argument is `true`

## Logex

[](#table-of-contents)
| op | name | instance | notes |
| -- | ----- | ------- | ----- |
| `!` | not | `!2 == 3` | logically negates value/object
| `&` | and | `1&2 @ [1,2,3,4]` | both 1 and 2 in array
| `\|` | or | `0\|1 @ [1,2,3,4]` | either 0 or 1 in array
| `!&` | nand | `0!&1 @ [1,2,3,4]` | not both 0 and 1 in array
| `!\|` | nor | `0!\|5 @ [1,2,3,4]` | neither 0 nor 5 in array
| `><` | xor  | `0><1 @ [1,2,3,4]` | either 0 or 1 in array, but not both

Not `!` logically negates the object, not the value. In any evaluation returning `true`, the notted object returns `false`. It is not simply flipping `true` values to `false` and vice versa. This highlights the difference between `~` and `!`. For instance: `![T,F] === [T,T]` is `true` because `[T,F]` doesn't match `[T,T]`. But `~[T,F] => [F,T] === [T,T]` is `false` because the flipped booleans don't match `[T,T]`. 

Logexes (logical expressions) are thus logical objects representing many cohabiting possibilities. Logex operators have very high precedence. Everything is a logex by definition — any object is considered a logex of *itself*.

## Metalogic

[](#table-of-contents)
| op | name | instance | notes |
| -- | ----- | ------- | ----- |
| `<=>` | equivalence | `!1\|!2 <=> 1!&2` | DeMorgan's Law
| `==>` | implication | `1&2 ==> 1\|2` | if both, then either is also true
| `>=<` | inequivalence | `1&2 >=< 3\ |4` | different logical universes

While `!2 === 3` is `true`, `!2 <=> 3` is `false`, since they don't represent the same logical universes. `!2` is *everything* except `2`, `3` is just `3`.

Equivalence `<=>` is useful in scenarios where `===` only matches across arrays/patterns, but not the same fundamental objects.

## Pattern
[](#table-of-contents)
| op | name | instance | notes |
| -- | ----- | ------- | ----- |
| `:` | wildcard | `[:] === [123]|["ignore"]` | matches anything
| `_` | match | `[_,_/2] === [2,1]|[6,3]` | matches each tracked occurence
| `*` | 0* | `[1,:*,5] === [1,5]|[1,2,3,4,5]|[1,"ignore",5]` | matches wildcard 0* times
| `+` | 1+ | `[1,:+,5] === [1,2,3,4,5]|[1,"ignore",5]` | matches wildcard 1+ times
| `?` | optional | `[1,2?,3] === [1,3]|[1,2,3]` | matches 0 or 1 times
| `?=` | lookback | `[?=5,6,7] === [6,7]` | matches pattern following lookback

Pattern syntax steals from Numpy and regex syntaxes to bring regular expressions to the array realm.

## Combinators

[](#table-of-contents)
| op | name | instance | notes |
| -- | ----- | ------- | ----- |
| `!°` | not | `0 !@ [1,2,3,4]` | negates membership
| `.°` | inner | `[1,2] .* [3,4] == [3,8]` | inner product
| `<>°` | outer | `[1,2] <>+ [0,10] == [[1,2],[11,12]]` | outer sum
| `~°` | swap | `a ~* b == b * a` | swaps operator order / associativity
| `(°)` | scan | `[1,2,3,4](+) == [1,3,6,10]` | cumulative sum scan

Combinators are special operators which can combine with other operators for *special effects*. 

* `!°` can combine with any operator, but is typically reserved for conditionals/booleans. Curiously, `!?:` can make a notted ternary conditional.
* Binary `.°` is fairly unnecessary for arithmetic/comparators (which are already elementwise). Array/membership is more like it: `.@`, `.$`, `.++`, `.**` 
* Unary `.°` does reductions. So `.+` is a sum: `.+[1,2,3] == 6`. `.==` checks whether every element is equal: `.==[1,1,1,1] == true`. 
* `<>°` pairs up each scalar from the 1st with every combination from the 2nd
* `~°` swaps associativity of operators, and `.~°` does a right-fold reduction (as opposed to left-fold default)

Scans follow a rule: `data(operator, window)`, where the `window` is optional:
```
[1,2,3,4,5](+)   === [1,3,6,10,15]               //does a rightward plus scan of the entire list
[1,2,3,4,5](*,2) === [2,6,12,20]                 //does a pairwise product
[1,2,3,4,5](:,3) === [[1,2,3],[2,3,4],[3,4,5]]   //grabs moving windows of size 3
[1,2,3,4](:) === [[1],[1,2],[1,2,3],[1,2,3,4]]   //grabs expanding window subarrays
```

### Examples

The examples section here is scant, and will be filled soon with tried and true examples. For those of you impatient, please check out ChatGPT's fairly accurate attempts at solving Noda programming questions— https://imgur.com/gallery/Tqh7SRH


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
   num :=:
      0:  "Monday"
      1:  "Tuesday"
      2:  "Wednesday"
      3:  "Thursday"
      4:  "Friday"
      5:  "Saturday"
      6:  "Sunday"
            
day(3)      //"Thursday"
```

#### Maximum Nested Parentheses (Switch Case)
Task: Calculate the maximum depth of nested parentheses of a string `s`—
```csharp
max_nested(s):= max(s(*"()":+-1)(+)) 
```

#### Prime Divisibility
```csharp
is_prime(n):= none(n %% [2:n])
```

```python
def is_prime(s):
    for i in range(2, n):
        if (n % i == 0):
            return False
    else:
        return True
        
not any(n % i == 0 for i in range(2,n))
```

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

pascal_triangle(n):= C([:n],[:[:n]])

diff(g):= .+(2g-1)(0) <>+ .+(2g-1)(1)

pluralize(word):= word * ("ch"|"sh"|"s"|"x"|"z"<-<word ? "es" : "s")

liebniz_pi = .+-4/[1:2:]
e = .+/!![0:]

npv = .+(costs./(1+r)^[0:])

norm(X):= ^/.+X.^2
softmax(X):= e^X/.+e^X

checkMatrix(m):= (1/\m) === (I(m)\/^I(m))

[][1,2,3,4] == [[1],[1,2],[1,2,3],[1,2,3,4]]
{}[1,2,3,4]

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



