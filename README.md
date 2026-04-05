# Lab-de-Troubleshooting-de-Rede-e-Servi-os
Este laboratório simula cenários reais de suporte técnico em ambientes Windows e Linux, abordando problemas comuns relacionados a:

Conectividade de rede
Serviços (Apache)
DNS
Firewall

O objetivo é diagnosticar e resolver falhas utilizando ferramentas de troubleshooting.

---

🖥️ Preparação do Ambiente
🔧 Configuração da Rede no VirtualBox

Ambas as máquinas configuradas com:

Adaptador 1: NAT

Adaptador 2: Rede Interna (lab-network)

![linux inicial](img/02-print-rede-virtualbox-linux.png)

![linux inicial](img/01-print-rede-virtualbox-win.png)

---

🐧 Configuração do Linux (Servidor)

ip a

sudo ip addr add 192.168.10.20/24 dev enp0s8

sudo ip link set enp0s8 up

![linux ip](img/03-print-ip-linux.png)

---

🪟 Configuração do Windows (Cliente)

ipconfig

![windows ip](img/04-print-ip-windows.png)

---

🔎 Teste de Conectividade

ping 192.168.10.20

✔ Comunicação funcionando

![ping ok](img/05-print-ping-ok.png)

---

💣 CENÁRIO 1 — Serviço Web Inativo

📌 Situação inicial (serviço funcionando)

 systemctl status apache2

![apache rodando](img/06-print-apache-rodando.png)

---

🌐 Teste no navegador

✔ Site funcionando

![site ok](img/07-print-site-ok.png)

---

💣 Falha simulada

sudo systemctl stop apache2

![apache parado](img/08-print-apache-parado.png)

---

🌐 Teste após falha

❌ Site fora do ar

![apache parado](img/09-print-site-down.png)

---

🔎 Teste de conectividade

ping 192.168.10.20

✔ Funciona

![conectividade ping](img/10-print-ping-ok-servico-off.png)

---

🔎 DIAGNÓSTICO

Verificação da porta

sudo ss -tuln

![porta ](img/13-print-porta-80-fechada.png)

---

Verificação do serviço

systemctl status apache2

![apache inativo](img/14-print-apache-inativo.png)

---

🧠 Diagnóstico

A conectividade com o servidor estava funcional, porém o serviço web não estava em execução, impedindo o acesso ao sistema.

---

🔧 Solução

sudo systemctl start apache2


![site restaurado](img/15-print-site-restaurado.png)














































































