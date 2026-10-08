# Oficina: "Enriquecendo seu portfólio com IA — criação de websites profissionais com low-code"

**Data do design:** 2026-10-08
**Duração:** 3 horas (180 min)
**Formato:** Presencial, laboratório de informática universitário (todos com computadores)
**Repositório de materiais:** https://github.com/marianarocha-dev/OficinaLowCode

---

## 1. Objetivo

Ao final das 3 horas, cada participante sai com:

- Um portfólio pessoal simples e profissional, publicado no GitHub **deles**
- Noção básica de HTML e CSS (sem dominar as linguagens)
- Experiência usando IA para gerar e melhorar código
- Noção de como escrever prompts mais eficientes
- Um projeto versionado com Git
- Uma base personalizável depois da oficina

**Filosofia central:**
> "Eu tenho uma ideia → uso IA para transformar a ideia em código → testo → identifico problemas → peço melhorias → versiono meu trabalho."

A IA **não faz tudo**. O aluno exercita análise: em metade das tarefas a IA apenas **mostra onde** está o código (aluno edita manualmente); na outra metade a IA **gera** o código (aluno aplica).

---

## 2. Público-alvo

Perfil variado — iniciantes e mais experientes no mesmo laboratório. A oficina deve ser fácil de explicar e funcionar para quem nunca tocou em código, mas com espaço para os experientes explorarem por conta.

**Mecanismo de nivelamento:** o template pronto é idêntico para todos. Iniciantes seguem as missões literalmente; experientes podem ir além nos prompts. Todos avançam no mesmo ritmo porque partem do mesmo ponto.

---

## 3. Ferramentas

| Função | Ferramenta | Observação |
|---|---|---|
| Geração de código via IA | **ChatGPT** (plano gratuito) | Interface web, sem instalação |
| Edição e visualização | **VS Code + Live Server** | Instalação necessária na máquina |
| Versionamento | **Git pelo terminal** | Instalação necessária na máquina |
| Hospedagem | **GitHub** + GitHub Pages (bônus) | Conta criada na hora |

**Ordem de instalação obrigatória: VS Code + Live Server PRIMEIRO, Git DEPOIS.** Instalar Git antes do VS Code pode causar erro de instalação na máquina.

---

## 4. Abordagem pedagógica

**Opção escolhida: Portfólio funcional desde o minuto 1.**

Clone → visualização imediata do portfólio no browser → missões que modificam o que já está na tela. Teoria é explicada no momento em que aparece na prática. Checkpoints de Git distribuídos ao longo. Ao final, `git push` para o GitHub do aluno.

Técnicas aplicadas:
- **Aprendizado ativo com scaffolding** — estrutura pronta, mas o aluno interage obrigatoriamente com ela
- **Pistas de recuperação** — respostas do quiz plantadas na apresentação (ver seção 7)

---

## 5. Cronograma (180 min)

| Horário | Bloco | Duração |
|---|---|---|
| 0:00 – 0:20 | Abertura + Setup | 20 min |
| 0:20 – 0:40 | Teoria mínima | 20 min |
| 0:40 – 1:30 | **Bloco 1 — IA como navegadora** (Missão 1 + Checkpoint Git #1) | 50 min |
| 1:30 – 1:50 | Como escrever bons prompts | 20 min |
| 1:50 – 2:40 | **Bloco 2 — IA como criadora** (Missão 2 + Checkpoint Git #2) | 50 min |
| 2:40 – 2:45 | Publicação rápida — push + GitHub Pages ao vivo | 5 min |
| 2:45 – 3:00 | **Quiz oficial** | 15 min |

**Sem intervalo.** Teoria só entra quando há prática imediata na sequência.

---

## 6. Estratégia do Repositório GitHub

Configurar `marianarocha-dev/OficinaLowCode` como **Template Repository** (não Fork).

**Por quê Template e não Fork:**

| | Fork | Template |
|---|---|---|
| Aparece "forked from X" no perfil | Sim | Não |
| Repo independente e totalmente do aluno | Não | Sim |
| Histórico de commits limpo | Não | Sim |

**Como configurar (feito uma vez pela instrutora):**
1. Acessar `github.com/marianarocha-dev/OficinaLowCode`
2. **Settings** → seção **General**
3. Marcar o checkbox **"Template repository"** (salva automaticamente)

**Fluxo do aluno:**
1. Acessa o repositório da oficina
2. **"Use this template" → "Create a new repository"**
3. Nomeia (ex: `meu-portfolio`)
4. `git clone https://github.com/SEU-USUARIO/meu-portfolio.git`
5. Trabalha localmente durante a oficina
6. Final: `git push` → portfólio publicado no GitHub dele

**Estrutura do repositório:**
```
OficinaLowCode/
├── index.html       ← portfólio com placeholders explícitos (NOME_AQUI, CURSO_AQUI, etc.)
├── style.css        ← estilos do layout
├── assets/
│   ├── foto-perfil.jpg   ← imagem placeholder
│   └── projeto.jpg       ← imagem placeholder de projeto
└── README.md        ← instruções de setup, passo a passo
```

O `index.html` precisa conter:
- As 5 seções prontas: Hero, Sobre mim, Habilidades, Projetos, Contato
- Pelo menos 1 card de projeto como exemplo (base da Missão 2.3)
- Placeholders em maiúsculas, fáceis de identificar

---

## 7. Missões

Tipos: **[LEITURA]** = IA mostra onde está, aluno edita manualmente; **[GERAÇÃO]** = aluno escreve prompt, IA gera, aluno aplica.

### Missão 1 — "Faça o portfólio ser seu" (Bloco 1, ~35 min)

**1.1 [LEITURA] — Identifique seus dados pessoais**
> Cole todo o `index.html` no ChatGPT: *"Esse é o código do meu portfólio. Me mostre exatamente onde estão o nome, título profissional e curso no HTML"*

Aluno lê o trecho destacado e edita manualmente no VS Code.

**1.2 [LEITURA] — Troque a foto de perfil**
> *"Me mostre onde está a imagem de perfil e me explique como trocar por outra"*

**1.3 [GERAÇÃO] — Mude a cor de fundo**
> *"Altere apenas a cor de fundo da página para [cor desejada]. Me mostre só o trecho do CSS que preciso substituir"*

**Checkpoint Git #1 (~10 min, guiado):**
```bash
git add .
git commit -m "personalização inicial do portfólio"
```
Explicar: o que é `add`, `commit`, e a mensagem de commit.

### Missão 2 — "Deixe a IA trabalhar por você" (Bloco 2, ~35 min)

**2.1 [GERAÇÃO] — Gere o texto "Sobre mim"**
> *"Sou [nome], [área], atualmente [o que faz/estuda]. Escreva um parágrafo curto e profissional para a seção 'Sobre mim' do meu portfólio"*

**2.2 [GERAÇÃO] — Personalize a seção de Habilidades**
> Cole o trecho da seção: *"Aqui está o código da minha seção de habilidades. Adicione: [lista]. Mostre apenas o HTML modificado dessa seção"*

**2.3 [GERAÇÃO] — Adicione um projeto real**
> Cole o HTML de um card existente: *"Aqui está um card de projeto. Crie um card igual para: [projeto, tecnologias, link]. Mostre apenas o HTML do novo card"*

**Checkpoint Git #2 (~10 min, guiado):**
```bash
git add .
git commit -m "novas seções geradas com IA"
```
Reforçar: por que commitamos — histórico, segurança, colaboração.

---

## 8. Quiz oficial e mapeamento das respostas

15 min ao final. Respostas plantadas nos slides em **negrito**, como estilo visual consistente (conceitos-chave sempre em negrito ao longo de toda a apresentação) — não como dica óbvia. Quem prestou atenção reconhece.

| # | Pergunta | Resposta | Onde a resposta é plantada |
|---|---|---|---|
| 1 | O que significa desenvolver com Low-Code? | **B** — ferramentas que reduzem a quantidade de código necessária | Slide de Teoria — definição de low-code |
| 2 | O que torna um portfólio profissional? | **D** — consistência visual, boa navegação, responsividade, informações claras | Slide de abertura |
| 3 | Site cortado no celular — o que revisar? | **A** — responsividade do layout | Bloco 1, ao mostrar o template funcionando |
| 4 | Qual prompt produz melhor resultado técnico? | **C** — prompt específico com contexto + requisitos técnicos | Slide de prompts — bom vs mau prompt |
| 5 | Como disponibilizar o site publicamente? | **B** — deploy | Slide de publicação |

**Perguntas completas (gabarito):**

1. O que significa desenvolver um website utilizando Low-Code?
   A) Criar um site sem utilizar nenhuma tecnologia de programação
   B) Utilizar ferramentas que reduzem a quantidade de código necessária para desenvolver uma aplicação ✓
   C) Utilizar apenas inteligência artificial para escrever todo o código
   D) Criar somente sites estáticos utilizando HTML

2. Qual destes elementos contribui para que um website de portfólio tenha aparência mais profissional?
   A) Utilizar o maior número possível de animações
   B) Colocar todas as informações em uma única página sem organização
   C) Utilizar várias fontes e cores diferentes para chamar atenção
   D) Manter consistência visual, boa navegação, responsividade e informações claras sobre os projetos ✓

3. IA gerou site que funciona no computador mas tem elementos cortados no celular. Qual conceito revisar prioritariamente?
   A) Responsividade do layout ✓
   B) Autenticação
   C) DNS
   D) Banco de dados

4. Qual prompt tende a produzir resultado técnico mais adequado?
   A) "Crie um site bonito."
   B) "Faça um portfólio profissional."
   C) "Crie um portfólio responsivo utilizando React, com componentes reutilizáveis, seção de projetos, navegação mobile e layout adaptável para desktop, tablet e smartphone." ✓
   D) "Crie o melhor site possível com o contexto de portfolio pessoal."

5. Após desenvolver localmente, qual processo disponibiliza o site publicamente?
   A) Compilação
   B) Deploy ✓
   C) Debugging
   D) Refatoração

---

## 9. Materiais a produzir (entregáveis)

### Repositório
- [ ] `index.html` — 5 seções, placeholders em maiúsculas, ≥1 card de projeto
- [ ] `style.css` — estilos do layout, responsivo
- [ ] `assets/foto-perfil.jpg` e `assets/projeto.jpg` — placeholders
- [ ] `README.md` — instruções de setup passo a passo
- [ ] Repositório marcado como Template no GitHub

### Slides
| Bloco | Conteúdo |
|---|---|
| Abertura | Título, objetivos, preview do portfólio final (planta Q2) |
| Setup | Passo a passo: **VS Code → Live Server → Git** → GitHub → clone |
| Teoria mínima | Low-code (planta Q1), HTML/CSS em 2 min, responsividade (planta Q3) |
| Bloco 1 | Enunciado Missão 1 + **trechos de código de referência** (nome, foto, cor de fundo) |
| Prompts | Anatomia de bom prompt (planta Q4), exemplos lado a lado |
| Bloco 2 | Enunciado Missão 2 + **trechos de código de referência** (card de projeto, habilidades) |
| Publicação | git push, GitHub Pages, deploy (planta Q5) |
| Quiz | 5 perguntas |

**Requisito dos slides:** incluir o código de referência de cada trecho (card, seção de habilidades, etc.) para os alunos que não conseguirem localizar sozinhos.

### Checklist pré-oficina
- [ ] Repositório criado e configurado como Template
- [ ] Todos os arquivos no repositório
- [ ] Slides prontos com trechos de código visíveis
- [ ] Conta GitHub da instrutora
- [ ] Testar fluxo completo uma vez (template → clone → editar → push)

---

## 10. Decisões em aberto (para a fase de materiais)

- Definir a identidade visual do template (paleta de cores, fonte) antes de gerar `index.html`/`style.css`
- Confirmar o conteúdo exato de cada "trecho de código de referência" que vai nos slides
- Decidir ferramenta de slides (PowerPoint, Google Slides, etc.)
