# 🛡️ Auditoria de Força Bruta e Password Spraying com Medusa

![Cybersecurity](https://img.shields.io/badge/Security-Pentesting-red)
![Kali Linux](https://img.shields.io/badge/OS-Kali%20Linux-blue)
![Target](https://img.shields.io/badge/Environment-Metasploitable%202%20%7C%20DVWA-orange)

Projeto prático desenvolvido para simular e documentar testes de autenticação (**Brute Force** e **Password Spraying**) utilizando a ferramenta **Medusa** contra alvos em ambiente controlado e isolado (**Metasploitable 2** e **DVWA**), integrando análise de vulnerabilidades e medidas defensivas de mitigação.

---

## 📋 Cenários Avaliados

| Cenário | Serviço / Alvo | Vetor de Teste | Credencial Identificada |
|---|---|---|---|
| **1. FTP Service** | Porta 21 (vsftpd) | Ataque de força bruta cruzada (User x Password) | `msfadmin:msfadmin` |
| **2. Password Spraying** | Porta 445 (SMB) | Pulverização de uma senha comum contra múltiplos usuários | `msfadmin:msfadmin` |
| **3. Web Form** | HTTP (DVWA) | Automação de POST contra formulário de login | `admin:password` |

---

## ⚙️ Topologia do Laboratório

* **Hypervisor:** Oracle VirtualBox
* **Rede:** Host-Only (`192.168.56.0/24`) isolada sem conexão externa
* **Máquina Atacante:** Kali Linux (`192.168.56.10`)
* **Máquina Alvo:** Metasploitable 2 (`192.168.56.20`)

---

## 🚀 Execução dos Cenários

### 1. Força Bruta em Serviço FTP
Ataque multithread direcionado ao daemon `vsftpd`:
```bash
medusa -h 192.168.56.20 -U wordlists/users.txt -P wordlists/passwords.txt -M ftp -t 5
