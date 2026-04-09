#  Roteiro Git — Grupo A / Squad Identidade Visual
### Atividade prática de versionamento com Git e GitHub

---

> **Seu papel hoje:** Você é o **Tech Lead** da startup DevSpace.
> O professor disponibilizou o repositório base do projeto — você vai fazer um **fork** dele
> e se tornar o dono do repositório oficial desta dupla de times.
> O Grupo B vai trabalhar em paralelo no mesmo projeto, **sem combinar o código com vocês**.
> Os conflitos vão surgir naturalmente. É exatamente assim que acontece em empresas reais.

---

## ⏱ Visão geral do tempo

| Fase | O que fazer | Tempo |
|------|-------------|-------|
| **1** | Fazer fork do repositório do professor | 10 min |
| **2** | Ativar GitHub Pages e ver o site no ar | 5 min |
| **3** | Abrir o Codespaces, criar branch e ativar o preview | 15 min |
| **4** | Desenvolver as funcionalidades | 30 min |
| **5** | Commitar, subir e criar o Pull Request | 10 min |
| **6** | Fazer o merge do seu PR | 5 min |
| **7** | Revisar e mergear o PR do Grupo B | 15 min |
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

## 📋 FASE 1 — Fazer fork do repositório do professor
### ⏱ ~10 minutos

> 🎯 Em vez de criar um repositório do zero, você vai **copiar** o projeto base que o professor
> já preparou. Isso se chama **fork** — e é o ponto de partida padrão em projetos reais
> onde você pega um template ou contribui com um projeto existente.

### 1.1 — Acessar o repositório do professor e fazer o fork

1. O professor vai passar a URL do repositório. Acesse ela no navegador:
   ```
   https://github.com/USUARIO_DO_PROFESSOR/devspace-site
   ```

2. No canto superior direito da página do repositório, clique no botão **`[ Fork ]`**
   *(ele tem um ícone de bifurcação — duas setas divergindo)*

3. Na página seguinte, verifique e preencha:

   | Campo | O que fazer |
   |-------|------------|
   | `Owner` | Deve ser **seu** nome de usuário (não o do professor) |
   | `Repository name` | Mantenha `devspace-site` |
   | `Description` | Deixe em branco ou escreva algo |
   | `Copy the main branch only` | ✅ **Marque esta opção** |

4. Clique no botão verde **`[ Create fork ]`**

5. Aguarde o GitHub processar. Você será redirecionado para o **seu fork**.

> 📘 **Como saber se deu certo?**
> No topo da página você verá:
> ```
> SEU_USUARIO / devspace-site
> forked from USUARIO_DO_PROFESSOR/devspace-site
> ```
> Isso confirma que é uma cópia sua, derivada do original do professor.

> 📘 **Por que fork e não "criar um repositório"?**
> O professor já colocou os arquivos HTML e CSS prontos no repositório base.
> O fork traz tudo isso para a sua conta instantaneamente — sem upload manual,
> sem risco de erro na estrutura de arquivos.

### 1.2 — Enviar a URL do seu fork para o Grupo B

Copie a URL da página do **seu fork** (não a do professor). Ela terá o formato:
```
https://github.com/SEU_USUARIO/devspace-site
```

Envie essa URL para o Grupo B agora. Eles vão fazer um fork do **seu** repositório.

> ⚠️ **Instrua o Grupo B:** eles podem começar a Fase 1 deles assim que você enviar a URL,
> mas **não devem criar o PR** até você completar a Fase 6 (merge do seu PR).
> O conflito só vai aparecer depois que você mergear primeiro.

---

## 📋 FASE 2 — Ativar o GitHub Pages para ver o site funcionando
### ⏱ ~5 minutos

O GitHub Pages transforma seu repositório em um site real, acessível por qualquer pessoa!

1. Na página do seu fork, clique na aba **`Settings`** *(ícone de engrenagem ⚙, última aba)*
2. Na barra lateral esquerda, clique em **`Pages`** *(dentro de "Code and automation")*
3. Na seção **"Build and deployment"**:
   - Em **`Source`**: selecione **`Deploy from a branch`**
   - Em **`Branch`**: selecione **`main`**
   - Na pasta ao lado: mantenha **`/ (root)`**
4. Clique no botão **`[ Save ]`**

5. Aguarde ~1 minuto e **recarregue a página** (F5)

6. No topo da seção Pages aparecerá:
   ```
   Your site is live at https://SEU_USUARIO.github.io/devspace-site/
   ```

7. Clique nessa URL para ver o site funcionando!

> 🎉 **Seu site está no ar, de verdade, na internet!**
> Qualquer pessoa no mundo pode acessar essa URL agora.
> E toda vez que você mergear um PR na `main`, o site é atualizado automaticamente em ~1 min.

---

## 📋 FASE 3 — Abrir o Codespaces, criar branch e ativar o preview
### ⏱ ~15 minutos

O **GitHub Codespaces** é um VS Code completo rodando no seu navegador.
Sem instalar nada. Sem configurar nada. Você abre e já funciona.

### 3.1 — Criar um Codespace no seu fork

1. Volte para a página inicial do **seu fork**
   *(clique no nome `devspace-site` no topo da página)*

2. Clique no botão verde **`[ <> Code ]`**
   *(lado direito, acima da lista de arquivos)*

3. Clique na aba **`Codespaces`**

4. Clique em **`[ Create codespace on main ]`**
   *(ou no `+` se esse botão não aparecer)*

5. **Aguarde** — pode levar de 30 segundos a 2 minutos na primeira vez.

### 3.2 — Conhecer o ambiente

Quando carregar, você verá o **VS Code no navegador**:

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

Se o terminal não estiver visível na parte de baixo:
- Pressione **Ctrl + `` ` ``** (acento grave, tecla abaixo do Esc)
- *OU:* Clique em **`View`** → **`Terminal`**

### 3.3 — Criar sua branch de trabalho

No terminal, execute um comando por vez:

```bash
git log --oneline
```
> Veja o histórico de commits que vieram do repositório do professor.

```bash
git checkout -b feature/identidade-visual
```
> 📘 Cria a branch `feature/identidade-visual` e já entra nela.
> **Nunca desenvolva diretamente na `main`** — branches são experimentos seguros.

```bash
git branch
```
> Confirme: deve aparecer `* feature/identidade-visual`

---

### 3.4 — 👁 Ativar o preview do site em tempo real

> 🎯 **Esta é uma das partes mais importantes da aula!**
> Você vai criar um mini-servidor local para ver as mudanças do HTML/CSS
> instantaneamente no navegador, sem precisar de nenhuma extensão.

No terminal do Codespaces, execute:

```bash
python3 -m http.server 8080
```

Você verá a saída:
```
Serving HTTP on 0.0.0.0 port 8080 (http://0.0.0.0:8080/) ...
```

**Agora abra o site em uma nova aba:**

Uma janela popup aparecerá no canto inferior direito do Codespaces dizendo
`"Your application running on port 8080 is available"`.
Clique em **`[ Open in Browser ]`**.

Se o popup não aparecer:
1. Clique no ícone **`Ports`** na barra de abas do terminal (ao lado de "Terminal")
2. Você verá a porta `8080` listada
3. Clique no ícone de globo 🌐 ao lado dela

> ✅ **Resultado:** O site `index.html` abre no navegador com o visual completo!

**Como usar o preview durante o desenvolvimento:**
- O servidor fica rodando em background no terminal
- Edite os arquivos HTML/CSS no editor do Codespaces
- Salve com **Ctrl+S**
- Vá para a aba do navegador com o preview e pressione **F5** para atualizar
- Você vê a mudança na hora!

> 💡 **Dica:** Abra uma segunda aba no terminal para continuar digitando comandos Git
> enquanto o servidor está rodando.
> Para abrir uma nova aba do terminal: clique no `+` ao lado de "Terminal" na barra inferior.

---

## 📋 FASE 4 — Desenvolver as funcionalidades
### ⏱ ~30 minutos

### 4.1 — Tarefa 1: Atualizar o slogan do hero

1. No painel lateral, clique em **`index.html`**
2. Use **Ctrl+F** para buscar: `hero-slogan`
3. Você encontrará:
   ```html
   <p class="hero-slogan">Tecnologia e colaboração em um só lugar</p>
   ```
4. **Altere** para:
   ```html
   <p class="hero-slogan">Onde grandes ideias ganham vida</p>
   ```
5. Salve com **Ctrl+S** → atualize o preview com **F5**

> 🤔 **Reflita:** O Grupo B está alterando esta mesma linha agora, mas com um texto diferente.
> O que você acha que vai acontecer quando tentarem juntar os dois?

---

### 4.2 — Tarefa 2: Atualizar o subtítulo do hero

Ainda em `index.html`, localize:

```html
<p class="hero-subtitulo">
    Espaço de coworking premium para desenvolvedores, designers e startups em São Paulo.
</p>
```

**Substitua** pelo texto abaixo:

```html
<p class="hero-subtitulo">
    O ambiente ideal para transformar suas ideias em produtos que mudam o mercado.
</p>
```

Salve com **Ctrl+S** → verifique no preview.

---

### 4.3 — Tarefa 3: Renomear o título da seção de espaços

Ainda em `index.html`, use **Ctrl+F** para buscar: `Nossos Espaços`

```html
<h2>Nossos Espaços</h2>
```

**Altere** para:
```html
<h2>Nossos Ambientes Criativos</h2>
```

Salve com **Ctrl+S** → verifique no preview.

---

### 4.4 — Tarefa 4: Mudar a cor principal do site

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
   --cor-primaria:    #0ea5e9;   /* Azul céu — nova identidade visual */
   ```
5. Salve com **Ctrl+S** → atualize o preview

> ✨ **Veja a mágica!** Ao salvar e atualizar o preview, TODO o site muda de cor
> de uma vez — header, botões, bordas, gradientes. Isso é o poder das variáveis CSS.

> 🤔 **Reflita:** A cor `--cor-primaria` é usada em vários lugares do CSS.
> Se você tivesse que mudar em cada lugar separadamente, quantas linhas editaria?

---

### 4.5 — Tarefa 5: Adicionar um card de "Mentoria 1:1"

Em `index.html`, use **Ctrl+F** para buscar: `GRUPO A: adicionar novo card`

Você encontrará o comentário:
```html
<!-- GRUPO A: adicionar novo card aqui -->
```

**Substitua** esse comentário pelo código abaixo:

```html
<div class="card">
    <div class="card-icone">🎯</div>
    <h3>Mentoria 1:1</h3>
    <p>Sessões individuais com mentores experientes em produto, tecnologia e negócios para impulsionar sua carreira.</p>
    <span class="card-preco">A partir de R$ 150/sessão</span>
</div>
```

Salve com **Ctrl+S** → verifique o novo card no preview.

---

### 4.6 — Tarefa 6: Adicionar o rodapé ao site

Em `index.html`, use **Ctrl+F** para buscar: `GRUPO A: adicionar rodapé`

Localize o comentário:
```html
<!-- GRUPO A: adicionar rodapé aqui -->
```

**Substitua** pelo código abaixo:

```html
<footer>
    <p>
        © 2025 DevSpace — Todos os direitos reservados.
        Fundado em 2021 por Carlos Mendes.
        |
        <a href="index.html">Início</a> ·
        <a href="sobre.html">Sobre nós</a> ·
        <a href="index.html#contato">Contato</a>
    </p>
</footer>
```

Salve com **Ctrl+S**.

Agora abra **`sobre.html`** e repita: localize o comentário
`<!-- GRUPO A: adicionar rodapé aqui (igual ao index.html) -->` e substitua pelo mesmo código do rodapé.

Salve com **Ctrl+S** → verifique o rodapé no preview de ambas as páginas.

---

### 4.7 — Verificar as mudanças no terminal

Na nova aba do terminal, execute:

```bash
git status
```
> Você verá os arquivos modificados listados em vermelho.

```bash
git diff index.html
```
> 📘 Mostra linha a linha o que mudou.
> - Linhas em **verde** com `+` = foram adicionadas
> - Linhas em **vermelho** com `-` = foram removidas
>
> Pressione **`q`** para sair da visualização.

---

## 📋 FASE 5 — Commitar e enviar para o GitHub
### ⏱ ~10 minutos

### 5.1 — Adicionar os arquivos ao staging

```bash
git add index.html sobre.html
```
> 📘 Marca os arquivos para inclusão no próximo commit.

```bash
git add estilo.css
```

Confirme:
```bash
git status
```
> Os arquivos devem aparecer em **verde** ("Changes to be committed") ✅

### 5.2 — Criar o commit

```bash
git commit -m "feat: nova identidade visual, card de mentoria e rodapé"
```
> 📘 Cria um ponto no histórico com a foto atual do projeto.
> `feat:` = nova funcionalidade | `fix:` = correção | `style:` = mudança visual

```bash
git log --oneline
```
> Seu novo commit aparece no topo. O histórico cresce para cima — mais recente primeiro.

### 5.3 — Enviar a branch para o GitHub

```bash
git push origin feature/identidade-visual
```
> 📘 Envia SUA BRANCH para o GitHub.
> A `main` continua intocada. Você está mandando a branch, não a main.

---

## 📋 FASE 6 — Criar e mergear o Pull Request
### ⏱ ~10 minutos

### 6.1 — Criar o PR no GitHub

1. Acesse seu fork no GitHub (abra uma nova aba):
   ```
   https://github.com/SEU_USUARIO/devspace-site
   ```

2. Você verá o **banner amarelo** no topo:
   ```
   feature/identidade-visual had recent pushes  [ Compare & pull request ]
   ```

3. Clique em **`[ Compare & pull request ]`**

> 📘 **O que é um Pull Request (PR)?**
> É um pedido formal para integrar sua branch na main.
> No mundo real, um colega revisaria seu código aqui antes de aprovar.

### 6.2 — Preencher o PR

**Título:**
```
feat: nova identidade visual, card de mentoria e rodapé
```

**Descrição:**
```
## O que foi feito neste PR

### Mudanças que podem gerar conflito com o Grupo B
- Slogan: "Onde grandes ideias ganham vida"
- Novo subtítulo do hero
- Renomeação da seção: "Nossos Ambientes Criativos"
- Cor primária alterada para azul céu (#0ea5e9)

### Funcionalidades exclusivas deste PR
- Card de Mentoria 1:1 na grade de serviços
- Rodapé com links de navegação no index e no sobre

## Como testar
- Verificar mudanças no hero e na seção de espaços
- Confirmar que o rodapé aparece no fundo de ambas as páginas
- Verificar que a cor do header e botões mudou para azul
```

Verifique que o PR aponta para:
- **base:** `main` ← **compare:** `feature/identidade-visual`

Clique em **`[ Create pull request ]`**

### 6.3 — Revisar e mergear

1. Clique na aba **`Files changed`** para revisar todas as mudanças
2. Volte para **`Conversation`**
3. Role até o final e clique em **`[ Merge pull request ]`**
4. Clique em **`[ Confirm merge ]`**
5. Clique em **`[ Delete branch ]`** *(boa prática: branches mergeadas devem ser deletadas)*

✅ **Mensagem de sucesso:** `Pull request successfully merged and closed`

> 📘 Suas mudanças agora estão na `main`. O GitHub Pages vai atualizar o site em ~1 minuto.

> ⚠️ **AGORA avise o Grupo B** que eles podem criar o PR deles.
> O conflito só acontece depois que você mergear. Se eles criarem antes, não haverá conflito.

---

## 📋 FASE 7 — Revisar e mergear o PR do Grupo B
### ⏱ ~15 minutos

### O que vai acontecer

O Grupo B vai tentar fazer o merge da `main` (atualizada com suas mudanças) na branch deles.
O Git vai detectar que os dois grupos modificaram as **mesmas linhas nos mesmos arquivos**.

**Resultado:** Conflito de merge. O Git não sabe qual versão escolher.

Enquanto eles resolvem, entenda como o Git marca conflitos:

```
<<<<<<< HEAD
Versão que está na branch deles (o que eles escreveram)
=======
Versão que estava na main antes (o que você mergeou)
>>>>>>> upstream/main
```

Para resolver, é preciso:
1. Escolher qual versão manter (ou criar uma combinando as duas)
2. Apagar os marcadores `<<<<<<<`, `=======` e `>>>>>>>`
3. Salvar → `git add` → `git commit`

### Seu papel

Não dite qual versão usar — isso é decisão deles.
Mas responda perguntas conceituais como "o que significa `<<<<<<< HEAD`?"

### 7.1 — Mergear o PR do Grupo B

Quando eles resolverem os conflitos e avisarem:

1. Na página do **seu fork** no GitHub, clique na aba **`Pull requests`**
2. Clique no PR aberto pelo Grupo B
3. Leia as mudanças na aba **`Files changed`**
4. Volte para **`Conversation`** → clique em **`[ Merge pull request ]`**
5. Confirme o merge

> 🎉 **Agora o site tem as contribuições dos dois grupos!**
> Acesse o GitHub Pages e veja o resultado final.

### 7.2 — Atualizar o Codespaces com o estado final

Volte ao Codespaces. Na aba do terminal com o servidor rodando, pressione **Ctrl+C** para parar.
Na outra aba do terminal:

```bash
git checkout main
```
> Volta para a branch main

```bash
git pull origin main
```
> Baixa tudo do GitHub, incluindo o que o Grupo B adicionou

```bash
git log --oneline --graph --all
```
> 📘 Mostra o gráfico visual do histórico completo, com as duas branches se separando
> e se unindo novamente. É a história do trabalho de equipe de vocês, registrada para sempre.

---

## 📋 FASE 8 — Reflexão Final
### ⏱ ~10 minutos

Discutam em conjunto com o Grupo B:

**Sobre o processo:**
1. 🤔 Em que momento exato o conflito "nasceu"? Quando você mergeou, ou ele já existia antes?
2. 🤔 O que teria acontecido se os dois grupos tivessem desenvolvido direto na `main`?
3. 🤔 Por que faz sentido deletar branches depois do merge?

**Sobre as decisões técnicas:**
4. 🤔 O Grupo B escolheu qual versão dos conflitos? Concordam com a escolha?
5. 🤔 Como o `git log --graph` ajuda a entender o histórico do projeto?

**Sobre o fluxo de trabalho:**
6. 🤔 Em um time com 10 devs, como você organizaria o trabalho para minimizar conflitos?
7. 🤔 O fork do professor foi mais rápido do que criar um repositório do zero? Por quê?

---

## 📌 Dicionário de Comandos Git desta atividade

| Comando | O que faz |
|---------|-----------|
| `git log --oneline` | Histórico compacto de commits |
| `git status` | Estado atual dos arquivos |
| `git diff arquivo` | Mostra o que mudou linha a linha |
| `git checkout -b nome` | Cria e entra em uma nova branch |
| `git branch` | Lista branches (a ativa tem `*`) |
| `git add arquivo` | Prepara arquivo para o commit |
| `git add .` | Prepara TODOS os arquivos modificados |
| `git commit -m "msg"` | Salva o estado com uma mensagem |
| `git push origin branch` | Envia branch para o GitHub |
| `git checkout main` | Volta para a branch main |
| `git pull origin main` | Baixa e integra mudanças do GitHub |
| `git log --oneline --graph --all` | Histórico visual de todas as branches |
| `python3 -m http.server 8080` | Inicia servidor local para preview |

---

> **Parabéns!** Você partiu do repositório do professor, liderou o projeto como Tech Lead,
> trabalhou com branches e Pull Requests, e entregou o site funcionando via GitHub Pages.
> Esse é o fluxo usado diariamente em empresas como Nubank, iFood, Google e Amazon.
