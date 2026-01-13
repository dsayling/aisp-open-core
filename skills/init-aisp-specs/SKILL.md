---
name: init-aisp-specs
description: Initialize AISP specification documentation for a codebase. Use when user wants to bootstrap AISP docs from scratch. Creates high-density (δ≥0.80) specs in specs/agents/ with auto-optimization.
---

# AISP Specification Initialization Skill

## Overview

This skill bootstraps AISP (AI Symbolic Protocol) documentation for any codebase, creating high-quality, low-ambiguity specifications that AI agents can use for understanding and coordinating work.

**What it does:**
- Analyzes repository structure and patterns
- Generates AISP 5.1 Platinum specifications (δ≥0.80)
- Creates `specs/agents/` directory with spec files
- Generates `.aisp-config.json` for the `update-specs` skill
- Updates `CLAUDE.md` with routing logic

**When to use:**
- User explicitly asks to "initialize AISP specs" or similar
- Starting a new project that will use AISP
- Converting existing requirements to AISP format

**Outputs:**
- `specs/agents/*.md` - AISP specification files
- `.aisp-config.json` - Configuration for update-specs
- `CLAUDE.md` - Updated with AISP routing guidance

**Goal:** Achieve Platinum tier (δ≥0.80) through auto-optimization.

## Workflow: 5 Interactive Phases

Follow these phases sequentially. Be interactive and get user approval at key decision points.

### Phase 1: Repository Discovery

**Objective:** Understand the codebase structure and identify documentable patterns.

**Steps:**

1. **Scan the repository:**
   - Identify primary languages (check file extensions: `.py`, `.js`, `.ts`, `.go`, `.rs`, etc.)
   - Find build files (`package.json`, `pyproject.toml`, `go.mod`, `Cargo.toml`, `Makefile`)
   - Detect framework indicators (imports, dependencies, config files)
   - Identify source directories (common: `src/`, `lib/`, `app/`, root-level modules)
   - Find test directories (`tests/`, `test/`, `__tests__/`, `*_test.go`, `*.test.js`)

2. **Analyze architecture patterns:**
   - Code organization (monolith, modules, microservices)
   - Design patterns (MVC, functional, OOP, factory, repository, etc.)
   - API structure (REST, GraphQL, gRPC, CLI, library)
   - Notable conventions (naming, file structure)

3. **Identify core components:**
   - Main entry points (main.py, index.js, main.go, lib.rs)
   - Public APIs or exported interfaces
   - Key abstractions or domain models
   - Configuration mechanisms
   - Error handling approaches
   - Testing infrastructure (fixtures, helpers, utilities)

4. **Present findings:**
   ```
   📊 Repository Analysis:

   Language: [Primary language]
   Type: [SDK/API/CLI/Web App/Library/Service]
   Framework: [Detected frameworks]
   Pattern: [Architecture pattern]

   Structure:
     • [source directory] - [description] ([N] files)
     • [test directory] - [description]
     • [config files]

   Key patterns identified:
     ✓ [Pattern 1]
     ✓ [Pattern 2]
     ✓ [Pattern 3]
   ```

5. **Ask user:** "What aspects of this codebase should we document?"
   - Present detected aspects as options
   - Common options: API/Functions, Data Models, Testing, Error Handling, Workflows, Configuration

### Phase 2: Determine Spec Structure

**Objective:** Decide which spec files to create and what each will contain.

**Steps:**

1. **Based on user selections, propose spec files:**
   - `llm-spec.md` - Architecture, APIs, functions, models (most common)
   - `test-spec.md` - Test patterns, fixtures, utilities
   - `error-spec.md` - Exception hierarchy, error handling
   - `workflow-spec.md` - Build/deploy/git workflows, commands
   - `component-spec.md` - UI components (for frontend)
   - Custom names based on domain

2. **Present proposed structure:**
   ```
   📁 Proposed spec structure:

   specs/agents/
     ├── llm-spec.md       - [What it covers]
     ├── test-spec.md      - [What it covers]
     └── workflow-spec.md  - [What it covers]
   ```

3. **Ask for approval:** "Proceed with this structure? [y/n/e (edit)]"
   - If edit: Ask which files to add/remove/rename

### Phase 3: Generate Initial Specs

**Objective:** Create AISP content for each spec file with δ≥0.80.

**For each spec file:**

1. **Start with minimal template** (see `minimal-template.md`)

2. **Fill each block based on codebase analysis:**

   **⟦Ω:Overview⟧** - Meta-level invariants
   - Core principles (e.g., `∀call:context_managed`)
   - Design patterns (e.g., `Pattern≜factory`)
   - System invariants (e.g., `∀req:authenticated`)

   **⟦Σ:Types⟧** - Domain types
   - Data models (e.g., `User≜⟨id:ℕ,name:𝕊⟩`)
   - Type definitions (e.g., `Response≜{data:T}|{error:E}`)
   - Domain concepts (e.g., `Request≜HTTP∧headers∧body`)

   **⟦Γ:Rules⟧** - Constraints and patterns
   - Validation rules (e.g., `∀u:User:len(u.name)>0`)
   - Patterns (e.g., `REST≜{GET:list/get,POST:create}`)
   - Conventions (e.g., `URL≜f"{base}/{version}/{resource}"`)

   **⟦Λ:Functions⟧** - Operations
   - Functions (e.g., `get_user≜λid.GET(f"users/{id}")→User`)
   - Group by logical sections (e.g., `⟦Λ:Users⟧`, `⟦Λ:Auth⟧`)
   - Show signatures, patterns, behavior

   **⟦Ε⟧** - Evidence metrics (calculate after generation)

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
   - Count symbols from Σ_512 glossary (see aisp-spec.md)
   - Target: δ ≥ 0.80 (Platinum tier)

5. **If δ < 0.80, optimize:**
   Apply density optimization strategies (see section below)

6. **Validate structure:**
   - All required blocks present: ⟦Ω⟧, ⟦Σ⟧, ⟦Γ⟧, ⟦Λ⟧, ⟦Ε⟧
   - Proper AISP grammar
   - Evidence block has correct metrics

### Phase 4: Interactive Refinement

**Objective:** Get user approval for each generated spec.

**For each spec file:**

1. **Present the generated spec with metrics:**
   ```
   ─────────────────────────────────────
   📝 Generated: llm-spec.md
   ─────────────────────────────────────

   [Show the AISP content]

   ─────────────────────────────────────
   Metrics:
     • Symbol density: 0.84 (◊⁺⁺ Platinum)
     • Completeness: 95% (covered/total)
     • Lines: 47
     • Compression: ~500 LOC → 47 lines (~11x)

   This spec covers:
     ✓ [Aspect 1]
     ✓ [Aspect 2]
     ✓ [Aspect 3]

   Accept this spec? [y/n/e (edit)/r (regenerate)]
   ```

2. **Handle user response:**
   - **y (yes)**: Move to next spec
   - **n (no)**: Skip this spec
   - **e (edit)**: Ask what to change, then regenerate
   - **r (regenerate)**: Generate again with different approach

3. **Iterate until user accepts or skips**

### Phase 5: Finalize and Create Supporting Files

**Objective:** Write all files and create integration points.

**Steps:**

1. **Create directory if needed:**
   ```bash
   mkdir -p specs/agents
   ```

2. **Write all accepted spec files to `specs/agents/`**

3. **Generate `.aisp-config.json`:**
   ```json
   {
     "version": "5.1",
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
     "quality_tier": "platinum"
   }
   ```

4. **Create or update `CLAUDE.md`:**

   If `CLAUDE.md` doesn't exist, create it:
   ```markdown
   # Repository Guide for Claude Code

   ## AISP Specifications

   This repository uses AISP specs in `specs/agents/` for high-density,
   low-ambiguity architectural context.

   **Routing Guide - When to read which spec:**
   - Adding features/APIs → specs/agents/llm-spec.md
   - Writing tests → specs/agents/test-spec.md
   - Debugging errors → specs/agents/error-spec.md
   - Understanding workflows → specs/agents/workflow-spec.md

   **Reading AISP:** The notation is intuitive:
   - ∀ = "for all"
   - λ = "function"
   - ⇒ = "implies"
   - ≜ = "is defined as"

   Just read relevant sections directly. See specs/agents/*.md for details.

   **Updating specs:** Use the `update-specs` skill to keep them synchronized
   with code changes.

   ## About AISP

   AISP (AI Symbolic Protocol) reduces ambiguity from 40-65% (prose) to <2%.
   Specs are proof-carrying and self-validating with symbol density δ≥0.80.

   For more: https://github.com/bar181/aisp-open-core
   ```

   If `CLAUDE.md` exists, add AISP section or update existing one.

5. **Report summary:**
   ```
   ✅ AISP Specs Initialized

   Created:
     📄 specs/agents/llm-spec.md (δ=0.84, ◊⁺⁺)
     📄 specs/agents/test-spec.md (δ=0.81, ◊⁺⁺)
     📄 .aisp-config.json
     📄 CLAUDE.md (updated)

   Coverage: [X]% of codebase documented

   Next steps:
   1. Review specs for accuracy
   2. Use update-specs skill to keep them in sync as code evolves
   3. Reference specs when working on features

   Files written to specs/agents/. Ready to commit!
   ```

## Density Optimization Strategies

If generated spec has δ < 0.80, apply these strategies:

### Strategy 1: Replace Prose with Symbols
**Before:**
```
For all users in the system, the email must be valid
```
**After:**
```aisp
∀u∈Users:valid(u.email)
```

### Strategy 2: Use One-Line Definitions
**Before:**
```
The function get_user takes a user ID as input.
It returns a User object.
```
**After:**
```aisp
get_user≜λid.User
```

### Strategy 3: Group Efficiently
**Before:**
```
list_users: Get all users
get_user: Get one user by ID
create_user: Create a new user
```
**After:**
```aisp
⟦Λ:Users⟧{
  list_users≜λp.GET("users",p)→{data:User[]}
  get_user≜λid.GET(f"users/{id}")→User
  create_user≜λd.POST("users",d)→User
  ⊢CRUD∧typed
}
```

### Strategy 4: Reference Patterns
**Before:**
```
list_users follows REST pattern
get_user follows REST pattern
create_user follows REST pattern
```
**After:**
```aisp
⟦Γ:Patterns⟧{
  REST≜{GET:list/get,POST:create,PATCH:update,DELETE:delete}
}

⟦Λ:Users⟧{
  ;; All follow REST pattern (see ⟦Γ⟧)
  list_users≜λp.GET("users",p)
  get_user≜λid.GET(f"users/{id}")
  create_user≜λd.POST("users",d)
}
```

### Strategy 5: Use Compound Symbols
**Before:**
```
The binding state can be crash, null, adapt, or zero-cost
```
**After:**
```aisp
Δ⊗λ∈{⊥:crash,∅:null,λ:adapt,⊤:zero}
```

### Density Calculation Formula
```aisp
δ ≜ λτ⃗.|{t∈τ⃗|t.k∈𝔄}| ÷ |{t∈τ⃗|t.k≢ws}|

Where:
  τ⃗ = token stream
  𝔄 = AISP symbols (from Σ_512)
  ws = whitespace
```

Iterate until δ≥0.80.

## Quality Validation Checks

Before finalizing any spec, verify:

1. **Density:** δ ≥ 0.80 (Platinum tier)
2. **Completeness:** All required blocks present
   - ⟦Ω:Overview⟧
   - ⟦Σ:Types⟧
   - ⟦Γ:Rules⟧
   - ⟦Λ:Functions⟧
   - ⟦Ε⟧ (Evidence)
3. **Grammar:** Valid AISP 5.1 structure
4. **Evidence Block:** Contains correct metrics
   - δ (density)
   - |𝔅| (block count)
   - φ (completeness percentage)
   - τ (tier: ◊⁺⁺, ◊⁺, ◊, ◊⁻, ⊘)
5. **Ambiguity:** Should be minimal (<2%)

If any check fails, regenerate or optimize.

## Examples

### Example 1: Function Definition
**Prose:** "The get_user function takes a user ID and returns a User object"

**AISP:**
```aisp
get_user≜λid.User
```

### Example 2: Universal Quantifier
**Prose:** "All users must have a valid email address"

**AISP:**
```aisp
∀u∈Users:valid(u.email)
```

### Example 3: Implication
**Prose:** "If a user is authenticated, then they can access protected resources"

**AISP:**
```aisp
authenticated(u)⇒access(u,protected)
```

### Example 4: Type Definition
**Prose:** "A User is an object with an ID, name, and email"

**AISP:**
```aisp
User≜⟨id:ℕ,name:𝕊,email:𝕊⟩
```

### Example 5: Pattern Group
**Python SDK Example:**
```aisp
⟦Λ:Endpoints⟧{
  ;; Records
  list_records≜λp.GET("records",p)→{data:Record[]}
  get_record≜λid.GET(f"records/{id}")→Record

  ;; Users
  list_users≜λp.GET("users",p)→{data:User[]}
  get_user≜λid.GET(f"users/{id}")→User

  ⊢CRUD∧typed∧paginated
}
```

## Reference Files

This skill includes bundled reference files:

- **`aisp-spec.md`** - Complete AISP 5.1 Platinum specification (bundled copy of AI_GUIDE.md). Use this to understand AISP notation, symbols, and structure.

- **`minimal-template.md`** - Bare-bones AISP template to start from.

- **`symbol-quick-ref.md`** - Quick reference for most common AISP symbols.

Load these files as needed during generation.

## Important Guidelines

1. **Language-Agnostic:** Don't hardcode language-specific patterns. Detect patterns from the actual codebase.

2. **Auto-Optimize:** Never accept specs with δ<0.80. Always iterate to reach Platinum tier.

3. **Interactive:** Get user approval at key decision points (aspects to document, spec structure, final specs).

4. **Metrics:** Always calculate and show δ, coverage %, compression ratio.

5. **Minimal:** Keep specs concise. Use AISP's density to compress maximum information into minimum space.

6. **Valid AISP:** Always follow AISP 5.1 grammar and structure.

7. **Self-Contained:** All specs should be understandable without external context.

## Success Criteria

A successful initialization must:
- ✅ Generate specs with δ ≥ 0.80
- ✅ Create valid AISP 5.1 structure
- ✅ Place files in `specs/agents/`
- ✅ Generate `.aisp-config.json`
- ✅ Update `CLAUDE.md`
- ✅ Get user approval for structure and content
- ✅ Provide clear metrics and next steps

## Notes

- This skill creates the initial specs. Use the `update-specs` skill (coming soon) to maintain them as code evolves.
- AISP reduces ambiguity from 40-65% (prose) to <2%.
- Symbol density δ≥0.80 is the Platinum tier standard.
- All specs are proof-carrying and self-validating.

---

**AISP 5.1 Platinum** | Created by Bradley Ross | Harvard ALM Digital Media Design 2026
