# Chapter 3: Simple Use Cases

## Introduction
In this chapter, we will explore the basic and practical applications of regular expressions in everyday tasks. These simple use cases will help you understand how to apply regular expressions to solve common problems effectively.

## Basic Pattern Matching

### Example 1: Finding a Word
To find a specific word in a text, you can use:
```regex
word
```
This pattern matches the exact word "word" in the text.

### Example 2: Case-Insensitive Search
To perform a case-insensitive search, use the `i` flag:
```regex
word/i
```
This matches "Word", "word", "WORD", etc.

## Searching for Text

### Example 1: Finding All Digits
To find all digits in a text:
```regex
\d+
```
This pattern matches sequences of digits like "123", "456", etc.

### Example 2: Finding Words with Specific Prefix
To find words starting with "pre":
```regex
\bpre\w*\b
```
This matches "prefix", "prelude", etc.
The \b in the regex \bpre\w*\b is a word boundary anchor. Word boundaries are used to ensure that the pattern matches only at the beginning and end of a word. Here’s why \b is used in this context:

	•	\bpre\w*\b:
	•	\b: Asserts a word boundary at the start.
	•	pre: Matches the literal string “pre”.
	•	\w*: Matches zero or more word characters (letters, digits, or underscores).
	•	\b: Asserts a word boundary at the end.

Using \b ensures that “pre” is matched only when it appears at the beginning of a word, not as part of another word. For example, it will match “prefix” but not “depression”.

## Validating Input

### Example 1: Email Address Validation
To validate an email address:
```regex
^[\w\.-]+@[a-zA-Z\d\.-]+\.[a-zA-Z]{2,6}$
```
This pattern checks for a valid email format.

### Example 2: Phone Number Validation
To validate a US phone number:
```regex
^\(\d{3}\) \d{3}-\d{4}$
```
This matches phone numbers in the format "(123) 456-7890".

## Replacing Text

### Example 1: Replacing All Spaces with Underscores
To replace spaces with underscores:
```regex
\s+/_/
```
This pattern replaces spaces with underscores.

### Example 2: Removing Punctuation
To remove all punctuation:
```regex
[^\w\s]+
```
This matches and removes all punctuation marks.

## Practical Examples in Everyday Tasks

### Example 1: Extracting URLs from Text
To extract URLs from a text:
```regex
https?://[^\s]+
```
This pattern matches "http://" or "https://" followed by non-space characters.

### Example 2: Finding Dates in Text
To find dates in the format "dd/mm/yyyy":
```regex
\d{2}/\d{2}/\d{4}
```
This matches dates like "23/07/2024".

### Example 3: Identifying Capitalized Words
To find all capitalized words:
```regex
\b[A-Z][a-z]*\b
```
This matches words starting with a capital letter.