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

##
##
##
##
##
##
##
##
##

