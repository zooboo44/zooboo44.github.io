---
title: Roadblocks
---

# Issue #1
---
## Problem
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
# Issue #2
---
## Problem
- Everytime a new torrent started to download, it would fail

## Cause
- Not entirely sure, suspect it was an issue with the SMB and NFS permission continutiy

## Solution
- Stripped ACL
- Deleted both NFS and SMB shares and reinitiated them using only NFS permissions
- Works for now, we'll see if there are any issues in the future

---
# Issue #3
---
## Problem
- Warning backing up docker-volumes with duplicati
 ```2023-03-03 09:00:05 +00 - [Warning-Duplicati.Library.Main.Operation.Backup.FileBlockProcessor.FileEntry-PathProcessingFailed]: Failed to process path: /source/logging_prometheus-data/_data/data/chunks_head/000814```

## Cause

## Solution
- Re-ran backup
- Not entirely sure if this issue was a fluke or if its a persisting issue and if this is just a temporary fix
- Come back to later