# CadMl
A new way to design things using structured language instead of complex CAD workflows.
# CADML

Declarative, AI-native CAD language for engineering design.

CADML is an experimental attempt to build a modern CAD description language optimized for:
- AI generation
- deterministic compilation
- semantic engineering objects
- parametric design
- manufacturable geometry
- human-readable syntax

Instead of manually drawing geometry through mouse-heavy CAD workflows, CADML focuses on describing *engineering intent*.

---

# Vision

Modern CAD software was designed for humans clicking buttons.

LLMs are bad at:
- GUI interaction
- procedural CAD APIs
- topology-level geometry editing

But LLMs are good at:
- structured text
- semantic hierarchies
- declarative systems
- schema-driven generation

CADML bridges this gap.

---

# Core Philosophy

CADML is inspired by:
- HTML
- Jetpack Compose
- React
- OpenSCAD
- BIM systems
- declarative UI frameworks
- schema-first architectures

The goal is not:
> "Programming language for geometry"

The goal is:
> "Intent language for engineering"

---

# Example

```cadml
assembly MotorMount {

  material: Steel.A36

  plate Base {
      size: [200mm, 120mm, 8mm]

      holes: Grid(
          rows=2,
          cols=2,
          dia=10mm,
          spacing=40mm
      )
  }

  bracket Support {
      attach: Base.top
      angle: 90deg
      thickness: 6mm
  }

  constraints {
      manufacturable: cnc
      tolerance: medium
      symmetry: true
  }
}
```

---

Design Goals

1. AI-Friendly

CADML should be:

deterministic

schema-validatable

composable

semantically meaningful

tolerant during authoring

strict during compilation



---

2. Declarative

Users describe:

objects

relationships

constraints

manufacturing intent


NOT low-level geometry operations.

Bad:

extrude(line(...))

Good:

beam width=40mm height=80mm


---

3. Semantic Engineering Objects

CADML prefers:

wall

beam

plate

shaft

bolt

gear

pipe

bracket


instead of raw vertices and faces.


---

4. Constraint-Driven

Geometry should emerge from:

dimensions

relationships

constraints

engineering rules


Example:

gear {
  teeth: 24
  module: 2
}

The compiler computes actual geometry.


---

5. Compiler-Based

CADML source should compile into:

STEP

STL

DWG

DXF

SVG

IFC


Potential pipeline:

CADML
  ↓
AST
  ↓
Constraint Solver
  ↓
Geometry Kernel
  ↓
Export Pipeline


---

Proposed Architecture

Frontend

Parser

PEG parser

AST generation

schema validation


Language Features

indentation-based blocks

minimal punctuation

reusable components

imports/modules

constraint expressions



---

Core Engine

Constraint Solver

Responsible for:

dimensions

alignments

relationships

dependencies


Geometry Kernel

Potential backends:

OpenCascade

CGAL

Parasolid (future)



---

AI Layer

CADML is designed for structured LLM generation.

Recommended workflow:

Prompt
  ↓
Structured AST generation
  ↓
Schema validation
  ↓
Repair loop
  ↓
Compilation

Avoid freeform geometry generation.


---

Syntax Philosophy

CADML should feel:

readable like YAML

composable like Compose

strict like SQL schemas

flexible like HTML authoring


Example:

room Bedroom {
  size: [4m, 5m]
  wallHeight: 3m

  window {
    width: 1.5m
    position: north
  }
}


---

Why Existing CAD Is Difficult For AI

Traditional CAD systems are:

procedural

GUI-heavy

topology-centric

legacy-oriented

difficult to diff/version-control


AI struggles with:

mouse actions

procedural geometry APIs

hidden constraints

implicit relationships


CADML externalizes intent into text.


---

Potential Features

Parametric Design

param width = 120mm

plate {
  width: width
  height: width * 2
}


---

Reusable Components

component BoltPattern {
  count: 4
  spacing: 40mm
}


---

Material System

material: Steel.A36
finish: anodized


---

Manufacturing Rules

constraints {
  manufacturable: injection_molding
  minWallThickness: 2mm
}


---

Long-Term Goals

AI-native CAD workflows

Git-friendly engineering

deterministic geometry compilation

open engineering schemas

browser-based CAD

collaborative engineering

simulation-aware design

manufacturability validation



---

Non-Goals

CADML is NOT intended to:

replace all CAD tools immediately

generate magic perfect engineering automatically

remove engineers from engineering workflows


Human validation remains critical.


---

MVP Roadmap

Phase 1

parser

AST

basic primitives

STL export


Phase 2

parametric constraints

OpenCascade backend

browser renderer


Phase 3

semantic engineering objects

manufacturing constraints

AI repair loops


Phase 4

STEP/DWG export

collaboration

simulation integration



---

Tech Stack Ideas

Language

Rust

Kotlin

TypeScript


Geometry

OpenCascade

CadQuery backend


Rendering

Three.js

WebGPU


AI Integration

JSON schema validation

constrained decoding

AST repair system



---

Example Future Workflow

User Prompt
    ↓
LLM generates CADML
    ↓
Validator checks schema
    ↓
Compiler resolves constraints
    ↓
Geometry engine builds solids
    ↓
Exports STEP/STL/DWG


---

Repository Status

Early concept stage.

Researching:

syntax design

compiler architecture

semantic geometry

AI-assisted engineering workflows



---

License

MIT


---

Contributing

Open to:

CAD engineers

geometry programmers

compiler developers

AI engineers

manufacturing experts

UI/UX contributors



---

Inspiration

Projects and ideas that influenced CADML:

OpenSCAD

CadQuery

FreeCAD

IFC/BIM systems

Jetpack Compose

React

HTML/CSS

parametric CAD systems



---

Final Idea

Web development evolved from:

manual pixel editing

to:

declarative structured systems

CAD may eventually follow the same transition.

---

## Scaffold Documents

- [SRS](docs/SRS.md)
- [Schema Overview](docs/SCHEMA_OVERVIEW.md)
- [References](docs/REFERENCES.md)
- [Scaffold Notes (txt)](docs/SCaffold_NOTES.txt)
- [Draft JSON Schema](schema/cadml.schema.json)
- [Minimal CADML Example](examples/minimal.cadml)
