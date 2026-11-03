Home Lab

A free, home-built SOC lab for hands-on threat detection, incident response, and vulnerability management practice. Built on Proxmox, with Wazuh as the SIEM, pfSense as the lab firewall, and a Windows endpoint for detection testing.

Status: In progress — infrastructure is being updated and maintained. Lab VMs are outlined below; detections are added only after they are actually tested. Nothing here is claimed as completed until it has been run.
Last updated: November 3, 2026

Architecture
Host: Dell OptiPlex 7040, 32 GB RAM, Proxmox VE
Proxmox was checked on November 3, 2026: VE 8.2, pve-manager 8.2.2. The enterprise repository was found enabled without a subscription, and the no-subscription repository was added as the fix.

Lab firewall: pfSense CE, 2 GB RAM
Confirmed up to date on November 3, 2026 via the console update check.
Syslog to Wazuh on UDP 514, scoped to the pfSense host.

SIEM: Wazuh all-in-one, 4 vCPU, 12 GB RAM, 120 GB disk, Ubuntu Server 24.04 LTS
Dashboard, indexer, and manager in a single VM.

Windows endpoint: Windows Server evaluation VM, ~8 GB RAM
Wazuh agent installed, Sysmon configured with a maintained Sysmon configuration.

Attack / test VM: Kali Linux, ~4 GB RAM
Run only during tests, snapshot first, then shut down. RAM on the 7040 is tight at 32 GB, so Kali does not run 24/7.

Other lab machines (not lab hosts):
HP ProDesk — left as a separate AI PC, not a lab host.
Dell OptiPlex 990 storage server — enrolled as a native Wazuh host agent and log source, not containerized.
Lenovo Yoga — dashboard / thin client only.
Dell 14 Slim — Python SOC-automation scripts and remote dashboard access.

What this lab is for
Monitoring endpoints and network logs in Wazuh.
Investigating alerts to root cause, using Sysmon and Windows event logs.
Testing detections with Atomic Red Team, mapped to MITRE ATT&CK.
Writing and tuning detection rules, and documenting what fired, what did not, and why.
Practicing incident response playbooks and runbooks in a safe, isolated lab — never on a production or employer network.

Labs
Lab
Objective
Tools
Status
01 — Wazuh SOC setup
Install Wazuh all-in-one, enroll Windows and Linux agents, confirm logs flowing
Proxmox, Wazuh, Sysmon
Planned
02 — pfSense logging
Send pfSense syslog to Wazuh, confirm firewall logs are searchable
pfSense, Wazuh
Planned
03 — Sysmon detection
Test a Sysmon-based detection, record the rule and the result
Windows Server, Sysmon, Wazuh
Planned
04 — Atomic Red Team test
Run a mapped ATT&CK technique in a controlled test, record detection / tuning
Kali, Atomic Red Team, Wazuh
Planned
Add a row only when a lab has actually been run. Do not mark a detection as fired until it has fired in this lab.

Detections
MITRE ATT&CK technique
Detection / rule
Fired?
Notes / tuning
Example only — replace with a real test
Rule name
No
What was observed

Skills practiced
SIEM monitoring and alert triage (Wazuh)
Incident investigation and forensic root-cause analysis
Sysmon and Windows event log analysis
pfSense firewall administration and log management
MITRE ATT&CK mapping
Detection tuning and documentation
Proxmox virtualization and Linux administration

Changelog
2026-11-03: Kali Linux updated — archive GPG key fixed, package index refreshed, full upgrade run, console and locale fixed to UTF-8 / en_US.UTF-8. pfSense confirmed up to date. Proxmox repository corrected to no-subscription.
2026-11-02: Lab outline created — Wazuh, pfSense, Windows Server, Kali, and Atomic Red Team on the OptiPlex 7040.
