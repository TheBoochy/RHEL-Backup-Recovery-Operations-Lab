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
| Part 3  | Create test data and backup source folders | Planned  |
| Part 4  | Manual tar backup                          | Planned  |
| Part 5  | Compressed backup archive                  | Planned  |
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
│   └── screenshot-02d-rhel-backup-target-review.png
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

Backup target locations were reviewed. No existing `/home/vulkan/backup-lab` folder was found, which means the lab backup folder can be created cleanly in the next part. The `/tmp` and `/var/tmp` directories were also reviewed.

The next step is to create safe test data and backup source folders under `/home/vulkan/backup-lab`.

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

Screenshot evidence is stored in:

```text
screenshots/
```

Current screenshot evidence:

| Screenshot                                                | Purpose                                    |
| --------------------------------------------------------- | ------------------------------------------ |
| `screenshot-01-project-structure-and-git-status.png`      | Initial project structure and Git status   |
| `screenshot-02a-rhel-baseline-system.png`                 | RHEL baseline system information           |
| `screenshot-02b-rhel-baseline-resources-and-security.png` | Disk, memory, SELinux and firewalld review |
| `screenshot-02c-rhel-backup-tool-availability.png`        | Backup tool and scheduling availability    |
| `screenshot-02d-rhel-backup-target-review.png`            | Backup target and temporary folder review  |

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

The `backup-lab` folder did not already exist, which provides a clean starting point for creating test backup data in Part 3.

Screenshots:

```text
screenshots/screenshot-02a-rhel-baseline-system.png
screenshots/screenshot-02b-rhel-baseline-resources-and-security.png
screenshots/screenshot-02c-rhel-backup-tool-availability.png
screenshots/screenshot-02d-rhel-backup-target-review.png
```

---

## Notes

This is a lab environment and not a production system.

The project is created for learning, documentation and portfolio demonstration.

Only safe test data should be used in this lab.

No real personal data, passwords, SSH keys, tokens, production configuration files or sensitive business files should be included in screenshots, backup archives or public documentation.

Python's built-in tools, shell commands and standard Linux utilities may be used where appropriate, but the focus is on basic sysadmin backup and recovery workflow.

The `rsync` command was not available during the initial backup tool review. This is documented as a limitation, and the lab continues with available standard tools.
