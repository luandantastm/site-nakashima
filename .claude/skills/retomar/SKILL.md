---
name: retomar
description: Retoma o trabalho no site do Dr. Paulo Nakashima. Lê as decisões consolidadas, as pendências e o último handoff em handoffs/, confere o estado do git e do filtro do WhatsApp, e apresenta um resumo de onde paramos e o que fazer a seguir. Use no início de cada sessão ou quando o usuário disser "retomar", "onde paramos", "continuar".
---

# Retomar

Objetivo: em poucos minutos, deixar claro **o que já foi decidido, o que está pendente e qual é o próximo passo**, sem reabrir decisões já tomadas.

## Passos

1. **Ler o histórico** (nesta ordem):
   - `handoffs/DECISOES.md`: decisões em vigor. Trate como acordadas; só reabra se o usuário pedir.
   - `handoffs/PENDENCIAS.md`: o que está em aberto, com prioridade.
   - O handoff diário mais recente: `ls handoffs/ | grep -E '^[0-9]{4}-[0-9]{2}-[0-9]{2}\.md$' | sort | tail -1`.
   - `CLAUDE.md`: regras do projeto.

2. **Conferir o estado do repositório:**
   - `git status --short`, `git log --oneline -5`, `git fetch -q && git status -sb` (está atrás ou à frente do GitHub?).
   - Há alterações que não estão no último handoff? Liste-as como "trabalho não registrado".

3. **Conferir a proteção do número do WhatsApp** (sem nunca exibir o número):
   - `git config nakashima.whatsapp >/dev/null && echo configurado || echo FALTANDO`
   - `test -x .git/hooks/pre-commit && echo hook ok || echo hook FALTANDO`
   - `grep -l NUMERO_WHATSAPP versao-*/index.html`: se aparecer arquivo, a cópia local está sem o número real (o filtro não foi aplicado). Oriente conforme o README.
   - Se algo estiver faltando, avise antes de qualquer commit.

4. **Apresentar o resumo** ao usuário, curto, neste formato:

   ```
   ## Onde paramos (último handoff: AAAA-MM-DD)
   - <o que foi feito por último, 2 a 4 itens>

   ## Decisões em vigor
   - <só as relevantes para o trabalho de hoje>

   ## Pendências
   1. [alta] ...
   2. [média] ...

   ## Estado
   git: <limpo | N arquivos alterados | atrás/à frente do GitHub> · filtro WhatsApp: <ok | faltando>

   ## Sugestão de próximo passo
   <uma recomendação concreta>
   ```

5. Pergunte se seguimos pela sugestão ou por outra pendência. Não comece a editar antes da resposta, a menos que o usuário já tenha dito o que quer.

## Regras
- Nunca mostre, copie ou registre o número do WhatsApp.
- Se `handoffs/` não existir ou estiver vazio, diga isso e monte o resumo a partir do `git log` e do `README.md`.
