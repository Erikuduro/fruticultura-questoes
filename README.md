# Simulado Interativo — Manga & Banana

Site estático (HTML/CSS/JS puro, sem dependências) com 30 questões interativas de correção instantânea, para revisão da disciplina de Fruticultura.

## Arquivos deste pacote

- `index.html` — o site completo (é o único arquivo que o navegador precisa; tudo está embutido nele).
- `render.yaml` — configuração opcional para deploy automático via "Blueprint" do Render.
- `README.md` — este guia.

## Passo a passo: GitHub → Render (auto-deploy)

### 1. Criar o repositório no GitHub
1. Acesse [github.com/new](https://github.com/new).
2. Dê um nome, por exemplo `simulado-fruticultura`.
3. Deixe como **Public** (necessário para o plano Free de Static Site do Render; se preferir **Private**, funciona também nos planos pagos ou instalando o GitHub App do Render).
4. Não marque nenhuma opção de inicialização (sem README/gitignore — vamos subir os arquivos prontos).
5. Clique em **Create repository**.

### 2. Subir os arquivos (upload direto, sem terminal)
Na página do repositório recém-criado:
1. Clique em **"uploading an existing file"** (ou "Add file" → "Upload files").
2. Arraste os três arquivos desta pasta (`index.html`, `render.yaml`, `README.md`).
3. Escreva uma mensagem de commit (ex: "primeiro deploy do simulado") e clique em **Commit changes**.

*(Se preferir usar `git` pelo terminal, os comandos são:)*
```bash
git init
git add index.html render.yaml README.md
git commit -m "primeiro deploy do simulado"
git branch -M main
git remote add origin https://github.com/SEU_USUARIO/simulado-fruticultura.git
git push -u origin main
```

### 3. Conectar no Render
1. Entre em [dashboard.render.com](https://dashboard.render.com).
2. Clique em **New +** → **Static Site**.
   - *(Static Site é o tipo certo aqui — é HTML/CSS/JS puro, sem backend. "Web Service" é para apps com servidor rodando; não é necessário e custaria mais.)*
3. Conecte sua conta do GitHub (se ainda não conectada) e selecione o repositório `simulado-fruticultura`.
4. Configurações de build:
   - **Build Command**: deixe em branco (não há nada para compilar).
   - **Publish Directory**: `.` (a raiz do repositório).
5. Clique em **Create Static Site**.
6. O Render já habilita **auto-deploy** por padrão: qualquer novo `git push` na branch `main` vai atualizar o site sozinho, em ~1 minuto.

### 4. Compartilhar com a turma
Após o primeiro deploy (leva menos de 1 minuto), o Render gera uma URL do tipo:
`https://simulado-fruticultura.onrender.com`

Basta enviar esse link para os colegas — o site funciona em qualquer navegador (celular ou computador), sem necessidade de login ou instalação.

## Atualizando o conteúdo depois

Sempre que quiser mudar/adicionar questões, edite o array `quizData` dentro de `index.html` (cada questão é um objeto JS com `question`/`items`, `options` ou `answer`), suba a alteração para o GitHub (upload do arquivo atualizado ou `git push`), e o Render republica automaticamente.
