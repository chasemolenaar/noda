# Noda
An Array-Oriented, OOP, FP, and Logical Programming Language for Concise Pseudocode-like Scalability

'Noda' is the faux-pluralization of the Latin word 'nodum', meaning 'knot'. It was named after the topological subfield of Knot Theory. Though many introduced to the language seem convinced it means "No duh!", which is equally accurate. ~~where I have conducted heavy research into devising an algorithm to solve the infamous Unknotting Problem. Neither Python nor Julia were up to the task, so I devised a new language.~~

Noda is ambitious. It seeks to bring the concision and power of array languages like APL to the readability and friendliness of Python. To make so accessible functional programming constructs like map-filter-reduce they seem trivial to kindergarteners. To popularize Prolog-like logical deduction for an evermore AI-driven world. To devise a language that is fun to write, quick to type, cool to look at, and pleases beginners and experts alike.

It is a language designed by Data Scientists, for Data Scientists.

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
! && || & | !! >< -> <-> <=> ==> >=<
~~ /\ \/ >-< >>> <<< 
+ - * / ^ % ^/ ^! \
= °= := ::= =< ?? 
== != > < >= <= ~= %% === !== 
-< +< <> -*
?: !: : |: ><: :: ; ;; ? 
# @ $ >-> <-< 
, << >> ++ -- \\ ** ^^
% ~ ` ~> ~< <~> ->> ,, +* =*
>==< >==> <==< <==> <<>>
=> =: :=: .:
!° °= °=> °: °:: ~° .° .~° [°] 
+- -+ °,° °|° °&° 
true false null *> +>
[] {} [} [) ()
^^ WE need a precedence table for this shit
```
#### Core Ideas
1. Noda

#### Basic Data Structures
```js
[]    list        [1,2,3,4,5]
[:)   range       [1:5) == [1,2,3,4]; [:5] == [0,1,2,3,4,5]
[::)  interval    [2::6)  // [2,6) in math, exclusive of 6
[;]   matrix      [1 2; 3 4]
{}    set         {1,2,3,4}
{:}   dict/map    {"a": 1, "b": 2, "c": 3}
{::}  dataframe   {["a","b","c"]:: [[4,5,6],[7,8,9],[10,11,12]]}
(:)   dat​etime   (8:35:42)  // 8 hours, 35 minutes, 42 seconds
""    str​ing     "Hi programmer!"
^""   fstring     ^"Hello {name}"
''    regex       '\d+'
1><2  logex       4&(!100|400)   // logical universe encapsulation
[_]   pattern     [_,_+1]        // pattern for consecutive pairs
```

#### Arithmetic
Arithmetic is like Julia, but also features a root operator.
```csharp
+   plus       2 + 3 == +5
-   minus      2 - 3 == -1
*   times      2 * 3 == 6
/   divide     3 / 6 == 0.5    /4 == 1/4 == 0.25
^   exponent   2 ^ 3 == 8
%   modulus    27 % 13 == 1
^/  root       3^/125 == 5     ^/100 == 10
\   ldivide    Ax = b   ==>    x = A\b     // Also for quotients?? Or class-defining operators?
```

#### String Arithmetic
String arithmetic is partly inspired by Julia, with many other features. All operations here apply to regexes too.
```csharp
+   space      "hi" + "there" == "hi there"
*   concat     "match" * "box" == "matchbox"
°   literal    "ship""yard" == "shipyard"
/   remove     "assassin"/"ass" == "in"
^   repeat     "na" ^ 4 == "nananana"     // batman!!
%   modulus    // 27 % 13 == 1
^/  strip      "xX_"^/"XXxUsernamexXX" == "Username"    ^/" \n\n   stuff  " == "stuff"
```
^Though frankly there should be a little section showing how these are used in unary fashion

Pattern Operations

```csharp
-<  split     "2/14/23"-<"/" == ["2","14","23"]     -<"Jane Smith" == ["Jade","Smith]   // can also be used on regexes
+<  snip      "2/14/23"+<"/" == ["2/","14/","23"]
<>  findall   "123def56"<>'\d+' == ["123","56"]
%   remainder "try-method" % "-" == "method"
```

#### Comparators

```csharp
==  equal
!=  inequal
<   less
<=  less or equal
>   greater
>=  greater or equal
%%  divisible
=== equivalent
!== nonequivalent       'str' !== "str"
~=  match               Also !~ too?
```

#### Assignment
```js
=   assign
°=  reassign
:=  func​tion
::= cl​ass
=<  vacuum
=*  dynamite
??  coalesce
```

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
```

#### Membership Operators
```csharp
#   length
@   in/at
$   subset/subsequence
>-> starts
<-< ends
```

#### Special Set Operators
```csharp
%   reverse
~   complement
`   transpose  
~<  tulip         ascend
~>  umbrella      descend
<~> hotdog        rotate mustache
->> pine          reshape
,,  zip
+*  cosmos
```

#### Relational Operators
```csharp
>==<  inner join
>==>  right join
<==<  left join
<==>  outer join
<<>>  disjoint

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

#### Logic Operators

```csharp
?   bool
&&  and
||  or
```

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
