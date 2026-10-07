# elics

"Explain Like I'm a College Student"

I wrote this skill to help me learn things as I'm doing them. Often times, it's helpful for me to learn the abstract concept and then the technical details, when trying to understand something.

This skill does just that.

The skill is more pointd towards technical programming concepts, but does work-ish with things in general.

Each answer has four parts:

1. **Analogy**: a concrete comparison from familiar machinery.
2. **Mechanism**: the real thing, in the field's own vocabulary.
3. **Seam**: where the analogy stops being true.
4. **Flagged simplification**: anything compressed that you'd otherwise have to unlearn.

Answers run 200–400 words and spend most of them on the step that makes the concept work. When the concept appears in your current repo, the answer points at the file and line.

## Install

Clone into your personal skills directory:

```sh
git clone <repo-url> ~/.claude/skills/elics
```

Or, for a single project, clone into `.claude/skills/elics` at that project's root.

## Usage

```
/elics what's a bloom filter
```

The skill sets `disable-model-invocation: true`, so Claude only runs it when you call `/elics` yourself.

## Files

- `SKILL.md`: the skill definition and instructions.
