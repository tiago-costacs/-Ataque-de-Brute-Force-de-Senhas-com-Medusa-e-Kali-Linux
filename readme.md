# Projeto: Ataques de Força Bruta com Kali + Medusa (Ambiente Controlado)




Escopo: Metasploitable2 (VM em VirtualBox), rede Host-Only, IPs internal — testes realizados apenas neste ambiente controlado. 
Limitações: Testes realizados somente nas máquinas citadas e em rede isolada; nenhum teste foi executado em sistemas em produção ou em redes públicas.

Projeto: Ataques de Força Bruta com Kali + Medusa (Ambiente Controlado)


Resumo rápido: laboratório com duas VMs (Kali e Metasploitable/DVWA). Ataques de força bruta em FTP, formulário web (DVWA) e password spraying em SMB usando Medusa. Documentação com comandos, wordlists de exemplo, logs e recomendações de mitigação.


## Conteúdo do repositório
- `report.md` — relatório técnico detalhado (passo a passo).
- `commands.sh` — script com os comandos usados (exemplos).
- `wordlists/` — listas de usuários e senhas de demonstração.
- `screenshots/` — evidências (prints).
- `artifacts/` — logs e saídas do Medusa.


## Aviso legal
Este repositório contém material destinado a ambientes controlados e para fins educativos. Não execute estes comandos em sistemas sem autorização.


## Sumário
1. Objetivo
2. Preparação do ambiente
3. Comandos usados
4. Validação e evidências
5. Recomendações de mitigação
6. Como reproduzir

 Verifica se o host está ativo.



