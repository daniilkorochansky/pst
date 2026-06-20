# PST-XXXX: Template for New Pawn Standards and Techniques

```text
PST: XXXX (Leave as XXXX, the editor will assign a number)
Title: <A short, descriptive title of your proposal>
Author: <Your Name> (<GitHub Profile Link or Email>)
Status: Draft
Type: <Standards | Informational | Process>
Created: <DD-Mmm-YYYY, e.g., 20-Jun-2026>
```

## 1. Abstract
Provide a short (2-3 sentences) technical summary of the problem and your proposed solution. This helps readers quickly understand the essence of the document.

## 2. Motivation
Explain why this standard is necessary. 
* What problem does it solve in the SAMP / open.mp development workflow?
* Why are current community practices insufficient or outdated?
* What are the consequences of not adopting this standard?

## 3. Specification and Technical Requirements
This is the core of your document. Describe the technical details of your proposal with utmost clarity.
* Provide clear rules, syntax requirements, or architectural patterns.
* Use `pawn` code blocks to illustrate **CORRECT** and **INCORRECT** implementations.

```pawn
// Example of a correct implementation according to your standard
public OnGameModeInit()
{
    // Your code here
    return 1;
}
```

## 4. Rationale and Rejected Ideas
Explain why you chose this specific design or technical approach over alternatives. 
* If there were alternative ideas discussed in the community, list them here and explain why they were rejected (e.g., performance issues, compatibility bugs, or complexity).
* This section prevents future developers from re-opening old debates that have already been resolved.

## 5. Backward Compatibility
Address how this standard impacts existing Pawn scripts and legacy servers.
* Does it break compatibility with old compiler versions or standard SA-MP includes?
* If it introduces changes that require rewriting code, outline a migration path or explain how an IDE (like Spawn) can automate the transition.
