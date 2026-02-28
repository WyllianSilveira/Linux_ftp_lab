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
````

### Distribuições baseadas em Red Hat (Rocky Linux, AlmaLinux, CentOS)
```bash
sudo dnf install vsftpd -y
````
### Em versões mais antigas:
```bash
sudo yum install vsftpd -y
````

### 3. Verificação da instalação

Após a instalação, é importante confirmar que o pacote foi instalado corretamente.

Em sistemas baseados em Red Hat:
```bash
rpm -qa | grep vsftpd
````
Em sistemas baseados em Debian:
````bash
dpkg -l | grep vsftpd
````
Se o pacote estiver instalado, ele aparecerá listado no resultado do comando.

Saída obtida no laboratório:
```bash
vsftpd-3.0.5-6.el9_7.2.x86_64
````

### 4. Habilitando e iniciando o serviço

Após a instalação, o serviço precisa ser habilitado e iniciado.
```bash
sudo systemctl enable vsftpd
sudo systemctl start vsftpd
````
Explicação dos comandos

systemctl enable vsftpd
Configura o serviço para iniciar automaticamente junto com o sistema operacional (boot).
Esse comando cria os links simbólicos necessários dentro do systemd para que o daemon seja carregado sempre que o servidor for reiniciado.

systemctl start vsftpd
Inicia o serviço imediatamente, na sessão atual, sem necessidade de reinicializar o sistema.
Esse comando é pontual e não garante que o serviço subirá automaticamente no próximo boot, caso o enable não tenha sido executado.

Verificar status do serviço
````bash
systemctl status vsftpd
````
Saída obtida no laboratório:
```bash
 vsftpd.service - Vsftpd ftp daemon
     Loaded: loaded (/usr/lib/systemd/system/vsftpd.service; enabled; preset: disabled)
     Active: active (running) since Fri 2026-02-27 20:37:37 -03; 1h 3min ago
    Process: 924 ExecStart=/usr/sbin/vsftpd /etc/vsftpd/vsftpd.conf (code=exited, status=0/SUCCESS)
   Main PID: 926 (vsftpd)
      Tasks: 1 (limit: 11061)
     Memory: 928.0K
        CPU: 30ms
     CGroup: /system.slice/vsftpd.service
             └─926 /usr/sbin/vsftpd /etc/vsftpd/vsftpd.conf

Feb 27 20:37:37 VMLINUX systemd[1]: Starting Vsftpd ftp daemon...
Feb 27 20:37:37 VMLINUX systemd[1]: Started Vsftpd ftp daemon.
````

Isso indica que o daemon está em execução e operando corretamente.
