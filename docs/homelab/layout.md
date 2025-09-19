---
title: Homelab Layout
date: 2025-09-18
---

# Homelab Layout

```mermaid
architecture-beta
  group server(server) [Dell R720]

  service docker(server) [Docker VM] in server
  service nas(server) [TrueNAS Core VM] in server
  service ha(server) [HomeAssistant VM] in server
  service gitlab(server) [GitLab] in server
```