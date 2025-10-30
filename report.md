---


## 2) report.md (preenchido com exemplos de saída)


```markdown
# Relatório Técnico — Ataques de Força Bruta com Medusa


## 1. Sumário executivo
Laboratório realizado em ambiente controlado (VirtualBox, rede Host-Only). Foram executados testes de força bruta contra FTP, formulário web (DVWA) e SMB usando Medusa. Foram obtidas credenciais válidas em FTP e confirmações de tentativas em SMB. Recomenda-se bloqueio por tentativas, MFA e políticas de senha fortes.


## 2. Escopo e autorização
- Alvo: Metasploitable 2 (DVWA disponível)
- Atacante: Kali Linux
- Rede: VirtualBox — Host-Only
- Autorização: Projeto acadêmico D.I.L.L. — Tiago Costa — Data: <DATA>


## 3. Ambiente
- Kali Linux: versão X.Y
- Metasploitable 2: versão standard
- Medusa: versão X.Y
- IP atacante: 192.168.56.100
- IP alvo: <TARGET_IP>


## 4. Wordlists usadas
- `wordlists/small-users.txt` (ex.: msfadmin, admin, user, root, www-data)
- `wordlists/small-pass.txt` (ex.: password, admin, 123456, msfadmin, toor)


## 5. Execução dos testes
> Todos os comandos foram executados a partir do Kali. Os outputs foram salvos em `artifacts/`.


### 5.1 FTP — Força bruta (usuário único)
**Comando:**
