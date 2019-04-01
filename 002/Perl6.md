# Challenge
`Write a script or one-liner to remove leading zeros from positive numbers.`
You can find it [here](https://perlweeklychallenge.org/blog/perl-weekly-challenge-002/)
# This solution uses Perl 6 :butterfly: Grammer
at first here is the code : 
```perl6
grammar Grammer {
    token TOP {[<int>]? [<decimal>]?}
    token decimal {<dot><digit>}
    token int {<zeros>? [<digit>]?}
    token digit { \d+ }
    token dot { '.' }
    token zeros {[0]+}
}
my $match = Grammer.parse(@*ARGS[0]);
my $number =  $match<int><digit> ~ $match<decimal>;
say $number;
```
at the first line we simply creat a Grammer With name 'Grammer' which is a Class that have methods (rules, tokens and regexes)
as documented [here](https://docs.perl6.org/language/grammars)
let's get the zeros token first : 

`[0]+` matches any number of Zeros in the input

`dot` token : matches only `.`

`digit` token : matches any number of digit characters

`int` token : uses zeros token and digit token to match the first part of the number incase it is decimal.

and i made it's parts optional using `?` as the first part may not contain zeros or digits input ex: .53 , 1.52

`decimal` token : matches a dot `.` followed by any number of digit characters

and putting them together in the main `TOP` token gives us the full number 

then we Parse the input from command line `Grammer.parse(@*ARGS[0]);`

then we assign the values to the `$number` var , but i used only this part of the match `$match<int><digit>` which returns the digit characters in the first part of the number then added to it the decimal part `$match<decimal>`
