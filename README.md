# JTBD Navigation Title Generator

A Claude Code skill for generating navigation titles following Red Hat JTBD consistency guidelines.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## Overview

This skill automates the creation of concise, user-friendly navigation titles from verbose JTBD (Jobs-to-be-Done) job titles, following Red Hat's documentation consistency guidelines.

## Installation

1. Copy `jtbd-navtitle-generator.md` to your Claude skills directory:
   ```bash
   cp jtbd-navtitle-generator.md ~/.claude/skills/
   ```

2. Verify installation:
   ```bash
   ls ~/.claude/skills/jtbd-navtitle-generator.md
   ```

3. Use the skill in Claude Code:
   ```
   /jtbd-navtitle-generator
   ```

## Usage

The skill can process:
- CSV files with JTBD structure (like the Builds example)
- Pasted JTBD content
- Individual job titles

### Input Format
Provide JTBD structure with these columns:
- L1 (Category)
- L2 (Job title)
- L3 (Sub-job)
- L4 (Topic)
- H1/H2 (Headings)

### Output Format
For each job:
1. L1 Category
2. L2 Job Title
3. L3 Job Title
4. L4 Job Title
5. H1 Heading
6. H2 Heading
7. **Nav Title** (generated)

## Example

**Input:** "Install the OpenShift Builds operator"
**Output Nav Title:** "Install the operator"

**Rationale:** Removed "OpenShift Builds" (redundant in product context)

## Guidelines Applied

- Shorter navigation titles (product name removed when redundant)
- Imperatives, not gerunds ("Install" not "Installing")
- Outcome-based language
- Removal of filler words (About, Understanding, etc.)
- Consistency with Red Hat JTBD taxonomy

## Reference

Based on Red Hat JTBD consistency guidelines.

Based on Red Hat's JTBD consistency guidelines and OpenShift Builds documentation example.
