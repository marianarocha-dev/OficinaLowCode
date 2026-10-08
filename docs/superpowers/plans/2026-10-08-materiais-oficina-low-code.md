# Materiais da Oficina Low-Code — Plano de Implementação

> **Para quem for executar:** Este plano produz **materiais didáticos** (site-template, assets, README, slides), não software testável por unidade. Onde um plano normal diria "rodar os testes", aqui dizemos "verificar visualmente no navegador" e "validar o fluxo do aluno". Os passos usam checkbox (`- [ ]`) para acompanhamento.

**Goal:** Produzir todos os materiais da oficina de 3h — um portfólio-template no GitHub (configurável pelos alunos) e os slides com código de referência e respostas do quiz plantadas.

**Architecture:** Um site estático de página única (HTML + CSS, sem build, sem JavaScript) com 5 seções e placeholders em maiúsculas. Hospedado em `marianarocha-dev/OficinaLowCode` como Template Repository. Slides separados cobrindo setup, teoria, missões (com trechos de código visíveis) e quiz.

**Tech Stack:** HTML5, CSS3 (sem frameworks), Git, GitHub (Template + Pages), ChatGPT (lado do aluno), VS Code + Live Server (lado do aluno).

**Referência:** Spec em [docs/superpowers/specs/2026-10-08-oficina-low-code-design.md](../specs/2026-10-08-oficina-low-code-design.md)

---

## Estrutura de Arquivos

```
OficinaLowCode/
├── index.html       ← portfólio, 5 seções, placeholders MAIÚSCULOS, 1 card de projeto
├── style.css        ← layout responsivo, variável CSS para cor de fundo
├── assets/
│   ├── foto-perfil.svg   ← placeholder de foto (SVG = leve, sem direitos de imagem)
│   └── projeto.svg       ← placeholder de capa de projeto
├── README.md        ← setup passo a passo: VS Code → Live Server → Git → clone
└── docs/
    └── roteiro-instrutora.md  ← roteiro de condução minuto a minuto (uso da instrutora)
```

**Decisões travadas aqui:**
- **SVG em vez de JPG** para placeholders: arquivo leve, sem questões de direitos de imagem, e o aluno troca por foto real facilmente.
- **Sem JavaScript:** mantém o foco em HTML/CSS, reduz pontos de falha, e o Live Server já dá o reload automático.
- **Variável CSS `--cor-fundo`** no `:root`: a Missão 1.3 (mudar cor de fundo) fica trivial de localizar e trocar.
- **Slides:** produzidos como arquivo Markdown estruturado (`slides.md`) que serve de roteiro de conteúdo. A conversão para PowerPoint/Google Slides é uma decisão posterior da instrutora — o Markdown garante que todo o conteúdo e as respostas plantadas existam primeiro.

---

## Task 1: Esqueleto do repositório e README

**Files:**
- Create: `README.md`

- [ ] **Step 1: Escrever o README com o fluxo de setup na ordem correta**

Ordem obrigatória: VS Code + Live Server ANTES do Git (instalar Git antes do VS Code pode dar erro na máquina — ver spec seção 3).

```markdown
# Oficina: Enriquecendo seu portfólio com IA

Bem-vindo(a)! Ao final desta oficina você terá um portfólio pessoal
profissional publicado no seu próprio GitHub.

## Antes de começar — Setup (siga NESTA ordem)

### 1. Instale o VS Code
Baixe em https://code.visualstudio.com e instale.

### 2. Instale a extensão Live Server
No VS Code: ícone de extensões (lado esquerdo) → busque "Live Server"
(autor: Ritwick Dey) → Install.

### 3. Instale o Git
Baixe em https://git-scm.com/downloads e instale.
(Instale o VS Code ANTES do Git para evitar erros de configuração.)

### 4. Crie seu portfólio a partir deste template
1. No topo deste repositório, clique em **"Use this template"** →
   **"Create a new repository"**.
2. Dê o nome `meu-portfolio` e crie.
3. Copie a URL do SEU novo repositório.

### 5. Clone o seu repositório
Abra o terminal e rode (troque SEU-USUARIO):
\`\`\`bash
git clone https://github.com/SEU-USUARIO/meu-portfolio.git
cd meu-portfolio
\`\`\`

### 6. Abra no VS Code e inicie o Live Server
1. Abra a pasta no VS Code.
2. Clique com o botão direito em \`index.html\` → **"Open with Live Server"**.
3. Seu portfólio abre no navegador. Pronto para personalizar!

## Estrutura do projeto
- \`index.html\` — o conteúdo do seu portfólio
- \`style.css\` — as cores e o layout
- \`assets/\` — suas imagens
```

- [ ] **Step 2: Verificar que a ordem VS Code → Git está correta e os links funcionam**

Abrir o `README.md` e conferir: passo 1-2 (VS Code + Live Server) vêm antes do passo 3 (Git). Links `code.visualstudio.com` e `git-scm.com/downloads` corretos.

- [ ] **Step 3: Commit**

```bash
git add README.md
git commit -m "docs: adiciona README com setup na ordem VS Code -> Git"
```

---

## Task 2: `style.css` — layout responsivo com variável de cor

**Files:**
- Create: `style.css`

- [ ] **Step 1: Escrever o CSS completo**

A primeira regra é `:root` com `--cor-fundo` em destaque (alvo da Missão 1.3). Media query garante responsividade (conceito da Q3 do quiz).

```css
/* ===================================================== */
/*  MUDE A COR DE FUNDO AQUI (Missão 1.3)                */
/* ===================================================== */
:root {
  --cor-fundo: #f4f4f9;
  --cor-destaque: #4f46e5;
  --cor-texto: #1f2937;
  --cor-card: #ffffff;
}

* { margin: 0; padding: 0; box-sizing: border-box; }

body {
  font-family: 'Segoe UI', system-ui, sans-serif;
  background-color: var(--cor-fundo);
  color: var(--cor-texto);
  line-height: 1.6;
}

.container { max-width: 960px; margin: 0 auto; padding: 0 20px; }

/* Hero */
.hero { text-align: center; padding: 60px 20px; }
.hero img {
  width: 150px; height: 150px; border-radius: 50%;
  object-fit: cover; border: 4px solid var(--cor-destaque);
}
.hero h1 { font-size: 2.5rem; margin-top: 20px; }
.hero p { font-size: 1.2rem; color: var(--cor-destaque); }

/* Seções */
section { padding: 40px 20px; }
section h2 {
  font-size: 1.8rem; margin-bottom: 20px;
  border-bottom: 2px solid var(--cor-destaque);
  display: inline-block;
}

/* Habilidades */
.habilidades-lista { display: flex; flex-wrap: wrap; gap: 12px; }
.habilidades-lista span {
  background: var(--cor-destaque); color: #fff;
  padding: 8px 16px; border-radius: 20px; font-size: 0.9rem;
}

/* Projetos */
.projetos-grid {
  display: grid; grid-template-columns: repeat(2, 1fr); gap: 20px;
}
.card-projeto {
  background: var(--cor-card); border-radius: 12px; overflow: hidden;
  box-shadow: 0 2px 8px rgba(0,0,0,0.08);
}
.card-projeto img { width: 100%; height: 160px; object-fit: cover; }
.card-projeto .conteudo { padding: 16px; }
.card-projeto h3 { margin-bottom: 8px; }

/* Contato */
.contato a { color: var(--cor-destaque); text-decoration: none; margin-right: 16px; }

/* Responsividade (Q3 do quiz) */
@media (max-width: 600px) {
  .hero h1 { font-size: 1.8rem; }
  .projetos-grid { grid-template-columns: 1fr; }
}
```

- [ ] **Step 2: Commit** (verificação visual acontece na Task 4, junto do HTML)

```bash
git add style.css
git commit -m "feat: adiciona layout responsivo com variavel de cor de fundo"
```

---

## Task 3: Assets placeholder (SVG)

**Files:**
- Create: `assets/foto-perfil.svg`
- Create: `assets/projeto.svg`

- [ ] **Step 1: Criar `assets/foto-perfil.svg`**

Círculo cinza com ícone de pessoa — placeholder neutro e óbvio.

```xml
<svg xmlns="http://www.w3.org/2000/svg" width="150" height="150" viewBox="0 0 150 150">
  <rect width="150" height="150" fill="#d1d5db"/>
  <circle cx="75" cy="60" r="28" fill="#9ca3af"/>
  <path d="M35 130 Q35 90 75 90 Q115 90 115 130 Z" fill="#9ca3af"/>
  <text x="75" y="145" font-family="sans-serif" font-size="10" fill="#6b7280" text-anchor="middle">sua foto</text>
</svg>
```

- [ ] **Step 2: Criar `assets/projeto.svg`**

Retângulo com texto "imagem do projeto".

```xml
<svg xmlns="http://www.w3.org/2000/svg" width="400" height="160" viewBox="0 0 400 160">
  <rect width="400" height="160" fill="#e5e7eb"/>
  <rect x="150" y="50" width="100" height="60" rx="6" fill="#9ca3af"/>
  <circle cx="175" cy="72" r="8" fill="#e5e7eb"/>
  <path d="M160 100 L185 78 L205 92 L230 68 L240 100 Z" fill="#e5e7eb"/>
  <text x="200" y="140" font-family="sans-serif" font-size="14" fill="#6b7280" text-anchor="middle">imagem do projeto</text>
</svg>
```

- [ ] **Step 3: Abrir cada SVG no navegador para confirmar que renderizam**

Abrir `assets/foto-perfil.svg` e `assets/projeto.svg` direto no navegador. Esperado: círculo com silhueta / retângulo com ícone de imagem.

- [ ] **Step 4: Commit**

```bash
git add assets/foto-perfil.svg assets/projeto.svg
git commit -m "feat: adiciona placeholders SVG de foto e projeto"
```

---

## Task 4: `index.html` — portfólio com placeholders e 1 card de projeto

**Files:**
- Create: `index.html`

- [ ] **Step 1: Escrever o HTML completo com placeholders MAIÚSCULOS**

Placeholders em maiúsculas (`NOME_AQUI`) ficam fáceis de localizar. Comentários HTML sinalizam cada seção. O card de projeto é a base da Missão 2.3.

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Portfólio de NOME_AQUI</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>

  <!-- ======================= HERO ======================= -->
  <header class="hero">
    <div class="container">
      <img src="assets/foto-perfil.svg" alt="Foto de NOME_AQUI">
      <h1>NOME_AQUI</h1>
      <p>TITULO_PROFISSIONAL_AQUI — CURSO_AQUI</p>
    </div>
  </header>

  <main class="container">

    <!-- ===================== SOBRE MIM ===================== -->
    <section class="sobre">
      <h2>Sobre mim</h2>
      <p>ESCREVA_AQUI_UM_PARAGRAFO_SOBRE_VOCE</p>
    </section>

    <!-- ==================== HABILIDADES ==================== -->
    <section class="habilidades">
      <h2>Habilidades</h2>
      <div class="habilidades-lista">
        <span>HABILIDADE_1</span>
        <span>HABILIDADE_2</span>
        <span>HABILIDADE_3</span>
      </div>
    </section>

    <!-- ===================== PROJETOS ====================== -->
    <section class="projetos">
      <h2>Projetos</h2>
      <div class="projetos-grid">

        <!-- CARD DE PROJETO (copie este bloco para adicionar mais) -->
        <div class="card-projeto">
          <img src="assets/projeto.svg" alt="Capa do projeto">
          <div class="conteudo">
            <h3>NOME_DO_PROJETO</h3>
            <p>DESCRICAO_CURTA_DO_PROJETO</p>
            <a href="COLE_O_LINK_DO_PROJETO_AQUI">Ver projeto</a>
          </div>
        </div>

      </div>
    </section>

    <!-- ====================== CONTATO ====================== -->
    <section class="contato">
      <h2>Contato</h2>
      <p>
        <a href="mailto:SEU_EMAIL_AQUI">SEU_EMAIL_AQUI</a>
        <a href="COLE_SEU_LINKEDIN_AQUI">LinkedIn</a>
        <a href="COLE_SEU_GITHUB_AQUI">GitHub</a>
      </p>
    </section>

  </main>

</body>
</html>
```

- [ ] **Step 2: Abrir no navegador via Live Server e verificar visualmente**

Abrir `index.html` com Live Server. Esperado: hero com foto redonda e nome, 4 seções visíveis, 1 card de projeto renderizado, cores do CSS aplicadas.

- [ ] **Step 3: Testar responsividade (valida Q3)**

Reduzir a janela para < 600px (ou DevTools modo mobile). Esperado: grid de projetos vira 1 coluna, nada cortado.

- [ ] **Step 4: Commit**

```bash
git add index.html
git commit -m "feat: adiciona portfolio HTML com 5 secoes e card de projeto"
```

---

## Task 5: Validar o fluxo completo do aluno ponta a ponta

Esta é a "suíte de testes" da oficina — garante que o caminho que o aluno percorrerá funciona de verdade.

**Files:** nenhum (validação)

- [ ] **Step 1: Marcar o repositório como Template**

No GitHub: `marianarocha-dev/OficinaLowCode` → **Settings** → **General** → marcar **"Template repository"**.

- [ ] **Step 2: Simular o fluxo do aluno com uma conta/pasta de teste**

```bash
# a partir do botão "Use this template", criar repo de teste, depois:
git clone https://github.com/SEU-USUARIO/portfolio-teste.git
cd portfolio-teste
```
Esperado: `index.html`, `style.css`, `assets/`, `README.md` presentes.

- [ ] **Step 3: Executar as 2 missões como um aluno faria**

Missão 1: trocar `NOME_AQUI`, `CURSO_AQUI`, a cor em `--cor-fundo`. Missão 2: preencher "Sobre mim", habilidades, duplicar o card. Verificar no Live Server a cada troca.

- [ ] **Step 4: Validar os dois checkpoints de Git**

```bash
git add .
git commit -m "personalização inicial do portfólio"
# ... mais edições ...
git add .
git commit -m "novas seções geradas com IA"
git push
```
Esperado: push sem erros, mudanças visíveis no GitHub.

- [ ] **Step 5: Validar o deploy (valida Q5)**

Ativar GitHub Pages (Settings → Pages → branch `main`). Esperado: portfólio acessível em `https://SEU-USUARIO.github.io/portfolio-teste/`.

- [ ] **Step 6: Limpar o repositório de teste**

Apagar o repo de teste no GitHub. Anotar qualquer passo que travou para ajustar o README/slides.

---

## Task 6: `slides.md` — conteúdo dos slides com respostas do quiz plantadas

**Files:**
- Create: `slides.md`

- [ ] **Step 1: Escrever o conteúdo dos slides com os conceitos-chave em negrito**

Regra de estilo: **conceitos-chave sempre em negrito** ao longo de toda a apresentação. As respostas do quiz ficam embutidas nesse padrão — parecem estilo, não dica (ver spec seção 8).

```markdown
# Slides — Oficina Low-Code

> Convenção visual: conceitos-chave SEMPRE em **negrito**. As respostas do
> quiz estão plantadas nesse padrão. Não quebre a convenção — é o que disfarça
> as pistas.

---

## Slide 1 — Abertura
- Título: Enriquecendo seu portfólio com IA
- O que você vai construir (mostrar preview do portfólio final)
- Um bom portfólio tem **consistência visual**, **boa navegação**,
  **responsividade** e **informações claras sobre os projetos**.  [planta Q2]

## Slide 2 — Objetivos
- Ideia → IA gera código → testo → peço melhorias → versiono
- A IA não faz tudo. Você analisa, decide e aplica.

## Slide 3 — Setup (ORDEM IMPORTA)
1. VS Code
2. Extensão Live Server
3. Git  ← depois do VS Code!
4. "Use this template" no GitHub
5. git clone
6. Open with Live Server

## Slide 4 — O que é Low-Code
- Low-code = usar **ferramentas que reduzem a quantidade de código**
  necessária para desenvolver uma aplicação.  [planta Q1]
- Não é "sem código". É "menos código manual" — a IA escreve, você guia.

## Slide 5 — HTML e CSS em 2 minutos
- HTML = estrutura (o conteúdo). CSS = aparência (cores, layout).
- Você não precisa decorar: a IA mostra onde está e gera o que falta.

## Slide 6 — Responsividade
- Um site **responsivo** adapta o **layout** a qualquer tela:
  desktop, tablet, celular.
- Se algo aparece cortado no celular, o que revisar primeiro?
  A **responsividade do layout**.  [planta Q3]

## Slide 7 — Bloco 1: IA como navegadora
- Missão 1 — "Faça o portfólio ser seu"
- 1.1 Nome, título, curso | 1.2 Foto | 1.3 Cor de fundo
- CÓDIGO DE REFERÊNCIA (para quem não achar) — ver Slide 7b

## Slide 7b — Código de referência (Missão 1)
Onde está o nome:
    <h1>NOME_AQUI</h1>
    <p>TITULO_PROFISSIONAL_AQUI — CURSO_AQUI</p>

Onde está a foto:
    <img src="assets/foto-perfil.svg" alt="Foto de NOME_AQUI">

Onde está a cor de fundo (style.css):
    :root {
      --cor-fundo: #f4f4f9;   /* troque este valor */
    }

## Slide 8 — Checkpoint Git #1
    git add .
    git commit -m "personalização inicial do portfólio"
- add = seleciona o que vai no commit
- commit = tira uma "foto" do projeto
- mensagem = descreve o que mudou

## Slide 9 — Como escrever bons prompts
- Prompt fraco: "Crie um site bonito." / "Faça um portfólio profissional."
- Prompt forte: contexto + requisitos técnicos + formato esperado.
- Ex.: "Crie um portfólio **responsivo** com **componentes reutilizáveis**,
  **seção de projetos**, **navegação mobile** e **layout adaptável** para
  desktop, tablet e smartphone."  [planta Q4 — opção C]

## Slide 10 — Bloco 2: IA como criadora
- Missão 2 — "Deixe a IA trabalhar por você"
- 2.1 Sobre mim | 2.2 Habilidades | 2.3 Novo projeto
- CÓDIGO DE REFERÊNCIA — ver Slide 10b

## Slide 10b — Código de referência (Missão 2)
Seção Sobre mim:
    <section class="sobre">
      <h2>Sobre mim</h2>
      <p>ESCREVA_AQUI_UM_PARAGRAFO_SOBRE_VOCE</p>
    </section>

Seção Habilidades:
    <div class="habilidades-lista">
      <span>HABILIDADE_1</span>
      <span>HABILIDADE_2</span>
      <span>HABILIDADE_3</span>
    </div>

Card de projeto (copie o bloco inteiro para adicionar outro):
    <div class="card-projeto">
      <img src="assets/projeto.svg" alt="Capa do projeto">
      <div class="conteudo">
        <h3>NOME_DO_PROJETO</h3>
        <p>DESCRICAO_CURTA_DO_PROJETO</p>
        <a href="#">Ver projeto</a>
      </div>
    </div>

## Slide 11 — Checkpoint Git #2
    git add .
    git commit -m "novas seções geradas com IA"
- Por que commitamos: histórico, segurança, poder voltar atrás.

## Slide 12 — Publicação
- Subir o site para o GitHub e torná-lo público é fazer o **deploy**.  [planta Q5]
- git push → GitHub Pages → seu site no ar.

## Slide 13 — Quiz (15 min)
- 5 perguntas. Quem prestou atenção já viu todas as respostas. 😉
```

- [ ] **Step 2: Conferir que as 5 respostas do quiz estão plantadas**

Checklist: Q1 no Slide 4, Q2 no Slide 1, Q3 no Slide 6, Q4 no Slide 9, Q5 no Slide 12. Cada uma em negrito, dentro da convenção de estilo.

- [ ] **Step 3: Conferir que os trechos de código de referência cobrem todas as missões**

Missão 1 (nome, foto, cor) no Slide 7b. Missão 2 (sobre, habilidades, card) no Slide 10b. Os trechos batem exatamente com o `index.html`/`style.css` das Tasks 2 e 4.

- [ ] **Step 4: Commit**

```bash
git add slides.md
git commit -m "docs: adiciona conteudo dos slides com respostas do quiz plantadas"
```

---

## Task 7: `docs/roteiro-instrutora.md` — roteiro de condução

**Files:**
- Create: `docs/roteiro-instrutora.md`

- [ ] **Step 1: Escrever o roteiro minuto a minuto**

```markdown
# Roteiro da Instrutora — minuto a minuto (180 min)

| Tempo | Bloco | O que fazer |
|-------|-------|-------------|
| 0:00–0:20 | Abertura + Setup | Slides 1-3. Circular pela sala garantindo que todos instalaram VS Code → Live Server → Git NESSA ordem. Todos com "Use this template" feito e clonado. |
| 0:20–0:40 | Teoria mínima | Slides 4-6. Low-code, HTML/CSS, responsividade. Falar devagar nos termos em negrito. |
| 0:40–1:30 | Bloco 1 | Slides 7-8. Missão 1 (35 min) + Checkpoint Git #1 (10 min guiado, resto buffer). Mostrar Slide 7b para quem não achar o código. |
| 1:30–1:50 | Prompts | Slide 9. Comparar prompt fraco vs forte ao vivo no ChatGPT. |
| 1:50–2:40 | Bloco 2 | Slides 10-11. Missão 2 (35 min) + Checkpoint Git #2 (10 min). Mostrar Slide 10b. |
| 2:40–2:45 | Publicação | Slide 12. git push ao vivo + ativar GitHub Pages. |
| 2:45–3:00 | Quiz | Slide 13. Aplicar o quiz oficial. |

## Lembretes
- SEM intervalo.
- Ordem de instalação: VS Code ANTES do Git (senão dá erro).
- Buffer de ~5 min por bloco para quem ficar para trás.
- Iniciantes seguem a missão literal; experientes podem ir além nos prompts.
```

- [ ] **Step 2: Conferir consistência com o cronograma da spec**

Os horários batem com a spec seção 5. Sem intervalo. Ordem de instalação correta.

- [ ] **Step 3: Commit**

```bash
git add docs/roteiro-instrutora.md
git commit -m "docs: adiciona roteiro minuto a minuto da instrutora"
```

---

## Self-Review (preenchido pela autora do plano)

**Cobertura da spec:**
- Objetivo/filosofia → README + slides + estrutura das missões ✓
- 5 seções do portfólio → Task 4 ✓
- Template Repository → Task 5 Step 1 ✓
- Fluxo use-template → clone → push → Task 1 (README) + Task 5 ✓
- Missão 1 (leitura) + Missão 2 (geração) → código de referência em Task 6 (7b, 10b) ✓
- 2 checkpoints de Git → Slides 8 e 11 + Task 5 Step 4 ✓
- Quiz com 5 respostas plantadas → Task 6 Step 2 ✓
- Ordem VS Code → Git → Task 1 Step 1 + Task 7 ✓
- Código de referência nos slides → Task 6 (7b, 10b) ✓
- Responsividade (Q3) → Task 2 media query + Task 4 Step 3 ✓

**Scan de placeholders:** Nenhum "TBD/TODO" no plano. Os placeholders MAIÚSCULOS dentro do `index.html` são conteúdo intencional (alvos das missões), não lacunas do plano.

**Consistência de tipos/nomes:** Classes CSS (`.card-projeto`, `.habilidades-lista`, `--cor-fundo`) idênticas entre Task 2 (CSS), Task 4 (HTML) e Task 6 (slides de referência). Caminhos de asset (`assets/foto-perfil.svg`, `assets/projeto.svg`) idênticos entre Task 3, Task 4 e Task 6.

**Itens adiados da spec seção 10 (decisões da instrutora, fora do escopo da produção):** paleta/fonte definitiva — valores padrão já fornecidos no CSS, trocáveis; ferramenta de slides — `slides.md` serve de fonte de conteúdo para converter depois.
