# Regex-Tutorial
A tutorial explaining how to understand a regular expression built to match a url to user input

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
Within regular expressions there are times where we would like to allow for alternatives when attempting to match against a user's input. Predominantly you would see them written explicitly as a ``` | ``` but as you can notice with our particular expression there are none of those. While we do not appear to have any Or Operators with the absence of that character, there are two implicit Or Operators hidden within. As we discuss these two hidden Or Operators we will see why including alternatives may be quite useful when utilizing a regular expression. 

In the ``` (https?:\/\/)? ``` section the ending "?" acts as an Or Operator as well as a Quantifier to specify that we are looking for http:// OR https:// either zero to one times. The reason this is an implicit Or Operator lies in the use of the quantifier itself behaving as an optional parameter. 

In the ``` [a-z\.] ``` section the "." acts as an Or Operator in much the same manner as the "?" from the previous example. It indicates implicitly that any lower cases letter or dot/period will be accepted for that particular set of parameters. 

Essentially in this entire regular expression most of the Or Operators are serving a dual purpose because they function more primarily as a Quantifier or as a Character Class to give us non-specifically what we are looking for. 

### Flags
Regular expressions can sometimes include characters called Flags that indicate we are looking for user input in a particular way and using these characters modifies the pattern we use to look within our given input. 

For example if at the end of the expression ``` `/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/` ``` we saw a ``` g ``` tacked onto the end after the closing ``` / ``` that would indicate that we are looking for a global match. This would limit the results to be ones that match all occurrences within the string as opposed to matching the first one.  

In our particular example of a regular expression we do not have a Flag included to strictly specify how exactly we are trying to limit the results of the search against our intended user input. 

### Character Escapes
Character Escapes are routinely used in order to help us utilize characters that can have multiple uses in the code as well as in our regular expression specifically. We wouldn't want the expression to confuse metacharacters with parameters for characters we are actually attempting to include. We will explore which characters have escapes in order for the expression to read them as the characters as opposed to characters included for syntax and pattern purposes. 

```\d``` represents any digit 0-9 as we discussed previously in the character class section. When combined in the entire class ```[\da-z\.-]``` it helps the class identify that we are looking for digits.

```\w``` represents any word character as previously mentioned in the character class section. Because it is included in the whole class ```[\/\w \.-]``` the expression recognizes that we are looking for characters that appear in any ASCII alphanumeric phrase including underscores but not including spaces. Which helps us understand then why there is a space after that character escape to help us then include spaces in that particular section of this expression. 

```\.``` represents a literal dot or period as previously explained in the character class section. In the character class sections that include this particular escape it helps us include the "." that you can often find in URL patterns without having the expression itself confuse the "." for an operational character that could mean something else.

What all of these escapes share is the inclusion of a ```\``` before the character which acts as a flag within the expression to denote that the character that follows behaves differently than had it not come immediately after a "\". 

## Author

