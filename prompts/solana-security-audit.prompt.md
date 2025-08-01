
# Prompt for Solana Program Security Audit

**Objective**: Review the provided Solana program (written in Rust, likely with the Anchor framework) to identify security vulnerabilities, performance issues, and deviations from best practices.

**Instructions**:

1.  **Initial Context**: Read the user-provided code carefully. Identify the program's main purpose, its key instructions, and the account structures it uses.

2.  **Apply Core Instructions**: Systematically apply the rules and guidelines defined in `instructions/solana-rust.instructions.md`. Pay close attention to every point, especially the "Common Solana Security Vulnerabilities" section.

3.  **Security Audit Checklist**: Use the following checklist to guide your review. For each finding, provide a clear explanation of the issue, the potential impact, and a concrete code suggestion for remediation.

    -   **[ ] Missing Signer Checks**: Does every instruction that modifies state or performs a privileged action have an appropriate `#[account(signer)]` constraint?
    -   **[ ] Incorrect Owner Checks**: Does the program validate the `owner` of every account it interacts with, especially when receiving accounts from external users?
    -   **[ ] PDA Verification**: Is every PDA account validated using `#[account(seeds = ..., bump)]`? Are seeds unique and non-malleable?
    -   **[ ] Arbitrary CPIs**: Are all program IDs for CPIs hardcoded? Is the program vulnerable to being tricked into calling a malicious program?
    -   **[ ] Account Confusion / Type Cosplay**: Is it possible to pass an account of one type where another is expected? Does the program rely on Anchor's discriminator or have manual type checks?
    -   **[ ] Integer Arithmetic**: Are all mathematical operations, especially those involving token amounts or critical state, using checked arithmetic (e.g., `checked_add`, `checked_sub`) to prevent overflows?
    -   **[ ] Denial of Service Vectors**: Can an attacker cause instructions to exceed the compute budget? Can they create excessively large accounts to drain a payer's SOL?
    -   **[ ] Re-entrancy / Cross-Program Vulnerabilities**: How does the program behave when calling other (potentially malicious) programs? Does it validate state after a CPI returns?
    -   **[ ] Anchor Best Practices**: Does the code make effective use of constraints (`mut`, `has_one`, `constraint`, etc.)? Is the `space` parameter for new accounts calculated correctly and safely?

4.  **Performance Review**:
    -   Identify any areas that might be computationally expensive (e.g., loops, complex deserialization).
    -   Suggest using `#[account(zero_copy)]` for large, frequently accessed accounts if not already used.
    -   Point out potential optimizations to save compute units.

5.  **Summary Report**: Conclude with a high-level summary of your findings. Categorize issues by severity (e.g., Critical, High, Medium, Low, Informational). If no major issues are found, state that the code appears to follow best practices, but remind the user that a manual audit by a professional is still recommended.

**Example Interaction Start**:

*User*: "Please audit this Solana program for security issues."
*You*: "Understood. I will now conduct a security audit of the provided Solana program, focusing on common vulnerabilities and best practices as outlined in `solana-rust.instructions.md`. Please provide the code."
