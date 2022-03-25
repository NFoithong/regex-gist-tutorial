# Regex or Regular Expression
Basically, a regular expression is a pattern describing a certain amount of text. Their name comes from the mathematical theory on which they are based. But we will not dig into that. You will usually find the name abbreviated to "regex" or "regexp". This tutorial uses "regex", because it is easy to pronounce the plural "regexes". On this website, regular expressions are shaded gray as regex.

# Summary Matching a Valid Date
Matches a date in yyyy-mm-dd format from 1900-01-01 through 2099-12-31, with a choice of four separators.
```md
^(19|20)\d\d[- /.](0[1-9]|1[012])[- /.](0[1-9]|[12][0-9]|3[01])$ 
```

## Table of Content
- [Anchors](#anchors)
- [Alternation](#alternation)
- [Back-references](#back-references)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [Grouping and Capturing](#grouping-and-capturing)

## Regex Components

### Anchors
```
^ ---> Matches the beginning of the string, or the beginning of a line if the multiline flag (m) is enabled. This matches a position, not a character.
$ ---> Matches the end of the string, or the end of a line if the multiline flag (m) is enabled. This matches a position, not a character.
```
make sure the entire variable is a date, and not a piece of text containing a date.

### Alternation (OR Operator)

```
| ---> Acts like a boolean OR. Matches the expression before or after the |.
It can operate within a group, or on a whole expression. The patterns will be tested in order.
```
allow the first two digits to be 19 or 20. <br>
```(19|20)``` The year is matched ```(19|20)\d\d```.
The parnetheses are mandatory. The regex engine would go looking for 19 or the remainder of the regular expression, which matches a date between 2000-01-01 and 2099-12-31.

### Back-references
```
\ ---> refer to a previous part of the matched regular expression. Back-references are specified with backslash and a single digit (e.g. ‘\2’). 
```
If you want to require the delimiters to be consistent, you could use a backreference. ```^(19|20)\d\d([- /.])(0[1-9]|1[012])\2(0[1-9]|[12][0-9]|3[01])$``` will match ```1999-01-01``` but not ```1999/01-01```.

### Bracket Expressions
```
[] ---> Match any character in the set.
```
The month is matched by ```0[1-9]|1[012]```, again enclosed by parentheses to keep the two options together. By using character classes, the first option matches a number between 01 and 09, and the second matches 10, 11 or 12.

### Character Classes
```
\d ---> matches any digit character (0-9).
```

### Grouping and Capturing
```
() ---> Groups multiple tokens together and creates a capture group for extracting a substring or using a backreference.
```
(0[1-9]|1[012])


## Author
Find more works at GitHub: [NFoithong](https://github.com/NFoithong)<br>
Get in touch: n.foithong1983@gmail.com
