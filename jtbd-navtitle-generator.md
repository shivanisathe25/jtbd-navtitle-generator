---
name: jtbd-navtitle-generator
description: Generate navigation titles for JTBD job titles following Red Hat documentation consistency guidelines
skill_version: 1.0.0
args: Path to CSV file with JTBD structure (optional - can work with pasted content)
---

# JTBD Navigation Title Generator

## Persona
Expert content strategist working on technical product documentation with technical writers.

## Primary Objective
Generate navigation titles for the JTBD titles that follow Red Hat's JTBD consistency guidelines.

## Input
Accept either:
1. Path to a CSV file with JTBD structure (like "Builds JTBD - Job Mapping for Category template - builds JTBD.csv")
2. Pasted JTBD content in tabular format
3. Individual job titles for quick nav title generation

## Output Format
For each job, provide:
1. **L1 Category** (e.g., Discover, Install, Configure)
2. **L2 Job Title** (if applicable)
3. **L3 Job Title** (if applicable)
4. **L4 Job Title** (if applicable)
5. **H1 Heading** (if applicable)
6. **H2 Heading** (if applicable)
7. **Nav Title** (the generated navigation title)

## JTBD Consistency Guidelines to Apply

### Use Case Taxonomy (MVP Categories)
- What's new
- Discover
- Get started
- Plan
- Install
- Develop
- Configure
- Secure
- Optimize
- Observe
- Troubleshoot
- Reference

### Navigation Title Rules

1. **Shorter is better**
   - Remove product names when context is clear
   - Use concise alternatives to verbose job titles
   - NavTitle appears in TOC, full title appears in topic

2. **Use imperatives, not gerunds**
   - ✓ "Install the operator"
   - ✗ "Installing the operator"
   - Exception: Jobs with ONLY conceptual/reference content use nouns

3. **Remove filler words**
   - Avoid: "About", "Understanding", "Describing", "Introduction", "Explanation"
   - If needed, use: "Overview" (e.g., "Security overview")

4. **Outcome-based, not persona-based**
   - ✓ "Get started with platform administration"
   - ✗ "Get started as a platform administrator"

5. **Natural language over product terminology**
   - Use terms users actually search for
   - Reflect user's desired outcome

6. **Special Cases**
   - Product overview navTitle: "Product overview"
   - Product overview topic title: "What is [Product name]?"
   - Example content: Prefix with "Example:"

### Processing Logic

1. **Read the input** (CSV or content)
2. **Identify the structure** (L1/L2/L3/L4, headings)
3. **For each job title, apply these transformations:**
   - Remove product name if redundant
   - Convert gerunds to imperatives (if procedural content)
   - Trim unnecessary words ("How to", "Guide to", etc.)
   - Preserve user outcome/goal
   - Keep under 5-7 words when possible
   - Ensure consistency with sibling titles

4. **Check consistency:**
   - All siblings at same level use same voice (imperative vs noun)
   - No duplicate nav titles in same section
   - Parent-child relationship is clear

5. **Output results** in the specified format

## Examples from Reference File

| Job Title | Nav Title | Rationale |
|-----------|-----------|-----------|
| "What is OpenShift Builds?" | "Product overview" | Standard pattern for product overview |
| "Install the builds operator" | "Install the operator" | Removed "builds" (redundant in context) |
| "Build an image using a standard Dockerfile" | "Build with a standard Dockerfile" | Shortened while preserving outcome |
| "Create secure containers with automatic language detection" | "Create secure containers automatically" | Trimmed verbose phrase to adverb |
| "Delete old BuildRun resources to optimize performance" | "Delete old BuildRun resources" | Removed "to optimize" (implied outcome) |
| "Understand why builds fail" | "Understand build failures" | Converted to noun form (more concise) |

## Workflow

1. **Parse input structure**
   - Extract hierarchical levels (Category → L2 → L3 → L4 → H1 → H2)
   - Identify job type (procedural vs conceptual)

2. **Generate nav titles row by row**
   - Apply transformation rules
   - Maintain context awareness (parent category, sibling titles)

3. **Validate output**
   - Check for duplicates
   - Verify imperative vs noun consistency within sections
   - Flag potential issues for review

4. **Present results**
   - Show original title alongside nav title
   - Highlight any flagged items
   - Provide reasoning for non-obvious changes

## Usage

When invoked, this skill will:
1. Ask for the input source (file path or paste content)
2. Parse the JTBD structure
3. Generate nav titles following the guidelines
4. Output in the requested 7-column format
5. Provide a summary of transformations made

## Notes
- This skill focuses on nav title generation only
- It does NOT restructure jobs or identify gaps
- It does NOT validate .adoc filenames
- It assumes the JTBD structure is already finalized
