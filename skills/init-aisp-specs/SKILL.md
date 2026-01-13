---
name: init-aisp-specs
description: Initialize AISP specification documentation for a codebase. Use when user wants to bootstrap AISP docs from scratch. Creates high-density (δ≥0.80) specs in specs/agents/ with auto-optimization. Executes autonomously with minimal user interaction.
---

# AISP Specification Initialization Skill

## Overview

This skill bootstraps AISP (AI Symbolic Protocol) documentation for any codebase, creating high-quality, low-ambiguity specifications that AI agents can use for understanding and coordinating work.

**What it does:**
- Analyzes repository structure and patterns (silent)
- Automatically determines which specs to create
- Generates AISP specifications (δ≥0.80)
- Creates `specs/agents/` directory with spec files
- Generates `.aisp-config.json` for the `update-specs` skill
- Updates `CLAUDE.md` with routing logic
- Reports concise summary at the end

**When to use:**
- User explicitly asks to "initialize AISP specs" or similar
- Starting a new project that will use AISP
- Converting existing requirements to AISP format

**Execution style:**
- **Autonomous:** Minimal questions, maximum action
- **Concise:** Brief progress updates only
- **Smart defaults:** Auto-detect languages, patterns, and structure

**Outputs:**
- `specs/agents/*.md` - AISP specification files
- `.aisp-config.json` - Configuration for update-specs
- `CLAUDE.md` - Updated with AISP routing guidance

**Goal:** Achieve symbol density δ≥0.80 through auto-optimization.

## Workflow: 3 Autonomous Phases

Execute these phases sequentially without user interaction. Be concise and move quickly.

### Phase 1: Repository Discovery (Silent)

**Objective:** Understand the codebase structure and identify documentable patterns.

**Scan quickly:**
- Identify primary languages (check file extensions: `.py`, `.js`, `.ts`, `.go`, `.rs`, etc.)
- Find build files (`package.json`, `pyproject.toml`, `go.mod`, `Cargo.toml`, `Makefile`)
- Detect framework indicators (imports, dependencies, config files)
- Identify source directories (common: `src/`, `lib/`, `app/`, root-level modules)
- Find test directories (`tests/`, `test/`, `__tests__/`, `*_test.go`, `*.test.js`)
- Analyze architecture patterns (MVC, functional, OOP, factory, repository, etc.)
- Identify core components (entry points, APIs, models, config, errors, tests)

**Decision logic for spec structure (automatic):**
- Always create `llm-spec.md` (core APIs, functions, models, patterns)
- If `tests/` or similar exists with test fixtures → add `test-spec.md`
- If dedicated error/exception classes exist → add `error-spec.md`
- If build/deploy files with complex workflows → add `workflow-spec.md`

### Phase 2: Generate All Specs (Silent)

**Objective:** Create AISP content for each spec file with δ≥0.80.

**For each spec file:**

1. **Start with minimal template** (see `minimal-template.md`)

2. **Fill each block based on codebase analysis:**
   - **⟦Ω:Overview⟧** - Meta-level invariants, core principles, design patterns
   - **⟦Σ:Types⟧** - Domain types, data models, type definitions
   - **⟦Γ:Rules⟧** - Constraints, validation rules, patterns, conventions
   - **⟦Λ:Functions⟧** - Operations grouped by logical sections (e.g., `⟦Λ:Users⟧`, `⟦Λ:Auth⟧`)
   - **⟦Ε⟧** - Evidence metrics (calculate after generation)

3. **Maximize symbol density:**
   - Replace prose with AISP symbols
   - Use ∀, ∃, λ, ⇒, ≜ extensively
   - One-line definitions where possible
   - Reference patterns instead of repeating
   - Use compound symbols (Δ⊗λ, Γ𝒫, etc.)

4. **Calculate δ (symbol density):**
   ```
   δ ≜ (count of AISP symbols) ÷ (total non-whitespace tokens)
   ```
   - Count symbols from Σ_512 glossary
   - Target: δ ≥ 0.80
   - If δ < 0.80, apply optimization strategies automatically

5. **Validate structure:**
   - All required blocks present: ⟦Ω⟧, ⟦Σ⟧, ⟦Γ⟧, ⟦Λ⟧, ⟦Ε⟧
   - Proper AISP grammar
   - Evidence block has correct metrics

### Phase 3: Finalize and Create Supporting Files (Report Results)

**Objective:** Write all files and create integration points. Report results concisely.

**Steps:**

1. **Create directory if needed:**
   ```bash
   mkdir -p specs/agents
   ```

2. **Write all spec files to `specs/agents/`**

3. **Generate `.aisp-config.json`:**
   ```json
   {
     "source_paths": ["src/", "lib/"],
     "exclude_patterns": ["*.test.js", "node_modules/", "*.pyc"],
     "spec_files": [
       {
         "path": "specs/agents/llm-spec.md",
         "patterns": {
           "functions": "[detected pattern, e.g., 'list_*', 'get_*', 'create_*']",
           "classes": "[detected pattern]",
           "modules": "[detected pattern]"
         }
       }
     ],
     "density_target": 0.80,
   }
   ```

4. **Create or update `CLAUDE.md` with routing guidance**

5. **Report results concisely:**
   ```
   ✅ AISP specs initialized

   Created:
   • specs/agents/llm-spec.md (δ=0.84, ◊⁺⁺, 47 lines)
   • specs/agents/test-spec.md (δ=0.82, ◊⁺⁺, 32 lines)
   • .aisp-config.json
   • CLAUDE.md (updated)

   Coverage: [N] functions, [M] types, [K] patterns documented
   ```

---

## CRITICAL INSTRUCTIONS

**Execution Mode:**
- **Phases 1-2**: Execute silently, no questions, no approval needed
- **Phase 3**: Report results only at the end
- **Be concise**: Minimize commentary, maximize action
- **Auto-optimize**: If δ < 0.80, apply strategies automatically
- **No verbosity**: Don't show full spec content unless explicitly asked
- **No approval loops**: Generate → write → report

**Default behavior:**
1. Scan repo structure
2. Decide spec files automatically (always include llm-spec.md)
3. Generate all specs with δ≥0.80
4. Write files
5. Report concise summary

Only ask questions if you encounter genuinely ambiguous situations that would significantly impact the output.

---

## Quality Validation Checks

Before finalizing any spec, verify:

1. **Density:** δ ≥ 0.80
2. **Completeness:** All required blocks present
   - ⟦Ω:Overview⟧
   - ⟦Σ:Types⟧
   - ⟦Γ:Rules⟧
   - ⟦Λ:Functions⟧
   - ⟦Ε⟧ (Evidence)
3. **Grammar:** Valid AISP structure
4. **Evidence Block:** Contains correct metrics
   - δ (density)
   - |𝔅| (block count)
   - φ (completeness percentage)
   - τ (tier: ◊⁺⁺, ◊⁺, ◊, ◊⁻, ⊘)
5. **Ambiguity:** Should be minimal (<2%)

If any check fails, regenerate or optimize.

## Reference Files

This skill includes bundled reference files:

- **`aisp-spec.md`** - Complete AISP specification (bundled copy of AI_GUIDE.md). Use this to understand AISP notation, symbols, and structure.

- **`minimal-template.md`** - Bare-bones AISP template to start from.

- **`symbol-quick-ref.md`** - Quick reference for most common AISP symbols.

Load these files as needed during generation.

## Important Guidelines

1. **Language-Agnostic:** Don't hardcode language-specific patterns. Detect patterns from the actual codebase.

2. **Auto-Optimize:** Never accept specs with δ<0.80. Always iterate to reach δ>0.80

3. **Interactive:** Get user approval at key decision points (aspects to document, spec structure, final specs).

4. **Metrics:** Always calculate and show δ, coverage %, compression ratio.

5. **Minimal:** Keep specs concise. Use AISP's density to compress maximum information into minimum space.

6. **Valid AISP:** Always follow AISP grammar and structure.

7. **Self-Contained:** All specs should be understandable without external context.

## Success Criteria

A successful initialization must:
- ✅ Generate specs with δ ≥ 0.80
- ✅ Create valid AISP structure
- ✅ Place files in `specs/agents/`
- ✅ Generate `.aisp-config.json`
- ✅ Update `CLAUDE.md`
- ✅ Provide clear metrics and next steps

## Notes

- This skill creates the initial specs. Use the `update-specs` skill (coming soon) to maintain them as code evolves.
- AISP reduces ambiguity from 40-65% (prose) to <2%.
- Symbol density δ≥0.80.
- All specs are proof-carrying and self-validating.
