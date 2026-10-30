---
name: fechar-dia
description: Fecha o dia de trabalho no site do Dr. Paulo Nakashima. Registra o handoff do dia em handoffs/AAAA-MM-DD.md, consolida decisões em handoffs/DECISOES.md e pendências em handoffs/PENDENCIAS.md, confere que o número do WhatsApp não vai para o repositório, faz commit e push para o GitHub (repo site-nakashima). Use quando o usuário disser "fechar dia", "encerrar", "salvar e subir".
---

# Fechar o dia

Mínimo obrigatório: **handoff do dia + decisões consolidadas + commit + push.**

## Passos

1. **Levantar o que mudou**
   - `git status --short` e `git diff --stat`.
   - Data do último handoff e `git log --oneline <desde o último handoff>`.
   - Releia a conversa da sessão: o que foi pedido, feito, decidido e deixado para depois.

2. **Escrever o handoff do dia** em `handoffs/AAAA-MM-DD.md` (data de hoje; se já existir, acrescente uma seção `## Sessão 2`, `## Sessão 3`...):

   ```markdown
   # Handoff · AAAA-MM-DD

   ## Feito
   - <entregas concretas, com arquivos>

   ## Decisões tomadas hoje
   - <decisão> · motivo: <por quê>

   ## Pendências abertas / atualizadas
   - [alta|média|baixa] <item> · <contexto mínimo para retomar>

   ## Próximo passo sugerido
   <uma frase>
   ```

3. **Consolidar decisões** em `handoffs/DECISOES.md`:
   - Acrescente as decisões novas na seção do tema certo (Conteúdo, Design, Infra/Git, Publicação...), com a data entre parênteses.
   - Se uma decisão substitui outra, risque a antiga (`~~texto~~`) e indique "substituída em AAAA-MM-DD". Não apague histórico.

4. **Atualizar pendências** em `handoffs/PENDENCIAS.md`:
   - Marque concluídas como `- [x]` e mova para "Concluídas" com a data.
   - Acrescente as novas como `- [ ]` com prioridade.

5. **Checar o número do WhatsApp antes do commit** (sem exibir o número):
   - `git config nakashima.whatsapp >/dev/null || echo "FILTRO NÃO CONFIGURADO: pare e avise o usuário"`.
   - Confirme que nenhum `.md` novo contém o número. O hook `pre-commit` também bloqueia, mas não dependa só dele.
   - Se o hook bloquear, corrija o arquivo apontado. **Nunca** use `--no-verify`.

6. **Commit e push**
   - `git add -A` e confira `git status`.
   - Mensagem em português, primeira linha ≤ 72 caracteres, resumindo o dia. Exemplo: `Fecha dia 2026-10-30: depoimentos e ajustes no mobile`. No corpo, liste as mudanças principais. Siga as regras de atribuição de commit em vigor na sessão.
   - `git push` (se não houver upstream: `git push -u origin main`).
   - Se o push falhar por divergência, faça `git pull --rebase` e tente de novo; se houver conflito, pare e explique ao usuário.

7. **Relatar ao usuário** em poucas linhas: hash do commit, o que entrou, pendências principais e link do repositório (`gh repo view --json url -q .url`).
