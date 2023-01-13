---
title: Roadblocks
---
# Issue #1
---
## Issues
- Radarr and Sonarr stopped working
- Checked other containers' status, werent functioning either
- Radarr config said it was having issues writing to /conf

## Cause
- 0% storage left, nowhere to write configs to

## Solution
- Only 30GB of the 60GB were allocated to the partition
- Expanded the partition with ```lvextend -r -l +100%FREE /dev/mapper/ubuntu--vg-ubuntu--lv```
- Shutdown docker containers, rebooted VM, spun up containers, backed up volumes
- [Refrence Video](https://youtu.be/rhvRs84rN9I)

---