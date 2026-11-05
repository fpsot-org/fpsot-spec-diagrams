# Instructions for agents

This repository holds the FPSOT diagrams specification.
It covers diagrams as code in PlantUML, the choice of C4, UML and BPMN, data model diagrams generated from LinkML, text alternatives and color in diagrams, SVG output and file names, and diagrams in English and French.

- The normative text is in `spec/en/` and `spec/fr/`. Every rule has an ID such as `DIA-001`.
- Follow `skill/SKILL.md` when you add or change a diagram. The spec text wins on any difference.
- Every page exists in English and in French, with the same file name and the same IDs.
- Accessibility rules and values belong to the FPSOT accessibility specification. Point to it and never restate a value.
- Terms and abbreviations come from the term base of `fpsot-spec-writing`. Add a missing term there first.
- Do not copy text from outside standards. Summarize them in your own words and cite the exact version.
- Commits follow Conventional Commits and are signed. Pull requests are squash-merged.
