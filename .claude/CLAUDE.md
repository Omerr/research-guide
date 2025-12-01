# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This is a book manuscript about managing Research in software companies. The book teaches engineering leaders practical methods for managing Research that creates product impact, based on Alan Schoenfeld's problem-solving framework.

**Key principle**: All work relates to `chapters/` directory. Internal working documentation MUST be written to `.claude/` (not elsewhere).

## Repository Structure

```
chapters/
├── 00 - Introduction/           # Book introduction
├── 01 - Part 1 - Foundations/   # What is Research, Research vs Development
├── 02 - Part 2 - Part 2 - Research Management Methods/  # Research Tree, TTL, etc.
├── 03 - Part 3 - Ensuring Product Impact/               # Choosing initiatives, Drawing backwards, End-to-end
└── 04 - Summary/                # Book conclusion

images/
└── chapter*/                    # Images organized by chapter number

Internal/                        # Author's internal notes (do not modify)
.cursor/                         # Cursor IDE style guide
styles/                          # Vale linting styles
```

## Writing Style Requirements

Content follows Omer Rosenbaum's distinctive writing style (detailed in `.cursor/omer-rosenbaum-style.mdc`):

### Core Voice & Tone
- Conversational but professional - write as if speaking directly to the reader
- Address reader as "you", refer to author as "I" (never "we" or "us")
- Measured enthusiasm for topics (avoid excessive exclamation marks)
- Use first-person singular consistently (avoid first-person plural)

### Language Patterns
- Use contractions naturally ("don't", "isn't", "you'll")
- Use "for example" instead of "e.g."
- Use "and so on" instead of "etc."
- Include rhetorical questions to engage readers
- Use specific phrases: "Let's get to it", "I encourage you to...", "As a reminder...", "Note that...", "By the way..."

### Structure
- Short to medium paragraphs (2-4 sentences)
- Build concepts gradually - foundational ideas before complex applications
- Frame explanations assuming reader curiosity but not expertise
- Emphasize understanding "why" something works, not just "how"
- Use **bold** for key terms when first introduced

### Formatting
- Use numbered lists for sequential processes
- Use bullet points for non-sequential items
- Include explicit references to diagrams ("Consider the drawing above")

### What to Avoid
- Formal academic tone
- Passive voice
- Excessive technical jargon without context
- Long paragraphs without breaks
- First person plural ("we will explore" - use "you will explore" or "I'll show you")
- Too many emoticons or exclamation marks

## Content Structure & Cross-References

### Chapter Numbering
Chapters are numbered sequentially starting from 00 (Introduction), continuing through Parts 1-3 to the Summary.

### Internal References
- Use markdown reference format with anchor IDs: `[chapter 1](#what-is-research)`
- Each chapter has an ID defined in the heading: `## Chapter 1 - What is Research? {#what-is-research}`
- Part headings also have IDs: `# Part 1 - Foundations {#part1-foundations}`

### Images
- Images are organized by chapter number in `images/chapter*/`
- Reference with relative paths: `![Description](images/chapter01/filename.png)`
- Always include descriptive alt text

## Book Content & Concepts

### Core Framework (Schoenfeld's Problem Solving)
The book is built on four components:
1. **Knowledge Base** - What you know
2. **Heuristics** - Strategies for approaching problems
3. **Control** - Monitoring and adjusting your approach
4. **Beliefs and Attitudes** - Mindset toward the problem

### Key Methods Taught
- **Research Tree** - Visual framework for managing solution exploration (implements "Control" component)
- **TTL (Time To Live)** - Time-boxing method for Research execution
- **Drawing Backwards** - Heuristic for working from desired output
- **End-to-End Iteration** - Validating with complete product flows

### Research vs Development Distinction
- **Research**: Problems where you don't know if solutions exist or which approaches will work
- **Development**: Applying known techniques with clear success criteria

## Quality Standards

### Linting
The repository uses Vale for style checking (`.vale.ini`):
- Styles: Vale, Google, proselint, write-good, alex, Readability, ResearchGuide
- MinAlertLevel: error
- Run on all `.md` files in `chapters/`

### Consistency
- Chapter files use `\newpage` separator at the beginning
- Headers follow clear hierarchy
- Examples use real-world scenarios (Swimm, COBOL extraction, medical diagnosis)
- Cross-references maintained when reorganizing content

## Common Operations

### Adding/Editing Chapters
1. Work only in `chapters/` directory
2. Follow existing naming convention: `##-chapter-name.md`
3. Include chapter ID in heading for cross-referencing
4. Add corresponding images to `images/chapter##/`
5. Maintain consistent voice and style per `.cursor/omer-rosenbaum-style.mdc`

### Working with Images
- Create chapter-specific subdirectories in `images/`
- Use descriptive filenames (e.g., `research_tree_complete.png`)
- Always reference with relative paths from chapter files
- Include meaningful alt text

### Reorganizing Content
- Update all cross-references when moving content
- Maintain chapter ID anchors
- Update image paths if moving chapters
- Check Internal/toc.md for overall structure guidance

## Important Notes

- The manuscript is work-in-progress - some chapters may be incomplete
- Author's notes in `notes_to_self.md` and `Internal/` should not be modified
- Current git branch structure may include work-in-progress rewrites
- Focus on practical, actionable content over academic theory (per "practicality principle")
