# Code Review Commenting Guide

## Purpose

The goal of code review is to improve code quality, share knowledge, reduce defects, and maintain architectural consistency. Effective review comments should help the author understand the issue and learn from the feedback.

---

# Principles of Good Review Comments

A good review comment should be:

* **Specific** – Clearly identify the issue.
* **Actionable** – Suggest what should be changed.
* **Constructive** – Focus on improving the code.
* **Respectful** – Review the code, not the developer.
* **Educational** – Explain the reasoning behind the recommendation.
* **Prioritized** – Distinguish between critical issues and minor suggestions.

---

# Recommended Review Comment Format

Use the following structure whenever possible:

## Observation → Impact → Suggestion

### Example

**Observation:**
XML validation is executed inside the processing loop.

**Impact:**
This may significantly increase execution time for large input files.

**Suggestion:**
Consider validating the XML once before processing or caching the validation results.

---

# Review Comment Categories

## 1. Correctness

Focus on bugs, edge cases, and unexpected behavior.

### Good Example

```text
If customerId is null, this code will throw a NullReferenceException.
Consider adding a null check before accessing the property.
```

### Avoid

```text
This looks wrong.
```

---

## 2. Reliability

Identify scenarios that may fail in production.

### Good Example

```text
This operation depends on an external service call.
How should the application behave if the service is unavailable?
```

---

## 3. Performance

Highlight inefficient algorithms and unnecessary resource usage.

### Good Example

```text
This LINQ query is executed for every iteration.
Consider materializing the results once before entering the loop.
```

### Good Example

```text
This operation has O(n²) complexity.
Would using a dictionary improve lookup performance?
```

---

## 4. Maintainability

Help future developers understand and modify the code.

### Good Example

```text
This method handles validation, transformation, and persistence.
Consider splitting it into smaller methods with a single responsibility.
```

---

## 5. Readability

Improve clarity without introducing unnecessary changes.

### Good Example

```text
The nested conditional logic is difficult to follow.
Consider using guard clauses to simplify the control flow.
```

---

## 6. Naming

Ensure code communicates intent.

### Good Example

```text
ProcessData() is quite generic.
Would ValidateAndTransformRegisters() better describe the behavior?
```

---

## 7. Architecture & Design

Check adherence to architectural principles.

### Good Example

```text
This class directly depends on a concrete implementation.
Consider depending on an interface to reduce coupling and improve testability.
```

### Good Example

```text
This component bypasses the established repository pattern.
Is there a reason for deviating from the project architecture?
```

---

## 8. Security

Identify potential vulnerabilities.

### Good Example

```text
The file path originates from user input.
Consider validating or sanitizing the value before using it.
```

---

## 9. Test Coverage

Ensure critical behavior is verified.

### Good Example

```text
Could we add a test covering the scenario where XML validation returns multiple schema errors?
```

### Good Example

```text
This change introduces new branching logic.
Please add unit tests covering the success and failure paths.
```

---

# Review Comment Priority Levels

## Must Fix

Use for correctness, security, reliability, and production-impacting issues.

```text
[Must Fix] This change introduces a race condition when multiple threads update the cache.
```

---

## Should Fix

Use for maintainability, performance, and design concerns.

```text
[Should Fix] Consider extracting this logic into a separate method to improve readability and testability.
```

---

## Suggestion

Use for optional improvements.

```text
[Suggestion] Consider using TryGetValue() to avoid double dictionary lookups.
```

---

## Question

Use when seeking clarification.

```text
[Question] Is there a reason for using a List instead of a HashSet here?
```

---

## Nitpick

Use only for minor style issues.

```text
[Nit] Extra blank line can be removed for consistency.
```

---

# Examples of Poor vs Good Comments

| Poor Comment       | Better Comment                                                                                                               |
| ------------------ | ---------------------------------------------------------------------------------------------------------------------------- |
| This is confusing. | The method performs validation, transformation, and persistence. Consider splitting responsibilities to improve readability. |
| Bad name.          | The method name does not clearly communicate intent. Would `ValidateConfiguration()` be more descriptive?                    |
| Optimize this.     | This query executes repeatedly inside a loop and may impact performance for large datasets. Consider caching the results.    |
| Looks wrong.       | If the input is null, this code path throws a NullReferenceException. Consider adding a guard clause.                        |

---

# AI-Assisted Code Review Checklist

When reviewing AI-generated code, pay extra attention to:

* Correctness
* Edge cases
* Null handling
* Thread safety
* Resource disposal
* Security vulnerabilities
* Performance implications
* Error handling
* API contract compliance
* Backward compatibility
* Test coverage

---

# Reviewer Do's

✅ Explain why a change is needed.

✅ Focus on the code, not the author.

✅ Provide examples when possible.

✅ Reference project standards and architectural guidelines.

✅ Acknowledge good implementations.

✅ Prioritize feedback based on risk.

---

# Reviewer Don'ts

❌ "This is bad."

❌ "I don't like this."

❌ "Rewrite this."

❌ Personal criticism.

❌ Comments without rationale.

❌ Style debates without established standards.

---

# Sample Review Comment Templates

## Bug

```text
[Must Fix]
This condition does not handle null input and may result in a runtime exception.
Consider adding a guard clause.
```

## Performance

```text
[Should Fix]
This query executes for every iteration of the loop.
Consider caching the result to reduce processing time.
```

## Design

```text
[Should Fix]
This class depends directly on the implementation.
Consider introducing an abstraction to reduce coupling.
```

## Testing

```text
[Should Fix]
Please add a test case covering the failure scenario introduced by this change.
```

## Clarification

```text
[Question]
Can you explain why this implementation was chosen instead of reusing the existing utility?
```

---

# Approval Checklist

Before approving a PR, verify:

* [ ] The code behaves correctly.
* [ ] Edge cases are handled.
* [ ] Tests are sufficient.
* [ ] No security concerns exist.
* [ ] No significant performance issues exist.
* [ ] Architecture guidelines are followed.
* [ ] Naming is clear and consistent.
* [ ] Documentation is updated if required.
* [ ] Backward compatibility is maintained.
* [ ] The code will be understandable six months from now.

---

# Key Takeaway

The best code review comments help the author understand:

1. What the issue is.
2. Why it matters.
3. How it can be improved.

Focus on learning, collaboration, and code quality—not on finding faults.
