# REGEX -- matching an email

 This will be a comprehensive and detailed explanation on how to match an email using a regular expression.

## Summary
 The regular expression used in this tutorial will be the following `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

 Throughout this tutorial I will be referencing the above regular expression in detail as I break down the smaller components and to create a clear and hopefully simple explanation on what we see in this regular expression.

 ## Table of Contents
* [Anchors](#anchors)
* [Quantifiers](#quantifiers)
* [Grouping Constructs](#grouping-constructs)
* [Bracket Expressions](#bracket-expressions)
* [Character Classes](#character-classes)
* [The OR Operator](#the-or-operator)
* [Flags](#flags)
* [Character Escapes](#character-escapes)
* [Email Validation Conclusion](#email-validation-conclusion)
* [Author](#author)

## Anchors
**Anchors come in two types:**
* Start Anchor `^`: This insures the start of the string is correct.
* End Anchor `$`: This insures the end of the string is correct.

These two anchors insure that the user is able to select where the start and the end of the string **must** end. 

**Example**
* `^hello$` will match nothing else but hello. Nothing leading and nothing following. `hello` - valid, `hello world` - invalid, `say hello`- invalid
* `^hello` will match anything that leads will hello but nothing that comes before. `hello` - valid, `hello world` - valid, `say hello` - invalid
* `hello$` will match anything that ends with hello but nothing that comes afterward. `hello` - valid, `hello world` - invalid, `say hello`- valid

## Quantifiers
Quantifiers in regular expressions define the frequency with which a pattern should appear, and they are positioned right after the pattern they modify.

The `+` quantifier, indicating "at least one occurrence," is applied to the pattern `[a-z0-9_\.-]` within the first capture group `([a-z0-9_\.-]+)`. This setup means that the pattern `[a-z0-9_\.-]` must appear at least once but can also appear several times in a row. Consequently, this group can capture a sequence consisting of one or more lowercase letters, digits, underscores, dots, or hyphens.


In a similar manner, the `+` quantifier follows the pattern `[\da-z\.-]` in the second capture group `([\da-z\.-]+)`, enabling this group to match sequences of one or more digits, lowercase letters, dots, or hyphens.


The quantifier `{2,6}` is applied to the character set `[a-z\.]` in the third capture group `([a-z\.]{2,6})`, allowing this group to match sequences of 2 to 6 lowercase letters or dots. This quantifier range is crucial for matching email addresses that conclude with a top-level domain of two to six letters in length, such as .au .com, .net, .info, or .co.uk.


When combined, the regular expression `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/` is crafted to identify valid email addresses. It looks for an initial segment of one or more lowercase letters, digits, underscores, dots, or hyphens, followed by the `@` symbol. This is then followed by a segment of one or more digits, lowercase letters, dots, or hyphens, and finally, a period followed by a top-level domain consisting of two to six letters, effectively capturing the structure of a standard email address.

## Grouping Constructs
Grouping constructs are utilized to combine characters or sub-patterns into a single unit within the expression. These constructs are delineated by parentheses `()` and serve several functions:


* They allow quantifiers to be applied to multiple characters as a whole.
* They enable the capturing of specific parts of the match for subsequent use. 
* They facilitate the creation of backreferences to groups that have been matched earlier.
* They permit the use of alternation within a set of characters.

The regular expression we are examining in this explanation: `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/` includes three three Grouping Constructs encapsulated within parentheses `()`. Each construct captures a distinct component of an email address: 1. Local-Part, 2. Domain, and 3. Top-level Domain.


To begin with, the 'Local-Part' `([a-z0-9_\.-]+)` is responsible for matching the user's identifier in the email address. Next, the 'Domain' `([\da-z\.-]+)` matches the domain name of the email. Lastly, the 'Top-Level Domain' `([a-z\.]{2,6})` matches the final segment of the email address, the top-level domain.

##
##
##
##
##
##

