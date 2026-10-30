# Site Dr. Paulo Nakashima

Site do coloproctologista Dr. Paulo Nakashima (Goiânia), refeito a partir de https://www.paulonakashima.com/ e do perfil no Doctoralia.

## Regras do projeto
- **Só HTML.** Cada versão é um único `index.html` com CSS e JS embutidos, mais a pasta `img/`. Sem build, sem frameworks, sem arquivos `.css`/`.js` separados.
- **O número do WhatsApp nunca vai para o GitHub.** Nos `.html` locais o número real aparece; no repositório aparece o marcador `NUMERO_WHATSAPP`. Quem faz a troca é o filtro git `whatsapp` (`.gitattributes`), que lê o número de `git config nakashima.whatsapp` (fica só em `.git/config`). O hook `.git/hooks/pre-commit` bloqueia qualquer commit que contenha o número.
  - Nunca escreva o número em handoffs, README, skills, mensagens de commit ou memória versionada.
- **Duas versões, mesmo conteúdo:** `versao-tecnologica/` (escura, animada) e `versao-classica/` (clara, tradicional). Mudança de conteúdo (endereço, serviço, depoimento) deve ser feita nas duas.
- **Publicidade médica (CFM):** manter CRM/RQE visíveis, não prometer resultado, não usar "melhor", não usar antes/depois. Não inventar dados que não estejam nas fontes.
- Mensagem padrão do WhatsApp: "Vim pelo site e gostaria de marcar uma consulta com o Dr. Paulo Nakashima".

## Continuidade
- `/retomar` no início da sessão, `/fechar-dia` no fim.
- Histórico em `handoffs/`: `DECISOES.md` (consolidado), `PENDENCIAS.md` (aberto) e um arquivo por dia `AAAA-MM-DD.md`.
