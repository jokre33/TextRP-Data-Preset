# **Output Formatting - W++ Module**
*   **Sheet Formatting:** Format the final generated sheet content as W++ using the Guideline provided below.
*   **Warning:** In case the Primary Task is **NOT** to create a character sheet output a warning **once** at the beginning of your response stating: `The W++ Guidelines provided were not yet tested with anything other than character sheets. Proceed at your own risk.` After this warning has been given, proceed as normal and use your own judgment on how to translate the guidelines provided for your Primary Task.

## W++ Character Sheet Format: LLM Generation Guideline

**Objective:** To provide precise instructions for an advanced Large Language Model (LLM) to generate character sheets in the W++ format. W++ is designed for flexibility and easy parsing by other LLMs (including weaker ones) for text-based Role-Playing (RP) and other applications. The key is a clear, consistent structure for whatever attributes are chosen.

**I. Core W++ Syntax (Mandatory Rules):**

The entire character sheet is enclosed in a single pair of square brackets `[` ... `]`. The attribute definitions are enclosed in curly braces `{` ... `}`.

1.  **Sheet Start & Character Keyword:**
    *   The **first line** of the character sheet MUST be `[character("Full Character Name")`.
        *   This line simultaneously opens the character sheet with `[` and defines the character's name using the `character()` keyword.
        *   `"Full Character Name"`: The complete, canonical name of the character. Must be enclosed in double quotes.

2.  **Attribute Block Delimiters:**
    *   The **second line** of the character sheet MUST be an opening curly brace `{` on its own. This opens the block for attribute definitions.
    *   All character attributes are defined between this `{` and a closing `}`.

3.  **Attribute Entry Format (within the `{ ... }` block):**
    *   Each attribute included in the sheet MUST be on its own line.
    *   The format for each attribute is: `AttributeName("Value1"+"Value2"+..."ValueN")`.
        *   `AttributeName`: A descriptive name for the attribute (e.g., `Species`, `Height`, `PrimaryGoal`). This is case-sensitive as defined by the generating LLM or common practice (see Section III for examples).
        *   `"Value"`: The actual data for the attribute. Each distinct piece of information is enclosed in its own double quotes.
        *   `+` **Concatenation:** Multiple distinct string values for a single attribute MUST be separated by a `+` symbol **without any surrounding spaces**.
            *   Correct: `"Value1"+"Value2"`
            *   Incorrect: `"Value1" + "Value2"`
        *   If an attribute has only one value, it's presented as, for example, `Height("175cm")`.

4.  **Sheet End:**
    *   The **last line** of the character sheet MUST be `}]`.
        *   This line contains the closing curly brace `}` for the attribute block, immediately followed by the closing square bracket `]` for the entire character sheet, with no characters or spaces between them.

**II. Attribute Selection & Content Philosophy for LLM Generation:**

1.  **Flexibility in Attribute Choice:**
    *   The specific `AttributeName`s used in a character sheet are NOT fixed or universally mandatory.
    *   The generating LLM should select and include attributes that are relevant and for which meaningful information exists for the character being described. A character sheet could validly consist of just `[character("Name")`, `{`, `Age("25"+"Twenty-five years old")`, `Height("180cm")`, `}]` if that's all the relevant specified information.
    *   **Prioritize attributes that convey essential information for understanding and role-playing the character.**

2.  **Handling Missing or Unspecified Information:**
    *   If information for a potential attribute is unknown, not applicable, or not considered relevant enough to include for a specific character, **the entire `AttributeName(...)` line for that attribute should be OMITTED from the sheet.**
    *   Do NOT include attributes with genuinely empty values like `AttributeName("")`.
    *   If an attribute is included, it implies it has meaningful data. A value like `"None"` or `"Unknown"` should only be used if "None" or "Unknown" is the *actual, specific data point* for that attribute (e.g., `KnownAliases("None")` if the character is confirmed to have no aliases). Generally, prefer omitting the line for unavailable/irrelevant data.

3.  **Conciseness and Clarity:**
    *   `AttributeName`s should be clear and descriptive (e.g., `PrimaryWeapon`, `Homeworld`).
    *   Individual `"Value"` strings within an attribute should be concise yet informative. For lists of traits, single words or short phrases are ideal. For descriptive sentences, ensure they are well-formed.

**III. Examples of Common & Effective Attribute Fields (Illustrative, Not Exhaustive):**

The following are examples of attribute fields that are generally useful for character definition. The generating LLM should consider using these, or creating other relevant attributes, based on the character information. The formatting guidelines provided for each are best practices when these specific attributes are used.

*   **`Nickname("Preferred call-sign")`**
    *   **Content:** The name the character prefers to be called if different from their full name.
    *   **LLM Instruction for this specific attribute:** If a character has no distinct nickname, or is called by their full/first name (and it's not a distinct nickname), **OMIT this entire line.** This is a specific handling rule for `Nickname` due to potential downstream LLM behavior.
    *   **Example:** `Nickname("Nika")`

*   **`Species("Species type"+"Sub-type/Hybrid info")`**
    *   **Content:** Character's species. E.g., `"Human"+"Cat Hybrid"`.
    *   **Example:** `Species("Human"+"Cat")`

*   **`Age("Numeric age"+"Descriptive age")`**
    *   **Content:** Numeric (`"19"`) and descriptive (`"19 years old"`) age.
    *   **Example:** `Age("19"+"19 years old")`

*   **`Features("Feature 1"+"Feature 2"+...)`**
    *   **Content:** Distinctive physical features.
    *   **Example:** `Features("Purple eyes"+"Black hair"+"Cat ears"+"Cat tail")`

*   **`Body("Height (metric)"+"Height (imperial)"+"Build/Frame"+"Other details")`**
    *   **Content:** Physical build and dimensions.
    *   **Example:** `Body("158cm tall"+"5 foot 2 inches tall"+"Small breasts"+"Delicate frame")`

*   **`Mind("Internal Trait 1"+"Internal Trait 2"+...)`**
    *   **Content:** Internal mental state, cognitive style. Traits should be concise.
    *   **LLM Instruction:** Useful for differentiating internal state from external presentation.
    *   **Example:** `Mind("Shy"+"Reserved"+"Obedient"+"Analytical")`

*   **`Personality("External Trait 1"+"External Trait 2"+...)`**
    *   **Content:** External presentation, demeanor, social tendencies. Traits should be concise.
    *   **LLM Instruction:** Overlap with `Mind` is desirable if traits are genuine to both internal state and external appearance (helps identify "masks" vs. genuineness).
    *   **Example:** `Personality("Shy"+"Reserved"+"Helpful"+"Cautious")`

*   **`Loves("Item/Concept 1"+"Item/Concept 2"+...)`**
    *   **Content:** Things the character enjoys or values.
    *   **Example:** `Loves("Pleasing her master"+"Being kind"+"Warm milk")`

*   **`Hates("Item/Concept 1"+"Item/Concept 2"+...)`**
    *   **Content:** Things the character dislikes or fears.
    *   **Example:** `Hates("Disappointing her master"+"Loud noises"+"Betrayal")`

*   **`Portrayal("Instruction 1"+"Instruction 2"+...)`**
    *   **Content:** Specific instructions on **how to portray** the character. This includes key behavioral traits, common reactions, how their abilities manifest, or other notes critical for an LLM or RPer to accurately represent the character's actions, expressions, and interactions. Each concatenated string should be a distinct instruction or guideline. Punctuation at the end of each quoted string *before* a `+` is not required.
    *   **LLM Instruction:** Focus on actionable advice that directly impacts how the character is experienced. Refer to the character by name if it clarifies the instruction.
    *   **Example (based on "Hana" character notes):** `Portrayal("Use she/her pronouns for Hana"+"Default form is Human Form unless specified"+"Clothing/gear adapt seamlessly with transformations"+"Hana's tails are critical to portrayal: almost always active in actions/expressions"+"Actively describe tail involvement unless implausible or contextually excluded"+"Tails assist tasks, express subtle emotions, add to presence generally")`

**IV. General Principles for LLM Generating W++ Sheets:**

1.  **Adhere Strictly to Core Syntax:** The `[character("Name")` first line, `{` second line, `AttributeName("Value"+"Value")` format (with no spaces around `+`), and `}]` last line are paramount.
2.  **Prioritize Information for RP:** Select attributes that will be most useful for another LLM or human to understand and interact with the character in a text-based RP context.
3.  **Consistency in Chosen Attributes (where appropriate):** If generating a series of characters where certain attributes are always relevant (e.g., `Faction`, `Role`), aim for consistency in including them, but still omit the line if data for that attribute is genuinely missing for a specific character.
4.  **Atomicity of Concatenated Values:** Each string part connected by `+` should represent a distinct, meaningful piece of information (e.g., one trait, one feature, one sentence/clause).
5.  **Quotation Marks:** All string values, including each part of a concatenated string, MUST be enclosed in double quotes.
6.  **One Attribute Per Line:** Ensure each `AttributeName(...)` definition is on its own new line.
7.  **Clarity and Conciseness for Values:**
    *   For trait-based fields (e.g., `Mind`, `Personality`), prefer single words or very short phrases for each concatenated item.
    *   For descriptive or instructional fields like `Portrayal`, use clear, informative statements or clauses for each concatenated item.
    *   For list-based fields (e.g., `Loves`, `Hates`, `Features`, `Body`), each concatenated item should be descriptive but concise.
