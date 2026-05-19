# CADML Schema Overview

This document explains the first schema boundary for CADML.

Note: the JSON schema describes the normalized/intermediate document form, not raw `.cadml` source syntax directly.

## Goals
- deterministic validation
- explicit typing
- semantic object-first modeling
- easy machine and human inspection

## Core Top-Level Shape
- `version`
- `kind`
- `name`
- `objects[]`
- `constraints[]`

## Object Shape (Draft)
- `type` (semantic object name)
- `name` (optional identifier)
- `properties` (dimension/material/domain properties)
- `relationships` (attachments, references, adjacency)

## Constraint Shape (Draft)
- `type`
- `target`
- `params`

## Validation Rules (Draft)
- required fields must be present
- unknown top-level fields should fail validation in strict mode
- units should be explicit for dimensional values
- object references should resolve within the same assembly scope

See `schema/cadml.schema.json` for the machine-readable draft.
