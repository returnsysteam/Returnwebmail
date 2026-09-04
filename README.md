# Impulsionante · Webmail

Cliente de webmail de página única para a caixa de e-mail entregue com as contas
da Impulsionante. Serve para ler as mensagens recebidas — principalmente códigos
de verificação — sem precisar de servidor próprio.

**Acesso:** https://peffmb.github.io/webimpulsionantemail

## Como funciona

- 100% estático (só `index.html`). Publicado via **GitHub Pages** a partir da
  branch `main`.
- Fala direto com a API do **DuckMail** (`https://api.duckmail.sbs`), compatível
  com o padrão mail.tm / Hydra. Sem backend, sem build.
- Login com o **e-mail + senha** da conta. As credenciais ficam apenas no
  `localStorage` do navegador (opção "Manter conectado").

## Recursos

- Sessão persistente + re-login silencioso quando o token expira
- Atualização automática (15s) com aviso de novas mensagens e notificação do SO
- Extração automática de **código de verificação** com botão de copiar
- Busca, filtros (não lidas / com código), paginação ("carregar mais")
- Leitor em `<iframe sandbox>` com bloqueio opcional de imagens remotas;
  todo link do e-mail abre em nova aba
- Excluir mensagem, baixar anexos, copiar texto
- "Recriar caixa e entrar" quando o endereço expirou (mesmo e-mail/senha)
- Tema claro/escuro, responsivo, atalhos de teclado (`/` buscar, `r` atualizar,
  `j`/`k` navegar, `Esc` voltar)

## Configuração

Tudo no topo do `<script>` em `index.html`:

```js
var CFG = {
  API: "https://api.duckmail.sbs",
  PAGE_SIZE: 30,
  AUTO_MS: 15000,
  ...
};
```

As cores são variáveis CSS em `:root` / `:root[data-theme="light"]` no início do
`<style>`.

## Publicar uma alteração

```bash
git add -A && git commit -m "..." && git push origin main
```

O GitHub Pages republica sozinho em ~1 min. Manter o arquivo `.nojekyll` para o
Pages não processar o conteúdo com Jekyll.
