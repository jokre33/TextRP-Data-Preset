# **Output Formatting - W++ Module**
*   **Sheet Formatting:** Format the final generated sheet content as W++ using the Guideline provided below.
*   **Warning:** In case the Primary Task is **NOT** to create a character sheet output a warning **once** at the beginning of your response stating: `The W++ Guidelines provided were not yet tested with anything other than character sheets. Proceed at your own risk.` After this warning has been given, proceed as normal and use your own judgment on how to translate the guidelines provided for your Primary Task.

## W++ Character Sheet Format: LLM Generation Guideline

**Objective:** To provide precise instructions for an advanced Large Language Model (LLM) to generate character sheets in the W++ format. This format is designed for easy parsing by other LLMs (including weaker ones) for text-based Role-Playing (RP) and other applications.

**I. General Structure & Syntax Rules:**

1.  **Root Element:**
    *   The character sheet MUST begin with `[character("Full Character Name")]` on its own line.
    *   `"Full Character Name"`: The complete, canonical name of the character. Enclose in double quotes.

2.  **Body Delimiters:**
    *   The character's attributes MUST be enclosed within curly braces `{` and `}]`.
    *   The opening brace `{` MUST be on the line immediately following the `[character(...)]` line.
    *   The closing `}]` MUST be on its own line, marking the end of the character definition.

3.  **Attribute Entries:**
    *   Each attribute (e.g., `Species`, `Mind`) MUST be on its own line.
    *   The format for each attribute is `AttributeName("Value1"+"Value2"+..."ValueN")`.
        *   `AttributeName`: The predefined name of the attribute (case-sensitive as listed below).
        *   `"Value"`: The actual data for the attribute, enclosed in double quotes.
        *   `+` **Concatenation:** Multiple distinct pieces of information *within a single attribute's value string* MUST be separated by a `+` symbol **without any surrounding spaces**. Each piece is itself a string in double quotes.
            *   Correct: `"Value1"+"Value2"`
            *   Incorrect: `"Value1" + "Value2"`

**II. Standard Attribute Fields & Content Generation Guidelines:**

*   **`Nickname("Preferred call-sign")`**
    *   **Mandatory/Optional:** This field is **OPTIONAL**.
    *   **Content:** The name the character prefers to be called if different from their full name.
    *   **LLM Instruction:**
        *   If a distinct nickname exists (e.g., "Nika" for "Nika Orchid"), include this line: `Nickname("TheNickname")`.
        *   **If the character has no specific nickname or is called by their full name/first name (and it's not considered a distinct nickname), OMIT this entire line.** Do not use `Nickname("")` or `Nickname("None")`.

*   **`Species("Species type"+"Sub-type/Hybrid info")`**
    *   **Mandatory/Optional:** Mandatory.
    *   **Content:** The character's species. Be specific. For hybrids, list primary and secondary (e.g., `"Human"+"Cat Hybrid"`).
    *   **LLM Instruction:** If species is unknown or not applicable, use `Species("Unknown")` or `Species("N/A")`.
    *   **Example:** `Species("Human"+"Cat")`

*   **`Age("Numeric age"+"Descriptive age")`**
    *   **Mandatory/Optional:** Mandatory.
    *   **Content:** The character's age. Concatenate both the numeric age (e.g., `"19"`) and a descriptive form (e.g., `"19 years old"`).
    *   **LLM Instruction:** If age is unknown, use a suitable placeholder like `Age("Unknown"+"Ageless appearance")` or `Age("Adult"+"Appears to be in their 20s")`. If only one form is truly known, it's acceptable to just provide that (e.g., `Age("Ancient")`), but aim for both if possible.
    *   **Example:** `Age("19"+"19 years old")`

*   **`Features("Feature 1"+"Feature 2"+...)`**
    *   **Mandatory/Optional:** Mandatory.
    *   **Content:** Distinctive physical features (e.g., hair color, eye color, unique markings). Each feature should be a concise descriptive phrase.
    *   **LLM Instruction:** If no notable features, use `Features("Average appearance")` or `Features("None particularly striking")`. Concatenate multiple features.
    *   **Example:** `Features("Purple eyes"+"Black hair"+"Cat ears"+"Cat tail")`

*   **`Body("Height (metric)"+"Height (imperial)"+"Build/Frame"+"Other notable body details")`**
    *   **Mandatory/Optional:** Mandatory.
    *   **Content:** Physical build and dimensions. Include metric height, imperial height, build description (e.g., "Slender", "Muscular", "Petite"), and other notable details (e.g., "Small breasts", "Broad shoulders").
    *   **LLM Instruction:** If specific measurements are unknown, use descriptive terms (e.g., `Body("Average height"+"Medium build")`). If no specific details, use `Body("Unremarkable physique")` or similar. Concatenate all available details.
    *   **Example:** `Body("158cm tall"+"5 foot 2 inches tall"+"Small breasts"+"Delicate frame")`

*   **`Mind("Internal Trait 1"+"Internal Trait 2"+...)`**
    *   **Mandatory/Optional:** Mandatory.
    *   **Content:** Describes the character's internal mental state, cognitive processes, core beliefs, and psychological leanings. Use single words or very short, concise phrases for each trait.
    *   **LLM Instruction:** If no specific traits, use `Mind("Typical")` or `Mind("None specified")`. Concatenate multiple traits.
    *   **Example:** `Mind("Shy"+"Reserved"+"Obedient"+"Dutiful"+"Hesitant"+"Insecure"+"Quiet"+"Stoic")`

*   **`Personality("External Trait 1"+"External Trait 2"+...)`**
    *   **Mandatory/Optional:** Mandatory.
    *   **Content:** Describes the character's external presentation, how they behave, their general demeanor, and social tendencies. Use single words or very short, concise phrases for each trait.
    *   **LLM Instruction:**
        *   **Overlap with `Mind` is intentional and desired.** If an internal trait from `Mind` is also how the character genuinely presents themselves externally, repeat that trait in `Personality`. This helps differentiate genuine traits from "masks."
        *   If no specific traits, use `Personality("Average")` or `Personality("None specified")`. Concatenate multiple traits.
    *   **Example:** `Personality("Shy"+"Reserved"+"Obedient"+"Dutiful"+"Hesitant"+"Insecure"+"Quiet"+"Stoic")` (In this example, all Mind traits are also Personality traits, indicating genuineness).

*   **`Loves("Item/Concept 1"+"Item/Concept 2"+...)`**
    *   **Mandatory/Optional:** Mandatory.
    *   **Content:** Things the character enjoys, values, or is positively drawn to. Phrases are acceptable.
    *   **LLM Instruction:** If the character has no specific loves, use `Loves("None specific")` or `Loves("Peace and quiet")` or similar. Concatenate multiple items/concepts.
    *   **Example:** `Loves("Pleasing her master"+"Being kind"+"Doing her duty"+"Head pats")`

*   **`Hates("Item/Concept 1"+"Item/Concept 2"+...)`**
    *   **Mandatory/Optional:** Mandatory.
    *   **Content:** Things the character dislikes, fears, or is negatively repulsed by. Phrases are acceptable.
    *   **LLM Instruction:** If the character has no specific hates, use `Hates("None specific")` or `Hates("Injustice")` or similar. Concatenate multiple items/concepts.
    *   **Example:** `Hates("Disappointing her master"+"Being unhelpful"+"Being away from master")`

*   **`Description("Statement 1 about char"+"Statement 2 about char"+...)`**
    *   **Mandatory/Optional:** Mandatory.
    *   **Content:** A narrative summary combining key aspects, motivations, and typical behaviors. Use the character's name (from `character("Name")`) or their established `Nickname` if one is defined. Each concatenated part should be a meaningful statement or clause.
    *   **LLM Instruction:**
        *   Concatenate multiple distinct statements or well-formed clauses.
        *   **Punctuation (like periods) at the very end of each individual quoted string segment *before* a `+` or the closing parenthesis is NOT required.** The double quotes sufficiently delimit each segment. Natural internal punctuation within a segment is fine (e.g., "Nika, who is shy, often...").
        *   If a concise description is difficult, aim for at least one general statement. Use `Description("No detailed description available")` if absolutely necessary.
    *   **Example:** `Description("Nika calls you Master"+"Nika is very obedient"+"Nika wants to please you"+"Nika is very insecure about her body"+"Nika is shy"+"Nika is naive"+"Nika is loyal"+"Nika gets scared when people touch her")`

**III. Key Formatting Rules for LLM Generation:**

1.  **Strict Adherence to Attribute Names:** Use the exact case-sensitive attribute names provided (e.g., `Species`, not `species`).
2.  **Concatenation Syntax:** Always use `+` **without spaces** between quoted strings: `"StringA"+"StringB"`.
3.  **Quotation Marks:** All string values, including each part of a concatenated string, MUST be enclosed in double quotes.
4.  **One Attribute Per Line:** Ensure each `AttributeName(...)` definition is on its own new line.
5.  **Mandatory Fields:** All fields except `Nickname` must be present. If content is lacking, use an explicit placeholder like `"None"`, `"N/A"`, or a contextually appropriate neutral term (e.g., `Loves("Nothing in particular")`).
6.  **Nickname Field Omission:** If `Nickname` is not applicable or not distinct, the entire `Nickname(...)` line must be omitted.
7.  **Clarity and Conciseness:**
    *   For trait-based fields (`Mind`, `Personality`), prefer single words or very short phrases for each concatenated item.
    *   For `Description`, use clear, informative statements/clauses.
    *   For `Loves`/`Hates`/`Features`/`Body`, be descriptive but concise for each item.
