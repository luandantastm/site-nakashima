# Decisões consolidadas

Decisões em vigor. As substituídas ficam riscadas, com a data da troca.

## Conteúdo
- Fontes: site atual (paulonakashima.com, plataforma DocPlanner) e perfil público no Doctoralia. Nada além do que está nelas foi inventado (2026-10-30).
- Dados usados: formação (UFU, HC-UFU, HGG), membro da SBCP, CRM-GO 13161 · RQE 8512, idiomas PT/EN, atendimento particular, 7 serviços, 12 doenças, 2 locais (IGM e GastroEla) com telefones e mapas, 4 avaliações (nota 5,0) (2026-10-30).
- Depoimentos: nomes abreviados como no Doctoralia. No depoimento da Francielly foi cortada a frase final, que cita o médico como "Dr Paulo Afonso" (2026-10-30).
- Preços não aparecem (o site atual não mostra valores) (2026-10-30).
- Rodapé com aviso "conteúdo educativo, não substitui consulta" e CRM/RQE, seguindo as regras de publicidade médica do CFM (2026-10-30).

## Design
- ~~Duas versões~~ → três versões com o mesmo conteúdo (2026-10-30):
  - `versao-tecnologica/`: escura, Space Grotesk + JetBrains Mono, verde-menta (herdado do tema "mint" do site atual) e violeta, retrato com moldura de HUD e linha de varredura, texto digitado, busca de doenças, FAQ.
  - `versao-classica/`: clara, Lora + Source Sans 3, azul-marinho e verde-azulado, barra de telefones no topo, layout tradicional.
  - `versao-gamer/`: fantasia sombria (Cinzel + Cormorant Garamond + Inter, dourado e brasa), tela de carregamento com dica de saúde (só na 1ª visita, pulável), menu principal de jogo com navegação por setas, ficha de personagem, árvore de progressão (formação), habilidades (procedimentos), compêndio com busca (doenças), mapa, crônicas (avaliações), conquistas desbloqueáveis e código secreto ↑↑↓↓←→←→BA (2026-10-30).
  - Na versão gamer, cada rótulo de jogo vem acompanhado do nome comum (ex.: "Habilidades · procedimentos") para pacientes que não jogam (2026-10-30).
  - Inspiração nos jogos favoritos do Dr. Paulo, mas 100% original: sem nomes, termos, logos ou elementos visuais dos jogos (2026-10-30).
- `index.html` na raiz é só um seletor entre as versões (`noindex`) (2026-10-30).
- Botão flutuante do WhatsApp no canto inferior direito, texto "Marque uma consulta", mensagem pronta: "Vim pelo site e gostaria de marcar uma consulta com o Dr. Paulo Nakashima" (2026-10-30).

## Infra / Git
- 100% HTML: cada versão é um único `index.html` com CSS/JS embutidos + `img/` (2026-10-30).
- ~~Repositório GitHub `site-nakashima`, privado~~ (substituída em 2026-10-30).
- Repositório GitHub `site-nakashima`, **público**, branch `main`, as duas versões em pastas no mesmo repo (2026-10-30).
- Publicação no GitHub Pages via GitHub Actions (`.github/workflows/pages.yml`) a cada push na `main`: https://luandantastm.github.io/site-nakashima/ . Só `index.html` e as pastas das versões vão para o ar (handoffs, skills e README não) (2026-10-30).
- No deploy, o número do WhatsApp vem do segredo `WHATSAPP_NUMERO` do repositório e substitui `NUMERO_WHATSAPP` nos .html. Se o número mudar, atualizar o segredo **e** o `git config nakashima.whatsapp` local (2026-10-30).
- Número do WhatsApp fora do GitHub: marcador `NUMERO_WHATSAPP` no repo, filtro git `whatsapp` (clean/smudge) com o número em `git config nakashima.whatsapp`, mais hook `pre-commit` que bloqueia o número (2026-10-30).
- Continuidade via skills `/retomar` e `/fechar-dia` em `.claude/skills/` e arquivos em `handoffs/` (2026-10-30).
