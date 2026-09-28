# Mulembe — App do Parceiro (página de download)

Página estática para disponibilizar o `.apk` do app do parceiro Mulembe enquanto ele não está nas lojas de aplicações. Sem isto, o ficheiro andava a ser reenviado manualmente por WhatsApp a cada parceiro novo.

**Site:** https://cesaltinofelix.github.io/mulembe_partner_app_download/ (ativa o GitHub Pages primeiro — ver abaixo)

## Como funciona

`index.html` é uma página única, sem build nem dependências. O botão de download **não está fixo a um ficheiro** — ao carregar a página, um pequeno script vai buscar o [último Release](../../releases) deste repositório pela API pública do GitHub e procura, entre os ficheiros anexados, um que termine em `.apk`. Se encontrar, o botão liga a esse ficheiro e mostra a versão, o tamanho e a data. Se não encontrar nenhum Release com `.apk`, mostra "Ainda não disponível" e sugere o WhatsApp como alternativa.

Isto quer dizer que **nunca é preciso editar o código** para publicar uma nova versão — só publicar um Release novo.

## Publicar uma nova versão do app

1. Vai a **Releases → Draft a new release** (menu lateral direito do repositório, ou `/releases/new`).
2. Em "Choose a tag", escreve uma tag nova, por exemplo `v1.0.0` (incrementa a cada versão).
3. Em "Attach binaries", arrasta o ficheiro `.apk` exportado do Flutter.
   - **Nome combinado:** `mulembe-parceiros.apk` — mas qualquer nome que termine em `.apk` funciona, a página não exige esse nome exato.
4. Clica em **Publish release**.
5. Recarrega a página — o botão de download atualiza-se sozinho (pode demorar um pouco a refletir por causa da cache do GitHub Pages/CDN).

Não é preciso marcar a versão anterior como obsoleta: a página usa sempre o **último** Release publicado.

## Ativar o GitHub Pages (só da primeira vez)

1. Neste repositório: **Settings → Pages**.
2. Em "Build and deployment" → "Source", escolhe **Deploy from a branch**.
3. Branch: **main**, pasta **/ (root)**.
4. Guarda. Em 1-2 minutos o site fica disponível em `https://cesaltinofelix.github.io/mulembe_partner_app_download/`.

Se mais tarde quiseres um domínio próprio (ex. `app.mulembe.ao`), adiciona-o em **Settings → Pages → Custom domain** e cria o registo DNS correspondente (CNAME apontado para `cesaltinofelix.github.io`).

## Identidade visual

A página reutiliza os tokens de cor e tipografia já usados nas páginas públicas do `mulembe_front_end` (fundo neutro tipo Apple, âmbar de marca `#F5A623`, tipografia Unbounded/Inter) — não é um design à parte.
