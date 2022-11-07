# Noda
An Array-Oriented, OOP, FP, and Logical Programming Language for Concise Pseudocode-like Scalability

'Noda' is the faux-pluralization of the Latin word 'nodum', meaning 'knot'. It was named after the topological subfield of Knot Theory. Though many introduced to the language seem convinced it means "No duh!", which is equally accurate. ~~where I have conducted heavy research into devising an algorithm to solve the infamous Unknotting Problem. Neither Python nor Julia were up to the task, so I devised a new language.~~

Noda is ambitious. It seeks to bring the concision and power of array languages like APL to the readability and friendliness of Python. To make so accessible functional programming constructs like map-filter-reduce they seem trivial to kindergarteners. To popularize Prolog-like logical deduction for an evermore AI-driven world. To devise a language that is fun to write, quick to type, cool to look at, and pleases beginners and experts alike.

It is a language designed by Data Scientists, for Data Scientists.

Hook the reader in with some twist, some draw to Noda's design. Why it's different, better than Python or other languages. Why it's powerful, terse, scalable. Something they can grasp quickly, without thinking.

Feature correspondent/equivalent Python code shown everywhere along the way, so the user is never confused as to what your syntax does.

Why does terseness matter? Why it isn't everything.

Explanation of awesome, terse examples, with equivalent Python and APL code to match.

We need a showcase of every oeprator's usages :)

Expectations— 
Let `°` represent any operator, `//` and `/* */` enclose comments, code comparisons to Python will be written in tandem. Nodan operators 

```
block of code example?
```

Does this `x` work?

```csharp
(<<,at)(L,n,i):= [*L[:i),n,*L(:i]]

// comment test
/* multiline comment test */
// /* */
? && || ! & | !! >< -> <-> <=> ==> >=< (!& and !| &!)
~~ /\ \/ >-< >>> <<< 
+ - * / ^ % ^/ ^! \
= °= := ::= =< ?? 
== != > < >= <= ~= !~ %% !% === !== 
-< +< <> -*
?: !: ?. !. : |: ><: :: ; ;;
# @ $ >-> <-< 
, << >> ++ -- \\ ** ^^
% ~ ` ~> ~< <~> ->> ,, +* =*
>==< >==> <==< <==> <<>> (>>=> <<=< >><<)
: => := =: :=: .:
!° °= °=> °: °:: ~° .° .~° [°] 
+- -+ °,° °|° °&° 
true false null *> +>
[] {} [} [) ()
^^ WE need a precedence table for this shit
```
#### Core Ideas
1. Noda

Noda targets both a Python audience. Noda is heavily inspired by Python, so it's safe to assume that constructs will look like Python if unspecified.
This tutorial assumes you know some Python....

#### Ground Rules
1. Noda indexes by 0, which is the superior choice
2. Noda is indentation sensitive, like Python
3. 

#### Basic Data Structures
```csharp
[]     list        [1,2,3,4,5]      // standard list/array
()     tuple       (1,2,3,4)        // similar to list
{}     set         {1,2,3,4}        // unordered
[}     ring        [1,2,3,4,5}      // loops on itself

[:)    range       [1:4) == [1,2,3] // range(1,4)
[::)   interval    [2::6)           // [2,6) in math, excludes 6
[;]    matrix      [1 2; 3 4]       // 2-dimensionsal data structure
{:}    dict        {"a": 1, "b": 2, "c": 3}
{::}   dataframe   {["a","b","c"]:: [[4,5,6],[7,8,9],[10,11,12]]}

""     string      "Hi programmer!" // regular string
^""    fstring     ^"Hello {name}"  // f"Hello {name}" equivalent
''     regex       '\d+'            // regex matching "42069"
^''    fregex      ^'_*{name}_*'    // regex matching "___me___"

!_|_   logex       4&(!100|400)     // logical universe encapsulation
[_+_]  pattern     [_,_+1]          // pattern for consecutive pairs
{_:_}  map         {_%%2: "even"}   // like dict, but pattern-matching
<>     empty       {} ~= <>         // matches to anything "empty"
```
Lists `[]`, sets `{}`, and tuples `()` behave similarly to Python. Lists are ordered, sets are not, tuples are immutable. 
Rings `[}` are similar to lists, but they loop back on themselves and can be indexed anywhere: `[0,1,2,3}[4] == [0,1,2,3}[0] == 0`
Ranges `[:)` are iterables which generate lists, often used for slicing. Use brackets `[`,`]` for inclusive, parens `(`,`)` for exclusive: `[1:4] == [1,2,3,4]`/`[1:4) == [1,2,3]`/`(1:4] == [2,3,4]` (doubly exclusive parens `(1:4)` is not supported). Omit one of the numbers to start at 0 or indicate an infinite range: `[:3] == [0,1,2,3]`/`(:3] == [1,2,3]`/`[0:] == [0,1,2..]`. {insert image here from presentation on ranges}. {mention linspace and stepwise}. 

![image](https://user-images.githubusercontent.com/84992695/200396390-b1cc877c-803d-45de-864b-5d8a91acc4f0.png)
![image](https://user-images.githubusercontent.com/84992695/200396524-b24a112d-ccd1-400c-a872-55775bbea1fe.png)

<img src="https://user-images.githubusercontent.com/84992695/200396390-b1cc877c-803d-45de-864b-5d8a91acc4f0.png" width="200">


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



#### Arithmetic
Arithmetic is like Julia, but also features a root operator.
```csharp
+   plus       2 + 3 == +5
-   minus      2 - 3 == -1
*   times      2 * 3 == 6
°   coef       9​n == 9 * n
/   divide     3 / 6 == 0.5    /4 == 1/4 == 0.25
^   exponent   2 ^ 3 == 8
%   modulus    27 % 13 == 1
^/  root       3^/125 == 5     ^/100 == 10
\   ldivide    Ax = b   ==>    x = A\b     // Also for quotients?? Or class-defining operators?
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
%   modulus    "try-my-lang" % "-" == "my-lang"     
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



