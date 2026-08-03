# SonicDE Multi-Repository Workspace

This is a generated, Git-ignored workspace containing many independent source repositories. `_WORK_` itself is not the source-control root for those repositories.

## Directory Structure

```text
_WORK_/
├── AGENTS.md
├── project.code-workspace
├── graphify-out/
│   └── graph.json                 # merged graph for all workspace projects
└── sources/
    ├── 3rdparty/
    │   ├── libdrm/
    │   └── qcoro6/
    ├── qt6/
    │   ├── qt5compat/
    │   ├── qtbase/
    │   ├── qtdeclarative/
    │   ├── qtlocation/
    │   ├── qtmultimedia/
    │   ├── qtpositioning/
    │   ├── qtsensors/
    │   ├── qtshadertools/
    │   ├── qtspeech/
    │   ├── qtsvg/
    │   ├── qttools/
    │   └── qtwebsockets/
    └── sonicde/
        └── <project>/             # one independent Git repository per project
```

The SonicDE directory currently contains the individual `silver-*`, `sonic-*`, and `xdg-desktop-portal-sonicde` repositories. Treat every immediate child of `sources/3rdparty/`, `sources/qt6/`, and `sources/sonicde/` as a separate project and potential Git repository.

## Context Protocol

1. For any codebase or architecture question, query the merged Graphify graph before searching raw source.
2. Resolve source paths relative to `_WORK_`; project code is under `sources/<group>/<project>/`.
3. Do not assume `_WORK_` has a useful Git state. Run Git commands inside the specific project repository being changed.
4. When a change crosses project boundaries, inspect every affected repository and verify dependency, API, and build-system alignment.

## Graphify

The merged workspace graph is `graphify-out/graph.json`. Each project may also have its own `sources/<group>/<project>/graphify-out/graph.json` generated during extraction.

When the user invokes `/graphify`, load and follow the installed Graphify skill before doing anything else.

Rules:

- For codebase questions, first run `GRAPHIFY_MAX_GRAPH_BYTES=1GB graphify query "<question>"` from `_WORK_`.
- The merged graph exceeds Graphify's default 512 MB input limit. Always set `GRAPHIFY_MAX_GRAPH_BYTES=1GB` for `graphify query`, `graphify path`, and `graphify explain` against the merged graph.
- Dirty `graphify-out/` files are expected and are not a reason to skip Graphify. Skip it only for stale/incorrect graph investigations or when explicitly requested.
- If `graphify-out/wiki/index.md` exists, use it for broad navigation. Read `graphify-out/GRAPH_REPORT.md` only for broad architecture review or when query/path/explain are insufficient.
- Graphify does not traverse the nested repositories when scanning `_WORK_` directly. Update the affected project graph from its project directory, then merge all project graphs back into `_WORK_/graphify-out/graph.json`.
- After changing source code, run `graphify update .` inside each affected project repository. Do not run it from `_WORK_` expecting nested repositories to be discovered.
