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
* [Character Escapes](#character-escapes)
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


## Bracket Expressions
Square brackets, denoted as `[]`, are employed to specify a group of characters that can be matched at a particular position within a text string. Any character enclosed within these brackets is considered part of the permissible set. Bracket expressions can encompass individual characters and can also define character ranges using a hyphen `-`, for instance, `a-z` to represent all lowercase letters or `0-9` to denote digits.

## Character Classes
Character classes, also referred to as character sets, are brief and more succinct representations in regular expressions that depict specific sets of characters. By utilizing character classes, you can streamline and abbreviate regular expression patterns.

Our regular expression(regex) `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/` incorporates a range of regex elements, such as `character classes`, `character sets`, `metacharacters`, and `repeating character classes`. These elements are essential for the accurate assessment and matching of email addresses.

### Character Classes and Character Sets:
The provided email regex utilizes the core character class: `\d` and `..` Character sets are enclosed within square brackets, for example `[a-z]`, , and `[.-]`. These sets represent multiple characters, enabling a single character match from the defined range.

The provided regex pattern is designed to match a solitary alphanumeric character, which may consist of an uppercase letter, a lowercase letter, or a digit. The character class `\d` is responsible for matching a digit, whereas the character sets `[a-z]` and `[A-Z]` are utilized to match lowercase and uppercase letters, correspondingly. Through the amalgamation of these character sets within square brackets, the pattern is formulated to effectively match any single alphanumeric character.

### Metacharacters Inside Character Classes:
Metacharacters in regex are special characters, such as the dot `(.)`, that hold particular meanings. When inside character classes, some metacharacters lose their special significance and are interpreted as literal characters. In the provided email regex, the hyphen `(-)` and the dot `(.)` are metacharacters enclosed within character classes `[a-z0-9_.-]` and `[\da-z.-]`. The dot `(.)` does not require escaping with a backslash, and the hyphen is utilized as a literal character without the need for escaping, given its placement at the beginning or end of the character set.

This regex pattern is designed to match a single digit, an uppercase letter, a lowercase letter, a literal period `(.)`, a comma `(,)`, or a hyphen `(-)`. The character classes `\d`, `[A-Z]`, and `[a-z]` correspond to digits, uppercase letters, and lowercase letters, respectively. The metacharacters `.` and `-` are integrated within the character class as literal characters, devoid of any special interpretation, due to their placement inside the class. The hyphen `(-)` is also used as a literal character without requiring an escape sequence, as it is positioned at the outset or conclusion of the character set.

### Repeating Character Classes:
The email regex makes use of the `+` and `{2,6}` quantifiers to signify repeating character classes, as previously explained. The plus sign `(+)` is employed to match one or more occurrences of the preceding character class or set, as evidenced in `[a-z0-9_.-]+` and `[\da-z.-]+`. Subsequently, the curly braces `({2,6})` establish a specific range of repetitions for the preceding character class or set, as demonstrated in `[a-z.]{2,6}`, which corresponds to 2 to 6 occurrences of lowercase letters or the literal period (dot) characters.

## Character Escapes
Character escapes play a crucial role in regex, enabling precise pattern matching by neutralizing the special meaning of metacharacters and denoting characters that cannot be directly input. Within the regex presented in this tutorial /^([a-z0-9_.-]+)@([\da-z.-]+).([a-z.]{2,6})$/, we can observe the employment of character escapes and their respective purposes:

### Backslash:
The backslash `\` is widely employed as an escape character in regex to interpret metacharacters as literals. In the provided regex, the dot `(.)` is preceded by a backslash, such as `.`, to ensure that it is recognized as a literal period rather than a wildcard.

### Escape Sequences
Escape sequences, consisting of characters that cannot be directly typed or represented in a string, are implemented and utilized as part of regex. These sequences are initiated with a backslash `\` followed by a single letter or a combination of letters. In the email regex, the escape sequence `\d` serves as a shorthand for the use of, representing any digit from 0 to 9.

Character escapes play a vital role in ensuring the accurate matching of text patterns by interpreting special characters as literals. They are instrumental in suppressing the special meanings of metacharacters and representing characters that cannot be directly typed. As a result, they contribute to the reliable validation of email addresses through the proper functioning of regex expressions

## Author
Follow me on Github at [Travis Shanhun](https://github.com/RaszeroT). Additional questions or concerns? feel free to contact me at shanhun.codes@gmail.com


**Deployed GitHub-Gist Link:**
[Click Here](https://gist.github.com/RaszeroT/3ea35329b82917bb669d617fae46e97e)

**GitHub Repository:**
[Click Here](https://github.com/raszerot/Regex-Tutorial-Travis-Shanhun)
