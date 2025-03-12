Nesse repositório não irei explicar o que é Git/Github/Versionamento de Código. Irei direto ao ponto, com uma linguagem simples, e voltado pro Windows.

# Instalando o Git

Entra nesse site: https://git-scm.com/downloads
Escolha o sistema operacional, baixa o executável e instale no seu computador. Ou seja, next -> next -> ... ao infinito e além ... -> Finalizar

![giphy 3](https://github.com/user-attachments/assets/926d30d5-70a8-4dc8-8b77-b2ba469a3fe1)

# Conectando o Git no Github

Pré-requisito: Ter uma conta no Github.

SÓ É NECESSÁRIO FAZER ISSO UMA VEZ (por conta/pc)

![giphy 4](https://github.com/user-attachments/assets/2f1a29ea-77e0-45d4-8512-9af234a0a9ea)

Primeiro, você precisa configurar seu nome de usuário e e-mail no Git. Essas informações serão usadas para identificar suas contribuições no GitHub.

Abra o terminal e execute os seguintes comandos:

```
git config --global user.name "Seu Nome"
git config --global user.email "seu-email@exemplo.com"
git config --global init.defaultBranch main
```
*Não precisa das aspas 

Isso evita que você precise digitar seu nome de usuário e senha toda vez que interagir com o GitHub,  é recomendável usar uma chave SSH.

Eu recomendo seguir o seguinte tutorial do próprio github pra configurar sua chave SSH: https://docs.github.com/pt/authentication/connecting-to-github-with-ssh/checking-for-existing-ssh-keys

Mas caso esteja com preguiça, vou direta ao ponto, e partindo da ideia que você não tem uma chave gerado de SSH.

Execute o seguinte comando para gerar uma nova chave SSH:  `ssh-keygen -t rsa -b 4096 -C "seu-email@exemplo.com"`. Pressione `Enter` para aceitar o local padrão e, se desejar, adicione uma senha para maior segurança. Confirme a senha. SSH GERADA.

Se tu não mudou o diretório, então sua chave deve estar em
```
C:\Users\nomeDoUsuarioAtual\.ssh\id_ed25519.pub
```

Agora, vá para o GitHub:

1. Acesse [GitHub SSH Keys](https://github.com/settings/keys).
2. Clique em "New SSH key" ou "Add SSH key".
3. Dê um título à chave (por exemplo, "Batata quente").
4. Cole a chave que você copiou no campo "Key".
5. Clique em "Add SSH key".

![[../00 - Resource/giphy 5.gif]]

Pra testar sua conexão, acesse o terminal, e digite: `ssh -T git@github.com`. Se der certo você ver a seguinte mensagem.

```
Hi seu-usuario! You've successfully authenticated, but GitHub does not provide shell access.
```

Ser der errado, melhor olhar a documentação do Github. Espero que dê tudo certo.
# Criando um projeto do zero

![giphy 1](https://github.com/user-attachments/assets/d55d9122-9122-4164-976a-55f693f01e87)

1) Entre no Github, crie um repositório novo.
	- No gitbub ele já dá um mini tutorial dos comandos que você deve fazer. Então se tu for preguiçoso, é só copiar linha por linha e colar no terminal.
	
2) Crie uma pasta no seu computador com o mesmo nome do repositório do GitHub (recomendado para evitar confusões). Em seguida, abra o terminal dentro dessa pasta.

Se for um projeto zerado, não tem `nenhum arquivo` siga esse passo a passo.
``` cmd
echo "# NOME-DO-PROJETO" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin <<LINK DO PROJETO>>
git push -u origin main
```

Agora se tu criou alguma coisa,  já `tem algumas arquivos`, siga esse:
``` cmd
git init
git add .
git commit -m "first commit"
git branch -M main
git remote add origin <<LINK DO PROJETO>>
git push -u origin main
```
# Copiando um projeto (Clone)

![giphy](https://github.com/user-attachments/assets/bf318228-d8db-4b29-8a68-9591c2721dda)

Acesse o repositório que você deseja clonar. Clique no botão verde `Code` no topo da página do repositório. Copie o URL do repositório (HTTPS ou SSH) do GitHub.

Crie uma pasta no seu PC ou vá na pasta onde tu deixa seus projetos, entre nela, então aperte com o botão direito > `Abrir terminal`.

``` cmd
git clone <URL_DO_REPOSITORIO>
```

OU você pode simplesmente baixar o zip do projeto e descompactar ele.
# Contribuindo para um projeto (Pull Request)

![[../00 - Resource/giphy 2.gif]]

1. Faça um **Fork** deste repositório;
2. Clone localmente `git clone` `link-DO-SEU-REPOSITÓRIO-do-fork`;
3. Pra manter seu repositório local atualizado: `git remote add upstream` `link-do-REPOSITÓRIO-ORIGINAL`.
4. `git pull upstream main` para baixar e mesclar as alterações no seu repositório local com base na branch main deste repositório original de onde você fez o fork, ou `git fetch upstream main` para baixar sem mesclar.
5. Crie uma nova **branch**: `git branch` `NOME-DA-NOVA-BRANCH`
6. Entre na branch criada: `git checkout` `NOME-DA-NOVA-BRANCH`

	> DICA: Uma maneira mais rápida de criar e mudar para a nova branch é usar o comando `git checkout -b` `NOME-DA-NOVA-BRANCH`
	
7.  Verifique qual branch você está: `git branch`. 
   Saída esperada:
```
* NOME-DA-NOVA-BRANCH
  main
```

8. Adicione suas alterações à àrea de espera do commit `git add .`;
9. Crie um commit e adicione a mensagem indicando a adição do seu perfil `git commit -m`  `MENSAGEM DO COMMIT"`;
10. Envie as alterações para o seu repositório remoto `git push origin` `NOME-DA-NOVA-BRANCH`;
11. Após enviar as alterações para o seu repositório remoto, vá para a página do seu fork no GitHub e crie um Pull Request para a branch `main` do repositório original.
### Considerações Adicionais:
- **Conflitos de Merge**: Se houver conflitos ao tentar mesclar sua branch com a `main` do repositório original, você precisará resolvê-los antes de finalizar o PR.
- **Revisão de Código**: Esteja preparado para receber feedback e fazer ajustes no seu código durante o processo de revisão do PR.
- **Boas Práticas**: Sempre siga as boas práticas de commit, como mensagens claras e descritivas, e evite commits desnecessariamente grandes.

# Baixar arquivos do seu repositório (Pull)
Ou seja, baixar as coisas novas que estão no repositório do Github. 

```
git pull
```

![giphy 6](https://github.com/user-attachments/assets/0e9fe8be-0b6e-4e35-948e-aaf746cbc297)

# Enviar arquivos pro Github (Push)
Enviar as modificações para o repositório remoto

```
git add .
git commit -m "Adicionei uma nova funcionalidade"
git push origin nome-da-branch
```

![giphy 7](https://github.com/user-attachments/assets/978b94c8-3421-44fe-9491-8ab9e46bbf90)

# Ramificações (Branch)

### Listar
```
git branch
```

### Criar 
```
git branch nova-branch
```

### Acessar 

```
git checkout nome-da-branch
```

### Criar e já acessar

```
git checkout -b nova-branch
```

### Mesclar
```
git merge nome-da-branch
```
Combina as mudanças de uma branch com a branch atual.

### Excluir
```
git branch -d nova-branch
```

![giphy 8](https://github.com/user-attachments/assets/103dbea1-b45b-4e4d-a5c0-13b24ad65b70)

# Conflito com a mesclagem

![giphy](https://github.com/user-attachments/assets/312b1b2d-a007-47db-8dba-aabd1d492750)

Abra os arquivos conflitantes. 
   - O Git marca os conflitos no arquivo da seguinte forma:
```
<<<<<<< HEAD
// Seu código local
=======
// Código do branch que você está tentando mesclar
>>>>>>> nome-do-branch
```

Edite o arquivo para resolver o conflito, escolhendo qual código manter ou combinando as alterações.

Após resolver os conflitos:
   ```bash
   git add nome-do-arquivo
   OU
   git add .
   ```

   ```bash
   git commit
   ```
   O Git criará um commit de merge automaticamente.

Envie as alterações para o repositório remoto
   ```bash
   git push origin nome-do-branch
   ```

#### **Dicas para Evitar Conflitos**
   - Sempre sincronize seu branch com o branch principal (`main`) antes de começar a trabalhar.
     ```bash
     git pull origin main
     ```
   - Evite trabalhar diretamente no branch principal. Use branches de *feature*/*fix* para isolamento.
