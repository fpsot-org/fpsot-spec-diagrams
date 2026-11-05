# Changelog

All notable changes to this specification are listed here.
The format follows [Keep a Changelog 1.1.0](https://keepachangelog.com/en/1.1.0/),
and versions follow [Semantic Versioning 2.0.0](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [0.1.0] - 2026-11-05

### Added

- Diagrams as code: PlantUML sources in `diagrams/`, their header comments, the pinned renderer, size, titles, legends and labels (DIA-001 to DIA-007).
- Notations: C4 views for architecture, UML 2.5.1 for structure and behavior, BPMN 2.0.2 for business processes drawn as PlantUML activity diagrams, and data model diagrams generated from LinkML (DIA-010 to DIA-018).
- Text alternatives and color: the short alternative, the long description per notation, color never alone, contrast through the accessibility specification, and an opaque background (DIA-020 to DIA-025).
- Output and file names: committed SVG files, how pages embed them, self-contained SVG and view endings in file names (DIA-030 to DIA-033).
- Diagrams in two languages: one source per language, shared layouts with label files, and names that stay in English (DIA-040 to DIA-044).
- Comparison data with an international baseline, Canada and Québec rows.
- A how-to guide with one PlantUML example per notation, a bilingual example diagram, the agent skill, `llms.txt` and a book per language.

### Known gaps

- The accessibility specification is written at the same time; its requirement IDs are not cited yet.
- No check yet confirms that a generated data model diagram matches its schema.
