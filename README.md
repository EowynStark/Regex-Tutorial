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
The characters in the above expression ``` ^ ``` and ``` $ ``` which come at the beginning and ending of the expression are what we would call Anchors. More specifically the ``` ^ ``` is our anchor that signifies the beginning of the string that matches a range of possible charaters that follow it. You can feed a literal string after the anchor, or with regular expressions we can feed it a series of parameters that help us open up the possibility for more correct answers than just one literal one. 

The ``` $ ``` anchor is what signifies the end of the expression. So, much like the beginning anchor, it signifies the expression that proceeds it contains the string we are looking for.

The text between these anchors fall under one of the following categories and further specify the types of characters or information that we are looking for when taking user input into account. Continue reading this tutorial to delve deeper into each part and learn more. 

### Quantifiers
In this regular expression we have multiple quantifiers that help us specify how many times something may or may not occur. We will break this expression down by our grouping constructs, which is a topic we will discuss in more detail further on in this tutorial. 

The ``` ? ``` you see in the beginning section ``` (https?:\/\/)? ``` sets a number of times you may or may not see ``` http:// ``` or ``` https:// ``` to be zero to one time. This could be expanded to mean that this particular protocol section is optional. 

The ``` + ``` you see in the following section ``` ([\da-z\.-]+) ``` sets the number of times you may or may not see a set of characters indicated by the parameters listed inside the parentheses to be one or more times. This would be expanded to mean that there must be at least one character in the domain name that follows the optional protocol. 

The ``` { } ``` you see in the following section ``` ([a-z\.]{2,6}) ``` sets a range of times you may or may not see a set of characters indicated by the parameters immediately proceeding quantifier there. In this case we would see between two and six characters in the top-level domain that follows the domain name. 

The ``` * ``` you see in the following section ``` ([\/\w \.-]*) ``` sets a range of times you may or may not see the proceeding sets of characters to be zero or more times. This section would specify then that the path portion of the URL can be empty or it can contain multiple paths.

The ``` ? ``` you see in the last section ``` \/? ``` sets a range of times you may or may not see the proceeding characters to be zero to one times. In this case that would mean that the trailing forward slash is optional much like the protocol listed above. 

When we take all of these quantifiers together we can see that within each grouping construct we have variable characters that are both optional and not optional specified by the particular quantifying characters utilized. This makes for a dynamic regular expression that is better able to adapt to user input when dealing with the URL of our oftentimes complex websites. 

### Grouping Constructs
For the regular expression that we have been working to unravel, there are mutiple sections hidden within that are called Grouping Constructs. Each one of these can be utilized to capture different parts of a URL as they are being written. Some of them actively capture the information that is input whereas others do not separate that information as stringently from the rest of the information around it.

In the above section while working to understand the quantifying parameters of our regular expression we were utilizing the grouping built in to help us stay organized on what information was being limited and where. This is the essential purpose of grouping constructs. 

The first group ``` (https?:\/\/) ``` contains a modifier of ``` ? ``` that indicates here that it is a non-capturing section. What that essentiall means is that the protocol does not become part of the URL data that we are actively using or manipulating but it does help to separate that particular bit of information from the sections that follow. 



### Bracket Expressions

### Character Classes

### The OR Operator

### Flags

### Character Escapes

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
