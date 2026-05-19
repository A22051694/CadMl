# CADML Software Requirements Specification (SRS)

## 1. Purpose
Define a deterministic, declarative, AI-friendly CAD language that captures engineering intent and compiles into manufacturable geometry outputs.

## 2. Scope
CADML covers:
- language syntax and parsing
- semantic object modeling
- schema validation
- constraint representation
- compilation pipeline to geometry/export backends

## 3. Stakeholders
- CAD engineers
- compiler/language developers
- AI engineers
- manufacturing/domain experts

## 4. Functional Requirements
1. Parse CADML source into a deterministic AST.
2. Validate AST against an explicit schema.
3. Represent semantic objects (e.g., plate, beam, bracket, gear).
4. Represent constraints and relationships.
5. Produce normalized intermediate representation for downstream geometry backends.

## 5. Non-Functional Requirements
- Determinism for same input + version.
- Human-readable and AI-friendly syntax.
- Clear validation errors.
- Composability of language blocks.

## 6. Out of Scope (Current MVP)
- Full enterprise collaboration features
- Polished GUI workflows
- Fully autonomous engineering design

## 7. Initial Deliverables
- parser skeleton
- AST model
- schema draft
- constraint model draft
