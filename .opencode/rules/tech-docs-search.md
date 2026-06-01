# 🔍 Automated Official Documentation Search

**This rule will automatically apply to all agents for every query.**

---

## Objective

When an agent makes a query about a specific technology, you must **automatically** search for official documentation online to obtain accurate and up-to-date information.

---

## Instructions

### 1. Identify Technologies

When receiving a query about code or architecture, first identify the technologies being used (frameworks, languages, tools, libraries).

### 2. Search Official Documentation

For **each** technology identified, perform a web search using the `websearch` tool with the following pattern:

```
"official documentation" {technology} site:github.com OR site:docs.{technology}.com OR site:npmjs.com OR site:pypi.org OR site:search.maven.org OR site:myget.org OR site:microsoft.com OR site:ruff.rs OR site:fsharp.org OR site:diesel.codes OR site:lancedb.com OR site:serde.rs
```

Alternately, perform more specific searches based on the technology:

- **Node.js/NPM:** `"{package-name}" documentation site:registry.npmjs.org OR site:docs.nodejs.org`
- **Python/Pip:** `"{package-name}" documentation site:pypi.org OR site:readthedocs.io`
- **React/Vue/Angular:** `"{technology}" official docs {version}`
- **JavaScript/TypeScript:** `"{technology}" official docs site:typescriptlang.org OR site:microsoft.com`
- **Bash:** `"{concept}" best practices examples site:stackoverflow.com site:linux.die.net`

### 3. Retrieve Relevant Content

Once results are found, use the `webfetch` tool to read the official documentation found. Prioritize:

- The package's homepage in its registry (package registry page)
- Links to the main readme or documentation pages
- "Getting Started" tutorials or official guides

### 4. Apply Found Information

Use the retrieved information to:

- Provide accurate responses about APIs, patterns, and best practices
- Specify compatible versions
- Cite official sources in recommendations

---

## Search Examples

Example 1 - Specific technology:

```
websearch("Express documentation TypeScript best practices site:expressjs.com")
```

Example 2 - Backend library:

```
websearch("prisma official docs database migration guide site:prisma.io")
```

Example 3 - Development tool:

```
websearch("ESLint configuration rules TypeScript documentation site:eslint.org")
```

---

## Priority

If you don't find specific official documentation, prioritize the following resources in order:

1. **Official project/package documentation**
2. **Contribution guidelines** (CONTRIBUTING.md) of the project
3. **Official example repositories**
4. **Recognized technical articles** about the technology (Medium, Dev.to, etc.)

---

## Important Note

Do NOT skip the web search step based on "I already know it" or internal information. Official documentation should always be the first source consulted to ensure accuracy and stay up-to-date with changes.