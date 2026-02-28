# 02 - Instalação do Serviço FTP (vsftpd)

## Objetivo

Este documento tem a finalidade de instruir tecnicamente a instalação do serviço FTP no Linux.

Será utilizado o serviço **vsftpd (Very Secure FTP Daemon)**, um servidor FTP leve, estável e com foco em segurança.  
Ele é amplamente utilizado em distribuições Linux e possui suporte a autenticação local, controle de permissões, modo passivo e integração com mecanismos de segurança como PAM e SELinux.

---

## 1. Pré-requisitos

- Sistema Linux com acesso root ou privilégios sudo
- Repositórios configurados e funcionando
- Conectividade com a internet para instalação do pacote


## 2. Instalação do pacote vsftpd

O comando de instalação depende da distribuição utilizada.

### Distribuições baseadas em Debian (Ubuntu, Debian)

```bash
sudo apt update
sudo apt install vsftpd -y

Distribuições baseadas em Red Hat (Rocky Linux, AlmaLinux, CentOS)
sudo dnf install vsftpd -y
