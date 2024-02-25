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

The first group ``` (https?:\/\/) ``` contains a modifier of ``` ? ``` that indicates here that it is a non-capturing section. What that essentially means is that the protocol does not become part of the URL data that we are actively using or manipulating but it does help to separate that particular bit of information from the sections that follow. 

The remaining groups are all capturing information that we can access separately in the case that we would need to or want to further analyze or process the input data. 

``` ([\da-z\.-]+) ``` Captures the domain name (such as www.website)

``` ([a-z\.]{2,6}) ``` Captures the top-level domain name (such as .com)

``` ([\/\w \.-]*) ``` Captures the entire path (such as /innerPage/evenDeeperPage)

``` [\/\w \.-] ``` Captures a single path within the entire pathway (such as /innerPage out of /innerPage/evenDeeperPage or even more lengthy paths)

Understanding that each parentheses separates bits of information that we are looking for in this regular expression helps us better visualize how URLs work and can be manipulated within our established code.

### Bracket Expressions
Within the regular expression that we have been working diligently to unravel, we see several groups of characters within brackets. These sections are broadly known as Bracket Expressions and within those we see something more specifically known as Character Classes. While these terms are used interchangeably they are still separate ideas. Not all Bracket Expressions are Character Classes while all Character Classes are contained within Bracket Expressions. 

``` [\da-z\.-] ``` 

``` [a-z\.] ```

```[\/\w \.-] ```

These brackets contain our specifications for what types of characters we are looking for when taking user input into account. We will delve further into what types of characters we are looking for when we discuss Character Classes later on. 

Much like our Grouping Constructs, our brackets enclose the information that we are looking for and allow us to better manipulate what we are looking for. This lowers the variability from infinity to exactly the ranges or options that we feed into the brackets as defined by the character classes within them.

### Character Classes
To expand upon the Bracket Expressions we can finally dissect each one and see what Character Classes do within our regular expression. 

``` [\da-z\.-] ``` This class is looking for multiple things and we can break this expression down further into its pieces. ``` \d ``` looks for any digit. ``` a-z\ ``` looks for a lowercase letter from "a" to "z". ``` . ``` looks for exactly what it looks like, a literal dot or period. ``` - ``` looks for exactly what it looks like as well, a literal hyphen. With this particular expression we see that we are looking for at least one of the following: digits, letters "a" through "z", ".", and or "-" but not limited to one of these. 

``` [a-z\.] ``` This class is looking for two potential characters. ``` a-z\ ``` specifies that we are looking for lower cased letters from "a" to "z". ``` . ``` specifies that we are looking for a literal dot or period. All together in this expression we are looking for a range of two to six of the following: letters "a" through "z" and or "." but limited to two through six of them as previously explored within our Quantifiers section. 

```[\/\w \.-] ``` This class is looking for multiple things and we can break it down further as well. ``` \/ ``` specifies that we are looking for a forward slash "/". ``` \w ``` specifies that we are looking for any word. It may be hard to notice it but there is a ```  ``` that follows that specifies we are looking for a space between characters. And again ``` . ``` and ``` - ``` specifies that we are looking for either a dot/period or a hyphen. When we take this into account we can see that we are looking for zero or multiple of the following: "/", words, "." and or "-" to create the path portion of this regular expression. 

So to summarize what we have just explored, Character Classes work within a Bracket Expression along with any additional Quantifiers to create the parameters that we are looking for within our particular regular expression. 

### The OR Operator

### Flags

### Character Escapes

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
