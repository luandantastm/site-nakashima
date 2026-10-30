# Site · Dr. Paulo Nakashima, coloproctologista

Duas propostas para o novo site, feitas a partir de [paulonakashima.com](https://www.paulonakashima.com/) e do [perfil no Doctoralia](https://www.doctoralia.com.br/paulo-nakashima/coloproctologista/goiania).

| Pasta | Estilo |
|---|---|
| `versao-tecnologica/` | Tema escuro, grade e brilhos, texto digitado, busca de doenças, animações ao rolar |
| `versao-classica/` | Visual claro e tradicional de consultório, tipografia serifada |

`index.html` na raiz é só uma página para escolher entre as duas.

Cada versão é **um único arquivo HTML** (CSS e JS embutidos) mais a foto em `img/`. Para publicar, envie a pasta da versão escolhida para qualquer hospedagem estática.

## Botão do WhatsApp

O botão flutuante (canto inferior direito) abre o WhatsApp com a mensagem
"Vim pelo site e gostaria de marcar uma consulta com o Dr. Paulo Nakashima".

O número **não fica no repositório**: aqui no GitHub os links usam o marcador `NUMERO_WHATSAPP`. Na cópia local ele é substituído automaticamente por um filtro git.

Para configurar num clone novo:

```sh
git config nakashima.whatsapp 55DDDNUMERO        # só dígitos, com 55 e DDD
git config filter.whatsapp.clean  'n=$(git config nakashima.whatsapp); if [ -n "$n" ]; then sed "s/$n/NUMERO_WHATSAPP/g"; else cat; fi'
git config filter.whatsapp.smudge 'n=$(git config nakashima.whatsapp); if [ -n "$n" ]; then sed "s/NUMERO_WHATSAPP/$n/g"; else cat; fi'
rm versao-*/index.html && git checkout -- .    # reaplica o filtro
```

## Publicação (GitHub Pages)

No ar em **https://luandantastm.github.io/site-nakashima/**:
- versão tecnológica: `/versao-tecnologica/`
- versão clássica: `/versao-classica/`

Cada push na `main` publica de novo (`.github/workflows/pages.yml`). No deploy, o marcador `NUMERO_WHATSAPP` é trocado pelo segredo `WHATSAPP_NUMERO` do repositório (Settings › Secrets and variables › Actions). Para trocar o número: `gh secret set WHATSAPP_NUMERO`.

## Rotina de trabalho (Claude Code)

- `/retomar`: lê decisões, pendências e o último handoff e resume onde paramos.
- `/fechar-dia`: registra o handoff do dia, consolida decisões e pendências, faz commit e push.
