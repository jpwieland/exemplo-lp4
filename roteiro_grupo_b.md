# 🟢 Roteiro Git — Grupo B / Squad Features
### Atividade prática de versionamento com Git e GitHub

---

> **Seu papel hoje:** Você é **Desenvolvedor(a) Full Stack** na startup DevSpace.
> O Tech Lead (Grupo A) fez um fork do repositório do professor e é o dono do repositório oficial.
> Você vai fazer um **fork do repositório deles** e contribuir com novas funcionalidades.
> Vocês trabalham em paralelo **sem combinar o código** — os conflitos vão surgir naturalmente.
>
> Em algum momento você vai descobrir que alguém já mexeu no código que você também mexeu.
> Isso vai gerar um conflito de merge — e você vai resolver de forma profissional, sem entrar em pânico.

---

## ⏱ Visão geral do tempo

| Fase | O que fazer | Tempo |
|------|-------------|-------|
| **1** | Fazer fork do repositório do Grupo A | 10 min |
| **2** | Abrir o Codespaces, criar branch e ativar o preview | 15 min |
| **3** | Desenvolver as funcionalidades | 30 min |
| **4** | Commitar e enviar para o GitHub | 10 min |
| **5** | Criar o PR e descobrir o conflito | 10 min |
| **6** | Resolver o conflito no Codespaces | 25 min |
| **7** | Enviar a versão corrigida | 5 min |
| **8** | Reflexão final | 10 min |

---

## 🗂 Legenda visual — o que você vai encontrar no GitHub

```
[ Botão ]         → Botão clicável (verde, azul ou cinza)
< Campo >         → Campo de texto para digitar
  ↳ Submenu       → Opção dentro de um menu ou aba
⚙ Ícone          → Ícone na interface
📁 Seção          → Área da página
```

---

## 📋 FASE 1 — Fazer fork do repositório do Grupo A
### ⏱ ~10 minutos

> ⏳ **Aguarde o Grupo A enviar a URL do fork deles antes de começar esta fase.**

### 1.1 — Entendendo a cadeia de forks desta atividade

```
Repositório do Professor (original)
        ↓  fork
Repositório do Grupo A (Tech Lead)  ← você vai fazer fork DESTE
        ↓  fork
Seu repositório (Grupo B)
```

No mundo real, esse é o fluxo clássico de **contribuição em projetos open source**:
você não tem permissão de escrever direto no repo principal — então faz um fork,
desenvolve na sua cópia, e manda um Pull Request pedindo para incluir suas mudanças.

### 1.2 — Fazer o fork do repositório do Grupo A

1. Acesse a URL que o Grupo A enviou:
   ```
   https://github.com/USUARIO_DO_GRUPO_A/devspace-site
   ```

2. No canto superior direito, clique no botão **`[ Fork ]`**
   *(ícone de bifurcação — duas setas divergindo)*

3. Na página seguinte, verifique:

   | Campo | O que fazer |
   |-------|------------|
   | `Owner` | Deve ser **seu** nome de usuário |
   | `Repository name` | Mantenha `devspace-site` |
   | `Copy the main branch only` | ✅ **Marque esta opção** |

4. Clique em **`[ Create fork ]`**

> 📘 **Como confirmar que deu certo?**
> No topo da página você verá:
> ```
> SEU_USUARIO / devspace-site
> forked from USUARIO_GRUPO_A/devspace-site
> ```

### 1.3 — Explorar o projeto antes de começar

Antes de alterar qualquer coisa, leia o código. Bons desenvolvedores entendem
o que já existe antes de adicionar coisas novas.

Clique em cada arquivo e responda:

**`index.html`:**
- Quantas seções (`<section>`) a página tem?
- Onde ficam os comentários `<!-- GRUPO B: ... -->`? São 2 lugares.
- O que é a classe `hero-slogan`? E `hero-subtitulo`?

**`estilo.css`:**
- Onde ficam as variáveis CSS (dentro de `:root`)?
- Se você mudar `--cor-primaria`, em quantos lugares o site vai mudar?

> 🤔 **Reflita:** Os comentários `<!-- GRUPO B: adicionar aqui -->` foram deixados pelo professor.
> Em projetos reais, esses "lugares reservados" seriam definidos em reuniões de planejamento.

---

## 📋 FASE 2 — Abrir o Codespaces, criar branch e ativar o preview
### ⏱ ~15 minutos

### 2.1 — Criar um Codespace no **seu fork**

1. Na página do **seu fork** *(não o do Grupo A!)*, clique no botão verde **`[ <> Code ]`**

2. Clique na aba **`Codespaces`**

3. Clique em **`[ Create codespace on main ]`**

4. **Aguarde** o Codespaces carregar (~30s a 2min na primeira vez)

> ⚠️ **Atenção:** Confirme que a URL da página tem o **seu** nome de usuário,
> não o do Grupo A. Você deve criar o Codespace no seu próprio fork.

### 2.2 — Reconhecer o ambiente

```
┌─────────────────────────────────────────────────────┐
│  BARRA DE MENUS (File, Edit, View...)               │
├──────────┬──────────────────────────────────────────┤
│          │                                          │
│ PAINEL   │                                          │
│ LATERAL  │         EDITOR DE CÓDIGO                 │
│          │     (aqui você edita os arquivos)        │
│ 📁 Files │                                          │
│ 🔍 Search│                                          │
│ 🌿 Git   │                                          │
│          │                                          │
├──────────┴──────────────────────────────────────────┤
│                                                      │
│              TERMINAL INTEGRADO                      │
│         (aqui você digita comandos git)              │
│                                                      │
└─────────────────────────────────────────────────────┘
```

Se o terminal não estiver visível:
- Pressione **Ctrl + `` ` ``** (acento grave, tecla abaixo do Esc)
- *OU:* Clique em **`View`** → **`Terminal`**

### 2.3 — Verificar o ambiente e criar a branch

No terminal:

```bash
git log --oneline
```
> Veja os commits que vieram do repositório do Grupo A (que vieram do professor).
> Você herdou todo o histórico do projeto.

```bash
git branch -a
```
> 📘 Lista todas as branches, incluindo as remotas (prefixo `remotes/origin/`).
> O `-a` significa "all" (todas). Você só deve ver `main` por enquanto.

```bash
git checkout -b feature/novos-servicos
```
> 📘 Cria a branch `feature/novos-servicos` e já entra nela.

```bash
git branch
```
> Confirme: deve aparecer `* feature/novos-servicos`

---

### 2.4 — 👁 Ativar o preview do site em tempo real

> 🎯 **Imprescindível!** Você vai criar um mini-servidor local para ver as mudanças
> do HTML/CSS instantaneamente no navegador — sem instalar nada.

No terminal, execute:

```bash
python3 -m http.server 8080
```

Você verá:
```
Serving HTTP on 0.0.0.0 port 8080 (http://0.0.0.0:8080/) ...
```

**Abra o site em uma nova aba do navegador:**

Uma janela popup aparecerá no canto inferior direito dizendo
`"Your application running on port 8080 is available"`.
Clique em **`[ Open in Browser ]`**.

Se o popup não aparecer:
1. Clique no ícone **`Ports`** na barra de abas do terminal (ao lado de "Terminal")
2. Localize a porta `8080` na lista
3. Clique no ícone de globo 🌐 ao lado dela

> ✅ **Resultado:** O site abre no navegador com o visual completo!

**Como usar o preview durante o desenvolvimento:**
- Edite os arquivos HTML/CSS no Codespaces
- Salve com **Ctrl+S**
- No browser, pressione **F5** para ver a mudança

> 💡 **Dica:** Abra uma **segunda aba do terminal** para continuar usando o Git
> enquanto o servidor roda na primeira.
> Clique no **`+`** ao lado de "Terminal" na barra inferior.

---

## 📋 FASE 3 — Desenvolver as funcionalidades
### ⏱ ~30 minutos

> 💡 A partir daqui, use o preview para ver cada mudança antes de continuar.
> Salve → F5 no browser → confira → siga em frente.

### 3.1 — Tarefa 1: Atualizar o slogan do hero

1. No painel lateral, clique em **`index.html`**
2. Use **Ctrl+F** para buscar: `hero-slogan`
3. Você encontrará:
   ```html
   <p class="hero-slogan">Tecnologia e colaboração em um só lugar</p>
   ```
4. **Altere** para:
   ```html
   <p class="hero-slogan">Seu espaço para criar, conectar e inovar</p>
   ```
5. Salve com **Ctrl+S** → atualize o preview com **F5**

> 🤔 **Reflita:** O Grupo A está alterando esta mesma linha agora, mas com texto diferente.
> Você não sabe o que eles estão escrevendo.
> Como o Git vai lidar com isso quando as duas versões se encontrarem?

---

### 3.2 — Tarefa 2: Atualizar o subtítulo do hero

Ainda em `index.html`, localize:

```html
<p class="hero-subtitulo">
    Espaço de coworking premium para desenvolvedores, designers e startups em São Paulo.
</p>
```

**Substitua** pelo texto abaixo:

```html
<p class="hero-subtitulo">
    Conecte-se com uma comunidade de mais de 150 devs e acelere o crescimento do seu projeto.
</p>
```

Salve com **Ctrl+S** → verifique no preview.

---

### 3.3 — Tarefa 3: Renomear o título da seção de espaços

Ainda em `index.html`, use **Ctrl+F** para buscar: `Nossos Espaços`

```html
<h2>Nossos Espaços</h2>
```

**Altere** para:
```html
<h2>O Que Você Encontra Aqui</h2>
```

Salve com **Ctrl+S** → verifique no preview.

---

### 3.4 — Tarefa 4: Mudar a cor principal do site

1. No painel lateral, clique em **`estilo.css`**
2. Use **Ctrl+F** para buscar: `--cor-primaria`
3. Localize:
   ```css
   /* COR PRINCIPAL — Grupo A e Grupo B alteram esta linha */
   --cor-primaria:    #6366f1;   /* Roxo índigo — identidade visual */
   ```
4. **Altere** para:
   ```css
   /* COR PRINCIPAL — Grupo A e Grupo B alteram esta linha */
   --cor-primaria:    #10b981;   /* Verde esmeralda — frescor e inovação */
   ```
5. Salve com **Ctrl+S** → atualize o preview

> ✨ **Observe:** Todo o site muda de cor de uma vez. Isso é o poder das variáveis CSS!

> 🤔 **Reflita:** Verde = crescimento, natureza, inovação. Azul = tecnologia, confiança.
> O Grupo A vai escolher uma cor diferente. Quando conflitar, alguém vai ter que
> tomar uma decisão de produto. Quem deveria ter essa responsabilidade em uma empresa real?

---

### 3.5 — Tarefa 5: Alterar o texto do botão CTA

Ainda em `index.html`, use **Ctrl+F** para buscar: `GRUPO B: alterar o texto do botão`

Você encontrará:
```html
<!-- GRUPO B: alterar o texto do botão abaixo -->
<a href="#contato" class="btn-cta-grande">Agendar uma visita</a>
```

**Altere apenas o texto** (mantenha o HTML ao redor):
```html
<!-- GRUPO B: alterar o texto do botão abaixo -->
<a href="#contato" class="btn-cta-grande">Agendar visita gratuita →</a>
```

Salve com **Ctrl+S** → verifique o novo texto do botão no preview.

---

### 3.6 — Tarefa 6: Adicionar a seção de depoimentos

Em `index.html`, use **Ctrl+F** para buscar: `GRUPO B: adicionar seção de depoimentos`

Localize o comentário:
```html
<!-- GRUPO B: adicionar seção de depoimentos aqui -->
```

**Substitua** pelo código completo abaixo:

```html
<!-- ===== DEPOIMENTOS ===== -->
<section class="depoimentos">
    <div class="container">
        <h2>O que nossos membros dizem</h2>
        <p class="secao-subtitulo">Histórias reais de quem faz parte da nossa comunidade</p>
        <div class="depoimentos-grid">

            <div class="depoimento-card">
                <p class="depoimento-texto">
                    Entrei no DevSpace como freelancer solo e em 3 meses fechei parceria
                    com dois outros devs que conheci aqui. Hoje somos uma startup.
                </p>
                <div class="depoimento-autor">
                    <div class="autor-avatar">👩‍💻</div>
                    <div>
                        <strong>Marina Costa</strong>
                        <span>Dev Frontend · Membro desde 2022</span>
                    </div>
                </div>
            </div>

            <div class="depoimento-card">
                <p class="depoimento-texto">
                    A internet aqui é melhor que no escritório da empresa onde trabalhei
                    por 5 anos. E o café é gratuito. Não tem por que voltar para casa.
                </p>
                <div class="depoimento-autor">
                    <div class="autor-avatar">👨‍💻</div>
                    <div>
                        <strong>Rafael Torres</strong>
                        <span>Engenheiro de Software · Membro desde 2021</span>
                    </div>
                </div>
            </div>

            <div class="depoimento-card">
                <p class="depoimento-texto">
                    Usamos a sala de reunião para nossa daily remota todo dia.
                    Os clientes ficam impressionados com o ambiente profissional.
                </p>
                <div class="depoimento-autor">
                    <div class="autor-avatar">👩‍🎨</div>
                    <div>
                        <strong>Julia Nakamura</strong>
                        <span>UX Designer · Membro desde 2023</span>
                    </div>
                </div>
            </div>

        </div>
    </div>
</section>
```

Salve com **Ctrl+S** → veja a nova seção de depoimentos aparecer no preview!

> 📘 **Observe:** Esta seção é exclusivamente sua — o Grupo A não vai mexer aqui.
> Por isso ela vai entrar no merge automaticamente, sem conflito.
> O Git só pede ajuda onde **duas pessoas modificaram as mesmas linhas**.

---

### 3.7 — Conferir as mudanças antes de commitar

Na segunda aba do terminal:

```bash
git status
```
> `index.html` e `estilo.css` em vermelho (modificados, não preparados).

```bash
git diff index.html
```
> Verde com `+` = adicionado. Vermelho com `-` = removido.
> Pressione **`q`** para sair.

> 🤔 **Reflita:** Este é o momento de revisar seu trabalho.
> Em um time real, isso seria feito por um colega no code review.
> Que tipo de erro você pode pegar com `git diff` antes de commitar?

---

## 📋 FASE 4 — Commitar e enviar para o GitHub
### ⏱ ~10 minutos

### 4.1 — Adicionar os arquivos ao staging

```bash
git add index.html
```

```bash
git add estilo.css
```

Confirme:
```bash
git status
```
> Os arquivos devem aparecer em **verde** ("Changes to be committed") ✅

### 4.2 — Criar o commit

```bash
git commit -m "feat: depoimentos, novo CTA e identidade verde"
```

```bash
git log --oneline
```
> Seu commit no topo. O commit original (do professor, via Grupo A) está abaixo.

### 4.3 — Enviar a branch para o GitHub

```bash
git push origin feature/novos-servicos
```
> Envia sua branch para o **seu fork** no GitHub.
> A `main` continua intocada.

---

## 📋 FASE 5 — Criar o PR e descobrir o conflito
### ⏱ ~10 minutos

> ⚠️ **ANTES de criar o PR:** Confirme com o Grupo A que eles **já fizeram o merge**
> do PR deles. Se ainda não mergearam, aguarde — o conflito só aparece depois disso.

### 5.1 — Criar o PR apontando para o repositório do Grupo A

O PR vai do **seu fork** para o **repositório do Grupo A** — simulando uma contribuição externa.

1. Acesse **seu fork** no GitHub:
   ```
   https://github.com/SEU_USUARIO/devspace-site
   ```

2. Você verá o banner amarelo:
   ```
   feature/novos-servicos had recent pushes  [ Compare & pull request ]
   ```
   Clique em **`[ Compare & pull request ]`**

3. **VERIFIQUE O DESTINO — é muito importante:**
   - **`base repository:`** `USUARIO_GRUPO_A/devspace-site` ← o repositório deles!
   - **`base:`** `main`
   - **`head repository:`** `SEU_USUARIO/devspace-site` ← seu fork
   - **`compare:`** `feature/novos-servicos`

   > Se estiver apontando para o seu próprio fork, clique em `compare across forks`
   > e ajuste o `base repository` para o repositório do Grupo A.

4. Preencha o PR:

   **Título:**
   ```
   feat: depoimentos, novo CTA e atualização de identidade
   ```

   **Descrição:**
   ```
   ## O que foi feito neste PR

   ### Mudanças que podem gerar conflito
   - Slogan: "Seu espaço para criar, conectar e inovar"
   - Novo subtítulo do hero com foco na comunidade
   - Renomeação da seção: "O Que Você Encontra Aqui"
   - Cor primária alterada para verde esmeralda (#10b981)

   ### Funcionalidades exclusivas deste PR
   - Seção de depoimentos com 3 cards de membros reais
   - Botão CTA atualizado: "Agendar visita gratuita →"

   ## Como testar
   - Verificar seção de depoimentos abaixo dos cards de espaços
   - Confirmar que o botão CTA tem o texto atualizado
   - Verificar que a cor do site mudou para verde
   ```

5. Clique em **`[ Create pull request ]`**

### 5.2 — Descobrir o conflito

Após criar o PR, o GitHub mostrará um aviso em vermelho/laranja:

```
⚠️  This branch has conflicts that must be resolved
```

> 🤔 **Antes de continuar, responda mentalmente:**
> 1. Por que existe conflito? O que o Grupo A fez que colide com o seu trabalho?
> 2. Quais arquivos você esperava que teriam conflito?
> 3. O conflito é um problema ou uma situação normal de trabalho em equipe?

---

## 📋 FASE 6 — Resolver o conflito no Codespaces
### ⏱ ~25 minutos

> 🎯 **Objetivo:** Integrar as mudanças do Grupo A ao seu código, resolver os conflitos
> e enviar a versão corrigida.

### 6.1 — Configurar o repositório do Grupo A como fonte remota

Volte ao **Codespaces** e na segunda aba do terminal:

```bash
git remote -v
```
> Lista as fontes remotas configuradas. Você só verá `origin` (seu fork).
> Precisamos adicionar o repositório do Grupo A.

```bash
git remote add upstream https://github.com/USUARIO_GRUPO_A/devspace-site.git
```
> 📘 Registra o repositório do Grupo A com o apelido `upstream`.
> - `origin` = seu fork (onde você tem permissão de escrita)
> - `upstream` = repositório do Grupo A (de onde vêm as mudanças a integrar)

Confirme:
```bash
git remote -v
```
> Agora você deve ver tanto `origin` quanto `upstream` listados.

### 6.2 — Baixar as mudanças do Grupo A

```bash
git fetch upstream
```
> 📘 Busca as atualizações do repositório do Grupo A sem aplicar ao seu código ainda.
> É como verificar novos e-mails sem abri-los.

```bash
git log upstream/main --oneline
```
> Veja os commits do Grupo A. Você vai ver o commit com as mudanças deles.

### 6.3 — Integrar as mudanças na sua branch

```bash
git merge upstream/main
```
> 📘 Tenta juntar `upstream/main` (mudanças do Grupo A) com sua branch.
> Como os dois grupos modificaram as mesmas linhas, o Git vai pedir sua intervenção.

O terminal vai mostrar algo assim:

```
Auto-merging index.html
CONFLICT (content): Merge conflict in index.html
Auto-merging estilo.css
CONFLICT (content): Merge conflict in estilo.css
Automatic merge failed; fix conflicts and then commit the result.
```

> 📘 **Leia a mensagem:** O Git diz exatamente quais arquivos têm conflito.
> Os outros arquivos (`sobre.html`, `README.md`) foram integrados automaticamente
> porque ninguém mais os modificou.

```bash
git status
```
> Arquivos com conflito aparecem como **`both modified`** — "os dois modificaram".

---

### 6.4 — Resolver os conflitos no editor

No painel lateral do Codespaces, os arquivos com conflito têm um **`C`** ou `!` vermelho.
Vamos resolver um por um.

> 🔑 **Como ler um bloco de conflito:**
> ```
> <<<<<<< HEAD
> O que você escreveu (sua versão)
> =======
> O que o Grupo A escreveu (a versão deles, que já está na main)
> >>>>>>> upstream/main
> ```
> **Para resolver:** escolha uma versão (ou combine as duas),
> depois **apague as 3 linhas de marcadores** e salve.

---

#### Arquivo 1: `index.html`

Clique em **`index.html`** no painel lateral.

Use **Ctrl+F** para buscar `<<<<<<<` — você vai encontrar **3 blocos de conflito**.

---

**Bloco 1 — Slogan do hero:**

```
<<<<<<< HEAD
    <p class="hero-slogan">Seu espaço para criar, conectar e inovar</p>
=======
    <p class="hero-slogan">Onde grandes ideias ganham vida</p>
>>>>>>> upstream/main
```

**Suas opções:**

*Opção A — Manter sua versão (Grupo B):*
```html
    <p class="hero-slogan">Seu espaço para criar, conectar e inovar</p>
```

*Opção B — Manter a versão do Grupo A:*
```html
    <p class="hero-slogan">Onde grandes ideias ganham vida</p>
```

*Opção C — Combinar as duas:*
```html
    <p class="hero-slogan">Onde grandes ideias ganham vida, são criadas e conectam pessoas</p>
```

Escolha uma, **apague as 3 linhas de marcadores**, deixe apenas o HTML limpo. Salve com **Ctrl+S**.

---

**Bloco 2 — Subtítulo do hero:**

```
<<<<<<< HEAD
            <p class="hero-subtitulo">
                Conecte-se com uma comunidade de mais de 150 devs e acelere o crescimento do seu projeto.
            </p>
=======
            <p class="hero-subtitulo">
                O ambiente ideal para transformar suas ideias em produtos que mudam o mercado.
            </p>
>>>>>>> upstream/main
```

Escolha uma versão (ou combine), remova os marcadores, salve.

---

**Bloco 3 — Título da seção de espaços:**

```
<<<<<<< HEAD
            <h2>O Que Você Encontra Aqui</h2>
=======
            <h2>Nossos Ambientes Criativos</h2>
>>>>>>> upstream/main
```

Escolha, remova os marcadores, salve.

---

#### Arquivo 2: `estilo.css`

Clique em **`estilo.css`** no painel lateral.

Use **Ctrl+F** para buscar `<<<<<<<` — você vai encontrar **1 bloco de conflito**:

```
<<<<<<< HEAD
    --cor-primaria:    #10b981;   /* Verde esmeralda — frescor e inovação */
=======
    --cor-primaria:    #0ea5e9;   /* Azul céu — nova identidade visual */
>>>>>>> upstream/main
```

> 🤔 **Pense como designer:** Qual cor combina mais com um coworking para devs?
> Verde = crescimento, natureza. Azul = tecnologia, confiança, profissionalismo.
> Não existe resposta certa — existe a decisão que você toma e consegue justificar.

Escolha, remova os marcadores, salve.

---

### 6.5 — Verificar se todos os conflitos foram resolvidos

No terminal, execute:

```bash
grep -r "<<<<<<" .
grep -r "=======" .
grep -r ">>>>>>>" .
```

> Se algum comando retornar resultado, ainda há marcadores. Volte ao arquivo e corrija.
> Se os três comandos não retornarem nada — **todos os conflitos estão resolvidos!** ✅

**Confira o resultado no preview:**

O servidor ainda deve estar rodando (se parou, execute `python3 -m http.server 8080` de novo).
Abra o preview no browser e pressione **F5**.

> 🎉 Você vai ver o site com as mudanças dos dois grupos integradas —
> a seção de depoimentos do Grupo B convivendo com o card de mentoria do Grupo A!

### 6.6 — Criar o commit de resolução

```bash
git add index.html estilo.css
```

```bash
git status
```
> Devem aparecer em verde ✅

```bash
git commit -m "fix: resolve conflitos de merge com upstream/main

Decisões tomadas:
- Slogan: [escreva qual versão você escolheu e por quê]
- Subtítulo: [escreva qual versão você escolheu e por quê]
- Título seção: [escreva qual versão você escolheu e por quê]
- Cor primária: [escreva qual cor você escolheu e por quê]"
```

> 📘 **Boa prática:** O commit de resolução deve documentar as **decisões tomadas**.
> Daqui a 6 meses, alguém pode querer saber por que a cor mudou ou qual slogan foi escolhido.
> O histórico do Git é a memória do projeto.

```bash
git log --oneline --graph
```
> Você vai ver o ponto onde as duas branches se separaram e se uniram no seu commit.

---

## 📋 FASE 7 — Enviar a versão corrigida e atualizar o PR
### ⏱ ~5 minutos

```bash
git push origin feature/novos-servicos
```
> Envia a branch atualizada (com os conflitos resolvidos) para o seu fork.

No **GitHub**, acesse o PR que você criou:

1. No seu fork, clique na aba **`Pull requests`**
2. Clique no PR aberto
3. A mensagem de conflito deve ter desaparecido:
   ```
   ✅  This branch has no conflicts with the base branch
   ```

4. **Avise o Grupo A** que o PR está pronto para revisão e merge.

---

## 📋 FASE 8 — Reflexão Final
### ⏱ ~10 minutos

Depois que o Grupo A mergear seu PR:

```bash
git fetch upstream
git log upstream/main --oneline --graph
```
> Veja o histórico completo com as contribuições dos dois grupos se unindo.

**Discutam em conjunto (ambos os grupos):**

**Sobre os conflitos:**
1. 🤔 Em que momento exato o conflito foi "criado"? Quando você escreveu, commitou, fez push, ou ao fazer merge?
2. 🤔 Por que o Git integrou a seção de depoimentos automaticamente mas não o slogan?
3. 🤔 Quais critérios você usou para resolver os conflitos? Foram técnicos, estéticos, ou outro tipo?

**Sobre o fluxo de trabalho:**
4. 🤔 Se vocês tivessem combinado antes quem ia alterar o quê, os conflitos ainda aconteceriam?
5. 🤔 O que é mais trabalhoso: resolver um conflito de 4 linhas (hoje) ou um de 400 linhas? Como evitar o segundo?
6. 🤔 Por que faz sentido ter um Tech Lead como responsável pelo repositório principal?

**Sobre o produto:**
7. 🤔 O site final ficou como esperavam? O que fariam diferente?

---

## 🆘 Algo deu errado? Guia de recuperação rápida

**"Comecei a resolver o conflito mas me perdi, quero recomeçar"**
```bash
git merge --abort
```
> Cancela o merge em andamento e volta ao estado antes do `git merge`.

**"Fiz commit na branch errada (commitei na main)"**
```bash
git reset HEAD~1          # Desfaz o commit mas mantém os arquivos
git checkout -b feature/novos-servicos
git add .
git commit -m "sua mensagem"
```

**"Adicionei um arquivo errado ao staging"**
```bash
git restore --staged nome-do-arquivo.html
```

**"O push foi rejeitado"**
```bash
# Leia o erro. Se a main remota tem commits que você não tem:
git pull upstream main
# Resolva eventuais conflitos e então:
git push origin feature/novos-servicos
```

**"Quero ver exatamente o que o Grupo A mudou"**
```bash
git show upstream/main
```

**"O servidor de preview parou"**
```bash
python3 -m http.server 8080
```
> Execute na primeira aba do terminal e reabra a aba do browser.

---

## 📌 Dicionário de Comandos Git desta atividade

| Comando | O que faz |
|---------|-----------|
| `git log --oneline` | Histórico compacto de commits |
| `git log --oneline --graph` | Histórico visual com branches |
| `git branch` | Lista branches locais (ativa tem `*`) |
| `git branch -a` | Lista todas as branches, incluindo remotas |
| `git checkout -b nome` | Cria e entra em uma nova branch |
| `git status` | Estado atual dos arquivos |
| `git diff arquivo` | Mostra o que mudou linha a linha |
| `git add arquivo` | Prepara arquivo para o commit |
| `git commit -m "msg"` | Salva o estado com uma mensagem |
| `git push origin branch` | Envia branch para o GitHub (fork) |
| `git remote -v` | Lista fontes remotas configuradas |
| `git remote add upstream URL` | Adiciona o repositório do Grupo A como fonte |
| `git fetch upstream` | Busca atualizações do Grupo A sem aplicar |
| `git merge upstream/main` | Integra mudanças do Grupo A na branch atual |
| `git merge --abort` | Cancela um merge em andamento |
| `git restore --staged arquivo` | Remove arquivo do staging |
| `grep -r "<<<<<<" .` | Verifica se ainda há marcadores de conflito |
| `python3 -m http.server 8080` | Inicia servidor local para preview do HTML |

---

> **Parabéns!** Você passou pela experiência mais importante do trabalho colaborativo:
> descobrir um conflito, entendê-lo completamente, e resolvê-lo com consciência —
> tomando decisões reais sobre o produto, não apenas sobre o código.
>
> Todo desenvolvedor sênior que você vai conhecer já resolveu centenas de conflitos
> como esses. Agora você também faz parte desse clube.
