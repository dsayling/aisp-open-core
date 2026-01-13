# Minimal AISP Template

This is a bare-bones AISP 5.1 specification template with placeholders.

```aisp
𝔸5.1.name@YYYY-MM-DD
γ≔domain.context
ρ≔⟨tags⟩
⊢claims

⟦Ω:Overview⟧{
  ;; Core invariants and principles
  ;; Example: ∀x∈Domain:Property(x)
}

⟦Σ:Types⟧{
  ;; Domain types and models
  ;; Example: Type≜definition
  ;; Example: Model≜⟨field:Type,field:Type⟩
}

⟦Γ:Rules⟧{
  ;; Constraints and patterns
  ;; Example: ∀x:Condition(x)⇒Consequence(x)
  ;; Example: Pattern≜structure
}

⟦Λ:Functions⟧{
  ;; Core functions and operations
  ;; Example: func≜λx.result
  ;; Example: operation:Input→Output
}

⟦Ε⟧⟨
  δ≜0.00
  |𝔅|≜0/5
  φ≜0
  τ≜⊘
⟩
```

## Block Descriptions

- **𝔸**: Header with version, name, date
- **γ**: Context/domain identifier
- **ρ**: Tags/keywords
- **⊢**: Claims/assertions
- **⟦Ω⟧**: Meta-level invariants and principles
- **⟦Σ⟧**: Type definitions and domain models
- **⟦Γ⟧**: Rules, constraints, and patterns
- **⟦Λ⟧**: Functions and operations
- **⟦Ε⟧**: Evidence block with metrics
  - δ: Symbol density (aim for ≥0.80)
  - |𝔅|: Block completeness (present/total)
  - φ: Completeness percentage
  - τ: Quality tier (◊⁺⁺, ◊⁺, ◊, ◊⁻, ⊘)
