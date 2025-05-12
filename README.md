# 🛡️ APT-420 - Red Team Scenario (Full Kill Chain)

## 🎯 Descrizione del Progetto

APT-420 è un'esercitazione pratica di **red teaming** che simula una catena di attacco realistica, suddivisa in due fasi, con l'obiettivo finale di ottenere privilegi massimi su un **Domain Controller Windows** partendo da una macchina **Linux esposta via web**.

Questa simulazione è stata documentata e realizzata sotto forma di **video suddiviso in due parti**, per permettere la visione passo-passo delle tecniche e degli strumenti impiegati.

Il penetration test report è allegato come documentazione del progetto.

⚠️ Tutte le attività sono state svolte in ambienti controllati e a fini educativi.

---

## 🎬 Video

### 🧷 Parte 1: Web & Linux Exploiting - Privilege Escalation su Ubuntu

[![Guarda su YouTube](https://img.youtube.com/vi/DWPYj6UDO2g/maxresdefault.jpg)](https://www.youtube.com/watch?v=DWPYj6UDO2g)

👉 In questa parte viene mostrata:
- Riconoscimento iniziale della superficie d'attacco
- Enumerazione di directory sensibili (`/dev`)
- Analisi del codice sorgente di un'app PHP
- Upload di web shell e RCE
- **Privilege Escalation via SUID su Python3**
- Accesso completo e persistenza come **root**

---

### 🧷 Parte 2: Network Pivoting & Windows Exploiting - Domain Controller Compromise

[![Guarda su YouTube](https://img.youtube.com/vi/pc4CM6xGF-4/maxresdefault.jpg)](https://www.youtube.com/watch?v=pc4CM6xGF-4)

👉 In questa parte viene mostrata:
- Accesso a share **SMB anonime**
- Recupero di **credenziali in chiaro**
- Uso di **CrackMapExec** e **smbclient**
- **Pivoting** verso rete interna
- Sfruttamento della vulnerabilità **noPac** (CVE-2021-42278, CVE-2021-42287)
- Escalation e persistenza come **Domain Admin**

---

## 🧰 Tecniche e Strumenti Utilizzati

| Categoria               | Tecnologie e Tool                                       |
|-------------------------|---------------------------------------------------------|
| 🖥️ Recon & Exploiting   | `nmap`, `dirb`, `smbclient`, `smbmap`, `evil-winrm`     |
| 🧠 PE Linux             | `python3 SUID`, `GTFOBins`                              |
| 🔄 Network Pivoting     | `chisel`, `proxychains`                                 |
| 🪟 PE Windows           | `crackmapexec`, `CVE-2021-42278`, `CVE-2021-42287`      |

---

## 📋 Vulnerabilità Identificate

| ID | Host         | Descrizione                                       | Rischio  |
|----|--------------|---------------------------------------------------|----------|
| 1  | 192.170.1.10 | Esposizione file di sviluppo                      | MEDIUM   |
| 2  | 192.170.1.10 | Vulnerabilità logica PHP con RCE                  | HIGH     |
| 3  | 192.170.1.10 | Privilege Escalation via SUID su Python3          | MEDIUM   |
| 4  | 10.10.10.9   | Accesso anonimo SMB + credenziali in chiaro       | HIGH     |
| 5  | 10.10.10.9   | PE tramite noPac (CVE-2021-42278 / 42287)         | HIGH     |

---

## 🧩 Ambiente di Test

- **Server Web**: Ubuntu (host 192.170.1.10)
- **Target interno**: Windows Server (host 10.10.10.9)
- **Dominio**: evil.corp
- **Struttura di rete simulata**: 10.10.10.0/24

---

## ✅ Conclusioni

Questo progetto dimostra un'intera **kill chain offensiva**, dall'accesso iniziale via web fino alla compromissione completa di un'intera rete Windows e di tutti i dispositivi associati.

Le tecniche impiegate coprono aspetti di:
- Exploiting Web
- Escalation di privilegi su Linux
- Movimento laterale/pivoting
- Compromissione di Active Directory
- Persistenza e escalation di privilegi su Windows

---

## 📜 Disclaimer

Questo progetto è stato realizzato esclusivamente a fini educativi e in ambiente controllato. Nessuna delle tecniche documentate deve essere utilizzata senza autorizzazione esplicita.

