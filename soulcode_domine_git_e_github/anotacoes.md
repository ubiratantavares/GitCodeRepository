# Soulcode - Domine Git e GitHub: Controle, Colabore e Compartilhe Código com Maestria

## I = Introdução ao curso

### Explicação do curso e o que será desenvolvido durante toda a jornada

## II - O que é Git e GitHub

### Explicação Git

### Explicação GitHub

## III - Preparando o Ambiente

### Aula 4 - Instalando e Configurando Git e Visual Code

Aqui está um guia passo a passo para instalar e configurar o **Git** e o **Visual Studio Code** no Ubuntu através do terminal:

### **1. Atualizar os pacotes**

Abra o terminal e execute:

```bash
sudo apt update && sudo apt upgrade -y
```

### **2. Instalar o Git**

1. **Instale o Git:**

   ```bash
   sudo apt install git -y
   ```

2. **Verifique a instalação:**

   ```bash
   git --version
   ```

3. **Configure o Git:**

   Substitua "Seu Nome" e "seuemail@dominio.com" pelos seus dados:

   ```bash
   git config --global user.name "Seu Nome"
   git config --global user.email "seuemail@dominio.com"
   ```

4. **Verifique a configuração:**

   ```bash
   git config --list
   ```

### **3. Instalar o Visual Studio Code**

1. **Adicione o repositório do VS Code:**

   ```bash
   sudo apt install wget gpg -y
   wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg
   sudo install -o root -g root -m 644 microsoft.gpg /usr/share/keyrings/
   sudo sh -c 'echo "deb [arch=amd64 signed-by=/usr/share/keyrings/microsoft.gpg] https://packages.microsoft.com/repos/code stable main" > /etc/apt/sources.list.d/vscode.list'
   rm -f microsoft.gpg
   ```

2. **Atualize os pacotes e instale o VS Code:**

   ```bash
   sudo apt update
   sudo apt install code -y
   ```

3. **Abra o VS Code para verificar a instalação:**

   ```bash
   code
   ```

### **4. Configurar o Git no VS Code**

1. **Instale a extensão GitLens (opcional):**

   No terminal, execute:

   ```bash
   code --install-extension eamodio.gitlens
   ```

2. **Habilite a integração do Git:**

   - No VS Code, pressione `Ctrl + ,` para abrir as configurações.

   - Pesquise por "Git" e configure as opções desejadas.

### **5. Teste o Git e VS Code**

1. **Clone um repositório para testar:**

   ```bash
   git clone https://github.com/seu-usuario/seu-repositorio.git
   cd seu-repositorio
   code .
   ```

2. **Faça alterações e commit:**

   - Edite um arquivo no VS Code.

   - Use o terminal integrado do VS Code (`Ctrl + '`):

     ```bash
     git add .
     git commit -m "Minha primeira alteração no VS Code"
     git push
     ```

### Aula 5 - Instalando e Configurando GitHub

O **GitHub** não é um software que precisa ser instalado. Em vez disso, você configura o **Git** (já instalado) para se conectar ao GitHub. 

Aqui está o guia para configurar o GitHub no Ubuntu:

### **1. Instalar o Git**

Certifique-se de que o Git está instalado (se ainda não estiver):

```bash
sudo apt update
sudo apt install git -y
```

Verifique a instalação:

```bash
git --version
```

### **2. Configurar o Git**

Configure o nome de usuário e o email associados à sua conta do GitHub:

```bash
git config --global user.name "Seu Nome no GitHub"
git config --global user.email "seuemail@dominio.com"
```

Para verificar a configuração:

```bash
git config --list
```

### **3. Criar uma Chave SSH**

A chave SSH permite autenticar de forma segura com o GitHub sem precisar digitar sua senha toda vez que fizer um `push`.

1. **Gerar a chave SSH:**

Substitua `seuemail@dominio.com` pelo email usado no GitHub:

   ```bash
   ssh-keygen -t ed25519 -C "seuemail@dominio.com"
   ```
   Pressione `Enter` para aceitar o local padrão (`~/.ssh/id_ed25519`) e, se desejar, insira uma senha para proteger sua chave.

2. **Adicionar a chave SSH ao agente:**

   Ative o agente SSH:

   ```bash
   eval "$(ssh-agent -s)"
   ```
   Adicione sua chave privada ao agente:

   ```bash
   ssh-add ~/.ssh/id_ed25519
   ```

3. **Copiar a chave SSH para o GitHub:**

   Copie o conteúdo da sua chave pública:

   ```bash
   cat ~/.ssh/id_ed25519.pub
   ```
   - Acesse [GitHub > Configurações > SSH e GPG keys](https://github.com/settings/keys).
   - Clique em **New SSH Key**, cole a chave copiada e salve.

4. **Testar a conexão SSH com o GitHub:**

   ```bash
   ssh -T git@github.com
   ```

   Se tudo estiver configurado corretamente, você verá uma mensagem semelhante a:
   ```
   Hi <seu-usuario>! You've successfully authenticated, but GitHub does not provide shell access.
   ```
### **4. Clonar um Repositório do GitHub**

1. Vá até o repositório no GitHub que deseja clonar.

2. Copie o link SSH do repositório.

3. Execute:

   ```bash
   git clone git@github.com:seu-usuario/seu-repositorio.git
   ```

### **5. Criar um Repositório e Fazer o Push**

1. **Crie um novo repositório no GitHub (sem README ou .gitignore).**

2. **Inicialize o repositório localmente:**

   ```bash
   git init
   ```

3. **Adicione um arquivo (opcional):**

   ```bash
   echo "# Meu Repositório" > README.md
   git add README.md
   git commit -m "Primeiro commit"
   ```
4. **Conecte ao repositório remoto:**

   Substitua `<seu-usuario>` e `<seu-repositorio>`:

   ```bash
   git remote add origin git@github.com:<seu-usuario>/<seu-repositorio>.git
   ```
5. **Envie os arquivos para o GitHub:**

   ```bash
   git branch -M main
   git push -u origin main
   ```

## IV - Comandos Git e GitHub

### Criando primeiro repositório

```bash
git init

git status

git add index.html

git commit -m "meu primeiro repositorio"

git status
```

### Enviando dados para o GitHub

```bash
git config --global user.name "meu-usuario"

git config --global use.email "meu-email"

git init

git add index.html

git commit -m "meu primeiro commit no github"

git branch -M main

git remote add origin https://github.com/rafaeldegomes/primeirotestegithub.git

git push -u origin main

git add index.html

git commit -m "segundo commit"

git push -u origin main

```

### Status/Add-Git

## Entendendo os Comandos `git status` e `git add`

**Git status** e **git add** são dois comandos fundamentais no Git que trabalham em conjunto para gerenciar as alterações em seus projetos. Eles são como as ferramentas de um pedreiro: o `status` mostra o que você tem para trabalhar, e o `add` prepara os materiais para serem usados na construção (no nosso caso, o commit).

### **git status**

O comando `git status` fornece um instantâneo do seu repositório Git atual. Ele mostra:

* **Arquivos modificados:** Quais arquivos você alterou desde o último commit.
* **Arquivos novos:** Quais arquivos você adicionou ao seu projeto.
* **Arquivos preparados:** Quais alterações estão prontas para serem incluídas no próximo commit.

**Por que usar:**
* **Verificar o progresso:** Saber quais arquivos foram alterados e quais ainda não foram.
* **Planejar o próximo commit:** Decidir quais alterações incluir no próximo commit.
* **Evitar commits acidentais:** Confirmar quais arquivos serão incluídos antes de fazer o commit.

**Exemplo de saída:**

```
On branch main
Your branch is up-to-date with 'origin/main'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md

Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)
        new file:   new_feature.py
```

### **git add**

O comando `git add` prepara as alterações para serem incluídas no próximo commit. Ele move as alterações do seu diretório de trabalho para a área de staging.

**Por que usar:**
* **Preparar alterações para o commit:** Adicionar as alterações desejadas ao próximo commit.
* **Controlar o que será commitado:** Adicionar arquivos um por um ou em grupos.

**Exemplo:**

```bash
git add README.md new_feature.py
```

**O que acontece quando você usa `git add`:**

1. **O arquivo é copiado para a área de staging:** Uma cópia do arquivo com as alterações é armazenada em um local especial dentro do seu repositório Git.
2. **As alterações são marcadas para serem commitadas:** As alterações nesse arquivo estarão incluídas no próximo commit, a menos que você as remova da área de staging.

### **Resumindo:**

* **git status:** Mostra o estado atual do seu repositório.
* **git add:** Prepara as alterações para serem commitadas.

**Fluxograma básico:**

1. **Você faz alterações nos arquivos.**
2. **Você usa `git status` para ver quais arquivos foram alterados.**
3. **Você usa `git add` para adicionar as alterações desejadas ao próximo commit.**
4. **Você usa `git commit` para criar um novo commit com as alterações.**

**Em resumo:**

* **`git status` é como olhar para uma lista de compras:** Você vê o que precisa ser feito.
* **`git add` é como colocar os itens na sacola:** Você está preparando os itens para levar para casa (ou para o seu repositório).

**Exemplo prático:**

Imagine que você está escrevendo um relatório. Você faz algumas alterações no arquivo `relatorio.txt`. Para ver quais arquivos foram alterados, você usa `git status`. Em seguida, você usa `git add relatorio.txt` para adicionar as alterações ao próximo commit. Finalmente, você usa `git commit -m "Finalizado a primeira parte do relatório"` para criar um novo commit.

Com esses dois comandos, você tem um controle preciso sobre as alterações em seu projeto e pode manter um histórico claro das mudanças ao longo do tempo.

**Gostaria de saber mais sobre algum outro comando do Git?** 

### Commit/Push-Git

## O Comando `git commit` no Git: Salvando suas Alterações

O comando `git commit` é fundamental no Git e representa o ato de salvar um "instantâneo" das alterações que você fez em seus arquivos. É como tirar uma foto do seu projeto em um determinado momento, marcando um ponto específico na sua linha do tempo de desenvolvimento.

**O que acontece quando você usa `git commit`:**

1. **Criação de um novo commit:** Um novo "commit" é criado no seu repositório Git. Esse commit contém as informações sobre as alterações que você fez, incluindo quais arquivos foram modificados e as mensagens que você escreveu para descrever essas mudanças.
2. **Criação de um ponteiro:** Um ponteiro (geralmente chamado de HEAD) é movido para apontar para esse novo commit, indicando que este é agora o commit mais recente na sua branch atual.

**Por que usar `git commit`:**

* **Salvar o progresso:** Cada commit marca um ponto específico no desenvolvimento do seu projeto, permitindo que você volte a essa versão mais tarde se precisar.
* **Criar um histórico:** A sequência de commits cria um histórico completo das alterações feitas no projeto, facilitando a rastreabilidade e a colaboração.
* **Colaboração:** Ao compartilhar seu repositório com outros desenvolvedores, os commits permitem que todos vejam as contribuições de cada um e trabalhem em conjunto de forma mais eficiente.

**Sintaxe básica:**

```bash
git commit -m "Mensagem do commit"
```

* **-m:** Opção para adicionar uma mensagem de commit. A mensagem é crucial para descrever as alterações feitas e ajudar a você e outros desenvolvedores a entenderem o propósito do commit.

**Exemplo:**

```bash
git commit -m "Adicionada a funcionalidade de busca"
```

**Boas práticas para mensagens de commit:**

* **Ser concisa e clara:** Explique o que foi feito de forma clara e objetiva.
* **Usar tempo verbal no passado:** Por exemplo, "Corrigido o bug de login" em vez de "Corrigir o bug de login".
* **Começar com um verbo:** Por exemplo, "Adicionado", "Removido", "Corrigido".
* **Ser específica:** Evite mensagens genéricas como "Alterações diversas".

**Em resumo:**

O comando `git commit` é como salvar um jogo: ele captura o estado atual do seu projeto e permite que você volte a ele mais tarde. Ao usar `git commit` com frequência e escrever mensagens de commit claras e concisas, você estará construindo um histórico sólido e compreensível do seu projeto.

**Gostaria de saber mais sobre algum outro aspecto do comando `git commit` ou sobre outros comandos do Git?** 

**Alguns tópicos que podemos explorar:**

* **Amendando commits:** Como modificar um commit já realizado.
* **Removendo commits:** Como remover um commit do histórico.
* **Branching:** Como criar e gerenciar diferentes versões do seu projeto.
* **Merging:** Como combinar diferentes branches.

## O Comando `git push`: Compartilhando Suas Alterações

O comando `git push` é como enviar uma mensagem em uma garrafa para um amigo distante, só que no mundo do desenvolvimento de software. Ele serve para **enviar** as alterações que você fez no seu repositório local (aquele no seu computador) para um repositório remoto (como o GitHub, GitLab ou Bitbucket).

**Para que serve o `git push`?**

* **Compartilhar código:** Quando você trabalha em um projeto com outras pessoas, o `git push` permite que você compartilhe suas alterações com o resto da equipe.
* **Fazer backup:** O repositório remoto serve como um backup seguro do seu código. Mesmo que algo aconteça com o seu computador, suas alterações estarão salvas no remoto.
* **Colaboração:** O `git push` é fundamental para a colaboração em projetos, pois permite que diferentes pessoas trabalhem em partes diferentes do código ao mesmo tempo.

**Como funciona o `git push`?**

1. **Você faz alterações nos seus arquivos locais e cria um commit.**
2. **Você usa `git push` para enviar esse commit para o repositório remoto.**
3. **O repositório remoto é atualizado com as suas alterações.**

**Sintaxe básica:**

```bash
git push <nome-do-repositório-remoto> <nome-da-branch>
```

* **<nome-do-repositório-remoto>:** Geralmente é "origin", que é o nome padrão dado ao repositório remoto quando você clona um repositório.
* **<nome-da-branch>:** O nome da branch local que você deseja enviar para o remoto.

**Exemplo:**

```bash
git push origin main
```

Esse comando enviará as alterações da sua branch local "main" para o repositório remoto chamado "origin".

**Por que usar `git push`?**

* **Sincronizar seu trabalho:** Garante que o seu repositório local esteja sempre atualizado com o repositório remoto.
* **Colaboração:** Permite que você trabalhe em equipe, mesclando suas alterações com as alterações de outros desenvolvedores.
* **Backup:** Cria um backup seguro do seu código.

**Em resumo:**

O `git push` é uma ferramenta essencial para qualquer desenvolvedor que trabalha com Git. Ele permite que você compartilhe seu trabalho, colabore com outros desenvolvedores e mantenha um histórico seguro do seu projeto.

**Gostaria de aprender mais sobre algum outro comando do Git?** 

Podemos explorar tópicos como:

* **`git pull`:** Baixar alterações de um repositório remoto para o seu local.
* **Branches:** Criar e gerenciar diferentes versões do seu projeto.
* **Merging:** Combinar diferentes branches.
* **Resolução de conflitos:** Lidar com situações em que duas pessoas alteram a mesma parte do código ao mesmo tempo.

### Entendendo Commit

## Entendendo Melhor o Comando `git commit`

O comando `git commit` é um dos pilares do Git e, apesar de ser relativamente simples de usar, possui nuances importantes que podem otimizar seu fluxo de trabalho e garantir um histórico de versionamento mais organizado e compreensível.

**O que o `git commit` faz?**

Em resumo, o `git commit` cria um "instantâneo" do seu projeto em um determinado momento. É como tirar uma foto do seu código, registrando todas as alterações feitas desde o último commit. Cada commit é um marco na evolução do seu projeto e permite que você volte a qualquer versão anterior se necessário.

**Por que as mensagens de commit são importantes?**

As mensagens de commit são como legendas das fotos que você tira do seu projeto. Elas descrevem as mudanças que foram feitas e o porquê. Uma boa mensagem de commit deve ser:

* **Concisa:** Vá direto ao ponto.
* **Clara:** Use linguagem simples e direta.
* **Informativa:** Explique o que foi feito e porquê.
* **Consistente:** Use uma estrutura similar para todas as suas mensagens.

**Boas práticas para mensagens de commit:**

* **Comece com um verbo:** "Adicionado", "Removido", "Corrigido".
* **Seja específico:** Evite mensagens vagas como "Alterações diversas".
* **Use o imperativo:** Escreva como se estivesse dando uma ordem: "Adicionada a funcionalidade de busca".
* **Quebre em linhas:** Use uma linha para cada ideia principal.

**Exemplo de uma boa mensagem de commit:**

```
Adicionada a funcionalidade de busca ao formulário de contato. 
Implementada a busca por nome e email.
```

**O que mais você pode fazer com o `git commit`?**

* **Amendar um commit:** Corrigir uma mensagem de commit ou adicionar arquivos esquecidos.
* **Dividir um commit:** Separar um commit grande em commits menores.
* **Mesclar commits:** Combinar múltiplos commits em um único.

**Como aprofundar seus conhecimentos sobre `git commit`?**

* **Documentação oficial do Git:** A documentação do Git é uma fonte confiável e completa de informações sobre todos os comandos, incluindo `git commit`.
* **Tutoriais online:** Existem diversos tutoriais e cursos online que abordam o Git de forma detalhada.
* **Livros sobre Git:** Livros como "Pro Git" são ótimas referências para quem quer aprender mais sobre o Git.
* **Experimentação:** A melhor forma de aprender é praticando. Crie um repositório e experimente diferentes comandos e opções do `git commit`.

**Algumas perguntas para te ajudar a explorar mais:**

* Qual a diferença entre `git add` e `git commit`?
* Como posso reverter um commit?
* O que são branches e como elas se relacionam com commits?
* Como posso colaborar com outros desenvolvedores usando o Git?

**Lembre-se:** O `git commit` é uma ferramenta poderosa que pode te ajudar a organizar seu trabalho e colaborar com outros desenvolvedores de forma mais eficiente. Ao entender os fundamentos do `git commit` e seguir as boas práticas, você estará no caminho certo para dominar o Git.

### Pull/Clone - Git

Os comandos `git pull` e `git clone` são ferramentas essenciais no Git para interagir com repositórios remotos. Embora ambos sirvam para obter código de um repositório remoto, eles têm funções e usos distintos.

### `git clone`

* **Cria um novo repositório local:** O comando `git clone` é usado para criar uma cópia completa de um repositório remoto em seu computador local. É como fazer um download completo de um projeto.
* **Configura a conexão remota:** Além de copiar os arquivos, o `git clone` configura automaticamente a conexão entre o seu repositório local e o remoto, permitindo que você faça push e pull de alterações no futuro.
* **Uso:** É utilizado quando você está iniciando um novo projeto a partir de um repositório existente ou quando precisa de uma cópia local completa de um projeto para trabalhar offline.

**Sintaxe:**

```bash
git clone <url-do-repositório-remoto>
```

**Exemplo:**

```bash
git clone https://github.com/usuario/meu-projeto.git
```

### `git pull`

* **Atualiza um repositório local existente:** O comando `git pull` é usado para atualizar um repositório local que já foi clonado anteriormente. Ele baixa as últimas alterações de um repositório remoto e as mescla com o seu repositório local.
* **Combina duas operações:** Na verdade, o `git pull` é uma combinação de dois comandos: `git fetch` (que baixa as alterações do remoto) e `git merge` (que mescla as alterações com o seu branch atual).
* **Uso:** É utilizado quando você já tem uma cópia local de um projeto e precisa sincronizá-la com a versão mais recente do repositório remoto.

**Sintaxe:**

```bash
git pull <nome-do-repositório-remoto> <nome-da-branch>
```

**Exemplo:**

```bash
git pull origin main
```

**Resumo da diferença:**

| Comando | Função | Quando usar |
|---|---|---|
| `git clone` | Cria um novo repositório local a partir de um remoto. | Ao iniciar um novo projeto ou criar uma cópia completa. |
| `git pull` | Atualiza um repositório local existente com as alterações do remoto. | Para sincronizar seu repositório local com o remoto. |

**Em resumo:**

* **`git clone`:** Cria uma cópia completa.
* **`git pull`:** Atualiza uma cópia existente.

**Quando usar cada um?**

* **`git clone`:** Quando você está começando um novo projeto ou precisa de uma cópia completa de um projeto.
* **`git pull`:** Quando você já tem uma cópia local e precisa sincronizá-la com a versão mais recente do repositório remoto.

**Exemplo prático:**

Imagine que você está trabalhando em um projeto e seu colega fez algumas alterações no repositório remoto. Para obter essas alterações, você usaria `git pull`. No entanto, se você quiser começar a trabalhar em um novo projeto que já existe no GitHub, você usaria `git clone` para criar uma cópia local.

**Gostaria de aprender mais sobre algum outro comando do Git?** 

Podemos explorar tópicos como:

* **`git push`:** Enviar alterações do seu repositório local para o remoto.
* **Branches:** Criar e gerenciar diferentes versões do seu projeto.
* **Merging:** Combinar diferentes branches.
* **Resolução de conflitos:** Lidar com situações em que duas pessoas alteram a mesma parte do código ao mesmo tempo.

### Rm/Log - Git

O comando `git rm` serve para **remover arquivos do controle do Git**. Isso significa que o arquivo será removido tanto do seu repositório local quanto do próximo commit que você fizer.

**Sintaxe:**

```bash
git rm <arquivo>
```

**Exemplos:**

* `git rm arquivo.txt`: Remove o arquivo `arquivo.txt` do controle do Git.

* `git rm -r pasta`: Remove a pasta `pasta` e todo o seu conteúdo recursivamente.

**Opções úteis:**

* `-f`: Força a remoção, mesmo que o arquivo tenha sido modificado.

* `--cached`: Remove o arquivo do índice, mas mantém o arquivo no sistema de arquivos.

**Quando usar:**

* Quando você deseja remover definitivamente um arquivo do seu projeto.

* Ao realizar uma limpeza de arquivos que não são mais necessários.


### `git log`

O comando `git log` exibe o **histórico de commits** do seu repositório. Ele mostra informações como a data do commit, o autor, o hash do commit e a mensagem de commit.

**Sintaxe:**

```bash
git log
```

**Exemplos:**

* `git log`: Mostra o histórico completo dos commits.

* `git log --oneline`: Mostra o histórico em uma única linha para cada commit.

* `git log --author="seu_nome"`: Mostra apenas os commits feitos por você.

* `git log --grep="corrigir bug"`: Filtra os commits que contém a palavra "corrigir bug" na mensagem.

**Opções úteis:**

* `-p`: Mostra as diffs (diferenças) entre os commits.

* `--since="2.weeks ago"`: Mostra os commits realizados nas últimas duas semanas.

**Quando usar:**

* Para ver o histórico de mudanças no seu projeto.

* Para encontrar um commit específico.

* Para analisar o que foi feito em determinada parte do código.

### Git Ckeckout

O comando `git checkout` serve para **mudar entre diferentes versões** do seu projeto ou **restaurar arquivos** a uma versão anterior.

**Sintaxe:**

* **Mudar de branch:**
  ```bash
  git checkout <nome_da_branch>
  ```
* **Restaurar um arquivo:**

  ```bash
  git checkout <commit_hash> <arquivo>
  ```

**Exemplos:**

* `git checkout main`: Muda para a branch `main`.

* `git checkout feature/nova-funcionalidade`: Muda para a branch `feature/nova-funcionalidade`.

* `git checkout HEAD~1 arquivo.txt`: Restaura o arquivo `arquivo.txt` para a versão anterior.

**Quando usar:**

* Para trabalhar em diferentes funcionalidades simultaneamente (utilizando branches).

* Para reverter alterações em um arquivo.

* Para experimentar novas ideias sem afetar a branch principal.

**Observações:**

* **Cuidado ao usar `git checkout`:** Se você fizer `git checkout` em um arquivo que foi modificado localmente, suas alterações serão perdidas se não forem commitadas.

* **Branch:** Uma branch é uma linha de desenvolvimento independente dentro do seu repositório.

**Em resumo:**

* `git rm`: Remove arquivos do controle do Git.

* `git log`: Mostra o histórico de commits.

* `git checkout`: Muda entre branches ou restaura arquivos.

**Dica:** Use as opções e argumentos adicionais desses comandos para personalizar a sua experiência e obter informações mais precisas.

## V - Branch

### Definição de branch

### Criando um branch

### Alternando entre branchs

### Apagando as branchs

### Merge em branchs

### Fim do tópico

## VI - Projeto criando

### Configurando GitPage

### Primeiro commit e teste

### Criando a página de portfólio

### Enviando arquivos e verificando

### Finalizando o curso

