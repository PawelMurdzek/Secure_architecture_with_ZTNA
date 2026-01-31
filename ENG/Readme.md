# Customer Service System Security Architecture

<p align="center">
    <img src="https://img.shields.io/badge/Security-ZTNA-blue?style=for-the-badge&logo=shield" alt="Security ZTNA">
    <img src="https://img.shields.io/badge/Architecture-Defense%20in%20Depth-navy?style=for-the-badge" alt="Defense in Depth">
    <img src="https://img.shields.io/badge/Status-Production%20Ready-green?style=for-the-badge" alt="Status">
</p>

---

## Core Principles

A comprehensive security infrastructure project for an individual customer service system, designed for maximum resource isolation and protection of sensitive data. Documentation was prepared using LaTeX.

The project is based on two pillars of modern cybersecurity:

1.  **Defense in Depth** – multi-layered control mechanisms at the network, application, and data levels.
2.  **Zero Trust Network Access (ZTNA)** – elimination of traditional VPN models in favor of identity and context-based authorization.

---

## System Architecture

The infrastructure has been divided into logical isolation zones, as visualized in the diagram below:

```mermaid
graph TD
    User((User)) --> DMZ
    subgraph DMZ [DMZ Zone - Edge]
        WAF[WAF / NGFW]
        SC[Scrubbing Center]
    end
    DMZ --> App
    subgraph App [Application Zone]
        AGW[API Gateway]
        ICAP[ICAP Inspection]
        Logic[Business Logic]
    end
    App --> Data
    subgraph Data [Data Zone]
        DB[(Database)]
        HSM[HSM Module]
        DAM[DAM Monitoring]
    end
    subgraph MGMT [Management Zone]
        SIEM[SIEM System]
        WORM[WORM Backup]
    end
    MGMT -.-> App
    MGMT -.-> Data
```

---

## Key Control Mechanisms

| Category | Mechanism / Standard | Description |
| :--- | :--- | :--- |
| **Identity** | IdP/IAM, OIDC, MFA | Authorization based on identity and multi-factor authentication. |
| **Cryptography** | mTLS, TLS 1.3, TDE | Encryption of data at rest and in transit. |
| **DevSecOps** | SAST, DAST, Container Scanning | Integration of security testing in the CI/CD pipeline. |
| **Resilience** | Write Once, Read Many (WORM) | Ransomware protection through immutable data copies. |

---

## Author

> [!NOTE]
> **Paweł Murdzek**
> *Security Architecture Specialist*
