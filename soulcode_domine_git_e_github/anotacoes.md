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

### Enviando dados 

### Status

### Commit

### Entendendo Commit

### Pull/Clone - Git

### RM/Log - Git

### Git Ckeckout

### Fim do tópico

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

