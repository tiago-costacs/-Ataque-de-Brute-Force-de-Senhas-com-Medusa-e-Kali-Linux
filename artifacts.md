## 6. Validação de acessos e evidências
- FTP: `screenshots/ftp_login_success.png` e `artifacts/medusa-ftp-output.txt`.
- SMB: `artifacts/medusa-smb-output.txt` e comando `smbclient` (print em `screenshots/smb_client.png`).
- Web: captura do POST em `screenshots/dvwa_post_capture.png`.


## 7. Análise de risco e impacto
- Serviços expostos com credenciais fracas permitem acesso não autorizado.
- Em ambiente real, acesso a SMB pode permitir movimentação lateral e exfiltração de dados.
- Risco alto se contas privilegiadas usarem senhas fracas.


## 8. Recomendações de mitigação
1. Implementar bloqueio temporário ou delay após N tentativas falhas.
2. Forçar políticas de senha fortes e expiração periódica.
3. Implementar autenticação multifator (MFA) para acessos críticos.
4. Limitar exposição de serviços ao público; usar VPN/segmentação de rede.
5. Monitoramento e alertas para padrões anômalos de autenticação.


## 9. Conclusão
O teste demonstrou que credenciais fracas facilitam acesso por força bruta. Medidas técnicas e políticas simples reduzem significativamente o risco.


## 10. Apêndices
- Comandos completos usados (ver `commands.sh`).
- Logs completos: `artifacts.md'.
- Screenshots em `screenshots/`.
