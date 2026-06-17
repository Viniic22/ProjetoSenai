# Industrial Kong — Registro de Melhorias

Projeto Mundo SENAI | Desenvolvido por Vinicius, Gustavo e equipe  
Repositório: https://github.com/gumengerr/ProjetoSenai

---

## Estrutura do Projeto

```
ProjetoSenaiGit/
├── index.html       ← site completo (HTML + CSS + JS embutidos)
├── hero-bg.png      ← imagem de fundo do Hero (pixel art industrial)
└── fotos/
    ├── carol.png
    ├── gustavo.png
    ├── nathallye.png
    ├── rafael.png
    ├── vinicius.png
    └── yasmin.png
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
