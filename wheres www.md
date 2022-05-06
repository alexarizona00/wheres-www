# Wheres Waldo's WWW

This is going to be both a high level and a nitty gritty breakdown of a regex built to isolate URLs!

## Summary
Want to find a URL in a sea of information? Don't know if its a .net, .com or .org? Use this regex to isolate URL strings of all kinds:

"Wheres WWW?":
 `/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/`

 flags: [i]


any URL starting with https will fall into the scope of this regex, read below to see how exactly it does this. 

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
This regex, henceforth named Wheres www?,  contains components to match specific characters, matching a fixed string at the beginning of a line, matching special characters and two location anchors. 
### Anchors
Wheres www? starts with a beginning anchor "^" which matches the beginning of the string. In this case, we used this to ensure we start at the beginning of the URL, especially if it contains https.

Also used is the end anchor "$", this is dictating where the end of the string is once all data that satisfies our search is found. 
### Quantifiers

?: 

We use the optional quantifier a few times, it first follows the https"?", this allows us to differentiate between http and https addresses since both are present on the web currently.

We again use the "?" optional quantifer on the entire capturing group containing "https" , this allows us to capture URLs that begin with "http/https" as well as ones that start with "www". 

*: the star qualifier which matches 0 or more of whatever criteria procedes it, is used twice in wheres www? 

It is utilized first to include any data following the ".com/.net/etc" top level dommain suffix. We provide it a character set and tell it to include those if they exist and if they dont then continue the search.

Then it is used again to include as many of these directories that occur, if any. IE " https://open.spotify.com/show/4kYCRYJ3yK5DQbP5tbfZby/" in this instance, "/show/4kYCRYJ3yK5DQbP5tbfZby" are both grabbed by these stars. 


{}: This is utilized to narrow down a certain amount of characters from a defined range, in this case it is being used to only match between 2 - 6 characters "{2,6}" of the top level domain IE ".gov"

+:
We use the plus to match 1 or more of the preceding criteria, which in this case is "[\da-z\.-]" which is allowing us to capture everything between "https://" and ".com"  


### Grouping Constructs
We break down potential URL structure into various groupings utilizing "()". for instance "https://www.google.com/images" will be grouped into the following

1. "https://"
2. "www.google"
3. "com"
4. "/images"
### Bracket Expressions
We use brackets to spell out various ranges and character sets however we dont use any negated sets. 

### Character Classes
We use character classes to provide search criteria for each section of a URL. Some include alphanumeric and various symbols such as slashes, dots and dashes. All of these are typical items you would find inside of a URL. 
### The OR Operator
in this particular regex we are not utilizing the OR operator "|"
### Flags
utilizing the case insensitive flag "i" , this will help us to account for any capital letters inside of a URL at unexpected places. 
### Character Escapes
We uses character escapes to represents the "//" in "https://" and all of the "." because URLs SHOULD contain several of each of those. 
## Author

Find more of Alex Albright's work on [Github](https://www.github.com/alexarizona00)


