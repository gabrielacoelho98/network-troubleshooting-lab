#  Lab de Troubleshooting de Rede e Serviços

Projeto prático de troubleshooting voltado à simulação de falhas comuns em ambientes de suporte técnico, abordando diagnóstico e resolução de problemas relacionados a conectividade de rede, serviços web, DNS e firewall em sistemas Windows e Linux.


---

##  Objetivo

Simular cenários reais de falhas operacionais encontradas em rotinas de suporte técnico e infraestrutura, aplicando procedimentos de diagnóstico e correção de problemas em serviços e conectividade.

---

##  Tecnologias Utilizadas

- Oracle VirtualBox  
- Windows  
- Ubuntu Linux  
- Apache2  
- UFW Firewall  
- Ferramentas nativas de diagnóstico de rede  

---

##  Estrutura do Ambiente

O laboratório foi desenvolvido com duas máquinas virtuais interligadas por rede interna para simulação de comunicação cliente-servidor.

- **Cliente:** Windows  
- **Servidor:** Ubuntu Linux  
- **Rede Virtual:** `lab-network`  
- **Serviço Web:** Apache2  

---

## ⚙️ Configuração do Ambiente

### Rede Virtual no VirtualBox
- Adaptador 1: NAT  
- Adaptador 2: Rede Interna (`lab-network`)  

![Rede Linux](img/02-print-rede-virtualbox-linux.png)

![Rede Windows](img/01-print-rede-virtualbox-win.png)

---

### Configuração do Servidor Linux
![IP Linux](img/03-print-ip-linux.png)

---

### Configuração do Cliente Windows
![IP Windows](img/04-print-ip-windows.png)

---

### Teste Inicial de Conectividade
![Ping Inicial](img/05-print-ping-ok.png)

---

##  Cenários de Troubleshooting

###  Cenário 1 — Serviço Web Inativo

 Simulação de falha do serviço Apache para análise de indisponibilidade de aplicação.

### Situação Inicial

 Serviço web em funcionamento e aplicação acessível via navegador.

#### Serviço em Execução
![Apache Rodando](img/06-print-apache-rodando.png)

#### Aplicação Disponível
![Site Online](img/07-print-site-ok.png)

---

#### Falha Simulada

O serviço Apache foi interrompido manualmente.

![Apache Parado](img/08-print-apache-parado.png)

---

### Sintomas Observados

Aplicação indisponível no navegador

Erro de acesso ao site


![Site Offline](img/09-print-site-down.png)

---

#### Análise e Evidências

Apesar da falha no acesso ao site:

O servidor ainda respondia na rede
Não havia perda de conectividade

![Ping Serviço Off](img/10-print-ping-ok-servico-off.png)

#### Verificação de porta:
![Porta 80 Fechada](img/13-print-porta-80-fechada.png)

#### Status do Serviço
![Apache Inativo](img/14-print-apache-inativo.png)

---

####  Diagnóstico:
A conectividade com o servidor permanecia funcional, porém o serviço Apache encontrava-se inativo, impedindo a entrega da aplicação web.

---

#### Solução

Reinicialização do serviço Apache no servidor.

#### Resultado Após Correção
![Site Restaurado](img/15-print-site-restaurado.png)

---

###  Cenário 2 — Falha de DNS

Simulação de erro de resolução de nomes causado por configuração incorreta de DNS.

---
### Situação Inicial

Ambiente com conectividade ativa, porém com falha ao acessar serviços por nome de domínio.

---
### Falha Simulada

Configuração manual de um servidor DNS inválido no cliente.

#### DNS Incorreto
![DNS Errado](img/16-print-dns-errado.png)

---
### Sintomas Observados
Falha ao realizar requisições por nome (ex: google.com) 

Erro ao utilizar ping com domínio

#### Ping Google Falha
![Ping Google Falha](img/17-print-ping-google-falha.png)

---

### Análise e Evidências

Teste direto com IP:

Comunicação com a internet funcionando

Problema isolado na resolução de nomes

#### Teste via IP
![Ping IP OK](img/18-print-ping-ip-ok.png)

---

### Diagnóstico: 
A conectividade com a internet permanecia operacional, porém a resolução de nomes falhava devido à configuração incorreta do servidor DNS.

---

### Solução

Correção do endereço do servidor DNS para um DNS válido.

---

#### Resultado Após Correção

A resolução de nomes foi restabelecida com sucesso.

![DNS Corrigido](img/19-print-dns-corrigido.png)

---

###  Cenário 3 — Firewall Bloqueando Serviço

### Situação Inicial

Servidor com serviço web ativo, porém com restrição de acesso configurada no firewall.

---

### Falha Simulada

Aplicação de regra no firewall bloqueando a porta 80 (HTTP).

#### Bloqueio Configurado
![Firewall Bloqueio](img/20-print-firewall-bloqueio.png)

---

Sintomas Observados

- Aplicação web indisponível no navegador

- Falha ao acessar o serviço HTTP

---

### Análise e Evidências

Teste de conectividade:

- Servidor respondendo normalmente na rede

- Comunicação via ping funcionando

#### Ping Firewall
![Ping Firewall](img/21-print-ping-ok-firewall.png)

Interpretação:

- Rede operacional

- Serviço aparentemente ativo

- Indício de bloqueio em camada de firewall

### Diagnóstico: 
O servidor permanecia acessível via rede, porém o firewall bloqueava a porta 80, impedindo acesso ao serviço web.

---

### Solução

Ajuste na regra do firewall para permitir conexões na porta 80 (HTTP).

---

#### Resultado Após Correção
![Firewall Corrigido](img/22-print-firewall-corrigido.png)

---

##  Conhecimentos Aplicados

- Troubleshooting de Serviços  
- Diagnóstico de DNS  
- Gerenciamento de Firewall  
- Análise de Portas e Serviços  
- Troubleshooting de Infraestrutura  
- Diagnóstico de Rede Cliente/Servidor  



##  Resultado

Ao final do laboratório foi possível identificar, diagnosticar e corrigir múltiplos cenários de falha relacionados a serviços, DNS, firewall e conectividade, reforçando conhecimentos práticos aplicáveis em rotinas de suporte técnico, help desk e infraestrutura de TI.
