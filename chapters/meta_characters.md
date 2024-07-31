# Chapter 2: Meta Characters

## Overview of Meta Characters

Meta characters are special symbols in regular expressions that represent types of characters or control the matching process. Understanding these characters is crucial for crafting effective regex patterns. This chapter introduces the key meta characters used in regular expressions.

## Character Classes and Sets

### Example 1: Character Class
A character class matches any single character within the brackets.
```regex
[abc]
```
This matches 'a', 'b', or 'c'.

### Example 2: Character Range
A character range specifies a range of characters to match.
```regex
[a-z]
```
This matches any lowercase letter from 'a' to 'z'.

### Example 3: Negated Character Class
A negated character class matches any character not in the brackets.
```regex
[^abc]
```
This matches any character except 'a', 'b', or 'c'.

## Anchors and Boundaries

### Example 1: Start of String Anchor
The caret (`^`) matches the start of a string.
```regex
^start
```
This matches 'start' only if it is at the beginning of a line.

### Example 2: End of String Anchor
The dollar sign (`$`) matches the end of a string.
```regex
end$
```
This matches 'end' only if it is at the end of a line.

### Example 3: Word Boundary
The word boundary (`\b`) matches the position between a word and a non-word character.
```regex
\bword\b
```
This matches 'word' as a whole word, not as part of another word like 'wording'.

## Quantifiers

### Example 1: Zero or More
The asterisk (`*`) matches zero or more occurrences of the preceding element.
```regex
a*
```
This matches '', 'a', 'aa', 'aaa', and so on.

### Example 2: One or More
The plus sign (`+`) matches one or more occurrences of the preceding element.
```regex
a+
```
This matches 'a', 'aa', 'aaa', and so on, but not an empty string.

### Example 3: Zero or One
The question mark (`?`) matches zero or one occurrence of the preceding element.
```regex
a?
```
This matches '' or 'a'.

### Example 4: Specific Number of Occurrences
Braces (`{n,m}`) match at least `n` and at most `m` occurrences of the preceding element.
```regex
a{2,3}
```
This matches 'aa' or 'aaa'.

## Grouping and Capturing

### Example 1: Grouping
Parentheses (`()`) group elements together.
```regex
(abc)
```
This matches 'abc'.

### Example 2: Capturing Groups
Parentheses also capture the matched text for later use.
```regex
(\d{3})-(\d{2})-(\d{4})
```
This matches a Social Security number format and captures each group of digits.

## Escape Sequences

### Example 1: Escaping Special Characters
The backslash (`\`) escapes a special character, making it literal.
```regex
\.
```
This matches a literal dot.

### Example 2: Common Escape Sequences
- `\d`: Matches any digit, equivalent to `[0-9]`.
- `\D`: Matches any non-digit.
- `\w`: Matches any word character (alphanumeric + underscore), equivalent to `[a-zA-Z0-9_]`.
- `\W`: Matches any non-word character.
- `\s`: Matches any whitespace character (space, tab, newline).
- `\S`: Matches any non-whitespace character.

## Lookahead and Lookbehind

### Example 1: Positive Lookahead
The positive lookahead (`(?=...)`) ensures that the following characters match the given pattern without consuming them.
```regex
a(?=b)
```
This matches 'a' only if it is followed by 'b'.

### Example 2: Negative Lookahead
The negative lookahead (`(?!...)`) ensures that the following characters do not match the given pattern.
```regex
a(?!b)
```
This matches 'a' only if it is not followed by 'b'.

### Example 3: Positive Lookbehind
The positive lookbehind (`(?<=...)`) ensures that the preceding characters match the given pattern without consuming them.
```regex
(?<=b)a
```
This matches 'a' only if it is preceded by 'b'.

### Example 4: Negative Lookbehind
The negative lookbehind (`(?<!...)`) ensures that the preceding characters do not match the given pattern.
```regex
(?<!b)a
```
This matches 'a' only if it is not preceded by 'b'.
