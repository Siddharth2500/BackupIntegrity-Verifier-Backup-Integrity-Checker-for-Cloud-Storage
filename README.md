# 🚀 BackupIntegrity-Verifier - Backup Integrity Checker for Cloud Storage

![Python](https://img.shields.io/badge/Python-3.10%2B-blue.svg?logo=python&logoColor=white)  
![Tool](https://img.shields.io/badge/Backup-Verifier-FF5252.svg?logo=database)  
![Features](https://img.shields.io/badge/Features-Checksum%20&%20Staleness-4CAF50.svg?logo=check-circle)  
![Reports](https://img.shields.io/badge/Reports-JSON-2196F3.svg?logo=json)  
![CI/CD](https://img.shields.io/badge/CI/CD-Ready-2088FF.svg?logo=githubactions)  
![Dependencies](https://img.shields.io/badge/Dependencies-None-green.svg?logo=python)
-----
**BackupIntegrity-Verifier** is a **Python 3** tool built for DevOps and cloud storage teams to simulate and audit backup file integrity. It checks backup files for size consistency, hash mismatches, missing files, and staleness (files older than a configured threshold) — then generates a JSON report summarizing the health of your backup fleet.

## 🛠 Tech & Languages

| Layer          | Tech / Format                | Purpose                                     |
|-----------------|-----------------------------|---------------------------------------------|
| Language         | **Python 3.10+**           | Core codebase                               |
| Core Logic       | JSON reading + File I/O + Hashing | Inventory load, hash/size checks, staleness |
| Reports          | **JSON**                   | Machine-readable summary of audit results   |
| Execution        | Script / Colab / Notebook  | Flexible runtime for testing or production  |
| Logging          | Console output + JSON file | Real-time feedback and persisted audit      |

---

## 🌐 Architecture

Flow:  
1. Step 1 – Load `backup_inventory.json` containing metadata of backup files (filename, size, hash, creation date).  
2. Step 2 – For each backup:
   - Check if file exists  
   - Compare actual size vs recorded size  
   - Recompute hash and compare vs recorded hash  
   - Check if file age exceeds the staleness threshold  
3. Step 3 – Build `backup_integrity_report.json` summarizing:
   - total backups  
   - healthy count  
   - unhealthy count  
   - list of failures (filename + issues)  
4. The JSON report can then be consumed by dashboards, CI/CD pipelines, or alert systems.

---

## ▶️ Run BackupIntegrity-Verifier

```bash
python backup_integrity_verifier.py --inventory data/backup_inventory.json --report data/backup_integrity_report.json --dir backups/
