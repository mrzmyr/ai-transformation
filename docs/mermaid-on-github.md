# Mermaid on GitHub

GitHub renders Mermaid diagrams inside Markdown when code is fenced with the `mermaid` language identifier.

````
```mermaid
flowchart LR
    A["AI in Products"]:::products --> B["Workflow Automation"]:::workflow
    classDef products fill:#8FE8D0,stroke:#111827,color:#111827;
    classDef workflow fill:#C8B6F3,stroke:#111827,color:#111827;
```
````

Use `classDef` for colors and attach classes with `:::className`. Avoid custom global Mermaid theme init for now because GitHub adapts Mermaid to light/dark mode, and hard-coded theme config can hurt readability.

References:

- GitHub Docs: https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/creating-diagrams
- Mermaid flowchart styling: https://mermaid.ai/open-source/syntax/flowchart.html#styling-and-classes

