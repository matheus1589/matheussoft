# Configuração de Envio de E-mails - INLOG

## Status da Integração

✅ **Código implementado e pronto para uso**
✅ **Pacote Resend instalado**
✅ **Variável de ambiente RESEND_API_KEY configurada**

## Como Funciona

O sistema está configurado para enviar e-mails automáticos de follow-up das viagens usando o serviço **Resend**.

### Modo de Teste (Padrão)

Por padrão, o sistema usa `onboarding@resend.dev` como remetente, que funciona sem necessidade de verificar domínio. Os e-mails serão enviados assim que você testar o disparo automático.

### Modo de Produção (Recomendado)

Para usar seu próprio domínio (ex: `noreply@inlog.com.br`):

1. **Acesse o Resend**: https://resend.com
2. **Crie uma conta** (se ainda não tiver)
3. **Obtenha sua API Key**:
   - Acesse o dashboard do Resend
   - Vá em "API Keys"
   - Crie uma nova chave (ou use a existente)
   - Copie a chave (começa com `re_...`)

4. **Configure o domínio**:
   - No dashboard do Resend, vá em "Domains"
   - Adicione seu domínio (ex: `inlog.com.br`)
   - Configure os registros DNS conforme indicado
   - Aguarde a verificação (pode levar alguns minutos)

5. **Atualize a variável de ambiente**:
   - Adicione `RESEND_FROM_EMAIL=INLOG <noreply@inlog.com.br>`
   - Certifique-se de que `RESEND_API_KEY` está configurada com sua chave

## Testando o Envio

Para testar se está funcionando:

1. Acesse o painel admin (`/admin`)
2. Faça login com suas credenciais
3. Clique em "Disparar Follow-Up por E-mail"
4. Selecione um cliente
5. Clique em "Enviar E-mails"
6. Verifique a caixa de entrada do e-mail cadastrado no cliente

## Estrutura do E-mail

Os e-mails automáticos incluem:

- ✉️ Cabeçalho com logo INLOG
- 📋 Dados completos da viagem (CRT, origem, destino, motorista, exportador)
- 📍 Histórico completo de rastreamento com timestamps
- 🎨 Design profissional responsivo
- 🔒 Assinatura automática da INLOG

## Troubleshooting

### E-mail não está sendo enviado

1. **Verifique a API Key**: Certifique-se de que `RESEND_API_KEY` está configurada
2. **Verifique o domínio**: Se usar domínio próprio, ele deve estar verificado no Resend
3. **Verifique o console**: Abra o console do navegador (F12) para ver logs de erro
4. **Teste com onboarding@resend.dev**: Use o remetente padrão para garantir que a API está funcionando

### E-mail vai para spam

- Configure SPF, DKIM e DMARC no seu domínio
- Use um domínio verificado no Resend
- Evite palavras que acionam filtros de spam no assunto

### Limite de envios

- Conta gratuita do Resend: 100 e-mails/dia
- Conta paga: volumes maiores conforme o plano

## Suporte

Para problemas com o Resend, consulte: https://resend.com/docs
