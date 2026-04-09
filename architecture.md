# 🌈 Platform Architecture

```mermaid
flowchart TD

    %% Entry Layer
    A[🌐 Internet] --> B[☁️ cloudflared]
    B --> C[🌐 Caddy Reverse Proxy]

    %% Core apps
    C --> D[🟢 WordPress]
    C --> E[🔐 Authentik]
    C --> F[🩶 Homepage]
    C --> G[🪟 Homarr]

    %% Authentik controls access
    E --> H[📚 Books - Calibre Web]
    E --> I[🎧 Audiobookshelf]
    E --> J[🎵 Navidrome]
    E --> K[📝 Shelfmark Requests]
    E --> L[🎶 Ombi Requests]
    E --> M[🧾 Invoice Ninja]
    E --> N[🆘 FreeScout]

    %% WordPress connects users to services
    D --> H
    D --> I
    D --> J
    D --> K
    D --> L
    D --> M
    D --> N

    %% Media storage
    subgraph Windows Host
        O[📚 Calibre Library]
        P[🎧 Audiobook Storage]
        Q[🎵 Music Storage]
    end

    O --> H
    P --> I
    Q --> J
