# Industrial Kong — Registro de Melhorias

Projeto Mundo SENAI | Desenvolvido por Vinicius, Gustavo e equipe  
Repositório: https://github.com/Viniic22/ProjetoSenai  
Site publicado: https://kongsenai.netlify.app (deploy automático a cada push)

---

## Estrutura do Projeto

```
ProjetoSenaiGit/
├── index.html       ← site completo (HTML + CSS + JS embutidos)
├── hero-bg.png      ← imagem de fundo do Hero (pixel art industrial)
└── fotos/
    ├── carol.png / carol.webp        (o .webp é o usado no site — muito mais leve)
    ├── gustavo.png / gustavo.webp
    ├── nathallye.png / nathallye.webp
    ├── rafael.png / rafael.webp
    ├── vinicius.png / vinicius.webp
    └── yasmin.png / yasmin.webp
```

---

## Correções de Bugs

| Item | Problema | Solução |
|---|---|---|
| Galeria | 2 itens com `src=""` e 2 com emojis soltos | Substituídos por placeholders com gradiente industrial + ícone + legenda |
| Seção O Jogo | Imagem externa do Google (copyright) | Substituída por arte SVG pixel art original |
| Seção Fliperama | Imagem de CDN aleatório quebrada | Substituída por SVG do gabinete artesanal |
| Emojis quebrados | Steps de desenvolvimento mostravam `??` | Corrigidos com ícones compatíveis |

---

## Melhorias Visuais — Fase 1

### Hero Section
- Fundo: imagem pixel art `hero-bg.png` com overlay escuro para legibilidade
- 6 engrenagens animadas girando lentamente no fundo (opacidade 6%)
- Layout 2 colunas no desktop: texto à esquerda + tela do jogo à direita
- Segundo botão "VER O JOGO ▶" ao lado do principal
- Efeito **glitch** no texto "KONG" a cada 5 segundos (deslocamento de cor em laranja/azul/ciano)

### Navbar
- Barra de progresso de leitura no topo (azul → laranja → amarelo) que cresce conforme scroll
- Destaque ativo na seção atual com sublinhado azul
- Menu mobile com transição suave de altura (em vez de aparecer instantaneamente)

### Seções
- Números editoriais decorativos atrás de cada título (`01` a `07`) em baixa opacidade
- Animações de entrada:
  - `fade-up` — elementos sobem ao aparecer na tela
  - `slide-left` — entra da esquerda (ex: SVG do jogo, texto do Fliperama)
  - `slide-right` — entra da direita (ex: fases do jogo, gabinete SVG)
- Linha divisória laranja entre seções

---

## Melhorias Visuais — Fase 2

### Seção Sobre
- Strip de 4 estatísticas com **contador animado**: 3 Fases / 6 Desenvolvedores / 1 Fliperama / 100% Artesanal

### Seção Desenvolvimento (Steps)
- Conector vertical com animação de preenchimento progressivo ao rolar
- Números dos steps em laranja com glow

### Seção O Jogo
- Arte SVG pixel art original: personagem técnico subindo escadas, gorila robótico no topo, barris, HUD em português (`PONTOS`, `TURNO`, `VIDAS`)
- Efeito CRT scan lines (linhas horizontais sutis) sobre o SVG
- **Display de controles visuais**: teclas estilizadas `◀ ▶` (Mover), `ESPAÇO` (Pular), `▲ ▼` (Escada) + indicador de Touch
- Barras de dificuldade animadas nos 3 cards de fase:
  - Chão de Fábrica — verde 33%
  - Linha de Montagem — amarelo 66%
  - Núcleo Industrial — vermelho 100%

### Seção Fliperama
- SVG original do gabinete artesanal de madeira com madeira texturizada, tela, joystick e botões coloridos
- Spec cards (Madeira / Feito à Mão / Projeto Técnico) com hover animado
- **Linha do tempo da construção** com 4 etapas conectadas por linha vertical:
  1. Projeto e Medidas
  2. Corte da Madeira
  3. Montagem e Acabamento
  4. Integração Eletrônica

### Seção Galeria
- Layout **featured**: primeiro item ocupa toda a altura esquerda, itens 2/3/4 empilhados à direita
- 4 placeholders com gradiente temático por categoria (gameplay, fliperama, cenário, equipe)

### Seção Equipe
- Avatar aumentado de 96px para 110px
- **Borda animada conic-gradient** no hover (azul → roxo → ciano girando)
- Linha laranja/amarela/azul no topo do card ao hover
- **Tooltip** com cargo do membro ao passar o mouse

### Seção Contato
- Texto atualizado para contexto escolar
- Instagram + link para seção Equipe
- Botão **Compartilhar** (Web Share API no celular; copia o link com toast de confirmação no desktop)
- Card com **QR code** apontando pro site publicado (`kongsenai.netlify.app`) — pra colar perto do fliperama artesanal na apresentação

---

## SEO e Metatags Sociais

- Favicon em SVG inline (engrenagem sobre fundo escuro, sem arquivo externo).
- Open Graph (`og:title`, `og:description`, `og:image`, `og:url`) e Twitter Card — agora o link do site mostra título, descrição e imagem de preview ao ser compartilhado no WhatsApp/Instagram/Twitter.
- `<link rel="canonical">` e `theme-color` apontando pro site publicado.

---

## Performance de Imagens

- Fotos da equipe: de **base64 embutido no HTML** (até 2,2MB por foto, ~300KB de HTML só nisso) para arquivos **WebP externos comprimidos** (`fotos/*.webp`, ~4 a 11KB cada) com `loading="lazy"`.
- Redução de **~59% no tamanho do `index.html`** (de ~312KB pra ~128KB).
- Processado com `sharp-cli` (resize 320×320 + qualidade 78%); os `.png` originais continuam no repositório como arquivo-fonte, só não são mais carregados pelo site.

---

## Analytics Simples por Seção

- Cada seção da página (Sobre, Jogo, Fliperama, Equipe etc.) incrementa um contador global na primeira vez que aparece na tela do visitante (1x por sessão), via a mesma API pública já usada no ranking do Instagram.
- Painel de estatísticas **oculto**, só visível acessando o site com `?stats` no final do link (ex: `kongsenai.netlify.app/?stats`) — mostra as seções ordenadas por popularidade. Uso interno da equipe, não aparece pra visitantes comuns.

---

## Tema Claro/Escuro

- Botão 🌙/☀️ na navbar alterna entre tema escuro (padrão) e um tema claro completo, com preferência salva no `localStorage` e detecção inicial via `prefers-color-scheme`.
- Script inline no `<head>` aplica o tema antes da primeira renderização, evitando "flash" do tema errado.
- **Hero e Modo Arcade mantêm a estética escura sempre**, mesmo com o tema claro ativo — decisão de design (o Hero tem uma foto de fundo escura com texto branco; o gabinete arcade simula uma máquina física) — feito "prendendo" as variáveis de cor localmente nesses dois blocos.

---

## Sons 8-bit no Modo Arcade

- Bipes retrô sintetizados via Web Audio API (sem arquivo de áudio nenhum): clique nos botões do gabinete, movimento dos analógicos, "power on/off" ao entrar/sair do modo arcade.
- Botão de mudo (🔊/🔇) no canto superior do gabinete, preferência salva no `localStorage`.

---

## Contador de Visitantes

- Badge retrô "VISITANTE Nº 000042" no Hero, no estilo contador de visitas old-school — usa a mesma API pública já validada no ranking do Instagram (namespace `industrial-kong-senai-cacador`, chave `site-visits`).
- Conta 1 vez por sessão do navegador (`sessionStorage`) pra não inflar a cada F5.

---

## Modo Impressão

- `@media print` sobrescreve as variáveis de cor (`--bg`, `--fg`, `--card`, etc.) pra fundo branco/texto escuro, evitando imprimir página toda preta.
- Corrige textos com gradiente (título, logo) que ficariam **invisíveis** na impressão por usarem `-webkit-text-fill-color:transparent`.
- Esconde elementos só-interativos (nav, arcade, botão voltar ao topo, toasts) e mostra a URL dos links externos entre parênteses.

---

## Ranking de Cliques no Instagram

- Cada clique no Instagram de um integrante incrementa um contador **global** (todos os visitantes, não só quem clicou), via API pública gratuita `abacus.jasoncameron.dev` — sem backend próprio.
- Badge "X cliques" abaixo do `@usuário` de cada card, atualizado ao carregar a página.
- Quem lidera ganha um 👑 animado + borda dourada no card (`.team-card.is-leader`).
- Risco: depende de serviço gratuito de terceiros sem SLA; se sair do ar, o link do Instagram continua funcionando, só o contador para de atualizar.

---

## Correções Mobile

| Item | Problema | Solução |
|---|---|---|
| Modo Arcade | Barra inferior (2 analógicos + 4 botões) precisava de ~450px de largura — estourava qualquer tela de celular; não existia media query pro arcade | `@media(max-width:640px)` reduzindo analógicos, botões e barras laterais (80px → 6px) |
| Analógicos no arcade | Toque sempre rolava pra cima (direção calculada via `mousemove`, que não existe em touch) | Handler de `touchstart` calculando a direção pelo ponto tocado |
| Contagem regressiva | 4 blocos com `min-width:70px` (280px total) estourava em telas ≤320px | Ajuste `@media(max-width:380px)` reduzindo padding/fonte |

---

## Melhorias de Acessibilidade

| Item | Problema | Solução |
|---|---|---|
| Navegação por teclado | Sem forma de pular a navbar | Link "Pular para o conteúdo principal" (`.skip-link`) visível ao focar |
| Foco visível | `outline:none` nos botões do modo arcade escondia o foco do teclado | `:focus-visible` restaurado em todos os elementos interativos |
| Modo arcade | Joysticks só funcionavam com mouse (drag) | `role="button"` + `tabindex` + suporte a `Tab`, setas `↑↓` e `Enter` |
| Movimento | Glitch, engrenagens girando, pulsos e parallax sempre ativos | `@media (prefers-reduced-motion: reduce)` desativa/reduz animações |
| Leitores de tela | Elementos decorativos (canvas de faíscas, engrenagens, emojis, seta do chevron, moldura do fliperama) eram lidos sem sentido | Marcados com `aria-hidden="true"` |
| Botões só-ícone | Menu hambúrguer, voltar ao topo e botões do arcade sem nome acessível | `aria-label` adicionado a todos |
| Menu mobile | Estado aberto/fechado não era informado a leitores de tela | `aria-expanded` sincronizado via JS |
| Fotos da equipe | `alt="Integrante 1"` a `"Integrante 6"` (genérico) | Trocado por nome + função de cada membro |
| Contraste | Legenda da galeria com `rgba(255,255,255,.22)` (~2:1, reprovado) | Aumentado para `.72` (~10:1, aprovado WCAG AA/AAA) |
| Contador regressivo | Atualização a cada segundo sem semântica | `role="timer" aria-live="off"` evita leitura ruidosa |

---

## Tela de Loading
- Splash screen com logo pulsando e barra de progresso
- Desaparece automaticamente após 1.3 segundos

---

## Botão Voltar ao Topo
- Aparece no canto inferior direito após scrollar 400px
- Laranja com glow, sobe 4px no hover

---

## Botão "Explorar Projeto"
- Efeito shimmer animado (brilho passando pela borda)
- Efeito ripple ao clicar (onda circular)

---

## Ícone do Café ☕
- 3 linhas de vapor animadas subindo acima do emoji

---

## Footer Expandido
- 3 colunas: logo + descrição + tags | navegação | links
- Tags "Arcade / Industrial / Artesanal"
- Barra inferior com copyright e crédito ao SENAI Caçador

---

## Paleta de Cores — Dual Azul + Laranja

| Variável | Cor | Uso |
|---|---|---|
| `--bg` | `#080c14` | Fundo principal |
| `--bg2` | `#0c1220` | Fundo secundário |
| `--card` | `#0d1728` | Cards |
| `--border` | `#1e2d42` | Bordas |
| `--primary` | `#1e90ff` | Estrutura (navbar, bordas, ícones) |
| `--primary-light` | `#5aadff` | Textos azuis secundários |
| `--accent` | `#ff6b00` | Destaques e CTAs (botões, labels, steps) |
| `--accent-light` | `#ff8c3a` | Laranja claro |
| `--fg` | `#e8edf5` | Texto principal |
| `--fg2` | `#7a8494` | Texto secundário |

**Azul** → navbar, bordas, feature icons, sombras de card  
**Laranja** → botões, labels, números, timeline, stats, barra de scroll, back-to-top  
**Gradiente azul→laranja** → título "INDUSTRIAL KONG", logo do footer  

---

## Commits no GitHub

| Hash | Descrição |
|---|---|
| `eee65fd` | Upload inicial do projeto |
| `880566e` | Update index.html (Gustavo) |
| `c44637b` | Update index.html com fotos base64 (Gustavo) |
| `3727eb8` | Melhorias visuais: hero bg, layout 2col, galeria featured, números seções, footer, animações, loading, glitch, stats, tooltips |
| `d45081b` | Paleta dual azul+laranja, slide animations, controls display, timeline fliperama, spec cards, mobile menu suave |

---

## Tecnologias Utilizadas

- **HTML5** — estrutura semântica
- **CSS3** — animações, gradientes, grid, custom properties, `@property`, `conic-gradient`
- **JavaScript** — IntersectionObserver, contadores animados, ripple, progresso de leitura
- **SVG** — arte pixel art do jogo e gabinete do fliperama (sem imagens externas)
- **Web Fonts** — Orbitron (display) + Inter (corpo) via Google Fonts
- **Git + GitHub** — controle de versão e colaboração
