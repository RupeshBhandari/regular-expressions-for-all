# Chapter 4: Advanced Use Cases

In this chapter, we delve into advanced applications of regular expressions, exploring complex patterns, recursion, conditional logic, and optimization techniques. These examples will demonstrate the power and versatility of regular expressions in handling more sophisticated text processing tasks.

## Complex Pattern Matching

### Example 1: Matching Balanced Parentheses
**Regex**:
```regex
\(([^()]*|(?R))*\)
```
**Explanation**:
- **`\(` and `\)`**: Match a literal opening `(` and closing `)` parenthesis.
- **`[^()]*`**: Matches any sequence of characters that are not parentheses. This part handles content within a single level of parentheses.
- **`|`**: Acts as an OR operator, allowing for the next pattern to be considered.
- **`(?R)`**: This is a recursive pattern that allows the regex to match nested parentheses by calling itself.
- **`*`**: Applies to the whole group, meaning zero or more occurrences of either content within parentheses or more nested parentheses.

**Usage**:
This pattern is useful in scenarios where you need to ensure that parentheses are properly balanced and nested, such as in mathematical expressions or programming languages.

### Example 2: Matching HTML Tags
**Regex**:
```regex
<([a-zA-Z]+)([^<]+)*(?:>(.*)<\/\1>|\/>)
```
**Explanation**:
- **`<` and `>`**: Match the opening and closing angle brackets of an HTML tag.
- **`([a-zA-Z]+)`**: Captures the tag name, consisting of one or more letters.
- **`([^<]+)*`**: Matches any content within the tag that does not include a `<` character, capturing attributes.
- **`(?: ... )`**: A non-capturing group that matches either a self-closing tag or a tag with content.
- **`>(.*)<\/\1>`**: Matches the tag content, using `.*` to capture anything between the tags and `\/\1` to ensure that the closing tag matches the opening tag captured in `\1`.
- **`|\/>`**: Matches self-closing tags like `<img />`.

**Usage**:
This regex can be used to extract and validate HTML tags, which is particularly useful for parsing or sanitizing HTML code.

### Example 3: Matching Delimited Strings
**Regex**:
```regex
"(?:[^"\\]|\\.)*"
```
**Explanation**:
- **`"`**: Matches the opening and closing double quotation marks.
- **`(?: ... )`**: A non-capturing group that matches the content within the quotes.
- **`[^"\\]`**: Matches any character that is not a double quote `"` or a backslash `\`.
- **`|\\.`**: Matches any escaped character within the string, ensuring that sequences like `\"` or `\\` are handled correctly.
- **`*`**: Matches zero or more occurrences of the previous group, covering the entire content within the quotes.

**Usage**:
This pattern is used to match strings enclosed in double quotes, handling escaped characters within the string, which is common in JSON or programming languages.

## Nested and Recursive Patterns

### Example 1: Matching Nested Structures
**Regex**:
```regex
\((?>[^()]+|(?R))*\)
```
**Explanation**:
- **`\(` and `\)`**: Match the literal parentheses.
- **`(?> ... )`**: An atomic group that prevents backtracking, ensuring that once a match is made, the regex engine does not reconsider it.
- **`[^()]+`**: Matches one or more characters that are not parentheses.
- **`|(?R)`**: Allows recursion, where `(?R)` refers to the entire regex pattern, enabling the matching of nested parentheses.
- **`*`**: Matches zero or more occurrences, handling multiple nested structures.

**Usage**:
This regex is useful for validating and extracting data from nested structures such as mathematical expressions, nested lists, or programming code with multiple levels of parentheses.

### Example 2: Matching Nested Lists
**Regex**:
```regex
\[(?>[^\[\]]+|(?R))*\]
```
**Explanation**:
- **`\[` and `\]`**: Match the opening and closing square brackets of a list.
- **`(?>[^\[\]]+)`**: Matches one or more characters that are not square brackets, preventing backtracking within the group.
- **`|(?R)`**: Recursively matches nested lists by calling the entire pattern again.
- **`*`**: Matches zero or more occurrences of the previous groups, handling multiple nested lists.

**Usage**:
This regex is particularly useful for processing nested list structures, such as those found in JSON arrays or other hierarchical data formats.

## Conditional Expressions

### Example 1: Conditional Matching
**Regex**:
```regex
(?(?=regex)then|else)
```
**Explanation**:
- **`(?=regex)`**: A lookahead assertion that checks if the specified pattern matches at the current position.
- **`then`**: The pattern to match if the condition is true.
- **`else`**: The pattern to match if the condition is false.

**Example**:
```regex
(?(?=cat)cat|dog)
```
- **`(?=cat)`**: Checks if "cat" is present.
- **`cat`**: Matches "cat" if the lookahead is true.
- **`dog`**: Matches "dog" if the lookahead is false.

**Usage**:
This conditional pattern is useful for situations where the pattern to match depends on the context, allowing for dynamic and flexible regex-based parsing.

### Example 2: Matching Optional Prefixes
**Regex**:
```regex
\.(?(?=\d)\d+|\w+)
```
**Explanation**:
- **`\.`**: Matches a literal dot.
- **`(?(?=\d)\d+|\w+)`**: Conditional that checks if a digit follows the dot.
  - **`(?=\d)\d+`**: If a digit is present, match one or more digits.
  - **`\w+`**: If a digit is not present, match one or more word characters.

**Usage**:
This regex is useful for parsing strings with optional prefixes, such as distinguishing between file extensions (like `.123` or `.txt`) based on the first character following the dot.

## Performance Optimization

### Example 1: Avoiding Catastrophic Backtracking
**Regex**:
```regex
(?>\d+|\w+)
```
**Explanation**:
- **`(?> ... )`**: An atomic group that prevents backtracking, ensuring that once a match is made, it is not reconsidered.
- **`\d+`**: Matches one or more digits.
- **`\w+`**: Matches one or more word characters.

**Usage**:
Avoiding backtracking is crucial for improving regex performance, especially in complex patterns where backtracking can lead to significant slowdowns.

### Example 2: Using Non-Capturing Groups
**Regex**:
```regex
(?:\d+|\w+)
```
**Explanation**:
- **`(?: ... )`**: A non-capturing group that groups elements without storing the matched text.
- **`\d+`**: Matches one or more digits.
- **`\w+`**: Matches one or more word characters.

**Usage**:
Non-capturing groups are used when you need to group parts of a regex for logical or quantification purposes without needing to capture the matched text, which can improve both performance and readability.

### Example 3: Using Anchors for Efficiency
**Regex**:
```regex
^\d+$
```
**Explanation**:
- **`^`**: Asserts the position at the start of the string.
- **`\d+`**: Matches one or more digits.
- **`$`**: Asserts the position at the end of the string.

**Usage**:
Anchors like `^` and `$` limit where the regex engine searches for matches, making the process more efficient by focusing only on the relevant parts of the text.

## Real-World Examples and Case Studies

### Example 1: Parsing Log Files
**Regex**:
```regex
\b\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}\b
```
**Explanation**:
- **`\b`**: Word boundary ensures the IP address is matched as a whole.
- **`\d{1,3}`**: Matches one to three digits, representing an octet of an IP address.
- **`\.`**: Matches a literal dot, separating octets.
- **`\d{1,3}`**: Repeated for each octet of the IP address.

**Usage**:
This regex is commonly used in log parsing to extract IP addresses from server logs, allowing for further analysis of network traffic or security events.

### Example 2: Extracting Data from CSV Files
**Regex**:
```regex
([^,]+),([^,]+),([^,]+)
```
**Explanation**:
- **`([^,]+)`**: Captures one or more characters that are not a comma, representing a CSV field.
- **`,`**: Matches the literal comma separating fields.
- **

`([^,]+)`**: Repeated for subsequent fields.

**Usage**:
This pattern is useful for extracting individual fields from CSV files, allowing for easy parsing and processing of tabular data.

### Example 3: Validating Complex Passwords
**Regex**:
```regex
^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[\W_]).{8,}$
```
**Explanation**:
- **`^`**: Asserts the position at the start of the string.
- **`(?=.*[a-z])`**: Positive lookahead ensuring at least one lowercase letter.
- **`(?=.*[A-Z])`**: Positive lookahead ensuring at least one uppercase letter.
- **`(?=.*\d)`**: Positive lookahead ensuring at least one digit.
- **`(?=.*[\W_])`**: Positive lookahead ensuring at least one special character or underscore.
- **`.{8,}`**: Ensures the password is at least 8 characters long.
- **`$`**: Asserts the position at the end of the string.

**Usage**:
This pattern is ideal for enforcing strong password policies, ensuring that passwords meet complexity requirements, making them more secure.

### Example 4: Web Scraping
**Regex**:
```regex
href="(https?://[^"]+)"
```
**Explanation**:
- **`href="`**: Matches the `href` attribute in an HTML tag.
- **`https?://`**: Matches either "http://" or "https://".
- **`[^"]+`**: Matches any sequence of characters that are not double quotes, representing the URL.
- **`"`**: Matches the closing double quote of the `href` attribute.

**Usage**:
This regex is commonly used in web scraping to extract URLs from HTML anchor tags, allowing for automated data collection from websites.

## Advanced Text Processing

### Example 1: Text Normalization
**Regex**:
```regex
\s+
```
**Explanation**:
- **`\s+`**: Matches one or more whitespace characters (spaces, tabs, newlines).

**Usage**:
This pattern is useful for normalizing text by replacing multiple spaces with a single space, making text more consistent for further processing.

### Example 2: Extracting Keywords
**Regex**:
```regex
\b(?:keyword1|keyword2|keyword3)\b
```
**Explanation**:
- **`\b`**: Word boundary ensures that the keywords are matched as whole words.
- **`(?: ... )`**: Non-capturing group that groups the keywords without capturing them.
- **`keyword1|keyword2|keyword3`**: Matches any of the specified keywords.

**Usage**:
This pattern is useful for extracting specific keywords from a text, which can be applied in search engines, tagging systems, or text analysis.

### Example 3: Advanced Search and Replace
**Regex**:
```regex
(?<=\bword1\b).+?(?=\bword2\b)
```
**Explanation**:
- **`(?<=\bword1\b)`**: Positive lookbehind that ensures the text is preceded by "word1".
- **`.+?`**: Matches any text between "word1" and "word2", as few characters as possible due to the lazy quantifier `?`.
- **`(?=\bword2\b)`**: Positive lookahead that ensures the text is followed by "word2".

**Usage**:
This regex is used for targeted search and replace operations, allowing you to manipulate text between two specific words.
