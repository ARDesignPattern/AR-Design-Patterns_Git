# HMD-AR Interaction Design Patterns

**A reusable design pattern language and Unity-based implementation toolkit for Head-Mounted Augmented Reality in museums and cultural heritage.**

This repository is part of the doctoral research of **Yu Liu** at Hochschule RheinMain, Germany.

The research investigates how reusable, parameterized, and composable interaction design patterns can support the design, development, and evaluation of Head-Mounted Augmented Reality (HMD-AR) experiences in museums and cultural heritage (CH) environments.

The repository provides technical implementations of selected interaction design patterns through Unity packages containing reusable prefabs, scripts, example scenes, and supporting resources.

**Research Portal:** [HMD-AR Interaction Design Patterns](https://yuliu.design/ar-interaction-patterns/)

**Unity Packages:** [GitHub Releases](https://github.com/ARDesignPattern/AR-Design-Patterns_Git/releases)

---

## 1. Overview

The purpose of this project is to bridge the gap between **interaction design knowledge and practical XR development**.

The underlying research develops an interaction design pattern language for recurring design problems in HMD-AR museum experiences. This repository focuses on transferring that design knowledge into reusable technical implementations.

The toolkit follows five principles:

- **Reusability:** Providing reusable interaction components that can be adapted to different cultural heritage applications.
- **Modularity:** Distributing individual interaction implementations as separate Unity packages.
- **Composability:** Supporting the integration of multiple interaction patterns within a shared Unity project and scene.
- **Parameterization:** Allowing Author Users to configure relevant interaction properties and adapt the implementations to their requirements.
- **Reproducibility:** Documenting technical dependencies, implementation requirements, and validated development environments.

The implementations are intended to support the creation of AR interactions across different cultural heritage scenarios, including museums, exhibitions, and heritage interpretation.

They provide **functional interaction components rather than complete, application-specific AR experiences**.

Final scene composition, content integration, parameter tuning, and experience evaluation remain the responsibility of the adopting developer.

---

## 2. Design Pattern Language

The research introduces a two-level pattern language consisting of:

- **3 Category-Level Patterns:** Higher-level design concepts organizing related interaction strategies.
- **9 Application-Level Patterns:** Concrete interaction design patterns addressing specific design problems in HMD-AR experiences.

Category-Level Patterns provide conceptual design guidance and organize the relationships between Application-Level Patterns.

Application-Level Patterns are the primary targets for reusable Unity implementations.

### Application-Level Patterns

| Category                | Application-Level Pattern | Unity Implementation   | Status   |
| ----------------------- | ------------------------- | ---------------------- | -------- |
| Point of Interest Guide | Avatar Guide              | Guide Avatar           | Released |
| Point of Interest Guide | Forward Cue-Routing       | Forward Cue            | Released |
| Experience Indicator    | Step-In Trigger           | Floor Circle Indicator | Released |
| Experience Indicator    | Exhibit Knowledge Trigger | —                      | Planned  |
| Experience Presenter    | Sequential Explanation    | Sequential Explanation | Released |
| Experience Presenter    | AR Labelling              | Digital Label          | Released |
| Experience Presenter    | Exhibit Reassembler       | —                      | Planned  |
| Experience Presenter    | Exhibit Feature Drawing   | —                      | Planned  |
| Experience Presenter    | Object Catching           | —                      | Planned  |

**Current implementation status:** Five Application-Level Pattern implementations have been released as reusable Unity packages.

An additional Foundation module supports the authoring and debugging process.

The remaining four Application-Level Patterns are planned for future technical implementation.

The complete design pattern definitions, including design problems, contexts, solutions, parameters, relationships, and research evidence, are documented separately through the [Research Portal](https://yuliu.design/ar-interaction-patterns/patterns.html).

---

## 3. Repository Structure

This repository contains a Unity project and its supporting technical configuration.

The implementations are organized into individual modules under `Assets/AR_Design_Patterns/`.

### Conceptual Implementation Structure

```text
AR-Design-Patterns_Git/
├── Assets/
│   └── AR_Design_Patterns/
│       ├── 00_Foundation_AuthoringControl/
│       ├── 01_ForwardCueRoot/
│       ├── 02_FloorCircle_Indicator/
│       ├── 03_SequentialExplanation/
│       ├── 04_DigitalLabel/
│       └── 05_GuideAvatar/
├── Packages/
├── ProjectSettings/
├── .gitignore
├── LICENSE
└── README.md
```

_This structure illustrates the implementation organization. The exact directory names and contents may vary between the repository, development project, and exported Unity packages._

Unity-generated directories, including `Library/`, `Temp/`, and `Logs/`, are excluded from version control where appropriate.

### Foundation – Authoring Control

The `00_Foundation_AuthoringControl` module is a reusable authoring and debugging component designed for **Author Users**, rather than museum visitors or other end users.

Unlike the five Application-Level Pattern implementations, it supports the development and testing of AR interactions.

The module provides two main functions:

**Spatial Scanning Control**

Provides an interface for controlling the scanning of the physical environment during AR authoring and testing.

**Interaction Control**

Provides an interface for starting and stopping AR interaction patterns through a reusable control panel.

Author Users can connect this interface to their selected Application-Level Pattern implementations by configuring the corresponding GameObjects, scripts, component references, and interaction events within Unity.

The provided example demonstrates the general control functionality. It does not prescribe a fixed interaction sequence or application architecture.

The Foundation module is a **technical authoring support module**, not an additional Application-Level Design Pattern.

Some implementations may depend on Foundation resources or scripts, while others can function independently once their required external dependencies are installed.

---

## 4. Development Environment

The existing Unity implementations were developed primarily for **Microsoft HoloLens 2**, using Unity and Microsoft Mixed Reality Toolkit.

### Original Project Configuration

| Component                       | Version              |
| ------------------------------- | -------------------- |
| Unity Editor                    | 2020.3.25f1          |
| Universal Render Pipeline (URP) | 10.7.0               |
| Mixed Reality Toolkit (MRTK)    | 2.8.3                |
| Microsoft Mixed Reality OpenXR  | 1.8.1                |
| Unity OpenXR Plugin             | 1.8.2                |
| XR Plugin Management            | 4.2.1                |
| TextMeshPro                     | 3.0.6                |
| Primary target device           | Microsoft HoloLens 2 |

These versions represent the original development and compatibility testing environment.

Compatibility with newer Unity versions, MRTK versions, rendering pipelines, or XR platforms has not yet been established.

**Important:** Unity 2020.3.25f1 is an older Unity version. It is documented for research reproducibility and compatibility with the original implementations, rather than recommended as the default choice for new production applications.

---

## 5. MRTK and XR Dependencies

The implementations use **MRTK 2.8.3** and associated XR components.

Depending on the selected implementation, the following packages may be required:

- Mixed Reality Toolkit Foundation
- Mixed Reality Toolkit Standard Assets
- Mixed Reality Toolkit Tools
- Mixed Reality Toolkit Extensions
- Mixed Reality Toolkit Examples
- Microsoft Mixed Reality OpenXR
- Unity OpenXR Plugin
- XR Plugin Management

Not every individual pattern requires all the components listed above.

### Installing MRTK

Two approaches are available for reproducing the original development environment.

**Option A: Mixed Reality Feature Tool**

Use the Microsoft Mixed Reality Feature Tool to install the required MRTK components into a compatible Unity project.

Refer to the [Microsoft Mixed Reality documentation](https://learn.microsoft.com/en-us/windows/mixed-reality/develop/unity/welcome-to-mrtk).

**Option B: Official MRTK Release Packages**

Download the required MRTK 2.8.3 packages from the [official MRTK GitHub Releases](https://github.com/microsoft/MixedRealityToolkit-Unity/releases).

Use the appropriate installation procedure for the selected package format.

### MRTK Scene Configuration

A scene using MRTK-dependent interaction components must contain a correctly configured `MixedRealityToolkit` instance with an assigned **Active Profile**.

The `DefaultMixedRealityToolkitConfigurationProfile` was used successfully during the compatibility tests.

For integration into existing applications, Author Users may configure the MRTK Profile according to their own application requirements.

When combining multiple patterns within one scene, a shared MRTK environment should be used instead of creating redundant MRTK instances for each pattern.

### MRTK Shaders and URP

Some provided materials use MRTK Standard shaders.

When importing these materials into a URP project, they may initially appear pink if the MRTK shaders have not been configured for the active rendering pipeline.

If necessary, use the MRTK shader upgrade utility:

`Mixed Reality → Toolkit → Utilities → Upgrade MRTK Standard Shader for Universal Render Pipeline`

This operation was required during compatibility testing to restore the intended material rendering.

### Local Package Dependencies

The original development project referenced locally stored `.tgz` packages through `Packages/manifest.json`.

When reproducing this configuration, ensure that the referenced packages are available at valid paths.

Copying the original `manifest.json` without its local dependencies may prevent Unity from resolving the required packages.

---

## 6. Using the Unity Pattern Packages

The existing implementations are distributed as individual `.unitypackage` files through GitHub Releases.

**[Download Unity Packages](https://github.com/ARDesignPattern/AR-Design-Patterns_Git/releases)**

Each package contains the technical resources required for its corresponding implementation, which may include:

- Unity Prefabs
- C# scripts
- Example scenes
- Materials and visual resources
- Interaction assets
- Supporting configuration resources

The packages provide reusable interaction functionality rather than complete AR applications.

### Basic Installation

1. Create or open a Unity project with the required Unity version and rendering configuration.
2. Install the necessary MRTK and XR dependencies.
3. Import the Foundation module if required by the selected pattern.
4. Download the desired `.unitypackage` from GitHub Releases.
5. In Unity, select `Assets → Import Package → Custom Package...`.
6. Review and import the package contents.
7. Open the included example scene or locate the imported Prefab.
8. Ensure the scene contains a correctly configured MRTK environment when required.
9. Locate the corresponding GameObjects in the Unity **Hierarchy**.
10. Replace the demonstration objects with the intended application-specific objects.
11. Reassign the necessary component references and interaction events.
12. Test the interaction functionality within the target application.

### Replacing Example Content

The provided example scenes demonstrate the intended interaction functionality using predefined objects and configurations.

Author Users can adapt these implementations by locating the relevant GameObjects in the Unity Hierarchy and replacing the provided demonstration objects with their own content.

Depending on the selected implementation, users may need to update:

- GameObject and Transform references
- Interaction event connections
- Navigation targets or points of interest
- Text and multimedia content
- Trigger regions and spatial positions
- Other exposed configuration parameters

**Basic knowledge of Unity is assumed**, particularly GameObjects, Prefabs, Components, the Inspector, and scene configuration.

Detailed instructions for general Unity operations and application-specific parameter tuning are outside the scope of this documentation.

### Combining Multiple Patterns

Multiple Application-Level Pattern implementations can be imported into a shared Unity project and combined within a single scene.

Author Users should ensure that the shared MRTK environment is configured correctly and that the individual implementations reference the intended GameObjects and interaction events.

Spatial arrangement, interaction sequences, and application-specific content integration can then be adapted according to the requirements of the intended cultural heritage experience.

### Compatibility and Validation Status

The six currently released Unity modules have undergone basic compatibility and functional testing using:

- Unity 2020.3.25f1
- MRTK 2.8.3
- URP 10.7.0

All six packages were successfully imported into a shared Unity project.

Their basic interaction functionality was tested individually. The six modules were also integrated into a shared Unity scene, where their basic interactions operated without observed runtime errors or script conflicts during the reported tests.

Two issues discovered during the testing process were corrected:

- **Sequential Explanation v1.0.1:** Corrected missing navigation Sprite references and updated the example scene's MRTK Profile.
- **Guide Avatar v1.0.1:** Corrected the JSON resource loading path used for navigation data.

The updated packages were subsequently re-imported and verified.

These results provide initial technical evidence supporting **reusability, modularity, and composability** within the tested environment.

They do not establish compatibility with every possible implementation combination, platform, hardware configuration, or application scenario.

---

## 7. Pattern Implementations and Downloads

The following Unity packages are publicly available.

### Foundation Module

**00 – Foundation: Authoring Control**

Version: `v1.0.0`

Provides an authoring and debugging interface for controlling spatial scanning and initiating AR interaction patterns.

This module supports Author Users and is not an additional Application-Level Design Pattern.

[Download and Release Notes](https://github.com/ARDesignPattern/AR-Design-Patterns_Git/releases/tag/Foundation_AuthoringControl_v1.0.0)

### Application-Level Implementations

| Module                    | Version | Primary Function                                                         |
| ------------------------- | ------- | ------------------------------------------------------------------------ |
| 01 Forward Cue–Routing    | v1.0    | Spatial navigation using floor-based directional cues and audio feedback |
| 02 Floor Circle Indicator | v1.0    | Proximity-based spatial interaction and activation feedback              |
| 03 Sequential Explanation | v1.0.1  | Step-by-step narrative presentation with Previous / Next navigation      |
| 04 Digital Label          | v1.0.0  | Spatially associated digital exhibit labels and descriptive content      |
| 05 Guide Avatar           | v1.0.1  | Virtual guidance using predefined navigation paths and playback controls |

All packages and their version-specific installation notes are available from:

**[GitHub – Unity Package Releases](https://github.com/ARDesignPattern/AR-Design-Patterns_Git/releases)**

Each Release includes the downloadable `.unitypackage`, a description of its functionality, installation requirements, basic usage guidance, and relevant compatibility information.

### Relationship to the Research Portal

The Research Portal provides the conceptual and research-oriented description of the interaction patterns.

The Technology section connects these pattern definitions with their Unity-based technical implementations.

**[Research Portal – Technology](https://yuliu.design/ar-interaction-patterns/tech.html)**

The Foundation module is presented as a supporting authoring resource, while the five Application-Level implementations correspond to specific patterns within the research pattern language.

---

## 8. Research Background

This repository supports doctoral research into reusable interaction design pattern languages for Head-Mounted Augmented Reality in museums and cultural heritage.

The research draws upon **Design Science Research (DSR)** and **Research through Design (RtD)**.

Its objectives include:

- Identifying recurring interaction design problems in HMD-AR museum experiences.
- Developing reusable and structured interaction design patterns.
- Defining relevant design parameters and implementation conditions.
- Investigating relationships and composition between patterns.
- Evaluating selected interaction designs through empirical studies.
- Supporting the transfer of research knowledge into practical XR development.

The pattern language and its Unity implementation toolkit represent two connected but distinct research outputs.

The pattern language documents reusable design knowledge, including problems, contexts, solutions, and relationships.

The Unity packages provide concrete technical implementations that support the application and further exploration of this design knowledge.

This distinction allows researchers and designers to study the conceptual patterns independently of the Unity development environment.

For additional research information, visit the [Research Portal](https://yuliu.design/ar-interaction-patterns/).

---

## 9. Citation

If you use these design patterns or technical implementations in academic work, please acknowledge the project and cite the relevant research publications.

The Research Portal provides further information about the research and associated publications.

When referring to a specific Unity implementation, please indicate the corresponding module and version.

A machine-readable `CITATION.cff` file and version-specific archival citation information may be provided in future releases.

---

## 10. License

This repository is distributed under the [MIT License](./LICENSE), subject to the scope of that license and any applicable third-party licensing conditions.

The repository includes software implementations and research-related technical resources.

Third-party materials, including MRTK components, Unity packages, models, and other externally sourced assets, may be subject to their own licensing terms.

Users must comply with the applicable licenses of any third-party dependencies or resources included in their applications.

Licensing of the design pattern research content published through the Research Portal should be considered separately from the licensing of software implementations.

---

## 11. Project Status and Roadmap

### Completed

- Development of the HMD-AR Interaction Design Pattern Language consisting of 3 Category-Level and 9 Application-Level Patterns.
- Technical implementation of five Application-Level Pattern modules.
- Development of the Foundation – Authoring Control module.
- Publication of six Unity packages through GitHub Releases.
- Basic functional testing of the six implementations.
- Shared-project import and compatibility testing.
- Shared-scene integration and basic interaction testing.
- Correction and revalidation of identified resource and configuration issues.
- Documentation of the original development environment and required dependencies.

### Future Development

The project will continue toward the implementation of the remaining four Application-Level Patterns:

- Exhibit Knowledge Trigger
- Exhibit Reassembler
- Exhibit Feature Drawing
- Object Catching

Additional planned activities include:

- Extending technical documentation where necessary.
- Connecting all published Unity implementations to their corresponding Research Portal pages.
- Improving implementation resources based on future research and development.
- Investigating compatibility with newer Unity versions and additional XR platforms.
- Exploring further reuse and composition of interaction patterns.

Category-Level Patterns remain part of the conceptual design knowledge system and are not currently planned as standalone Unity packages.

---

## 12. Contact

**Yu Liu**  
HMD-AR Interaction Design Research  
Hochschule RheinMain, Germany

**Research Portal:** https://yuliu.design/ar-interaction-patterns/

**Personal Website:** https://yuliu.design

**GitHub Organization:** https://github.com/ARDesignPattern

**Email:** yu.liu.design@outlook.com

---

_This repository is part of an academic research initiative on reusable, parameterized, and composable interaction design patterns for Head-Mounted Augmented Reality in museums and cultural heritage._

_The provided technical implementations support AR interaction authoring and development. Application-specific integration, configuration, and final experience evaluation remain the responsibility of the adopting Author User._
