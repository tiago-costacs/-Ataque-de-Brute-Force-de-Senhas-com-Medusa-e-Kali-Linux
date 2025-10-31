# Relatório Técnico — Ataques de Força Bruta com Medusa

## 1. Sumário executivo
Laboratório realizado em ambiente controlado para demonstrar técnicas de força bruta (Medusa) e mapeamento de serviços (Nmap). Testes foram conduzidos contra FTP, formulário web (DVWA) e SMB. Credenciais fracas foram identificadas em ambiente de teste; recomendações de mitigação foram propostas.

---

## 2. Objetivos
- Demonstrar ataques de força bruta em serviços FTP e SMB usando Medusa.  
- Demonstrar automação contra formulário web (DVWA) via `http-post` (exemplo).  
- Mapear portas e serviços com Nmap (TCP/UDP) e identificar SO.  
- Documentar procedimentos, resultados e recomendações.

---

## 3. Ambiente de teste
- Atacante: Kali Linux (versão: <KALI_VERSION>)  
- Alvo: Metasploitable 2 / DVWA (versão: padrão do lab)  
- Ferramentas: Medusa (versão: <MEDUSA_VERSION>), Nmap (versão: <NMAP_VERSION>), smbclient  
- Rede: VirtualBox — Host-Only/Internal  
- IPs: todos substituídos por placeholders no repositório público (`<TARGET_IP>`)

---

## 4. Wordlists utilizadas
- `wordlists/small-users.txt`: lista de usuários de exemplo.  
- `wordlists/small-pass.txt`: lista de senhas de exemplo (para demonstração).  
> Observação: listas reduzidas apenas para demonstração; auditorias reais exigem wordlists apropriadas e autorização.

---

## 5. Comandos executados (resumo)
> Substitua `<TARGET_IP>` e `<PORTA>` pelos valores do seu laboratório.

### 5.1 Conectividade
```bash
ping -c 4 <TARGET_IP>


