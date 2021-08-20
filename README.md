# gtlang
simple programming language

Sameple code:


==========================================================================================================================
#!/bin/gtlang
use_language_file "./en-us.gtlang" // using translation file
include "source_a.gtc" // inclusion
/*
    <html>
    multiline comments<br />
    could use html tags in here<br />
    <b>bold text</b>
    </html>
*/
$var:Hello world // <html>assign "Hello world" to variable name <b>var</b></html>
@echo var has value $var // output: var has value Hello world
$x,$y:0,1 // assign multiple vars in 1 command
1+1
@echo $@ //$@ get previous command's result, output: 2
//=================================================================
$a:0;$b:1;@echo Hello // multiple commands in 1 line
$a:Some long string that we should put it on several lines ...
        instead of just one line\, becase is will be much ...
        prettier that way
//=================================================================
@func: //define a function
    @echo this is func\, enjoy\.
@func // output: this is func, enjoy.
$func_var : @func
@$func_var // output: this is func, enjoy.
@func1 $a, $b:7: //define a function with optional param $b
    @echo \if fun1 $a // "if" is a keyword.
@func1 $a, $b //define a function with optional param $b
    return $a-$b, $a+$b // return multiple values.
//regex-named function
@add{[0-9]*} $num:
    return $num + $func_name_params[0]
@add1 1 // return 2
@add2 2 // return 4 
3 @add4 // return 7
(3 @add4) @add5 // return 12
//=================================================================
if $a>2
    @echo abc
for 10 times
    @echo $time + "\n"
for 11 $i
    @fun abc
for $i=0,$i<222,$i++
    @echo xyz
while $a<333
    $a++
    echo abc
for 10 times
//=================================================================
// complex function
$p:$q:0
@fun2 $a $b: //com
    for 11 $i
        for $i=0,$i<222,$i++
            @echo xyz
            if $$q=0 // global variable $q=0
                if $$p=0// global variable $p=0
                    @echo hi
                else
                    @echo hello
                $$q:1
                @unset $$p // delete Global $p
//=================================================================                    
^Human: // class Human
    $name
    private $spicies: Homo Sapien //space before Homo is trimmed
    @printinfo
        @echo $name \; $spicies
    @new $name // constructor
        $this.$name : $name
$human:(new ^Human)
$human.$name=John\, Smith
$human.(@printinfo) // John, Smith ; Homo Sapien

^Student << ^Human: // class Student extends class Human
new ^Student Annie Brown
$@.(@printinfo) // Annie Brown ; Homo Sapien
//=================================================================
@fun0 $a $b:
    $result $a/$b
    defcat //default catch
        ^MathException $e
            @echo MathException $e
        ^Exception $e
            @echo Exception $e
    deffin //default finally
        return $result

try
    $a/$b
catch ^MathException $e
    @echo MathException $e
catch ^Exception $e
    @echo Exception $e

defcat //default catch for main
    ^MathException $e
        @echo $e
    ^Exception $e
        @echo $e
deffin //default finally for main
    @exit 0
===============================================================================================================================
