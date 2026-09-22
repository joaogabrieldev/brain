<div align="center">

# 🧠 brain

![Claude Code](https://img.shields.io/badge/Claude_Code-Agent_Skills-D97757?style=for-the-badge&logo=anthropic&logoColor=white)
![Cursor](https://img.shields.io/badge/Cursor-Compat%C3%ADvel-0A0A0A?style=for-the-badge)
![Markdown](https://img.shields.io/badge/Markdown-SKILL.md-000000?style=for-the-badge&logo=markdown&logoColor=white)
![Python](https://img.shields.io/badge/Python-Scripts-3776AB?style=for-the-badge&logo=python&logoColor=white)
![PT-BR](https://img.shields.io/badge/Sa%C3%ADda-PT--BR-009C3B?style=for-the-badge)

[![Skills](https://img.shields.io/badge/Skills-5_autorais-6E56CF?style=for-the-badge&logo=anthropic&logoColor=white)](#-skills-disponíveis)
[![SkillDrop](https://img.shields.io/badge/SkillDrop-.skill_%E2%86%92_.zip-111111?style=for-the-badge&logo=vercel&logoColor=white)](https://projeto-skilldrop.vercel.app)
[![GitHub](https://img.shields.io/badge/GitHub-joaogabrieldev-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/joaogabrieldev)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-joaogabrielrocha-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/joaogabrielrocha)

O sistema nervoso central dos meus agentes de IA — um cofre de **skills autorais** que transformam Claude Code e Cursor em especialistas com método, e não em geradores de palpite.

</div>

---

## 📑 Índice

- [🧩 Skills disponíveis](#-skills-disponíveis)
- [📖 Sobre](#-sobre)
- [🧱 Padrões e Fundamentos](#-padrões-e-fundamentos)
- [🛠️ Tecnologias e Bibliotecas](#️-tecnologias-e-bibliotecas)
- [🗂️ Estrutura do Projeto](#️-estrutura-do-projeto)
- [⚙️ Como rodar localmente](#️-como-rodar-localmente)
- [👨‍💻 Contato](#-contato)

---

## 🧩 Skills disponíveis

Repositório oficial:

### 🔗 [github.com/joaogabrieldev/brain](https://github.com/joaogabrieldev/brain)

> **Todas as skills abaixo foram escritas por mim** (João Gabriel R. Rocha). Não são forks nem cópias de pacotes de terceiros: cada `SKILL.md`, cada arquivo de `references/`, cada template de relatório e cada script de auditoria nasceu aqui, a partir de auditorias e projetos reais.

| Skill | O que faz | Aciona quando você diz |
|---|---|---|
| 🛡️ **[appsec-universal](#️-appsec-universal)** | Auditoria AppSec sênior agnóstica de linguagem, em modo zero-tolerância | "audita a segurança", "isso é seguro?", "está pronto para produção?" |
| 🏗️ **[ci-pipeline-auditor](#️-ci-pipeline-auditor)** | Audita a esteira de GitHub Actions e pluga o SonarQube como quality gate bloqueante | "audita minha esteira", "implementa SonarQube", "hardening de Actions" |
| 🔎 **[deep-research](#-deep-research)** | Pesquisa profunda na web com triangulação de fontes e síntese citada | "pesquisa a fundo", "estado da arte de", "faz um levantamento completo" |
| 📐 **[prd-max-extractor](#-prd-max-extractor)** | Converte um PRD em fundação spec-driven para React/Next.js + TypeScript | "extrai o máximo desse PRD", "transforma esse PRD em código" |
| 📄 **[readme-creator](#-readme-creator)** | Gera READMEs completos no meu padrão visual (este aqui saiu dela) | "cria o README", "atualiza o README desse projeto" |

---

### 🛡️ appsec-universal

Auditor AppSec de primeira linha para **qualquer** linguagem — Python (Django/Flask/FastAPI), Go, Rust, PHP (Laravel), Java (Spring), Ruby (Rails), C#/.NET e o que vier.

- **10 protocolos de auditoria**: injeção (SQL/NoSQL/OS/LDAP), validação multicamada, sessão e autenticação, criptografia e segredos, XSS/CSRF/CORS, deserialização insegura, SSTI, path traversal e upload, SSRF, exposição de dados e logging.
- Ancorado em **OWASP Top 10** e **Defesa em Profundidade**, com mentalidade de privilégio mínimo e Zero Trust.
- **Delega** para skills dedicadas quando detecta TypeScript/Node/Next/Bun ou Swift/Kotlin/React Native.
- Entrega correções como **arquivo completo, nunca diff**, seguidas de checklist de verificação por ecossistema (`bandit`, `gosec`, `brakeman`, `govulncheck`, `pip-audit`…).

### 🏗️ ci-pipeline-auditor

Auditoria de esteira **GitHub Actions** + implantação de **SonarQube** como gate bloqueante, em 7 fases e 5 modos de operação (auditoria, remediação, implantação Sonar, esteira nova, encaminhamento).

- **4 eixos**: cadeia de suprimentos e segredos · confiabilidade e custo · SonarQube · governança do repositório.
- Cobre SHA pinning, `permissions` mínimas, template injection, `pull_request_target`, OIDC, timeouts, `concurrency` e actions deprecadas.
- **Veredito determinístico** (✅ Aprovada · ⚠️ Com ressalvas · ❌ Reprovada · 🚨 Bloqueada) + **nota de maturidade 0–100**.
- Inclui auditor estático próprio em Python (`audit_workflows.py`) e workflows hardened prontos em `assets/`.
- Padrões: **OpenSSF Scorecard**, **SLSA**, **OWASP CI/CD Top 10**, **Sonar Clean as You Code**.

### 🔎 deep-research

Skill de **processo**: define como pesquisar, não o que responder.

- Fluxo obrigatório: planejar → buscar amplo → ler fontes → **triangular** → revisar cobertura → sintetizar com fontes.
- **Escala de esforço** proporcional ao pedido e critério explícito de parada.
- Contrato de saída fixo: resumo executivo, seções por sub-pergunta, tabela comparativa, divergências e limitações, e lista final de fontes.
- **Guardrails anti-alucinação invioláveis** — nada de responder a partir de um único trecho de buscador.

### 📐 prd-max-extractor

Transforma um PRD (PDF, doc, markdown ou texto colado) na fundação de um projeto React/Next.js + TypeScript, pelo padrão **spec → contracts → design → roadmap → build**.

- **7 fases**, com as fases 1.5 (clarificação) e 4.5 (análise) funcionando como **gates** que não podem ser atravessados em silêncio.
- Trava os **contratos de dados** antes de qualquer tela: tipos + Zod + services de fetch.
- Design system **derivado do PRD**, sem paleta fixa imposta.
- Build loop resiliente: todo componente com dados entrega estados de **loading, error e empty**.
- Stack assumida: Next.js, TypeScript, **TailwindCSS v4** (CSS-first, sem `tailwind.config.js`) e Zod.

### 📄 readme-creator

Gera READMEs completos **em português**, no meu padrão visual — badges `for-the-badge`, blocos centralizados, emojis temáticos nos H2 e ícones de devicon/skillicons/simpleicons.

- Coleta as informações que faltam **antes** de escrever, agrupadas em no máximo 3 perguntas.
- Estrutura obrigatória com catálogo de ícones e template base em `references/`.
- Checklist de validação antes da entrega + lista explícita de anti-padrões.
- Sabe **atualizar** um README existente preservando o que já está bom.

---

## 📖 Sobre

**brain** é o meu repositório de contexto para agentes de IA. Em vez de repetir o mesmo briefing a cada conversa — "audita com rigor", "responda em PT-BR", "não invente biblioteca" —, esse conhecimento está versionado aqui como skills empacotadas, prontas para serem carregadas pelo Claude Code ou pelo Cursor.

A ideia é simples: **um agente genérico chuta; um agente com skill segue método.** Cada skill deste cofre carrega o processo que eu uso de verdade — as fases, os critérios de severidade, os formatos de relatório e as regras que não se negociam.

- **Autoria própria** — as 5 skills foram escritas por mim, do frontmatter ao último arquivo de referência.
- **Engenharia de contexto, não prompt solto** — instruções longas moram em `references/`, carregadas só quando a fase exige.
- **Cobertura ponta a ponta** — segurança de aplicação, segurança de esteira, pesquisa, arquitetura de produto e documentação.
- **Saída em português do Brasil** — relatórios, achados e checklists em PT-BR; só nomes técnicos permanecem em inglês.
- **Portátil** — cada skill é um `.skill` (ZIP) autocontido, sem dependência de runtime além do próprio agente.

---

## 🧱 Padrões e Fundamentos

O projeto segue fundamentos importantes de arquitetura:

- **Progressive disclosure** (`SKILL.md` enxuto na raiz e material pesado em `references/`, lido sob demanda para não estourar o contexto);
- **Frontmatter como contrato de acionamento** (`name` + `description` com gatilhos *e* anti-gatilhos explícitos, para a skill disparar na hora certa e ficar calada no resto);
- **Fases e gates explícitos** (nenhuma skill pula etapa: reconhecimento antes de auditar, contratos antes de tela, plano antes de busca);
- **Severidade por impacto, não por esforço** (escalas 🔴 🟠 🟡 🔵 com veredito determinístico, sem "provavelmente está ok");
- **Guardrails invioláveis** (regras anti-alucinação e anti-atalho que sobrevivem a qualquer reformulação do pedido);
- **Delegação entre skills** (cada skill conhece seus limites e encaminha para a especialista quando a stack foge do escopo);
- **Contrato de idioma** (raciocínio interno livre, entregável sempre em PT-BR);
- **Empacotamento versionado** em arquivos `.skill` (ZIP) rastreados pelo Git.

---

## 🛠️ Tecnologias e Bibliotecas

<div align="center">
  <img src="https://skillicons.dev/icons?i=githubactions,github,git,py,bash,md,vscode" alt="Stack principal" />
</div>

### 🚀 Stack principal

- **Claude Code / Agent Skills** (formato `SKILL.md` + `references/` + `assets/` + `scripts/`)
- **Cursor** (mesmas skills consumidas como regras de contexto)
- **Markdown + YAML frontmatter** (linguagem de autoria das skills)
- **Python 3.9+** (auditor estático do `ci-pipeline-auditor`)

### 📚 Padrões e referências adotados

- **AppSec**: `OWASP Top 10 2021`, `Defesa em Profundidade`, `Zero Trust`, `Privilégio Mínimo`
- **CI/CD**: `OWASP CI/CD Top 10`, `OpenSSF Scorecard`, `SLSA`, `GitHub Actions security hardening`
- **Qualidade**: `SonarQube`, `Clean as You Code`, `Quality Gate bloqueante`, `Dependabot`
- **Produto & código**: `spec-driven development`, `Zod`, `Next.js`, `TailwindCSS v4`
- **Documentação**: `shields.io`, `devicon`, `skillicons`, `simpleicons`

### 🧪 Ferramentas de apoio

- `audit_workflows.py` (auditor estático de workflows, saída ranqueada e `--fail-on`)
- `workflow-ci-node-sonar.yml`, `workflow-ci-maven-sonar.yml`, `workflow-actions-gate.yml`
- `sonar-project.properties`, `dependabot.yml`
- `report-template.md`, `remediation-patterns.md`, `icon-catalog.md`

### 🧩 Ícones das stacks

<div align="center">
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/markdown/markdown-original.svg" width="44" height="44" alt="Markdown" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/python/python-original.svg" width="44" height="44" alt="Python" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/bash/bash-original.svg" width="44" height="44" alt="Bash" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/githubactions/githubactions-original.svg" width="44" height="44" alt="GitHub Actions" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/sonarqube/sonarqube-original.svg" width="44" height="44" alt="SonarQube" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/git/git-original.svg" width="44" height="44" alt="Git" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/github/github-original.svg" width="44" height="44" alt="GitHub" />
</div>

---

## 🗂️ Estrutura do Projeto

Cada `.skill` é um pacote ZIP autocontido — se preferir abrir sem terminal, converta para `.zip` no [SkillDrop](#-alternativa-sem-terminal--skilldrop). Descompactado, o conteúdo segue este formato:

```bash
brain/
├── appsec-universal.skill        # Auditoria AppSec agnóstica de linguagem
├── ci-pipeline-auditor.skill     # Auditoria de GitHub Actions + SonarQube
├── deep-research.skill           # Pesquisa profunda com fontes citadas
├── prd-max-extractor.skill       # PRD -> fundação spec-driven
├── readme-creator.skill          # Geração de READMEs no meu padrão
└── README.md

# Conteúdo de um pacote (exemplo: ci-pipeline-auditor.skill)
ci-pipeline-auditor/
├── SKILL.md                      # Frontmatter + fluxo de execução
├── references/                   # Material pesado, lido sob demanda
│   ├── actions-security-checklist.md
│   ├── remediation-patterns.md
│   ├── report-template.md
│   └── sonarqube-integration.md
├── assets/                       # Arquivos prontos para copiar no projeto
│   ├── dependabot.yml
│   ├── sonar-project.properties
│   ├── workflow-actions-gate.yml
│   ├── workflow-ci-maven-sonar.yml
│   └── workflow-ci-node-sonar.yml
└── scripts/
    └── audit_workflows.py        # Auditor estático (Python 3.9+ e PyYAML)
```

---

## ⚙️ Como rodar localmente

### Pré-requisitos

- `git` e `unzip`
- **Claude Code** (ou **Cursor**) instalado
- `Python 3.9+` e `PyYAML` — opcional, apenas para o `audit_workflows.py`

### Passos

```bash
git clone https://github.com/joaogabrieldev/brain.git
cd brain

# Instala todas as skills no diretório pessoal do Claude Code
mkdir -p ~/.claude/skills
for skill in *.skill; do
  unzip -o "$skill" -d ~/.claude/skills/
done
```

Para instalar apenas uma skill:

```bash
unzip -o appsec-universal.skill -d ~/.claude/skills/
```

Para deixar as skills disponíveis só em um projeto específico, troque o destino por `<seu-projeto>/.claude/skills/`. Reinicie o agente e chame a skill pelo gatilho — por exemplo, `audita a segurança desse módulo` ou `/readme-creator`.

### 📦 Alternativa sem terminal — SkillDrop

Não tem `unzip` à mão (ou está no Windows)? Um `.skill` nada mais é que um ZIP com outra extensão, e eu também criei uma ferramenta web para fazer essa conversão:

### 🔗 [projeto-skilldrop.vercel.app](https://projeto-skilldrop.vercel.app)

- **100% client-side** — a conversão roda no próprio navegador com **JSZip**; nenhum byte sai do seu dispositivo, sem backend, upload, login ou analytics;
- **Arraste e solte** vários `.skill` de uma vez e baixe cada `.zip` convertido;
- **Validação** por arquivo (extensão `.skill` e limite de 500 MB) e **deduplicação** de nomes no download;
- **Remove a pasta raiz redundante** quando todo o conteúdo do pacote está sob um único diretório.

Depois de baixar o `.zip`, é só descompactar dentro de `~/.claude/skills/` — o resultado é idêntico ao do `unzip`.

Repositório do projeto: [github.com/joaogabrieldev/projeto-skilldrop](https://github.com/joaogabrieldev/projeto-skilldrop)

### Scripts úteis

- `unzip -l <skill>.skill` -> inspecionar o conteúdo do pacote sem instalar
- `zip -r <skill>.skill <skill>/` -> reempacotar a skill após editá-la
- `python3 ~/.claude/skills/ci-pipeline-auditor/scripts/audit_workflows.py .` -> auditoria estática da esteira
- `python3 .../audit_workflows.py . --json --fail-on HIGH` -> saída em JSON para uso dentro de CI

---

## 👨‍💻 Contato

<div align="center">

### João Gabriel R. Rocha

[![GitHub](https://img.shields.io/badge/GitHub-joaogabrieldev-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/joaogabrieldev)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-joaogabrielrocha-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/joaogabrielrocha)
[![Portfólio](https://img.shields.io/badge/Site-joaogabriel.dev-0A0A0A?style=for-the-badge&logo=googlechrome&logoColor=white)](https://joaogabriel.dev)

</div>

---

<div align="center">
Feito com ❤️, Markdown e muito café.
</div>
