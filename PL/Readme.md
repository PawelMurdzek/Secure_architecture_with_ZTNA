# Architektura Bezpieczeństwa Systemu Obsługi Klienta


<p align="center">
    <img src="https://img.shields.io/badge/Security-ZTNA-blue?style=for-the-badge&logo=shield" alt="Security ZTNA">
    <img src="https://img.shields.io/badge/Architecture-Defense%20in%20Depth-navy?style=for-the-badge" alt="Defense in Depth">
    <img src="https://img.shields.io/badge/Status-Production%20Ready-green?style=for-the-badge" alt="Status">
</p>

---

## Główne Założenia

Kompleksowy projekt infrastruktury bezpieczeństwa dla systemu obsługi klientów indywidualnych, zaprojektowany z myślą o maksymalnej izolacji zasobów i ochronie danych wrażliwych. Dokumentacja została przygotowana w systemie LaTeX.

Projekt opiera się na dwóch filarach nowoczesnego cyberbezpieczeństwa:

1.  **Defense in Depth (Obrona w głębokości)** – wielowarstwowe mechanizmy kontrolne na poziomie sieci, aplikacji i danych.
2.  **Zero Trust Network Access (ZTNA)** – eliminacja tradycyjnych modeli VPN na rzecz autoryzacji opartej na tożsamości i kontekście.

---

## Architektura Systemu

Infrastruktura została podzielona na logiczne strefy izolacji, co wizualizuje poniższy diagram:

```mermaid
graph TD
    User((Użytkownik)) --> DMZ
    subgraph DMZ [Strefa DMZ - Brzeg]
        WAF[WAF / NGFW]
        SC[Scrubbing Center]
    end
    DMZ --> App
    subgraph App [Strefa Aplikacyjna]
        AGW[API Gateway]
        ICAP[Inspekcja ICAP]
        Logic[Logika Biznesowa]
    end
    App --> Data
    subgraph Data [Strefa Danych]
        DB[(Baza Danych)]
        HSM[Moduł HSM]
        DAM[Monitoring DAM]
    end
    subgraph MGMT [Strefa Zarządzania]
        SIEM[System SIEM]
        WORM[Backup WORM]
    end
    MGMT -.-> App
    MGMT -.-> Data
```

---

## Kluczowe Mechanizmy Kontrolne

| Kategoria | Mechanizm / Standard | Opis |
| :--- | :--- | :--- |
| **Tożsamość** | IdP/IAM, OIDC, MFA | Autoryzacja oparta na tożsamości i wieloskładnikowym uwierzytelnianiu. |
| **Kryptografia** | mTLS, TLS 1.3, TDE | Szyfrowanie danych w spoczynku i w locie. |
| **DevSecOps** | SAST, DAST, Container Scanning | Integracja testów bezpieczeństwa w potoku CI/CD. |
| **Odporność** | Write Once, Read Many (WORM) | Ochrona przed ransomware dzięki niezmiennym kopiom danych. |

---

## Autor

> [!NOTE]
> **Paweł Murdzek**
> *Specjalista ds. Architektury Bezpieczeństwa*