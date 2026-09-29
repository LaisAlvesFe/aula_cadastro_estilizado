# Registration Project
 
Página de **cadastro de usuário** construída do zero com HTML5 semântico, formulário com validação nativa e CSS usando seletores por tag e por id. Projeto de estudo, sem back-end.
 
## Prévia
 
- Cabeçalho azul com a logo circular ao lado do nome do sistema
- Formulário centralizado em um cartão branco, sobre fundo cinza
- Rodapé azul com os direitos autorais
## Estrutura do projeto
 
```
cadastro_estilizado/
├── index.html   # Estrutura, conteúdo e formulário
├── styles.css   # Estilização da página
└── logo.jpg     # Logo exibida no cabeçalho
```
 
## Tecnologias
 
- HTML5
- CSS3
- JavaScript (apenas um pequeno bloco para simular o envio)
- Git (versionamento em 3 checkpoints)
## Estrutura semântica
 
A página usa apenas tags com significado definido, sem nenhuma `<div>`:
 
| Tag | Função |
|---|---|
| `<header>` | Cabeçalho com o `<h1>` (logo + nome do sistema) |
| `<main>` | Conteúdo principal |
| `<section>` | Seção de cadastro, com `<h2>` e o formulário |
| `<footer>` | Rodapé com o texto de direitos autorais |
 
## Formulário de cadastro
 
O `<form>` tem `id="formCadastro"` e `method="POST"` (a senha não deve trafegar na URL, como aconteceria com `GET`).
 
| Campo | `type` | `id` / `name` | Validação |
|---|---|---|---|
| Nome completo | `text` | `nome` | `required` |
| E-mail | `email` | `email` | `required` (o navegador valida o formato) |
| Senha | `password` | `senha` | `required`, `minlength="8"`, `maxlength="12"`, `pattern` |
| Termos de uso | `checkbox` | `termos` | `required` |
| Envio | `submit` | `btnEnviar` | `value="Cadastrar"` |
 
### Regra da senha
 
- Entre 8 e 12 caracteres
- Pelo menos um número
- Se a regra não for cumprida, o navegador mostra a mensagem definida no atributo `title`

### Acessibilidade
 
- Todo `<input>` (exceto o checkbox) tem um `<label for="...">` ligado pelo `id`, então clicar no texto foca o campo.
- No checkbox, o `<label>` envolve o próprio `<input>`, então o texto "Concordo com os termos de uso" também é clicável.
- A imagem da logo tem o atributo `alt`.
## Estilização (CSS)
 
### Seletores por tag
 
`*`, `body`, `header`, `footer`, `main`, `h2`, `p`, `label` e `input`.
 
- `*` zera `margin` e `padding` e aplica `box-sizing: border-box`.
- `header, footer` compartilham cor de fundo, texto branco, espaçamento e alinhamento centralizado.
- `label` usa `display: block` para ficar acima do campo.
- `input` ocupa 100% da largura, com `padding`, borda e cantos arredondados.
### Seletores por classe
 
- `header .logo` e `header .logo img`: espaçamento do título e logo redonda (`border-radius: 50%`) alinhada ao texto.
### Seletores por id
 
| Seletor | O que faz |
|---|---|
| `#formCadastro` | Largura máxima de 400px, centralizado, fundo branco, cantos arredondados |
| `#nome`, `#email`, `#senha` | Borda escura e fundo cinza claro, diferentes dos demais inputs |
| `#termos` | `width: auto`, para o checkbox não ocupar 100% da largura |
| `#btnEnviar` | Botão verde, texto branco, sem borda, cursor de mão |
 
> Como seletores de id têm mais especificidade que seletores de tag, `#termos { width: auto }` sobrescreve o `input { width: 100% }`.
 
## Simulação de envio
 
Como não há servidor, o `index.html` inclui um bloco `<script>` que impede o recarregamento da página e exibe um alerta:
 
```js
document.getElementById('formCadastro').addEventListener('submit', function (event) {
  event.preventDefault();
  alert('Dados enviados');
});
```
 
Se algum campo obrigatório estiver vazio ou inválido, o navegador bloqueia o envio antes de o alerta aparecer (validação nativa do HTML5).
 
## Como executar
 
1. Clone ou baixe a pasta do projeto.
2. Abra a pasta no VS Code:
```bash
   cd cadastro_estilizado
   code .
```
3. Abra o `index.html` de uma das formas:
   - **Live Server** (recomendado): botão direito no `index.html` → *Open with Live Server*
   - **Terminal:** `start index.html` (Windows), `open index.html` (macOS) ou `xdg-open index.html` (Linux)
## Histórico Git
 
O projeto foi desenvolvido em 3 checkpoints:
 
1. `Checkpoint 1: cria estrutura semantica da pagina`
2. `Checkpoint 2: cria formulario de cadastro com validacao nativa`
3. `Checkpoint 3: estiliza formulario com seletores por tag e id`
Para conferir: `git log --oneline`
 
