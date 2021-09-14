# Learn Regex

Regular expressions contain a series of characters that define a pattern of text to be matched to make a filter more specialized, or general. In this tutorial we will be going over basic information about regex that would help you understand and learn regex easily.

## Summary

A regular expression (shortened as regex or regexp; also referred to as rational expression) is a sequence of characters that specifies a search pattern. Usually such patterns are used by string-searching algorithms for "find" or "find and replace" operations on strings, or for input validation.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [The OR Operator](#the-or-operator)
- [Flags](#flags)
- [Character Escapes](#character-escapes)
- [Closing Remark](#closing-remark)
- [Author Info](#author-info)

## Regex Components

### Anchors

Anchors belong to the family of regex tokens that don't match any characters, but that assert something about the string or the matching process. Anchors assert that the engine's current position in the string matches a well-determined location: for instance, the beginning of the string, or the end of a line.
For example:

```javascript
let str = "Hassan";
console.log(/^H/.test(str));
```

_Output_

```javascript
true;
```

_The /^H/ match any text that starts with the letter J. It returns true_

---

### Quantifiers

Quantifiers specify how many instances of a character, group, or character class must be present in the input for a match to be found.

Exact count {n}. A number in curly braces {n}is the simplest quantifier. When you append it to a character or character class, it specifies how many characters or character classes you want to match.

_For example, the regular expression /\d{4}/ matches a four-digit number. It is the same as /\d\d\d\d/:_

```javascript
let str = "ECMAScript 2020";
let d = /\d{4}/;

let result = str.match(d);

console.log(result);
```

_Output_

```javascript
["2020"];
```

---

### Grouping Constructs

Grouping constructs delineate the subexpressions of a regular expression and capture the substrings of an input string. You can use grouping constructs to do the following: 
1. Match a subexpression that is repeated in the input string. 
2. Include a subexpression in the string that is returned by the Regex

_An example, email format is: name@domain. Any word can be the name, hyphens and dots are allowed. In regular expressions that’s [-.\w]+._

```javascript
let regexp = /[-.\w]+@([\w-]+\.)+[\w-]+/g;

console.log("my@mail.com @ his@site.com.uk".match(regexp));
```

_Output_

```javascript
// my@mail.com, his@site.com.uk
```

---

### Bracket Expressions

A bracket expression is either a matching list expression or a non-matching list expression. It consists of one or more expressions: ordinary characters, collating elements, collating symbols, equivalence classes, character classes, or range expressions.
_An example:_

```javascript
"kangaroo".match(/[abcd]/); // -> matches 'a'
```

_You will often see ranges of the alphabet or all numerals. [A-Za-z] [0-9] Remember that these character sets are case sensitive, unless you set the i flag._

```javascript
"kangaroo".match(/[a-d]/); // -> matches 'a'
"kangaroo".match(/[A-D]/); // -> no match
"kangaroo".match(/[A-D]/i); // -> matches 'a'
```

---

### Character Classes

Character class can tell the regex engine to match only one out of several characters.

_A character class allows you to match any symbol from a certain character set. A character class is also called a character set. Suppose that you have a phone number like this:_

```javascript
"+1-(408)-555-0105";
```

_Now, you can turn the phone number into a plain number as follows:_

```javascript
let phone = "+1-(408)-555-0105";
let re = /\d/g;

let numbers = phone.match(re);
let phoneNo = numbers.join("");

console.log(phoneNo); // -> 14085550105
```

---

### The OR Operator

_The OR operator, also known as alternation which is it's term in regular expression._

_In a regular expression it is denoted with a vertical line character_ **|**

_For instance, if we need to find the programming languages: HTML, PHP, Java or JavaScript._

_The corresponding regexp:_ html | php | java(script) ?.

_A usage example:_

```javascript
let regexp = /html|php|css|java(script)?/gi;

let str = "First HTML appeared, then CSS, then JavaScript";

console.log(str.match(regexp));
```

_Output_

```javascript
// 'HTML', 'CSS', 'JavaScript'
```

---

### Flags

_Regular expressions may have flags that affect the search.
There are only 6 of them in JavaScript:_

```javscript
"i"
```

With this flag the search is case-insensitive: no difference between A and a.

```javscript
"g"
```

With this flag the search looks for all matches, without it – only the first match is returned.

```javscript
"m"
```

Multiline mode (covered in the chapter Multiline mode of anchors ^ $, flag "m").

```javscript
"s"
```

Enables “dotall” mode, that allows a dot . to match newline character \n.

```javscript
"u"
```

Enables full Unicode support. The flag enables correct processing of surrogate pairs.

```javscript
"y"
```

“Sticky” mode: searching at the exact position in the text.

---

### Character Escapes

_Let’s say we want to find literally a dot. Not “any character”, but just a dot._
_To use a special character as a regular one, prepend it with a backslash: `\`._

_That’s also called “escaping a character”._
_For example:_

```javascript
console.log("Chapter 5.1".match(/\d\.\d/)); // 5.1 (match!)
console.log("Chapter 511".match(/\d\.\d/)); // null (looking for a real dot \.)
```

_Parentheses are also special characters, so if we want them, we should use \(. The example below looks for a string "g()":_

```javascript
console.log("function g()".match(/g\(\)/)); // "g()"
```

_If we’re looking for a backslash \, it’s a special character in both regular strings and regexps, so we should double it._

```javascript
console.log("1\\2".match(/\\/)); // '\'
```

---

## Closing Remark

Thank you for taking the time to read out my tutorial. I hope you learned something out of this tutorial that would benefit you in form or another.

---

## Author Info

I am always open to meet new engineers and developers. I can be reached via email cs@developer.com.
My name is Hassan Yusuf and here is the link to my Portfolio: [www.hassanyusuf.com](https://hassany99.github.io/Portfolio-2/)
