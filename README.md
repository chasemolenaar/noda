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

#### Basic Data Structures
```csharp
[]    list        [1,2,3,4,5]
[:)   range       [1:5) == [1,2,3,4]; [:5] == [0,1,2,3,4,5]
[::)  interval    [2::6)       // [2,6) in math, exclusive of 6
[;]   matrix      [1 2; 3 4]   // 2-dimensionsal data structure
[}    ring        [1,2,3,4,5}  // loops on itself
{}    set         {1,2,3,4}    // unordered
{:}   dict/map    {"a": 1, "b": 2, "c": 3}
{::}  dataframe   {["a","b","c"]:: [[4,5,6],[7,8,9],[10,11,12]]}
""    string      "Hi programmer!"
^""   fstring     ^"Hello {name}"
''    regex       '\d+'          // regex matching "42069"
^''   fregex      ^'_*{name}_*'  // regex matching _____me____
!_|_  logex       4&(!100|400)   // logical universe encapsulation
[_]   pattern     [_,_+1]        // pattern for consecutive pairs
<>    empty       {} ~= <>       // matches to anything "empty"
```
Sections to be added—
1. Lists, rings, and sets
2. Ranges and Intervals

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
    coef       10n == 10 * n
/   divide     3 / 6 == 0.5    /4 == 1/4 == 0.25
^   exponent   2 ^ 3 == 8
%   modulus    27 % 13 == 1
^/  root       3^/125 == 5     ^/100 == 10
\   ldivide    Ax = b   ==>    x = A\b     // Also for quotients?? Or class-defining operators?
```

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
3. Make clear that == checks the value and can differ across structures where '' == "" and 0x1f == 31
4. Equivalence === checks the object identify, so '' !== "" for instance. (differently ordered dicts fall in this category, ^"" !== "")
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
,   comma
<<  append
>>  pop
++  concat
--  difference
\\  remove
**  intersect
^^  symdiff
.°  dot
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
5. Tulip & Umbrella (sorting) made simple. Also show usage in dataframes `Users[~<"length"]` `Users["last"=='Wu'|'Kim']`
   Make cool parallel with .<=(~<X) and .>=(~>X) and monotonicity (hence scans & reductions need to come first)
7. Usage of hotdog for rotation <~>. Unary <~>X rotates rightward once.
8. Using ->> to shape objects (lists->>lists, matrices->>matrices, str->>list, dict->>dict)
9. Zip examples shown simply, alongside Python. Recall that it deletes stuff


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

#### Functional Operators
```csharp
:=  define
=>  as/map
=:  filter
#   compose
-*  wand
:=: dogbone
.:  grapevine
```

## LOGIC

#### Coercive Logic Operators
```csharp
?   bool
&&  and
||  or
```
Each of these coerce non-booleans into boolean values. `?3 == true` 

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

Since !° is a combinator, you can use it on 

#### Metalogic Operators
```csharp
<=> equivalent
==> entail/imply
>=< nonequivalent
```


#### Bitwise Operators
```js
~~  complement
/\  and
\/  or
>-< xor
>>> rshift
<<< lshift
```



#### Procedural Operators
```csharp
:   if/elif       (|:  double-if)
><: else
::  loop
;   semicolon     (;; for break?)
?:  ternary       (?: !: try except)
```

#### Combinators
```csharp
!°  not
°:  switch        (but also +: and -: should be mentioned)
~°  swaperator
.°  reduce/elementwise
[°] scan
```

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



