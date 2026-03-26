# Construction — Design-First Workspace

This folder manages the design-before-writing workflow for the Amazon-VT CFP proposal.

## Structure

```
construction/
├── README.md            # This file
├── spec_builder.md      # Design document template
├── design/              # Design documents (created before writing)
├── requirements/        # CFP submission requirements and checklists
└── sprints/             # Sprint plans for executing designs
```

## Workflow

1. **Design** — Create a design doc in `design/` using `spec_builder.md` template
2. **Requirements** — Validate against submission requirements in `requirements/`
3. **Sprint** — Break design into tasks in `sprints/`
4. **Execute** — Write proposal content per sprint plan
5. **Validate** — Check against CFP requirements

## Rules

- No proposal content is drafted without an approved design document
- Every design maps to one or more CFP topic areas
- Sprint tasks have clear acceptance criteria
- Completed sprints are archived to `memory-bank/archive/`
