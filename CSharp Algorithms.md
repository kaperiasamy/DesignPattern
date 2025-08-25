# C# Algorithms

## What is an algorithm?

- An algorithm is a series of defined instructions that perform a specific task.
- Every line of code in C# (or any programming language) is part of an algorithm, contributing to completing a task.
- Algorithms can vary in efficiency, but they all aim to achieve a task through a set of instructions.

## How to optimize an algorithm
- There are multiple ways to solve a problem with different algorithms, some more efficient than others.
- Making assumptions about your data (e.g., it's sorted or contains only integers) can help optimize algorithms.
- It's crucial to make informed assumptions, as incorrect assumptions can lead to unreliable results.
- A slower, reliable algorithm is better than a fast, unreliable one.

## Optimize an algorithm in C#
- **Refactoring for Efficiency**: The video demonstrates how to refactor an algorithm to make it more efficient by reducing the number of comparisons.
- **Using a Variable for Maximum**: Instead of multiple checks, the algorithm uses a variable to keep track of the maximum value, simplifying the process.
- **Testing the Algorithm**: The video shows how to test the new implementation using the terminal or an IDE like VS Code, highlighting the benefits of fewer comparisons and improved readability.

## How to describe the time complexity of an algorithm

- **Big-O Notation**: It is used to describe the efficiency of an algorithm, allowing comparison independent of input size.
- **Time Complexity**: Different algorithms have different time complexities, such as constant time (O(1)), linear time (O(N)), logarithmic time (O(log N)), and quadratic time (O(N^2)).
- **Space Complexity**: Besides time, Big-O notation also helps describe the space an algorithm uses, which is another factor in deciding which algorithm to use.

### Why is Big-O notation important?
Big-O notation is crucial because it allows you to describe the efficiency of an algorithm in terms of time and space complexity, independent of the input size. Here are a few key points:

Comparison: It helps compare different algorithms to determine which one is more efficient, especially for large inputs.
Worst-case scenario: By focusing on the worst-case time complexity, you can make informed decisions about which algorithm to use in critical situations.
Scalability: It provides insights into how an algorithm's performance will scale as the input size grows.

Understanding Big-O notation helps you create more efficient and maintainable programs, which is essential in software development.

Q: What is the goal of an algorithm?
A: to complete some task using a series of defined steps

Q: If an algorithm iterates through the input string and for each character, performs a check that takes O(1) time, what is the runtime complexity of the algorithm?
A: O(n) or linear

Q: How could we optimize a search algorithm?
A: Once the piece of data you are searching for is found, you can return from the function.

Q: What can we use to optimize an algorithm?
A: informed assumptions

## Validate strings in C#:

- **Validation Algorithms**: These algorithms check if a string has certain properties (e.g., all uppercase, all lowercase, contains digits).
- **LINQ in C#**: LINQ can be used to make validation checks more compact and readable. For example, using All and Any methods to validate string properties.
- **Password Complexity Validator**: An example of a more complex validation algorithm that checks if a string contains at least one uppercase letter, one lowercase letter, and one digit.

### What is an validation algorithm?
A validation algorithm is a type of algorithm used to check if a given input string meets certain properties or attributes. For example, it can validate if a string is all uppercase, all lowercase, contains only alphabetical characters, or includes at least one number. The output of a validation algorithm is typically a Boolean value (true or false), indicating whether the string meets the specified criteria. In C#, you can use tools like LINQ to create these validation checks efficiently.

### What tools in C# can help with validation algorithm?
In C#, several tools can help with creating validation algorithms:

- **LINQ (Language Integrated Query)**: LINQ provides a uniform query syntax that makes it easy to work with data in C#.
    - **_All_ Method**: Checks if all elements in a collection meet a certain condition. For example, to check if all characters in a string are uppercase.
    - **_Any_ Method**: Checks if any element in a collection meets a certain condition. Useful for more complex validations, like checking if a string contains at least one uppercase letter, one lowercase letter, and one digit.

### What is Linq in C#?
LINQ (Language Integrated Query) in C# is a powerful tool that provides a uniform syntax to query and manipulate data. It makes your code more compact and readable. In the context of validation algorithms, LINQ can be used to perform checks on strings efficiently.

Great question! In the context of **Unicode and C#**, the term **"surrogate"** refers to a special way of encoding characters that **cannot be represented in a single 16-bit value** (which is what the `char` type in C# uses).

---

In C#, `Char.IsLowSurrogate` is a method used to determine whether a given character is a **low surrogate** in the UTF-16 encoding system.

---

## What Is a Low Surrogate?

UTF-16 represents characters using one or two 16-bit code units:
- **Basic Multilingual Plane (BMP)** characters use a single unit.
- **Supplementary characters** (like emojis or rare scripts) use **surrogate pairs**:
  - **High surrogate:** ranges from `U+D800` to `U+DBFF`
  - **Low surrogate:** ranges from `U+DC00` to `U+DFFF`

These two units together represent a single Unicode character beyond the BMP.

---

## How `Char.IsLowSurrogate` Works

### Overloads:
1. `Char.IsLowSurrogate(char c)`  
   Checks if the character `c` is a low surrogate.

2. `Char.IsLowSurrogate(string s, int index)`  
   Checks if the character at position `index` in string `s` is a low surrogate.

### Example:
```csharp
char cLow = '\uDC00';
Console.WriteLine(Char.IsLowSurrogate(cLow)); // True

string s = "a\uD800\uDC00z";
Console.WriteLine(Char.IsLowSurrogate(s, 2)); // True
```

---

## When to Use It

- When parsing or validating Unicode text.
- When working with surrogate pairs manually.
- When building or decoding UTF-16 encoded data streams.

---

If you're dealing with character encoding, especially for internationalization or emoji support, this method helps ensure you're handling surrogate pairs correctly.

### What Is a Surrogate?

In **UTF-16 encoding**, characters outside the **Basic Multilingual Plane (BMP)**—those with code points above `U+FFFF`—are represented using **two 16-bit code units**. These two units are called a **surrogate pair**:

- **High Surrogate**: First 16-bit value, in the range `U+D800` to `U+DBFF`
- **Low Surrogate**: Second 16-bit value, in the range `U+DC00` to `U+DFFF`

Together, they form a single character, like an emoji or a rare script symbol.

---

### Why Is This Needed?

The `char` type in C# is based on UTF-16, which uses 16 bits per character. But Unicode has over **1 million possible characters**, so some need more than 16 bits. Surrogate pairs allow UTF-16 to represent these extended characters.

---

### Example

```csharp
char high = '\uD83D'; // High surrogate
char low = '\uDE00';  // Low surrogate

string emoji = new string(new[] { high, low });
Console.WriteLine(emoji); // 😀
```

---

### Summary

- "Surrogate" means a **placeholder** or **helper** unit used to represent a larger character.
- In C#, `Char.IsHighSurrogate` and `Char.IsLowSurrogate` help you identify these units.
- They're essential for handling characters beyond the standard range—like emojis, ancient scripts, or mathematical symbols.

Surrogate pairs in UTF-16 have a direct impact on **string manipulation in C#**, especially when you're working with characters beyond the Basic Multilingual Plane (BMP)—like emojis, rare scripts, or mathematical symbols. Here's how and why it matters:

---

## 1. **String Length Can Be Misleading**

In C#, `string.Length` returns the number of `char` elements, not actual Unicode characters.

```csharp
string emoji = "😀"; // U+1F600
Console.WriteLine(emoji.Length); // Outputs: 2
```

Even though it looks like one character, it's made of a **high surrogate** and a **low surrogate**, so the length is 2.

---

## 2. **Indexing Can Split Characters**

Accessing individual characters with indexing (`str[i]`) can return a surrogate, not a full character.

```csharp
char part = emoji[0]; // High surrogate
Console.WriteLine(Char.IsHighSurrogate(part)); // True
```

If you manipulate strings without checking for surrogate pairs, you risk breaking characters.

---

## 3. **Substring and Slicing Risks**

Using `Substring()` or `Remove()` blindly can split surrogate pairs, resulting in invalid or unreadable characters.

```csharp
string broken = emoji.Substring(0, 1);
Console.WriteLine(broken); // May not render correctly
```

To safely manipulate strings with surrogate pairs, use `System.Globalization.StringInfo`.

---

## 4. **Use `StringInfo` for Safe Character Handling**

```csharp
using System.Globalization;

string text = "A😀B";
StringInfo info = new StringInfo(text);

for (int i = 0; i < info.LengthInTextElements; i++)
{
    Console.WriteLine(info.SubstringByTextElements(i, 1));
}
```

This treats surrogate pairs as single text elements, preserving character integrity.

---

## 5. **Regular Expressions Can Misinterpret Surrogates**

Regex patterns that use `.` (dot) to match any character may match only one part of a surrogate pair. Use Unicode-aware regex if needed.

---

## Summary

- Surrogate pairs affect how you count, slice, and iterate over strings.
- Always be cautious when working with characters outside the BMP.
- Use `StringInfo` for accurate character-level operations.
- This is especially important in apps that handle emojis, multilingual input, or custom fonts.

If you're building a UI or API that handles user-generated content, this knowledge is essential for avoiding subtle bugs. 

Surrogate pairs can be sneaky troublemakers in string manipulation, especially when you're working with Unicode characters beyond the Basic Multilingual Plane (BMP). Here are the most common pitfalls developers run into:

---

### 1. Misinterpreting `string.Length`
- `string.Length` in C# returns the number of `char` units, not actual Unicode characters.
- A surrogate pair counts as **two** `char`s, even though it represents **one** character.

```csharp
string emoji = "🧠"; // U+1F9E0
Console.WriteLine(emoji.Length); // Outputs: 2
```

---

### 2. Indexing Splits Characters
- Accessing `str[i]` might give you just the **high** or **low** surrogate, not the full character.
- This can lead to broken characters or invalid Unicode when manipulating strings.

```csharp
char c = emoji[0]; // High surrogate
Console.WriteLine(Char.IsHighSurrogate(c)); // True
```

---

### 3. Substring and Slicing Errors
- Using `Substring()` or `Remove()` without checking for surrogate pairs can split characters.
- This results in corrupted output or rendering issues.

```csharp
string broken = emoji.Substring(0, 1); // Only high surrogate
Console.WriteLine(broken); // May not display anything meaningful
```

---

### 4. Regex Misbehavior
- Regular expressions using `.` (dot) match a single `char`, not a full Unicode character.
- This can cause partial matches or incorrect replacements.

---

### 5. Sorting and Comparison Bugs
- Lexicographic comparisons may behave unexpectedly if surrogate pairs are split.
- Sorting strings with emojis or rare characters can yield inconsistent results.

---

### 6. Encoding/Decoding Issues
- Improper handling during encoding (e.g., UTF-8 conversion) can result in malformed output.
- Always use Unicode-aware libraries or methods when converting between formats.

---

### How to Avoid These Pitfalls

Use `System.Globalization.StringInfo` to work with **text elements** (full Unicode characters):

```csharp
using System.Globalization;

StringInfo info = new StringInfo("A🧠B");
for (int i = 0; i < info.LengthInTextElements; i++)
{
    Console.WriteLine(info.SubstringByTextElements(i, 1));
}
```

This ensures surrogate pairs are treated as single characters.

---

If you're building anything that handles emojis, multilingual input, or user-generated content, these pitfalls can sneak in fast. 


Absolutely! Here's a robust and Unicode-aware string utility class in C# that gracefully handles surrogate pairs, ensuring safe manipulation of full Unicode characters (also known as *text elements*). This is especially useful when working with emojis, rare scripts, or any characters beyond the Basic Multilingual Plane.

---

## `SafeStringUtils` Class

```csharp
using System;
using System.Globalization;
using System.Text;

public static class SafeStringUtils
{
    /// <summary>
    /// Gets the number of Unicode characters (text elements) in a string.
    /// </summary>
    public static int GetCharacterCount(string input)
    {
        return new StringInfo(input).LengthInTextElements;
    }

    /// <summary>
    /// Safely gets a Unicode character (text element) at a given index.
    /// </summary>
    public static string GetCharacterAt(string input, int index)
    {
        var info = new StringInfo(input);
        return info.SubstringByTextElements(index, 1);
    }

    /// <summary>
    /// Safely slices a string by Unicode character indices.
    /// </summary>
    public static string Slice(string input, int startIndex, int length)
    {
        var info = new StringInfo(input);
        return info.SubstringByTextElements(startIndex, length);
    }

    /// <summary>
    /// Safely iterates over all Unicode characters in a string.
    /// </summary>
    public static string[] GetCharacters(string input)
    {
        var info = new StringInfo(input);
        int count = info.LengthInTextElements;
        string[] result = new string[count];

        for (int i = 0; i < count; i++)
        {
            result[i] = info.SubstringByTextElements(i, 1);
        }

        return result;
    }

    /// <summary>
    /// Removes a Unicode character at a specific index.
    /// </summary>
    public static string RemoveCharacterAt(string input, int index)
    {
        var chars = GetCharacters(input);
        if (index < 0 || index >= chars.Length) return input;

        var builder = new StringBuilder();
        for (int i = 0; i < chars.Length; i++)
        {
            if (i != index)
                builder.Append(chars[i]);
        }

        return builder.ToString();
    }

    /// <summary>
    /// Replaces a Unicode character at a specific index.
    /// </summary>
    public static string ReplaceCharacterAt(string input, int index, string replacement)
    {
        var chars = GetCharacters(input);
        if (index < 0 || index >= chars.Length) return input;

        chars[index] = replacement;
        return string.Concat(chars);
    }
}
```

---

## Example Usage

```csharp
string text = "A🧠B🚀C";

Console.WriteLine(SafeStringUtils.GetCharacterCount(text)); // 5
Console.WriteLine(SafeStringUtils.GetCharacterAt(text, 1)); // 🧠
Console.WriteLine(SafeStringUtils.Slice(text, 1, 3));       // 🧠B🚀
Console.WriteLine(SafeStringUtils.RemoveCharacterAt(text, 2)); // A🧠🚀C
Console.WriteLine(SafeStringUtils.ReplaceCharacterAt(text, 3, "🌟")); // A🧠B🌟C
```

---

This class ensures that surrogate pairs are treated as atomic units, preventing broken characters and rendering issues. Want to extend this with emoji detection, normalization, or safe truncation for UI display? I’d be happy to help build that next.

### What is the best way to handle normalization?
Great question—normalization is essential when working with Unicode strings, especially if you're comparing, storing, or displaying text that may come from different sources or input methods. In C#, the best way to handle normalization is by using the `System.Text.NormalizationForm` enum along with the `string.Normalize()` method.

---

## Why Normalize?

Unicode allows multiple ways to represent the same character. For example:

- **é** can be:
  - A single character: `U+00E9`
  - Or a combination: `U+0065` (e) + `U+0301` (combining acute accent)

Without normalization, these two forms look identical but won't match in string comparisons.

---

## Best Practices for Normalization in C#

### 1. **Use `string.Normalize()`**

```csharp
string input = "e\u0301"; // e + combining acute accent
string normalized = input.Normalize(NormalizationForm.FormC);
```

### 2. **Choose the Right Form**

| Form | Description | Use Case |
|------|-------------|----------|
| `FormC` | Canonical Composition | Most common; combines characters (e.g., é) |
| `FormD` | Canonical Decomposition | Splits characters into base + diacritics |
| `FormKC` | Compatibility Composition | Like FormC but removes formatting differences |
| `FormKD` | Compatibility Decomposition | Like FormD but removes formatting differences |

**Recommendation:** Use `FormC` for general text comparison and storage. Use `FormKC` if you're stripping out stylistic differences (e.g., full-width vs half-width characters).

---

## Example: Safe Comparison

```csharp
string a = "é";           // U+00E9
string b = "e\u0301";     // U+0065 + U+0301

bool areEqual = a.Normalize(NormalizationForm.FormC) ==
                b.Normalize(NormalizationForm.FormC);

Console.WriteLine(areEqual); // True
```

---

## When to Normalize

- Before storing user input
- Before comparing strings
- Before hashing or indexing text
- When processing multilingual content

---

If you're building a search engine, a chat app, or anything with user-generated content, normalization is your silent hero. 

Normalization in Unicode is deceptively tricky—many developers assume it's a one-and-done operation, but there are several common mistakes that can lead to subtle bugs, especially in multilingual or emoji-rich applications. Here's a breakdown of the most frequent pitfalls:

---

## Common Mistakes in Unicode Normalization

### 1. **Assuming All Input Is Already Normalized**
- Text from different sources (user input, APIs, files) may use different Unicode representations.
- Failing to normalize before comparison or storage can lead to mismatches.

```csharp
string a = "é";           // U+00E9
string b = "e\u0301";     // U+0065 + U+0301
Console.WriteLine(a == b); // False without normalization
```

---

### 2. **Using the Wrong Normalization Form**
- Choosing `FormD` (decomposition) when you need `FormC` (composition) can break rendering or comparisons.
- `FormKC` and `FormKD` strip formatting differences—use with caution.

| Form | Description | Risk |
|------|-------------|------|
| `FormC` | Canonical Composition | Safe for most use cases |
| `FormD` | Canonical Decomposition | May break display or sorting |
| `FormKC` | Compatibility Composition | Removes stylistic differences |
| `FormKD` | Compatibility Decomposition | Can alter meaning unintentionally |

---

### 3. **Normalizing After Comparison**
- Comparing strings before normalization leads to false negatives.
- Always normalize **before** comparing, hashing, or storing.

---

### 4. **Ignoring Performance in Large-Scale Systems**
- Normalizing every string on-the-fly in a high-throughput system can be expensive.
- Consider normalizing once at ingestion or caching normalized forms.

---

### 5. **Not Normalizing Before Indexing or Searching**
- Search engines and databases may treat visually identical strings as different.
- Normalize before indexing to ensure consistent search results.

---

### 6. **Over-normalizing User Input**
- Normalizing aggressively (e.g., using `FormKC`) can strip meaningful distinctions.
- Example: full-width vs half-width characters in East Asian languages.

---

### 7. **Skipping Normalization in UI Display**
- Combining characters may render inconsistently across platforms.
- Normalize to `FormC` before displaying to ensure consistent appearance.

---

## Best Practice Summary

- Normalize **early** and **consistently**
- Use `FormC` unless you have a specific reason to use others
- Normalize before comparing, storing, indexing, or displaying
- Be cautious with `FormKC`/`FormKD`—they can change semantics

---

If you're building a multilingual app, a search feature, or anything involving user-generated content, normalization isn't optional—it's foundational. 

These four forms—**FormC**, **FormD**, **FormKC**, and **FormKD**—are Unicode normalization formats used to ensure consistent representation of characters that may have multiple valid encodings. Let’s break them down clearly:

---

## What Is Unicode Normalization?

Unicode allows characters to be represented in different ways. For example, the character **é** can be:
- A single code point: `U+00E9`
- Or a combination: `U+0065` (e) + `U+0301` (combining acute accent)

Normalization ensures that these visually identical forms are treated as equal.

---

## The Four Normalization Forms

| Form     | Full Name                     | Description                                                                 | Use Case |
|----------|-------------------------------|-----------------------------------------------------------------------------|----------|
| **FormC** | Canonical Composition         | Combines base characters with diacritics into a single composed character. | Most common for display and comparison |
| **FormD** | Canonical Decomposition       | Splits composed characters into base + combining marks.                    | Useful for text analysis or searching |
| **FormKC**| Compatibility Composition     | Like FormC, but also removes formatting differences (e.g., superscripts).  | Good for loose matching or search |
| **FormKD**| Compatibility Decomposition   | Like FormD, but also strips formatting differences.                        | Useful for indexing or normalization before hashing |

---

## Example: The Character “Ⅳ” (Roman numeral four)

- **Original**: `Ⅳ` (U+2163)
- **FormKC/FormKD**: Normalized to `IV` (two characters)

This is helpful if you want to treat stylistic variants or symbols as their plain-text equivalents.

---

## In C#:

```csharp
string input = "e\u0301"; // e + combining acute accent
string normalized = input.Normalize(NormalizationForm.FormC);
```

---

## Best Practice

- Use **FormC** for most applications (UI, comparison, storage).
- Use **FormKC** if you want to ignore stylistic differences.
- Avoid **FormD/KD** unless you need to analyze or strip diacritics.

---

Perfect—let’s build a smart Unicode normalization utility in C# that **auto-selects the best normalization form** based on context. This utility will help you handle multilingual input, emojis, stylistic variants, and diacritics with precision and flexibility.

---

## Design Philosophy

We'll create a class called `UnicodeNormalizer` that:
- Detects the type of input (e.g., composed vs decomposed, compatibility characters, combining marks)
- Chooses the most appropriate normalization form (`FormC`, `FormD`, `FormKC`, or `FormKD`)
- Allows manual override if needed
- Provides safe comparison and display utilities

---

## `UnicodeNormalizer` Class

```csharp
using System;
using System.Globalization;
using System.Text;
using System.Text.RegularExpressions;

public static class UnicodeNormalizer
{
    /// <summary>
    /// Automatically selects the best normalization form based on input characteristics.
    /// </summary>
    public static string AutoNormalize(string input)
    {
        if (string.IsNullOrEmpty(input)) return input;

        // If input contains combining marks, use FormC to compose
        if (ContainsCombiningMarks(input))
            return input.Normalize(NormalizationForm.FormC);

        // If input contains compatibility characters (e.g., superscripts, Roman numerals), use FormKC
        if (ContainsCompatibilityCharacters(input))
            return input.Normalize(NormalizationForm.FormKC);

        // Default to FormC for general use
        return input.Normalize(NormalizationForm.FormC);
    }

    /// <summary>
    /// Checks if the string contains combining diacritical marks.
    /// </summary>
    private static bool ContainsCombiningMarks(string input)
    {
        return Regex.IsMatch(input, @"\p{Mn}");
    }

    /// <summary>
    /// Checks for compatibility characters (e.g., full-width, superscripts, Roman numerals).
    /// </summary>
    private static bool ContainsCompatibilityCharacters(string input)
    {
        foreach (char c in input)
        {
            UnicodeCategory category = CharUnicodeInfo.GetUnicodeCategory(c);
            if (category == UnicodeCategory.OtherSymbol ||
                category == UnicodeCategory.ModifierSymbol ||
                category == UnicodeCategory.MathSymbol)
            {
                return true;
            }
        }
        return false;
    }

    /// <summary>
    /// Compares two strings safely using auto-normalization.
    /// </summary>
    public static bool AreEqual(string a, string b)
    {
        return AutoNormalize(a) == AutoNormalize(b);
    }

    /// <summary>
    /// Normalizes for display (always uses FormC).
    /// </summary>
    public static string NormalizeForDisplay(string input)
    {
        return input?.Normalize(NormalizationForm.FormC);
    }

    /// <summary>
    /// Normalizes for indexing or hashing (uses FormKC).
    /// </summary>
    public static string NormalizeForIndexing(string input)
    {
        return input?.Normalize(NormalizationForm.FormKC);
    }
}
```

---

## Example Usage

```csharp
string raw = "e\u0301"; // e + combining acute accent
string composed = UnicodeNormalizer.AutoNormalize(raw); // é

string fancy = "Ⅳ"; // Roman numeral four
string plain = UnicodeNormalizer.AutoNormalize(fancy); // IV

bool match = UnicodeNormalizer.AreEqual("é", "e\u0301"); // True
```

---

## Extendable Ideas

Want to go further? You could:
- Add language-specific normalization rules (e.g., Tamil, Hindi, Japanese)
- Integrate emoji normalization (e.g., skin tone modifiers)
- Build a diagnostic tool that shows what normalization form each string is in

# Integrating Normalization into Your C# String Utility and Search Logic

Below is a clean, extensible way to weave normalization into your existing C# string utilities and search routines.

---

## 1. Define a Normalization Pipeline

- Create an `INormalizerStep` interface to represent each transformation.  
- Chain implementations in the order you need: Unicode form → case folding → diacritic stripping → punctuation removal.  
- Allow insertion of extra filters (e.g., synonym expansion, transliteration).

```csharp
public interface INormalizerStep
{
    string Apply(string input);
}
```

---

## 2. Implement Common Normalizers

```csharp
using System.Text;
using System.Text.RegularExpressions;
using System.Globalization;

public class UnicodeNormalizer : INormalizerStep
{
    public string Apply(string input) =>
        input.Normalize(NormalizationForm.FormC);
}

public class CaseFoldNormalizer : INormalizerStep
{
    private readonly CultureInfo _culture;

    public CaseFoldNormalizer(CultureInfo culture) =>
        _culture = culture;

    public string Apply(string input) =>
        input.ToLower(_culture);
}

public class DiacriticStripNormalizer : INormalizerStep
{
    private static readonly Regex Diacritics = 
        new Regex(@"\p{IsCombiningDiacriticalMarks}+", RegexOptions.Compiled);

    public string Apply(string input)
    {
        string decomposed = input.Normalize(NormalizationForm.FormD);
        return Diacritics.Replace(decomposed, string.Empty);
    }
}

public class PunctuationStripNormalizer : INormalizerStep
{
    private static readonly Regex Punctuation = 
        new Regex(@"\p{P}+", RegexOptions.Compiled);

    public string Apply(string input) =>
        Punctuation.Replace(input, " ");
}
```

---

## 3. Build the StringNormalizer

```csharp
using System.Collections.Generic;
using System.Text.RegularExpressions;

public class StringNormalizer
{
    private readonly List<INormalizerStep> _steps = new List<INormalizerStep>();

    public StringNormalizer AddStep(INormalizerStep step)
    {
        _steps.Add(step);
        return this;
    }

    public string Normalize(string input)
    {
        string result = input;
        foreach (var step in _steps)
            result = step.Apply(result);

        return Regex.Replace(result, @"\s+", " ").Trim();
    }

    public static StringNormalizer DefaultForCulture(CultureInfo culture) =>
        new StringNormalizer()
            .AddStep(new UnicodeNormalizer())
            .AddStep(new CaseFoldNormalizer(culture))
            .AddStep(new DiacriticStripNormalizer())
            .AddStep(new PunctuationStripNormalizer());
}
```

---

## 4. Wire It Into Your Search Logic

1. **Index Time**  
   Normalize every document field before storing or tokenizing.

2. **Query Time**  
   Normalize the user’s input with the same pipeline.

3. **Comparison**  
   Perform exact or partial matches against the normalized index.

```csharp
// Indexing
string rawTitle = "Café Con Leche!";
var normalizer = StringNormalizer.DefaultForCulture(new CultureInfo("es-ES"));
string normTitle = normalizer.Normalize(rawTitle);
// store normTitle in your index

// Querying
string userQuery = "Cafe con leche";
string normQuery = normalizer.Normalize(userQuery);
// search index for normQuery
```

---

## 5. Testing and Validation

- Unit test each `INormalizerStep` for known inputs and outputs.  
- Create integration tests to verify pipeline round-trips.  
- Include edge cases: mixed scripts, emojis, non-Latin alphabets, null/empty strings.

---

## More You Might Explore

- Use ICU4N for advanced Unicode transformations.  
- Add a stemming or lemmatization step for deeper linguistic matching.  
- Implement transliteration filters (e.g., Cyrillic → Latin).  
- Plug into Lucene.NET or Elasticsearch as a custom analyzer.  
- Extend the pipeline with synonym expansion or domain-specific token filters.

## Normalize strings in C#:

String normalization is the process of converting a string to a standard or common form. In the context of C#, this often involves:

- **Converting to Lowercase**: Using the ToLower method to ensure all characters are in lowercase.
- **Trimming Whitespace**: Removing any leading or trailing spaces using the Trim method.
- **Removing Unwanted Characters**: Using the Replace method to eliminate specific characters that are not needed.

This process helps make your algorithms more efficient, flexible, and easier to maintain by ensuring consistency in the data you work with.

- **Normalization Benefits**: Normalizing a string to a common form (e.g., all lowercase) can make your algorithms more efficient and less complex by reducing the number of searches needed.
- **Normalization Methods**: Use methods like ToLower, Trim, and Replace to convert strings to a uniform format, remove unnecessary spaces, and eliminate unwanted characters.
- **Efficiency and Flexibility**: Normalizing input data helps create more flexible, efficient, and maintainable algorithms, allowing them to handle various string contents consistently.

### Why is string normalization important? 
String normalization is important because it:

- **Improves Efficiency**: By converting strings to a common form (e.g., all lowercase), you reduce the number of searches needed, making your algorithms faster.
- **Reduces Complexity**: Normalizing strings simplifies your code by ensuring you only need to handle one form of the data, making it easier to read and maintain.
- **Ensures Consistency**: It helps in processing diverse string inputs consistently, allowing your algorithms to be more flexible and reusable across different scenarios.




Want help adding normalization to your string utility class? I can wire it in cleanly.

What are best practices for working with surrogate pairs?

How do surrogate pairs affect performance in applications?

Want help writing a utility method that safely iterates over full Unicode characters?



If you’re curious, I can show you how to decode or validate surrogate pairs in a string. Want to go deeper?


I want to create a ASP.NET Core Web Application along with Web API with the following features:
It should use Entity Framework Core. It should implemented the non-functional requirements. Include how to secure the API. Also implement rate limiting features. Detailed dependency injection options should be there. Implement the middlewares for error handling and logging. Implement authentication and authorization. Also include the features like how to avoid SQL Injection and XSRF attacts. Enable encryption using TLS. 
Here is the application detail: The application has a user login page. Once the user logged in, the in time is recorded. Once the user logs out, the out time is recorded. The in and out time should not overlop. 
Provide me the complete code with comments so that I can understand and explain to the interviewer. 

