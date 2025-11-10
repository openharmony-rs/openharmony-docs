# Community Supply Chain Security Governance

## Overview

To ensure the integrity, security, and compliance of the OpenHarmony open-source project, the community has established a comprehensive supply chain security governance framework that spans the entire software lifecycle. This framework implements strict controls across three core stages: **Source Security**, **Internal Community Operation Security**, and **Release Security**. It is supported by an **SBOM (Software Bill of Materials) Data Foundation** as its unified technical backbone to achieve end-to-end security for the software supply chain.

### Governance Flowchart

```mermaid
graph TB
    %% Define Styles
    classDef processBox fill:#90e0ef,color:#000,stroke:#0096c7,stroke-width:2px
    classDef subBox fill:#caf0f8,color:#000,stroke:#0096c7,stroke-width:1px,stroke-dasharray: 5 5
    classDef greenBox fill:#52b788,color:#fff,stroke:#2d6a4f,stroke-width:2px
    classDef lightGreen fill:#d8f3dc,color:#000,stroke:#52b788,stroke-width:2px
    classDef sbomStyle fill:#2d6a4f,color:#fff,stroke:#1b4332,stroke-width:3px
    
    %% Source Security Area
    subgraph SG1["Source Security"]
        direction TB
        S1["Binaries"]:::subBox
        S2["Open-Source Software"]:::subBox
        S3["Open-Source License Management"]:::greenBox
        S4["Open-Source Import Management<br/>License Compliance Check"]:::subBox
        
        S1 -->|Binary Source Security| S4
        S2 -->|OSS Source Security| S3
        S3 -->|Lifecycle Check| S4
    end
    
    %% Internal Community Operation Security Area
    subgraph SG2["Internal Community Operation Security"]
        direction TB
        
        subgraph SG2_1["Build System"]
            C1["Community Code Repository"]:::greenBox
            C2["Isolated Build<br/>Build-as-Code<br/>Automated Build Process"]:::subBox
        end
        
        subgraph SG2_2["Development Environment"]
            C3["Code Commit"]:::greenBox
            C3_1["Commit Signing"]:::subBox
            C3_2["Snippet Reference Check"]:::subBox
        end
        
        subgraph SG2_3["Archiving"]
            C4["Automated<br/>Version Signing"]:::subBox
        end
        
        C3 --> C3_1
        C3_1 --> C1
        C3 --> C3_2
        C3_2 --> C1
        C1 --> C2
        C2 --> C4
    end
    
    %% Release Security Area
    subgraph SG3["Release Security"]
        direction TB
        
        R1["Version Archiving"]:::lightGreen
        R2["Supporting Docker Build Environment"]:::lightGreen
        R3["Version Tagging"]:::lightGreen
        R4["Release Branch"]:::lightGreen
        
        R5["Image Server"]:::processBox
        R6["Image Hosting Server"]:::processBox
        R7["HPM Package Manager"]:::processBox
        R8["Publish Packages & Distributions<br/>Publish Signed Archives<br/>Release History Traceability"]:::processBox
        
        R1 --> R5
        R2 --> R6
        R3 --> R7
        R4 --> R8
        
        R5 --> R9["Community Release"]
        R6 --> R9
        R7 --> R9
        R8 --> R9
    end
    
    %% SBOM Data Foundation
    SBOM["SBOM Data Foundation<br/>Design Tree / Build Tree"]:::sbomStyle
    
    %% Main Flow Connections
    S4 -->|Automated Repo Setup| C3
    S4 --> SBOM
    C2 --> R1
    C2 --> R2
    C2 --> R3
    C2 --> R4
    C1 --> SBOM
    
    %% Set Subgraph Styles
    style SG1 fill:#e3f2fd,stroke:#00b4d8,stroke-width:3px
    style SG2 fill:#e3f2fd,stroke:#00b4d8,stroke-width:3px
    style SG3 fill:#e3f2fd,stroke:#00b4d8,stroke-width:3px
    style SG2_1 stroke:#999,stroke-width:1px,stroke-dasharray: 5 5,fill:none
    style SG2_2 stroke:#999,stroke-width:1px,stroke-dasharray: 5 5,fill:none
    style SG2_3 stroke:#999,stroke-width:1px,stroke-dasharray: 5 5,fill:none
```

## Detailed Governance Process

### 1. Source Security

Source security is the first line of defense for the supply chain, aiming to ensure that all software components and code entering the community repository are trustworthy and compliant.

-   **Third-Party Open-Source Software Import**: All third-party components planned for import must undergo a strict admission review, including vulnerability scanning, community health assessment, and license compliance analysis.
-   **Community Contributor Code**: Code submissions from community contributors must pass automated code review and security scanning processes to ensure code quality and security.
-   **Open-Source License Management**: The community has a dedicated license management mechanism to check the compliance of all imported components and records the results in the **SBOM** Data Foundation to mitigate legal risks.

### 2. Internal Community Operation Security

After code enters the community, it is continuously monitored through an automated security toolchain and processes to promptly identify and remediate risks.

-   **Community Code Repository**: As the repository for trusted code, all code changes are logged and traceable.
-   **Automated Security Gates**: The code integration process triggers a series of automated scans that act as security gates:
    -   **Static Code Scanning **: Checks for potential security flaws in the source code.
    -   **Software Composition Analysis **: Identifies all direct and indirect dependencies in the project, analyzing their sources, versions, and licenses.
    -   **Vulnerability Scanning**: Compares the identified open-source components against known vulnerability databases (e.g., NVD/CVE) to detect potential security vulnerabilities.
-   **Risk Data Consolidation**: All scan results are aggregated into the **SBOM** Data Foundation for continuous risk assessment and monitoring.

### 3. Release Security

Release security is the final checkpoint for delivering trusted software to end-users, ensuring that the released artifacts are complete, traceable, and untampered.

-   **Version Archiving**: Build artifacts that pass security audits are securely archived in the artifact repository.
-   **Supporting Docker Build Environment**: A corresponding Docker build environment is provided for each official release to ensure the reproducibility of the build process, facilitating security audits and troubleshooting.
-   **Version Identification and Traceability**: By applying clear Git tags and creating dedicated release branches, a precise traceability chain is established from binary artifacts back to the source code.
-   **Secure Distribution**: The final release versions are distributed to users through official and trusted channels.

### 4. SBOM Data Foundation

The **SBOM** Data Foundation is the core of the entire supply chain security governance framework. It provides comprehensive software transparency and serves as the basis for continuous risk monitoring and rapid incident response.

-   **Core Function**: As a dynamically updated database, it records detailed information about all software components in the OpenHarmony project, including their sources, versions, licenses, dependencies, and known vulnerabilities.
-   **Design Tree vs. Build Tree**: The **SBOM** foundation manages both the "Design Tree" (components planned for inclusion during development) and the "Build Tree" (components actually included in the final build artifact). By comparing the two, potential supply chain risks can be accurately identified.
-   **Data-Driven Security**: Through continuous analysis of **SBOM** data, the community can quickly locate components affected by newly disclosed vulnerabilities and efficiently organize remediation and version updates.