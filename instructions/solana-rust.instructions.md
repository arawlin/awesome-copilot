
# Instructions for Solana Rust/Anchor Program Analysis

When reviewing or writing Solana programs, adhere to the following principles and checks.

## 1. Core Solana Concepts

- **Accounts Model**: Remember that Solana is stateless. All data is stored in accounts. State is modified by passing accounts to programs.
- **Program-Derived Addresses (PDAs)**:
    - PDAs are essential for creating program-owned accounts.
    - Always validate that a PDA was derived with the correct seeds and bump. Anchor handles this with constraints, but manual checks are critical in non-Anchor code.
    - Ensure bumps are canonical. A non-canonical bump can lead to different addresses for the same seeds.
- **Cross-Program Invocations (CPIs)**:
    - When calling another program, ensure all required accounts are passed correctly and have the right permissions (e.g., `mut`, `signer`).
    - Treat CPIs as a trust boundary. The called program could be malicious or buggy. Validate any data returned or state changed by the CPI.
- **Compute Units (CU)**:
    - Every instruction has a limited budget (default 200,000 CU).
    - Operations like deserialization, complex calculations, or large loops consume CUs.
    - Write efficient code to avoid "ComputeBudgetExceeded" errors. Profile and optimize critical paths.

## 2. Anchor Framework Best Practices

- **Use Constraints Extensively**: Anchor's account constraints are the primary defense against security vulnerabilities.
    - `#[account(mut)]`: Ensures an account can be modified.
    - `#[account(signer)]`: Verifies that the account holder has signed the transaction.
    - `#[account(init, ...)]`: For creating new accounts. Ensure `payer` and `space` are correctly defined.
    - `#[account(seeds = [...], bump)]`: The most critical constraint for PDAs. It ensures the account address matches the seeds.
    - `#[account(owner = ...)]`: Verifies the account is owned by the expected program (often `SystemProgram` for new accounts or the calling program itself).
    - `#[account(constraint = ...)]`: For custom validation logic (e.g., `my_pda.owner == *program_id`). Use this for complex checks.
- **Zero-Copy Deserialization**: For performance-critical accounts with large state, use `#[account(zero_copy)]`. This avoids costly deserialization by mapping the account data directly to a struct.
- **Event Logging**: Use `emit!` to log events. This is crucial for off-chain clients and indexers to track program activity.

## 3. Common Solana Security Vulnerabilities

- **Missing Signer Check**: An instruction that should only be callable by a specific user/authority is missing a `signer` check. This allows anyone to call it.
- **Incorrect Owner Check**: The program interacts with an account without verifying its `owner` field. A malicious user could pass an account owned by a different program, leading to unexpected behavior.
- **Arbitrary CPI**: Allowing a user to specify which program to CPI to. This is extremely dangerous and can lead to theft of funds or state corruption. Program IDs for CPIs should almost always be hardcoded.
- **Type Cosplay / Account Confusion**: A user passes an account of one type where an account of another type is expected. Use Anchor's `#[account(discriminator)]` or manual checks to prevent this. Anchor 8+ adds a discriminator automatically.
- **PDA Sharing/Collision**: Using the same seeds for different types of PDAs. Always include a unique prefix (e.g., `b"user_state"`) in your seeds.
- **Integer Overflow/Underflow**: Rust's `u64` and other integer types can overflow in `debug` builds but will panic in `release` builds by default if not using `wrapping_` or `saturating_` arithmetic. Always use checked arithmetic (`checked_add`, `checked_sub`, etc.) for financial calculations.
- **Denial of Service (DoS)**:
    - **Large Account Creation**: Allowing a user to create an arbitrarily large account, potentially draining a payer's funds. Use `space` checks.
    - **Compute-Intensive Logic**: Logic that can be made to loop or perform heavy computation based on user input, exceeding the compute budget.

## 4. Code Style and Structure

- **Modularize Logic**: Separate validation logic from business logic. Use private functions within your instruction handlers.
- **Clear Error Types**: Use custom, descriptive error types (`#[error(...)]`) to make debugging easier.
- **Follow Rust Idioms**: Write clean, idiomatic Rust. Use `Result`, `Option`, and iterators effectively.
