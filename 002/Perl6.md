# Challenge
`Write a script or one-liner to remove leading zeros from positive numbers.`
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
