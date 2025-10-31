Arquivo com explicações curtas e diretas sobre cada comando que usei.


## Ping — testar se host responde
`ping -c 4 <IP>`
- Envia 4 pacotes ICMP. Confirma conectividade e mede latência.


---


## FTP — checar serviço
`ftp <IP>`
- Abre cliente FTP interativo. Verifica se o serviço FTP responde na porta 21.


---


## Criar wordlist de usuários
`echo -e "user
msfadmin
admin
root" > user.txt`
- Cria arquivo `user.txt` com usuários, uma entrada por linha. Use aspas normais.


---


## Criar wordlist de senhas (password spraying)
`echo -e "password
123456
welcome
msfadmin" > senhas_spray.txt`
- Cria arquivo de senhas comuns. Útil para password spraying (tentar poucas senhas em muitos usuários).


---


## Medusa — brute force / password spray (exemplo básico)
`medusa -h <IP> -U users.txt -P senhas_spray.txt -M <serviço> -t 10`
-h <TARGET_IP>: alvo.

-U users.txt: arquivo com lista de usuários.

-P senhas_spray.txt: arquivo com lista de senhas.

-M <serviço>: módulo/protocolo (ftp, smbnt, http-post, etc.).

-t 10: threads (tentativas simultâneas). Ajuste conforme CPU/rede.

**Exemplo SMB:**
`medusa -h 192.168.56.110 -U smb_users.txt -P senhas_spray.txt -M smbnt -t 10`


---


## smbclient — listar compartilhamentos SMB
`smbclient -L //<IP> -U msfadmin`
- Lista compartilhamentos e informações. Use `-U user%password` para testar login inline (não recomendado para logs públicos).


---


## Nmap — varredura UDP
`sudo nmap -v -sU -p <portas> <IP>`
- `-sU` scan UDP; `-v` verbose; `-p` portas (ex.: `-p 53,123` ou `-p-` para todas).
- UDP é lento e suscetível a falso-negativo.


---
## Nmap — ignorar descoberta de host e mostrar só portas abertas

sudo nmap -v -T5 -sS -Pn --open <TARGET_IP>

-Pn: pula a etapa de discovery/ping (assume host ativo).

--open: exibe apenas portas abertas.

Útil quando ICMP/ping está bloqueado mas você sabe que host existe.

