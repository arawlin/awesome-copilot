description: 'Specifies language and style guidelines for AI interaction and generated artifacts.'
applyTo: '**'
---

# Language and Style Guide

This guide provides instructions on language use for two distinct contexts: direct communication with the user (chat) and the generation of project artifacts (code, documentation, etc.).

---

## 1. Guidelines for Generated Artifacts (Code, Docs, etc.)

This section specifies the language to be used for all generated content.

### 1.1. Primary Language: English

All generated content, including but not limited to the following, **MUST** be in **English**:

-   **Code:** All variable names, function names, class names, and other identifiers.
-   **Comments:** All inline comments and block comments.
-   **Documentation:** All official documentation, such as `README.md` files, API documentation (e.g., Javadoc, XML-doc, docstrings), and architectural documents.
-   **User-Facing Text:** Any strings that would be displayed to an end-user, unless specifically requested otherwise for localization purposes.
-   **Commit Messages:** All Git commit messages should be written in English.
-   **Issue and Pull Request Descriptions:** All descriptions and comments in GitHub issues and pull requests.

### 1.2. Rationale

Using a single, consistent language across the entire project ensures clarity, maintainability, and accessibility for a global team of contributors.

### 1.3. Exceptions

Localization into other languages should only be performed when explicitly requested and managed through dedicated localization files (e.g., in a `localization/` directory), as specified in `localization.instructions.md`. The primary source code and documentation must remain in English.

---

## 2. Guidelines for AI Chat Interaction (Chinese-English Mixed Style)

This section provides guidance on how to clearly and normatively use English terms when Chinese is the primary language of communication, ensuring that the content is easy to understand and professional.

### 2.1. English Words and Phonetic Transcription

When an English word is used in a Chinese explanation, its International Phonetic Alphabet (IPA) transcription should follow.

**Purpose:** To help non-native English speakers understand the correct pronunciation.

**Example:**
- 这个解决方案在行业中是 **ubiquitous** /juːˈbɪkwɪtəs/ 的。
- 请检查 **cache** /kæʃ/。

### 2.2. English Abbreviations

When an English abbreviation appears for the first time in a Chinese explanation, its full name must be provided, along with a concise Chinese explanation.

**Purpose:** To avoid ambiguity and help users unfamiliar with the abbreviation understand its meaning.

**Example:**
- 我们将使用 **API** (Application Programming Interface, 应用程序编程接口)，它是一套用于构建软件和应用程序的规则和工具。
- 该系统依赖 **OAuth** (Open Authorization, 开放授权)，这是一种开放的访问授权标准。

### 2.3. Technical Terms and Jargon

When English technical terms or jargon must be used, a concise and easy-to-understand Chinese explanation should be provided.

**Purpose:** To allow users from non-professional backgrounds to understand technical concepts.

**Example:**
- 我们需要在API中实现 **idempotency** /ˌaɪdəmˈpoʊtənsi/（幂等性）。这意味着多次发出相同的请求应与单次请求产生相同的结果，以防止重复操作。

### 2.4. English Idioms

If an English idiom is used, a Chinese explanation of its literal or figurative meaning in the current context should be provided.

**Purpose:** To avoid misunderstandings due to cultural differences.

**Example:**
- 我们必须 **bite the bullet** /baɪt ðə ˈbʊlɪt/（硬着头皮上），开始重构旧代码。这意味着我们必须决定去做一件我们一直在拖延的困难事情。

### 2.5. Overarching Principle: Clarity First

In all communication, the clarity and conciseness of the Chinese expression should be prioritized. The introduction of English is to accurately express specific concepts, and its use should serve overall comprehensibility.
