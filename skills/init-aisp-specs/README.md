# init-aisp-specs Skill

Initialize AISP (AI Symbolic Protocol) specification documentation for any codebase.

## What It Does

This skill bootstraps high-quality, low-ambiguity AISP specifications that AI agents can use to understand and coordinate work on your codebase. It creates specifications with symbol density δ≥0.80 (Platinum tier) through automatic optimization.

## Quick Start

In any repository with Claude Code, simply ask:

```
Initialize AISP specs for this repo
```

or

```
Set up AISP documentation
```

## Outputs

The skill creates:

1. **`specs/agents/*.md`** - AISP specification files
   - Language-agnostic, high-density documentation
   - Symbol density δ≥0.80 (Platinum tier)
   - Reduces ambiguity from 40-65% (prose) to <2%

2. **`.aisp-config.json`** - Configuration file
   - Detected patterns and conventions
   - Source paths and spec mappings
   - Used by `update-specs` skill (coming soon)

3. **`CLAUDE.md`** - Updated or created
   - Routing guide for which spec to read
   - Instructions for reading AISP notation
   - Integration with your workflow

## How It Works

The skill follows a 5-phase interactive workflow:

### Phase 1: Repository Discovery
- Scans file types, build files, frameworks
- Identifies source directories, patterns, test structure
- Presents findings and asks what to document

### Phase 2: Determine Structure
- Proposes spec file organization based on your selections
- Common specs: `llm-spec.md`, `test-spec.md`, `error-spec.md`, `workflow-spec.md`
- Gets your approval before proceeding

### Phase 3: Generate Specs
- Creates AISP content for each spec file
- Maximizes symbol density (uses ∀, ∃, λ, ⇒, ≜ extensively)
- Auto-optimizes until δ≥0.80

### Phase 4: Refinement
- Shows generated specs with metrics (δ, coverage, compression)
- Gets your approval (accept/edit/regenerate)
- Iterates until you're satisfied

### Phase 5: Finalize
- Writes all files to `specs/agents/`
- Generates `.aisp-config.json`
- Updates `CLAUDE.md` with routing logic
- Reports summary with metrics

## Example Output

After running, you'll see:

```
✅ AISP Specs Initialized

Created:
  📄 specs/agents/llm-spec.md (δ=0.84, ◊⁺⁺)
  📄 specs/agents/test-spec.md (δ=0.81, ◊⁺⁺)
  📄 .aisp-config.json
  📄 CLAUDE.md (updated)

Coverage: 87% of codebase documented

Next steps:
1. Review specs for accuracy
2. Use update-specs skill to keep them in sync
3. Reference specs when working on features
```

## Files in This Skill

- **`SKILL.md`** - Complete skill instructions for Claude Code (500 lines)
- **`aisp-spec.md`** - Bundled AISP 5.1 Platinum specification
- **`minimal-template.md`** - Bare-bones AISP template
- **`symbol-quick-ref.md`** - Quick reference for common symbols

## Why AISP?

- **Low Ambiguity:** <2% vs 40-65% for natural language
- **High Density:** δ≥0.80 compresses ~500 LOC to ~50 lines
- **AI-Native:** Every AI interprets AISP identically
- **Proof-Carrying:** Self-validating specifications
- **Pipeline-Safe:** 10-agent pipeline: 82% success (vs 0.84% with prose)

## Use Cases

- **Multi-Agent Coordination:** Specs ensure agents understand each other
- **Onboarding:** New AI agents get precise architectural context
- **Documentation:** High-density, low-ambiguity codebase docs
- **API Contracts:** Formal specifications with type guarantees
- **Maintenance:** Keep specs in sync with `update-specs` skill

## AISP Notation Quick Reference

Common symbols you'll see in generated specs:

| Symbol | Meaning | Example |
|:------:|---------|---------|
| `≜` | defined as | `x≜5` |
| `∀` | for all | `∀x∈S:P(x)` |
| `λ` | function | `f≜λx.result` |
| `⇒` | implies | `A⇒B` |
| `⟨⟩` | tuple/record | `User≜⟨id:ℕ,name:𝕊⟩` |
| `⟦⟧` | block | `⟦Λ:Functions⟧{...}` |

The notation is intuitive - most symbols match their mathematical meaning.

## Requirements

- Claude Code v2.0+
- Git repository (recommended)
- Any programming language

## Support

For more about AISP:
- [AISP 5.1 Specification](../../AI_GUIDE.md)
- [Reference Guide](../../reference.md)
- [Evidence & Validation](../../evidence/)

## Coming Soon

- **update-specs** - Keep specs in sync with code changes
- **validate-aisp** - Check spec quality and compliance

---

**AISP 5.1 Platinum** | Created by Bradley Ross | Harvard ALM Digital Media Design 2026
