<div align="center">

<img src="https://raw.githubusercontent.com/woodfine/woodfine-media-assets/main/ASSET-SIGNET-MASTER.svg" width="80" alt="Woodfine Signet">

# Corporate Identity | Identidad Corporativa
### *Brand Assets & PointSav Theme Injection*

[![Aesthetic](https://img.shields.io/badge/Aesthetic-Institutional_Brutalism-164679?style=flat-square)](#)
[![Tokens](https://img.shields.io/badge/Tokens-CSS_Variables-164679?style=flat-square)](#)
[![Status](https://img.shields.io/badge/Status-Verified-54924E?style=flat-square)](#)

[ **Active Fleet Manifest** ](https://github.com/woodfine/woodfine-fleet-deployment) | [ **PointSav Design System** ](https://github.com/pointsav/pointsav-design-system) | [ **Main Profile** ](https://github.com/woodfine)

</div>

---

<details>
<summary><b>🛡️ VIEW IP ISOLATION DOCTRINE</b></summary>
<br>
This repository contains the proprietary visual identity and system routing parameters for Woodfine Management Corp. While the <code>pointsav-design-system</code> defines the universal physics of the web, this repository acts as the "Opinionated Paint" injected into the agnostic PointSav core.
<br><br>
By isolating our brand identity into this independent repository, we guarantee that our vendor's infrastructure remains generic, open-source, and devoid of Woodfine intellectual property.
<br><br>
</details>

## 🎨 The Customer Theme Injection Architecture
```mermaid
graph TD;
    subgraph Woodfine (Customer)
        A[token-global-color.yaml] --> B[theme-woodfine-light.yaml];
    end
    subgraph PointSav (Vendor Core)
        B -.->|Injects via Alias| C[token-alias-ui.yaml];
        C --> D[Sovereign UI Components];
    end
    
    style A fill:#164679,stroke:#111827,stroke-width:2px,color:#fff
    style B fill:#164679,stroke:#111827,stroke-width:2px,color:#fff
    style C fill:#111827,stroke:#869FB9,stroke-width:1px,color:#fff
    style D fill:#292929,stroke:#869FB9,stroke-width:1px,color:#fff
```

### 📂 Master Index: Theme Injection
| File | Role | Description |
| :--- | :--- | :--- |
| `token-global-color.yaml` | Global Values | The raw hex codes defining the Woodfine palette. |
| `token-global-telemetry.yaml` | Config | Defines the active Woodfine transmission URL and port (`8082`). |
| `theme-woodfine-light.yaml` | Alias Mapper | Injects Woodfine Global colors into PointSav UI aliases. |

### 📂 Master Index: Print & Vectors
* **`ASSET-LOGO-PRIMARY.svg`**: Master vector marks.
* **`OM-STATIONERY-GUIDE.pdf`**: Print standards for Offering Memorandums.
* **`ASSET-SIGNET-MASTER.svg`**: Normalized Woodfine Corporate Signet.

---
*© 2026 Woodfine Management Corp.*
