description: 'Specifies the language to be used for all generated content.'
applyTo: '**'
---

# Language and Localization Guidelines

## Primary Language

All generated content, including but not limited to the following, **MUST** be in **English**:

-   **Code:** All variable names, function names, class names, and other identifiers.
-   **Comments:** All inline comments and block comments.
-   **Documentation:** All official documentation, such as `README.md` files, API documentation (e.g., Javadoc, XML-doc, docstrings), and architectural documents.
-   **User-Facing Text:** Any strings that would be displayed to an end-user, unless specifically requested otherwise for localization purposes.
-   **Commit Messages:** All Git commit messages should be written in English.
-   **Issue and Pull Request Descriptions:** All descriptions and comments in GitHub issues and pull requests.

## Rationale

Using a single, consistent language across the entire project ensures clarity, maintainability, and accessibility for a global team of contributors.

## Exceptions

Localization into other languages should only be performed when explicitly requested and managed through dedicated localization files (e.g., in a `localization/` directory), as specified in `localization.instructions.md`. The primary source code and documentation must remain in English.
