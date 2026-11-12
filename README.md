# Dashboard SMACSS · GABARITO (professor)

Versão resolvida da atividade. Não distribuir antes da devolutiva.

## Estrutura final
```
scss/
├── abstracts/   _tokens.scss (era _variables.scss), _functions.scss, _mixins.scss
├── base/        _reset.scss, _root.scss (gera --dsc-*), _base.scss
├── layout/      _dashboard.scss (era _layout.scss; .dashboard -> .l-dashboard)
├── module/      _header, _sidebar, _card, _btn (era components/)
├── state/       _state.scss
├── theme/       _escuro.scss (theme switcher)
└── main.scss
```

## O que foi corrigido do projeto-final
- `rgba (0, 0, 0, 0.08)` com espaço invalidava o `box-shadow`. Agora é o token `--dsc-sombra-elevada`.
- Blocos vazios (`&__nav {}`, `&__item {}`, `&__sidebar {}`) removidos.
- `_variables.scss` gerava CSS sozinho; virou `abstracts/_tokens.scss` (só dados) + `base/_root.scss` (gera o `:root`).
- Imagens externas de placeholder trocadas por `img/projeto.svg` local.
- `minmax(300px, 1fr)` virou `minmax(min(300px, 100%), 1fr)` para não estourar em telas menores que 300px.
- Animação do card respeita `prefers-reduced-motion`.

## Como abrir o projeto

### Opção A · GitHub Codespaces (recomendado, roda na nuvem)
1. Crie um repositório novo no GitHub e envie **todos os arquivos desta pasta**, incluindo a pasta `.devcontainer`
   (pelo site: *Add file → Upload files* e arraste o conteúdo da pasta).
2. No repositório: botão **Code → Codespaces → Create codespace on main**.
3. Espere a primeira abertura (1 a 2 minutos): o `npm install` roda sozinho.
4. No terminal do Codespaces: `npm run dev`. A prévia do Dashboard abre ao lado; se não abrir, vá na aba **Portas** e clique no globo da porta 5173.
5. `npm run lint` confere a arquitetura.

Contas pessoais do GitHub têm uma cota mensal gratuita de Codespaces, suficiente para a aula. Pare o codespace ao terminar.

### Opção B · StackBlitz (sem conta no GitHub)
1. Acesse **stackblitz.com** e crie um projeto em branco do tipo **Node.js**.
2. Apague os arquivos de exemplo e **arraste o conteúdo desta pasta** para o painel de arquivos.
3. No terminal do StackBlitz: `npm install` e depois `npm run dev`.

### Opção C · VS Code local (Node 18 ou superior)
```bash
npm install
npm run dev      # abre em http://localhost:5173
npm run lint
```

## Regras
- Dentro dos módulos, **só `var(--dsc-*)`**. Valores brutos ficam em `abstracts/_tokens.scss`.
- **BEM continua** dentro dos módulos (`card__title`, `btn--primary`).
- **Modificador `--`** é variação escolhida no HTML. **Estado `is-`** é ligado pelo JavaScript.
- Estado de um módulo fica **no arquivo do módulo** (`.sidebar.is-aberta`).
- Sem ID em seletor e no máximo 3 níveis (o lint verifica).
