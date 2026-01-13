# AISP Symbol Quick Reference

## Most Common Symbols

### Logic & Proof
| Symbol | Meaning | Example |
|:------:|---------|---------|
| `≜` | defined as | `x≜5` |
| `≔` | assigned to | `y≔x+1` |
| `≡` | identical | `a≡b` |
| `⇒` | implies | `A⇒B` |
| `⊢` | proves | `Γ⊢P` |
| `∎` | QED (proof complete) | `π:...∎` |

### Quantifiers
| Symbol | Meaning | Example |
|:------:|---------|---------|
| `∀` | for all | `∀x:P(x)` |
| `∃` | exists | `∃x:P(x)` |
| `∃!` | unique exists | `∃!x:f(x)=0` |
| `λ` | lambda (function) | `λx.x+1` |

### Sets & Relations
| Symbol | Meaning | Example |
|:------:|---------|---------|
| `∈` | element of | `x∈S` |
| `⊆` | subset | `A⊆B` |
| `∩` | intersection | `A∩B` |
| `∪` | union | `A∪B` |
| `∅` | empty/null | `S≡∅` |

### Operators
| Symbol | Meaning | Example |
|:------:|---------|---------|
| `⊕` | plus/sum | `A⊕B` |
| `⊖` | minus/difference | `ψ_*⊖ψ_have` |
| `⊗` | tensor/product | `Δ⊗λ` |
| `→` | function type | `f:A→B` |
| `↦` | maps to | `x↦y` |

### Structure
| Symbol | Meaning | Example |
|:------:|---------|---------|
| `⟨⟩` | tuple/record | `⟨a:A,b:B⟩` |
| `⟦⟧` | block delimiter | `⟦Σ:Types⟧{...}` |
| `◊` | quality tier | `◊⁺⁺` (platinum) |
| `𝔸` | AISP header | `𝔸5.1.name@date` |

## Quality Tiers
| Symbol | Name | Threshold | Use |
|:------:|------|:---------:|-----|
| `◊⁺⁺` | Platinum | δ≥0.75 | Production |
| `◊⁺` | Gold | δ≥0.60 | Staging |
| `◊` | Silver | δ≥0.40 | Development |
| `◊⁻` | Bronze | δ≥0.20 | Review |
| `⊘` | Reject | δ<0.20 | Rejected |

## Common Patterns

**Function definition:**
```aisp
f≜λx.result
```

**Universal quantifier:**
```aisp
∀x∈S:P(x)
```

**Implication:**
```aisp
condition⇒consequence
```

**Type definition:**
```aisp
Type≜definition
```

**Record type:**
```aisp
Model≜⟨field₁:T₁,field₂:T₂⟩
```

For complete symbol reference, see `aisp-spec.md`.
