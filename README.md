# Regex-Tutorial
A tutorial explaining how to understand a regular expression built to match a url 

## Summary

In this tutorial we will be examining the regular expression that defines how we Match a URL in a search. 
The regular expression is as follows:
Matching a URL: `/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/`

When we utilize this expression in our code it allows us to check against any user input and match it with the set parameters of the expression itself. It may look like a collection of random characters bashed together, but each part has a purpose. Later in this tutorial we will be dissecting and learning how this particular expression helps us match user input to the parameters hidden in the regular expression above. 

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [The OR Operator](#the-or-operator)
- [Flags](#flags)
- [Character Escapes](#character-escapes)

## Regex Components
```md
`/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/`
```
### Anchors
The characters in the above expression ``` ^ ``` and ``` $ ``` which come at the beginning and ending of the expression are what we would call Anchors. More specifically the ``` ^ ``` is our anchor that signifies the beginning of the string that matches a range of possible charaters that follow it. You can feed a literal string after the anchor, or as we do with regular expressions we feed it a series of parameters that help us open up the possibility for more correct answers than just one literal one. 
The ``` $ ``` anchor is what signifies the end of the expression. So much like the beginning anchor it signifies the expression that proceeds it contains the string we are looking for.

The text between these anchors fall under one of the following categories and further specify the types of characters or information that we are looking for when taking user input into account. 
### Quantifiers

### Grouping Constructs

### Bracket Expressions

### Character Classes

### The OR Operator

### Flags

### Character Escapes

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
