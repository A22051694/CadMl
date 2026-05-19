# AGENTS.md

Guidelines for AI agents contributing to CADML.

---

# Project Overview

CADML is an experimental declarative CAD language focused on:
- semantic engineering objects
- AI-friendly syntax
- deterministic compilation
- constraint-driven geometry
- human-readable design workflows

The project is intentionally early-stage and architecture-first.

Agents should prioritize:
1. clarity
2. consistency
3. composability
4. deterministic behavior
5. semantic structure over raw geometry operations

---

# Core Philosophy

CADML is NOT:
- another low-level geometry scripting API
- a GUI automation layer
- procedural CAD wrapped in text

CADML IS:
- an intent-oriented engineering language
- schema-driven
- composable
- compiler-oriented
- AI-native

The language should feel closer to:
- HTML
- Compose
- React
- YAML

than traditional CAD scripting systems.

---

# High-Level Goals

Agents should optimize for:

## 1. Semantic Design

Prefer:
```cadml
wall length=4m
```

Over:
```cadml
extrude(line(...))
```

Engineering intent matters more than geometric primitives.

---

## 2. Declarative Syntax

CADML should describe:
- objects
- relationships
- constraints
- manufacturing intent

Avoid imperative/procedural workflows whenever possible.

Bad:
```cadml
create line
move edge
extrude face
rotate object
```

Good:
```cadml
beam {
  width: 40mm
  height: 80mm
}
```

---

## 3. AI-Friendly Structure

AI systems perform best with:
- predictable syntax
- explicit schemas
- shallow ambiguity
- reusable components
- deterministic parsing

When designing syntax/features:
- reduce ambiguity
- minimize hidden state
- avoid magic behavior
- avoid context-sensitive parsing

---

## Architectural Priorities

Priority order:
1. Parser simplicity
2. AST consistency
3. Constraint system
4. Semantic modeling
5. Geometry backend
6. Rendering/UI

UI is NOT the core problem.

---

## Language Design Rules

### Keep Syntax Minimal

Avoid:
- excessive punctuation
- symbolic overload
- deeply nested syntax
- unnecessary keywords

Prefer:
```cadml
plate {
  size: [100mm, 50mm, 5mm]
}
```

Over:
```cadml
create_plate(size=(100mm,50mm,5mm))
```

---

### Prefer Human Readability

The language should be readable by:
- engineers
- designers
- developers
- LLMs

Avoid syntax that only compiler engineers enjoy.

---

### Tolerant Authoring, Strict Compilation

Input may be flexible.

Compilation must be deterministic.

Example:
```cadml
plate 100x50x5
```

may internally normalize into:

```json
{
  "type": "plate",
  "width": 100,
  "height": 50,
  "thickness": 5
}
```

---

## Constraints First

Geometry should emerge from:
- constraints
- dimensions
- relationships
- semantic intent

NOT from manually defined topology.

Preferred:
```cadml
gear {
  teeth: 24
  module: 2
}
```

Avoid requiring users to define every edge/face manually.

---

## Semantic Objects

Prefer high-level engineering concepts:
- wall
- beam
- shaft
- gear
- bolt
- plate
- pipe
- bracket
- joint

Avoid low-level mesh-centric APIs unless necessary internally.

---

## AI Agent Guidelines

### When Generating Code

Agents should:
- keep syntax consistent
- avoid inventing unsupported features
- prefer explicitness over cleverness
- maintain deterministic outputs
- generate schema-valid structures

---

### When Extending Syntax

Before adding syntax:
1. Does it improve semantic clarity?
2. Is it deterministic?
3. Is it AI-friendly?
4. Can it be validated cleanly?
5. Does it compose well?

If not, reconsider.

---

### When Designing Features

Prefer:
- declarative systems
- composable blocks
- explicit constraints
- semantic naming

Avoid:
- hidden side effects
- stateful procedural flows
- GUI assumptions
- implicit geometry mutations

---

## Suggested Internal Pipeline

```
CADML Source
    ↓
Lexer
    ↓
Parser
    ↓
AST
    ↓
Schema Validation
    ↓
Constraint Solver
    ↓
Geometry Kernel
    ↓
Exporters
```

---

## Proposed Tech Direction

These are suggestions, not strict requirements.

### Frontend
- Rust
- Kotlin
- TypeScript

### Geometry
- OpenCascade
- CadQuery backend

### Visualization
- Three.js
- WebGPU

### AI Integration
- JSON schema validation
- AST repair loops
- constrained decoding

---

## Non-Goals

CADML should NOT:
- attempt magic fully autonomous engineering
- replace engineers
- optimize for legacy CAD workflows first
- become another procedural scripting layer

---

## MVP Focus

Current focus:
- syntax experimentation
- parser architecture
- AST design
- semantic object model
- constraint representation

Not currently prioritized:
- polished UI
- enterprise features
- advanced rendering
- plugin ecosystems

---

## Contribution Principles

Good contributions:
- simplify syntax
- improve determinism
- improve semantic clarity
- improve composability
- improve AI interoperability

Bad contributions:
- unnecessary abstraction
- procedural complexity
- syntax bloat
- hidden compiler behavior
- feature creep

---

## Philosophy Summary

CADML treats CAD as:
- structured intent
- semantic relationships
- engineering constraints

not:
- mouse actions serialized into text.

The long-term idea is:
```
Human intent
    ↓
Structured language
    ↓
Constraint system
    ↓
Geometry generation
```

instead of:
```
GUI operations
    ↓
Geometry mutations
```
