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

- 	\bpre\w*\b:
- \b: Asserts a word boundary at the start.
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
Breakdown of the Regular Expression

	1.	^: Asserts the position at the start of the string.
	2.	[\w\.-]+:
	•	[ and ]: Define a character class.
	•	\w: Matches any word character (equivalent to [a-zA-Z0-9_]).
	•	\.: Matches a literal dot (.). The backslash is used to escape the dot, as a dot normally matches any character.
	•	-: Matches a literal hyphen (-).
	•	+: Quantifier that matches one or more occurrences of the preceding element (in this case, any word character, dot, or hyphen).
	•	In total: This part matches one or more characters that are either word characters, dots, or hyphens, representing the local part of the email address (the part before the @).
	3.	@: Matches the literal “@” character.
	4.	[a-zA-Z\d\.-]+:
	•	[ and ]: Define a character class.
	•	a-zA-Z: Matches any uppercase or lowercase letter.
	•	\d: Matches any digit (equivalent to [0-9]).
	•	\.: Matches a literal dot (.).
	•	-: Matches a literal hyphen (-).
	•	+: Quantifier that matches one or more occurrences of the preceding element (in this case, any letter, digit, dot, or hyphen).
	•	In total: This part matches one or more characters that are letters, digits, dots, or hyphens, representing the domain part of the email address (the part after the @).
	5.	\.: Matches a literal dot (.), separating the domain name and the top-level domain (TLD).
	6.	[a-zA-Z]{2,6}:
	•	[ and ]: Define a character class.
	•	a-zA-Z: Matches any uppercase or lowercase letter.
	•	{2,6}: Quantifier that matches between 2 and 6 occurrences of the preceding element (in this case, any letter).
	•	In total: This part matches a top-level domain (TLD) that consists of 2 to 6 letters (e.g., “com”, “org”, “net”, “info”).
	7.	$: Asserts the position at the end of the string.


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