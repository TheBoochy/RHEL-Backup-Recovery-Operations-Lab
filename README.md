# RHEL Backup and Recovery Operations Lab

## Overview

RHEL Backup and Recovery Operations Lab is a voluntary sysadmin portfolio project focused on basic Red Hat Enterprise Linux backup, restore and recovery verification tasks.

The lab is designed to practice backup planning, test data creation, archive creation, compressed backups, checksum verification, restore testing, backup scripting, scheduled backup review, log review and documentation.

Public documentation uses the name **Vulkan**.

---

## Scenario

A small organization stores important configuration and document files on a Red Hat Enterprise Linux server.

The goal of this lab is to create, verify and document a basic backup and recovery workflow using a structured sysadmin process.

The lab focuses on safe backup and restore testing in a controlled environment. It uses test data only and does not include real personal data, secrets or production files.

---

## Lab goals

The goals of this lab are to:

* Create a clean Red Hat-focused backup and recovery project.
* Verify the RHEL server baseline.
* Review backup target folders and available tools.
* Create safe test data for backup and restore testing.
* Create manual tar backups.
* Create compressed backup archives.
* Verify backup contents.
* Generate and verify checksums.
* Perform restore testing from backup.
* Create a reusable backup script.
* Review scheduled backup options with cron or systemd timer.
* Review backup logs and command output.
* Document recovery limitations and future improvements.
* Track work through Git and GitHub.

---

## Planned parts

| Part    | Topic                                      | Status   |
| ------- | ------------------------------------------ | -------- |
| Part 1  | Repository setup and planning              | Complete |
| Part 2  | RHEL baseline and backup target review     | Complete |
| Part 3  | Create test data and backup source folders | Complete |
| Part 4  | Manual tar backup                          | Complete |
| Part 5  | Compressed backup archive                  | Complete |
| Part 6  | Backup verification and checksums          | Planned  |
| Part 7  | Restore test from backup                   | Planned  |
| Part 8  | Backup script creation                     | Planned  |
| Part 9  | Scheduled backup review                    | Planned  |
| Part 10 | Backup logs and result documentation       | Planned  |
| Part 11 | Recovery reflection document               | Planned  |
| Part 12 | Final README and GitHub polish             | Planned  |

---

## Project structure

```text
RHEL-Backup-Recovery-Operations-Lab/
├── backups/
│   └── .gitkeep
├── docs/
│   └── .gitkeep
├── results/
│   └── .gitkeep
├── screenshots/
│   ├── .gitkeep
│   ├── screenshot-01-project-structure-and-git-status.png
│   ├── screenshot-02a-rhel-baseline-system.png
│   ├── screenshot-02b-rhel-baseline-resources-and-security.png
│   ├── screenshot-02c-rhel-backup-tool-availability.png
│   ├── screenshot-02d-rhel-backup-target-review.png
│   ├── screenshot-03a-rhel-backup-lab-folder-structure.png
│   ├── screenshot-03b-rhel-backup-test-file-content.png
│   ├── screenshot-04a-rhel-manual-tar-backup-created.png
│   ├── screenshot-04b-rhel-manual-tar-backup-contents.png
│   ├── screenshot-05a-rhel-compressed-backup-created.png
│   └── screenshot-05b-rhel-compressed-backup-contents.png
├── scripts/
│   └── .gitkeep
├── logbook.md
└── README.md
```

---

## Current progress

The project structure has been created and committed.

The RHEL server baseline has been reviewed, including hostname, operating system, current user, date and uptime information.

Resource and security checks were completed, including disk usage, memory usage, SELinux mode and firewalld status.

Backup tool availability was reviewed. The system has `tar`, `gzip` and `sha256sum` available, which are suitable for basic backup archive creation and checksum verification. The `rsync` command was not available on the system and is documented as an optional missing tool.

Scheduling options were reviewed. No user crontab was found, but systemd timers were available and listed.

Backup target locations were reviewed. No existing `/home/vulkan/backup-lab` folder was found before the lab structure was created. The `/tmp` and `/var/tmp` directories were also reviewed.

Safe backup test data was created under `/home/vulkan/backup-lab/source`. The test data includes lab configuration files, lab documents and a backup scope report. Supporting folders were also created for backups, restore testing and result output.

A manual tar backup archive was created from `/home/vulkan/backup-lab/source` and saved as `/home/vulkan/backup-lab/backups/manual-source-backup.tar`. The archive was verified with `ls`, `file` and `tar -tf`. The archive contents were also saved to a results file.

A compressed backup archive was created from `/home/vulkan/backup-lab/source` and saved as `/home/vulkan/backup-lab/backups/compressed-source-backup.tar.gz`. The compressed archive was verified with `ls`, `file` and `tar -tzf`. The compressed archive contents were also saved to a results file.

The next step is to verify backup integrity with checksums.

---

## Skills demonstrated

This project will demonstrate:

* Red Hat Enterprise Linux administration
* Backup planning
* Linux file and folder review
* Test data creation
* Archive creation with `tar`
* Compressed backups
* Backup content verification
* Checksum generation and validation
* Restore testing
* Backup scripting
* Scheduled task review with cron or systemd timer
* Log and result review
* Recovery documentation
* Markdown documentation
* Screenshot-based evidence collection
* Git and GitHub workflow

---

## Documentation and evidence

Main documentation files:

| File         | Purpose                            |
| ------------ | ---------------------------------- |
| `README.md`  | Main GitHub project overview       |
| `logbook.md` | Step-by-step project documentation |

Screenshot evidence is stored in the `screenshots/` folder.

The README links to screenshot files instead of displaying them inline, so the project overview stays clean while the detailed visual evidence remains available in the logbook and screenshots folder.

Current screenshot evidence:

| Screenshot                                                | Purpose                                             |
| --------------------------------------------------------- | --------------------------------------------------- |
| `screenshot-01-project-structure-and-git-status.png`      | Initial project structure and Git status            |
| `screenshot-02a-rhel-baseline-system.png`                 | RHEL baseline system information                    |
| `screenshot-02b-rhel-baseline-resources-and-security.png` | Disk, memory, SELinux and firewalld review          |
| `screenshot-02c-rhel-backup-tool-availability.png`        | Backup tool and scheduling availability             |
| `screenshot-02d-rhel-backup-target-review.png`            | Backup target and temporary folder review           |
| `screenshot-03a-rhel-backup-lab-folder-structure.png`     | Backup lab folder structure verification            |
| `screenshot-03b-rhel-backup-test-file-content.png`        | Backup test file content verification               |
| `screenshot-04a-rhel-manual-tar-backup-created.png`       | Manual tar archive creation and verification        |
| `screenshot-04b-rhel-manual-tar-backup-contents.png`      | Manual tar archive content verification             |
| `screenshot-05a-rhel-compressed-backup-created.png`       | Compressed tar.gz archive creation and verification |
| `screenshot-05b-rhel-compressed-backup-contents.png`      | Compressed archive content verification             |

Command results and verification output may be stored in:

```text
results/
```

Scripts may be stored in:

```text
scripts/
```

Small lab backup examples may be stored in:

```text
backups/
```

---

## Part 2 — RHEL baseline and backup target review

Status: Complete

This part reviewed the RHEL server baseline, available backup tools, scheduling options and possible backup target locations before creating test backup data.

Commands used:

```bash
hostnamectl
whoami
cat /etc/os-release
date
uptime

df -h
free -h
getenforce
sudo systemctl status firewalld --no-pager

tar --version
gzip --version
sha256sum --version
rsync --version
crontab -l 2>/dev/null || echo "No user crontab found"
systemctl list-timers --all --no-pager | head -20

pwd
ls -la ~
ls -ld ~/backup-lab 2>/dev/null || echo "No existing backup-lab folder found"
ls -ld /tmp
ls -ld /var/tmp
```

Results:

* The RHEL server baseline was reviewed.
* Disk usage and memory usage were reviewed.
* SELinux status was reviewed.
* firewalld status was reviewed.
* `tar` was available.
* `gzip` was available.
* `sha256sum` was available.
* `rsync` was not installed.
* No user crontab was found.
* systemd timers were available and listed.
* No existing `/home/vulkan/backup-lab` folder was found.
* `/tmp` and `/var/tmp` were available.

Notes:

The missing `rsync` command was documented as a limitation. The lab can continue using `tar`, `gzip` and `sha256sum`, which are available and sufficient for basic archive backup, compression and integrity verification.

The `backup-lab` folder did not already exist, which provided a clean starting point for creating test backup data in Part 3.

Screenshot links:

[screenshot-02a-rhel-baseline-system.png](screenshots/screenshot-02a-rhel-baseline-system.png)
[screenshot-02b-rhel-baseline-resources-and-security.png](screenshots/screenshot-02b-rhel-baseline-resources-and-security.png)
[screenshot-02c-rhel-backup-tool-availability.png](screenshots/screenshot-02c-rhel-backup-tool-availability.png)
[screenshot-02d-rhel-backup-target-review.png](screenshots/screenshot-02d-rhel-backup-target-review.png)
---

## Part 3 — Create test data and backup source folders

Status: Complete

This part created a safe backup lab folder structure and test data for future backup and restore operations.

The backup lab folder was created under `/home/vulkan/backup-lab`. Test source files were created under the `source` folder, and separate folders were prepared for backup archives, restore testing and result output.

Commands used:

```bash
mkdir -p ~/backup-lab/source/config
mkdir -p ~/backup-lab/source/documents
mkdir -p ~/backup-lab/source/reports
mkdir -p ~/backup-lab/backups
mkdir -p ~/backup-lab/restore-test
mkdir -p ~/backup-lab/results

cat > ~/backup-lab/source/config/app.conf <<'EOF'
# Lab application configuration
# This is safe test data for the RHEL Backup and Recovery Operations Lab.

app_name=backup-lab-demo
environment=lab
backup_required=true
owner=Vulkan
EOF

cat > ~/backup-lab/source/config/service.conf <<'EOF'
# Lab service configuration
# No real secrets are stored in this file.

service_name=example-service
service_port=8080
service_enabled=true
EOF

cat > ~/backup-lab/source/documents/operations-notes.txt <<'EOF'
RHEL Backup and Recovery Operations Lab

This document represents safe operational notes for backup testing.

No real business data, credentials, keys or personal data are included.
EOF

cat > ~/backup-lab/source/documents/recovery-plan.txt <<'EOF'
Basic Recovery Plan

1. Identify the latest valid backup.
2. Verify the backup checksum.
3. Extract the archive into a restore-test folder.
4. Compare restored files with expected contents.
5. Document recovery result.
EOF

cat > ~/backup-lab/source/reports/backup-scope.txt <<'EOF'
Backup Scope

Included:
- Lab configuration files
- Lab documents
- Lab reports

Excluded:
- Real credentials
- SSH keys
- Personal data
- Production files
EOF

tree ~/backup-lab 2>/dev/null || find ~/backup-lab -type f -o -type d

ls -lR ~/backup-lab
cat ~/backup-lab/source/config/app.conf
cat ~/backup-lab/source/documents/recovery-plan.txt
```

Results:

* Created `/home/vulkan/backup-lab`.
* Created source folders for configuration files, documents and reports.
* Created backup support folders for backup archives, restore testing and results.
* Created safe lab test files.
* Verified the folder structure.
* Verified file permissions and file contents.
* Confirmed that no real credentials, SSH keys, production files or personal data were used.

Notes:

The `tree` command was not required because the fallback `find` command successfully listed the backup lab structure.

All files created in this part are safe test data for the lab.

Screenshot links:

[screenshot-03a-rhel-backup-lab-folder-structure.png](screenshots/screenshot-03a-rhel-backup-lab-folder-structure.png)
[screenshot-03b-rhel-backup-test-file-content.png](screenshots/screenshot-03b-rhel-backup-test-file-content.png)
---

## Part 4 — Manual tar backup

Status: Complete

This part created a manual tar backup archive from the backup lab source folder.

The source folder was:

```text
/home/vulkan/backup-lab/source
```

The backup archive was saved as:

```text
/home/vulkan/backup-lab/backups/manual-source-backup.tar
```

Commands used:

```bash
ls -lR ~/backup-lab/source

cd ~/backup-lab
tar -cvf backups/manual-source-backup.tar source

ls -lh ~/backup-lab/backups
file ~/backup-lab/backups/manual-source-backup.tar

tar -tf ~/backup-lab/backups/manual-source-backup.tar

tar -tf ~/backup-lab/backups/manual-source-backup.tar > ~/backup-lab/results/manual-source-backup-contents.txt
cat ~/backup-lab/results/manual-source-backup-contents.txt
```

Results:

* Verified that the backup source folder existed.
* Created a manual tar archive named `manual-source-backup.tar`.
* Stored the archive in `/home/vulkan/backup-lab/backups`.
* Verified that the archive file existed.
* Verified the archive file type.
* Listed the archive contents without extracting it.
* Saved the archive content listing to `/home/vulkan/backup-lab/results/manual-source-backup-contents.txt`.

Notes:

This backup archive is not compressed. It is a basic tar archive used to demonstrate manual archive creation and content verification.

The archive contains the safe lab test data created in Part 3.

Screenshot links:

[screenshot-04a-rhel-manual-tar-backup-created.png](screenshots/screenshot-04a-rhel-manual-tar-backup-created.png)
[screenshot-04b-rhel-manual-tar-backup-contents.png](screenshots/screenshot-04b-rhel-manual-tar-backup-contents.png)
---

## Part 5 — Compressed backup archive

Status: Complete

This part created a compressed `tar.gz` backup archive from the backup lab source folder.

The source folder was:

```text
/home/vulkan/backup-lab/source
```

The compressed backup archive was saved as:

```text
/home/vulkan/backup-lab/backups/compressed-source-backup.tar.gz
```

Commands used:

```bash
ls -lR ~/backup-lab/source
ls -lh ~/backup-lab/backups

cd ~/backup-lab
tar -czvf backups/compressed-source-backup.tar.gz source

ls -lh ~/backup-lab/backups
file ~/backup-lab/backups/compressed-source-backup.tar.gz

tar -tzf ~/backup-lab/backups/compressed-source-backup.tar.gz

tar -tzf ~/backup-lab/backups/compressed-source-backup.tar.gz > ~/backup-lab/results/compressed-source-backup-contents.txt
cat ~/backup-lab/results/compressed-source-backup-contents.txt
```

Results:

* Verified that the backup source folder existed.
* Reviewed existing backup archives.
* Created a compressed archive named `compressed-source-backup.tar.gz`.
* Stored the archive in `/home/vulkan/backup-lab/backups`.
* Verified that the compressed archive file existed.
* Verified the archive file type.
* Listed the compressed archive contents without extracting it.
* Saved the compressed archive content listing to `/home/vulkan/backup-lab/results/compressed-source-backup-contents.txt`.

Notes:

This backup archive uses gzip compression through the `tar -z` option.

The compressed archive contains the same safe lab test data as the manual tar archive from Part 4, but stores it in a compressed `tar.gz` format.

Screenshot links:

[screenshot-05a-rhel-compressed-backup-created.png](screenshots/screenshot-05a-rhel-compressed-backup-created.png)
[screenshot-05b-rhel-compressed-backup-contents.png](screenshots/screenshot-05b-rhel-compressed-backup-contents.png)
---

## Notes

This is a lab environment and not a production system.

The project is created for learning, documentation and portfolio demonstration.

Only safe test data should be used in this lab.

No real personal data, passwords, SSH keys, tokens, production configuration files or sensitive business files should be included in screenshots, backup archives or public documentation.

Python's built-in tools, shell commands and standard Linux utilities may be used where appropriate, but the focus is on basic sysadmin backup and recovery workflow.

The `rsync` command was not available during the initial backup tool review. This is documented as a limitation, and the lab continues with available standard tools.
