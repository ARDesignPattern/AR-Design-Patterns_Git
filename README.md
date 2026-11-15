# HMD-AR Interaction Design Patterns

**A reusable design pattern language and Unity-based implementation toolkit for Head-Mounted Augmented Reality in museums and cultural heritage.**

This repository is part of the doctoral research of **Yu Liu** at Hochschule RheinMain, Germany.

The research investigates how reusable and parameterized interaction design patterns can support the design, development, and evaluation of Head-Mounted Augmented Reality (HMD-AR) experiences in museums and cultural heritage environments.

The project provides Unity-based implementations of selected interaction design patterns, including reusable prefabs, scripts, example scenes, and supporting technical resources.

**Research Portal:** [HMD-AR Interaction Design Patterns](https://yuliu.design/ar-interaction-patterns/)

---

## 1. Overview

The goal of this project is to bridge the gap between **interaction design knowledge and practical XR development**.

While the research defines interaction design patterns as reusable solutions to recurring design problems, this repository focuses on their technical implementation and reuse in Unity.

The project aims to support:

- **Reusability:** Providing reusable interaction components for HMD-AR applications.
- **Modularity:** Organizing implementations into individual Unity packages.
- **Composability:** Supporting the combination of multiple interaction patterns within a single XR application.
- **Parameterization:** Exposing relevant design parameters for configuration and adaptation.
- **Reproducibility:** Documenting development environments, dependencies, and implementation requirements.

The design patterns are intended primarily for museum and cultural heritage applications. Their applicability to other XR contexts depends on the relevant design conditions and constraints.

## 2. Design Pattern Language

The research introduces a two-level pattern language consisting of:

- **3 Category-Level Patterns:** Higher-level design concepts that organize related interaction strategies.
- **9 Application-Level Patterns:** Concrete interaction design patterns addressing specific design problems.

The Category-Level Patterns provide conceptual guidance, while the Application-Level Patterns are the primary targets for reusable Unity implementations.

### Application-Level Patterns

| Category                | Application-Level Pattern | Implementation         |
| ----------------------- | ------------------------- | ---------------------- |
| Point of Interest Guide | Avatar Guide              | Guide Avatar           |
| Point of Interest Guide | Forward Cue-Routing       | Forward Cue            |
| Experience Indicator    | Step-In Trigger           | Floor Circle Indicator |
| Experience Indicator    | Exhibit Knowledge Trigger | Planned                |
| Experience Presenter    | Sequential Explanation    | Sequential Explanation |
| Experience Presenter    | AR Labelling              | Digital Label          |
| Experience Presenter    | Exhibit Reassembler       | Planned                |
| Experience Presenter    | Exhibit Feature Drawing   | Planned                |
| Experience Presenter    | Object Catching           | Planned                |

_The table shows the current mapping between the research patterns and their technical implementations. Existing implementation packages are undergoing compatibility and documentation review. Availability of validated downloads will be updated progressively._

The complete pattern definitions, including design problems, contexts, solutions, design parameters, relationships, and research evidence, are available through the [Research Portal](https://yuliu.design/ar-interaction-patterns/patterns.html).

## 3. Repository Structure

This repository contains a Unity project and its supporting configuration files.

```text
AR-Design-Patterns_Git/
├── Assets/
│   └── AR_Design_Patterns/
│       ├── 00_Foundation/
│       ├── 01_ForwardCue/
│       ├── 02_FloorCircleIndicator/
│       ├── 03_SequentialExplanation/
│       ├── 04_DigitalLabel/
│       └── 05_GuideAvatar/
├── Packages/
├── ProjectSettings/
├── .gitignore
├── LICENSE
└── README.md
```

_The pattern directories above illustrate the implementation organization. Their exact names and contents may differ in the current Unity project._

Unity-generated directories, such as `Library/`, `Temp/`, and `Logs/`, are excluded from version control where appropriate.

### Foundation Module

The Foundation module contains shared functionality used by certain pattern implementations.

Some pattern packages reference resources or scripts from Foundation and therefore require it to be installed before the corresponding pattern package.

Other implementations may operate without Foundation, subject to their external dependencies.

The Foundation module is a **technical support module**, not an additional Application-Level Design Pattern.

## 4. Development Environment

The current implementations were developed using a Unity and Microsoft Mixed Reality Toolkit environment primarily targeting HoloLens 2.

### Original Project Configuration

| Component                      | Version              |
| ------------------------------ | -------------------- |
| Unity Editor                   | 2020.3.25f1          |
| Universal Render Pipeline      | 10.7.0               |
| Mixed Reality Toolkit (MRTK)   | 2.8.3                |
| Microsoft Mixed Reality OpenXR | 1.8.1                |
| Unity OpenXR Plugin            | 1.8.2                |
| XR Plugin Management           | 4.2.1                |
| TextMeshPro                    | 3.0.6                |
| Primary target device          | Microsoft HoloLens 2 |

These versions describe the original development environment and should not be interpreted as a guarantee of compatibility with newer Unity, MRTK, or OpenXR versions.

The original Unity version is provided for reproducibility and compatibility testing. It is not recommended as a default environment for new production applications without considering its age and security limitations.

## 5. MRTK and XR Dependencies

The original project uses **Mixed Reality Toolkit (MRTK) 2.8.3** and related XR components.

Depending on the implementation, the following packages may be required:

- Mixed Reality Toolkit Foundation
- Mixed Reality Toolkit Standard Assets
- Mixed Reality Toolkit Tools
- Mixed Reality Toolkit Extensions
- Mixed Reality Toolkit Examples
- Microsoft Mixed Reality OpenXR
- Unity OpenXR Plugin
- XR Plugin Management

Not every individual pattern requires every component listed above.

### Installing MRTK

Two installation approaches are available for recreating the development environment.

**Option A: Mixed Reality Feature Tool**

Use the Microsoft Mixed Reality Feature Tool to select compatible MRTK components and import them into the Unity project.

Refer to the [Microsoft Mixed Reality documentation](https://learn.microsoft.com/en-us/windows/mixed-reality/develop/unity/welcome-to-mrtk).

**Option B: Original MRTK release packages**

MRTK 2.8.3 packages can be obtained from the [official MRTK GitHub releases](https://github.com/microsoft/MixedRealityToolkit-Unity/releases).

Use the appropriate package format and installation procedure for the selected release.

**Important:** The original project also referenced locally stored `.tgz` packages through `Packages/manifest.json`. When reproducing this setup, those local packages must be available at the referenced paths or their dependencies must be reconfigured using valid package sources.

Simply copying the original `manifest.json` without providing its local dependencies may prevent Unity from resolving the project environment.

## 6. Using the Unity Pattern Packages

Individual implementations are intended to be distributed as `.unitypackage` files.

Available releases can be found in the [GitHub Releases section](https://github.com/ARDesignPattern/AR-Design-Patterns_Git/releases).

### Basic Installation

1. Create a Unity project using a compatible Unity version and rendering configuration.
2. Install the required MRTK and XR dependencies.
3. Import the Foundation package if required by the selected pattern.
4. Download the desired pattern `.unitypackage`.
5. In Unity, select `Assets > Import Package > Custom Package...`.
6. Review the import contents and confirm the import.
7. Locate the imported Prefab and supporting assets.
8. Add the Prefab to a suitable scene and configure its parameters.
9. Check the Unity Console and Inspector for missing scripts, missing references, or dependency errors.
10. Test the implementation in the intended XR environment.

Individual implementations may require additional scene setup, references, interaction managers, or runtime configuration.

### Combining Multiple Patterns

The intended toolkit architecture supports combining multiple Application-Level Patterns within one Unity project.

To evaluate multiple packages together:

1. Install the shared dependencies.
2. Import Foundation where required.
3. Import the selected pattern packages individually.
4. Check for overlapping assets, scripts, and dependency conflicts.
5. Verify that each pattern works independently.
6. Place multiple pattern prefabs into the same scene.
7. Test interactions, input handling, shared services, and runtime behavior.

**Compatibility status:** Cross-package integration testing is ongoing. Independent importability and composability should not yet be assumed for every package or combination.

Compatibility information will be updated as individual implementations are reviewed and validated.

## 7. Pattern Implementations and Downloads

The technical implementations are presented in the Technology section of the Research Portal:

**[Technology – Unity Prefab Library](https://yuliu.design/ar-interaction-patterns/tech.html)**

Each published implementation is intended to provide:

- An overview of its interaction functionality.
- A reusable Unity Prefab.
- Supporting scripts and assets.
- Information about dependencies and setup.
- Configuration guidance.
- A downloadable Unity package.
- A link to the corresponding design pattern, where applicable.

### Existing GitHub Releases

- [Forward Cue-Routing v1.0](https://github.com/ARDesignPattern/AR-Design-Patterns_Git/releases/tag/ForwardCue_Routing_v1.0)
- [Floor Circle Indicator v1.0](https://github.com/ARDesignPattern/AR-Design-Patterns_Git/releases/tag/floor_circle_indicator_v1.0)

Additional implementations will be reviewed and published progressively.

## 8. Research Background

This repository supports doctoral research investigating the design and implementation of interaction pattern languages for HMD-based Augmented Reality in museums.

The research adopts a design-oriented approach, drawing on **Design Science Research (DSR)** and **Research through Design (RtD)**.

Its objectives include:

- Identifying recurring interaction design problems in HMD-AR museum experiences.
- Developing reusable and structured interaction design patterns.
- Defining relevant design parameters and implementation conditions.
- Exploring relationships and composition between patterns.
- Evaluating selected interaction designs through empirical studies.
- Supporting the transfer of research knowledge into practical XR development.

The design pattern language is documented separately from its Unity implementations.

This distinction allows researchers and interaction designers to explore the design knowledge independently of the Unity development environment.

For further details, visit the [Research Portal](https://yuliu.design/ar-interaction-patterns/).

## 9. Citation

If you use the design patterns or technical implementations in academic work, please acknowledge the project and cite the relevant research publications.

The Research Portal provides further information on the corresponding research and publications.

A machine-readable `CITATION.cff` file and version-specific archival citation information may be provided in future releases.

## 10. License

The repository contains source code, Unity assets, and research-related documentation.

The repository is distributed under the [MIT License](./LICENSE), subject to the scope of that license and the licensing terms of individual components.

Third-party resources, including MRTK components, Unity packages, models, and other external assets, may be governed by their respective licenses.

Licensing of research content published through the Research Portal should be considered separately from licensing of software implementations.

Users are responsible for complying with applicable third-party license requirements.

## 11. Project Status and Roadmap

The project is being developed toward a reusable library of Unity implementations corresponding to the nine Application-Level Patterns.

Current priorities include:

- Reviewing existing Unity packages and their dependencies.
- Validating individual package installation.
- Testing compatibility between multiple pattern implementations.
- Improving technical documentation and configuration guidance.
- Preparing additional pattern implementations for public release.
- Maintaining links between the Research Portal and GitHub resources.

Category-Level Patterns remain part of the design knowledge system and are not currently planned as standalone Unity packages.

## 12. Contact

**Yu Liu**  
HMD-AR Interaction Design Research  
Hochschule RheinMain, Germany

**Research Portal:** https://yuliu.design/ar-interaction-patterns/  
**Personal Website:** https://yuliu.design  
**GitHub Organization:** https://github.com/ARDesignPattern  
**Email:** yu.liu.design@outlook.com

---

_This repository is part of an academic research initiative on reusable interaction design patterns for HMD-based Augmented Reality._
