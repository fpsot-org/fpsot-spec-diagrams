---
name: fpsot-diagrams
description: Diagram rules for FPSOT repositories. Use when adding or changing a diagram, choosing between C4, UML and BPMN, generating a data model diagram from LinkML, writing the text alternative of a diagram, or making a diagram in English and French.
---

# FPSOT diagrams

Summary of the FPSOT diagrams specification. It adds no rules of its own.
The spec text in `spec/` wins on any difference. Each line cites its requirement ID and keeps its strength: must, should or may.
Accessibility rules and values come from the FPSOT accessibility specification, not from here.

## Diagrams as code

- Every diagram must be PlantUML source, never only an image or a drawing-tool file (DIA-001).
- Each diagram must be its own file directly in `diagrams/`, with `@startuml <base-name>` (DIA-002).
- Hand-written sources must start with an SPDX license comment and a comment saying what the diagram shows and which page or IDs it serves. A generated `.iuml` file is exempt from DIA-002, DIA-003 and DIA-006; its wrapper source must meet them (DIA-003).
- Sources must render with the pinned PlantUML and the Smetana layout, need no Graphviz, and must not include files from the network. They may include the standard library and files from `diagrams/` (DIA-004).
- A diagram should show one idea, about twenty elements at most, and should be split when larger (DIA-005).
- Each diagram must have a `title` with its kind and subject, and a legend for any shape, line or color its notation does not define (DIA-006).
- Labels must use term base terms; abbreviations must be spelled out in the legend or long description (DIA-007).

## Notations

- Pick the notation by purpose and never mix two in one diagram; other purposes may use plain boxes with a legend (DIA-010).
- Architecture: C4 system context, container or component views with the stdlib C4 macros. Never draw the code level by hand (DIA-011).
- C4 elements must show name and description, with the type in the element or legend; containers and components must name their technology. Relationships must point one way with a specific label, and container links must name the protocol. Call `SHOW_LEGEND()` (DIA-012). Landscape, dynamic and deployment views may be added (DIA-013).
- Structure and behavior: UML 2.5.1, should be class, sequence, state machine or use case. Never reuse a UML symbol with another meaning (DIA-014).
- Business processes: BPMN 2.0.2, Descriptive subclass elements only (DIA-015), drawn as a PlantUML activity diagram with the mapping table of DIA-016, titled as a process, with the mapping in the legend. Mark a collapsed sub-process with a visible label, such as `:Pay the fee (sub-process);`. One diagram per pool is recommended (DIA-016).
- A process that a BPMN tool exchanges or an engine runs must keep its `.bpmn` interchange file in `diagrams/` as the source of record, matched by the diagram (DIA-017).
- Data models must be generated with LinkML `gen-plantuml`, written from standard output to a `<name>.iuml` file, never with `-d` (it renders through an online server). The `.iuml` must never be drawn or edited by hand, must be regenerated in the same commit as the schema, and its command must be recorded. Each language must have a small wrapper `.puml` with the name, title and legend that includes the `.iuml`; the workflow renders the wrapper with the pinned PlantUML (DIA-018).

## Text alternatives and color

- Each embedded diagram must have a short alternative in the image macro: kind, subject, main point in one sentence; not the file name, not "Image of" (DIA-020).
- Each diagram must also have a long description right after the image, with the same facts in the reading order of its notation (table in DIA-021). It may point to text right before that already describes it in full.
- Alternatives must change in the same commit as the source, and reviews must check them (DIA-022).
- Color must never be the only cue; each color meaning must also show as a label, shape, line style or legend word. Diagrams should read in gray (DIA-023).
- Text, lines and shapes must meet the accessibility spec's contrast values. Use `skinparam monochrome true` where possible; check other colors, and fix failing C4 defaults with `UpdateElementStyle` (DIA-024).
- The rendered image must have an opaque light background; never set it transparent (DIA-025).

## Output and file names

- Render to SVG with the pinned PlantUML and commit it beside its source; never edit it by hand, never publish a raster-only diagram (DIA-030).
- Embed with an image macro and a relative path such as `../../diagrams/name.svg`; never render PlantUML at build time. A `[source,plantuml]` block may show source as code (DIA-031).
- The SVG must not load anything from another host and must not hold a script (DIA-032).
- Names must follow NAM-070 and NAM-071, and should be `<subject>-<kind>`, such as `registry-container` (DIA-033).

## Two languages

- Diagrams with words people read must exist in English and French; each page embeds its language and has alternatives in its language (DIA-040).
- Name them `<name>-en.puml` and `<name>-fr.puml` (DIA-041).
- Shared layouts should live in `<name>.iuml` with labels in `<name>-labels-en.iuml` and `<name>-labels-fr.iuml` (DIA-042). Small diagrams may have two full sources, which must then match (DIA-043).
- Names that programs read must not be translated; a diagram of only such names must be one file with no language ending, such as a generated data model `.iuml` (DIA-044).
