# Banner Generator Pro

Gerador de **banners (imagem PNG)** e **vídeos (MP4)** de filmes e séries, prontos para WhatsApp, Instagram, Telegram e Status.
Roda inteiramente no navegador (não precisa de servidor próprio) e busca as informações e capas na API do TMDB.

> **Versão atual: 1.10.0** · Histórico completo no final deste arquivo.

> ### ⚠️ Sobre os endereços (links) — leia primeiro
> Este projeto é um **código-fonte**: cada pessoa publica o **próprio** site e usa os **próprios** endereços.
> **Nenhum endereço deste arquivo é um site real.** Os endereços escritos aqui são apenas **EXEMPLOS DE FORMATO**.
> O seu endereço real aparece no painel do GitHub / do Cloudflare depois que você publica (veja a seção 1).

---

## Índice
1. [Acessos: os dois tipos de endereço e como encontrar o seu](#1-acessos-os-dois-tipos-de-endereço-e-como-encontrar-o-seu)
2. [Diferenças entre as duas versões](#2-diferenças-entre-as-duas-versões)
3. [Tutorial rápido: qual versão usar?](#3-tutorial-rápido-qual-versão-usar)
4. [Instalação passo a passo (para quem vai publicar o próprio site)](#4-instalação-passo-a-passo-para-quem-vai-publicar-o-próprio-site)
5. [Atualizações: como manter as duas versões iguais](#5-atualizações-como-manter-as-duas-versões-iguais)
6. [Sobre o projeto e funcionalidades](#6-sobre-o-projeto-e-funcionalidades)
7. [Compressão otimizada de MP4 (detalhes técnicos)](#7-compressão-otimizada-de-mp4-detalhes-técnicos)
8. [Solução de problemas](#8-solução-de-problemas)
9. [Histórico de versões](#9-histórico-de-versões)

---

## 1. Acessos: os dois tipos de endereço e como encontrar o seu

Você pode publicar **uma** versão (GitHub Pages) ou **duas** (GitHub Pages + Cloudflare Pages). Cada uma tem o seu endereço:

| Versão | Para que serve | Formato do endereço (**EXEMPLO — não é real**) |
|---|---|---|
| **GitHub Pages** | Versão padrão: criar banners e vídeos normalmente, **sem** a etapa de compressão otimizada de MP4. | `https://usuario.github.io/repositorio/` |
| **Cloudflare Pages** | Mesma versão, **com** compressão otimizada de vídeos MP4 (quando o navegador permite). | `https://nome-do-projeto.pages.dev/` |

### Onde encontrar o seu endereço
- **GitHub Pages:** no GitHub, abra o seu repositório → **Settings → Pages**. No topo aparece *"Your site is live at …"* com o seu endereço.
- **Cloudflare Pages:** no painel do Cloudflare → **Workers & Pages** → clique no seu projeto. O endereço (terminado em `.pages.dev`) aparece na página do projeto / em *Deployments*. (Os nomes dos botões podem mudar um pouco no painel.)
- **Domínio próprio (opcional):** se você usa um domínio seu, esse é o endereço que vale.

### Como o sistema sabe onde está
Você **não precisa configurar nada**: o site identifica sozinho se está num endereço `*.github.io` (GitHub Pages), `*.pages.dev` (Cloudflare Pages) ou em outro lugar, e liga ou desliga a compressão conforme a compatibilidade. O resultado aparece:
- no **rodapé** da página (ex.: *"Hospedagem: GitHub Pages · Compressão otimizada: indisponível aqui"*);
- em **Configurações → Compressão otimizada de vídeos MP4**;
- no painel e no resultado dos geradores de vídeo.

> As configurações (chaves da API, logo, cores, textos dos boxes) ficam salvas **no navegador, separadamente para cada endereço**. Se você usar os dois endereços, configure em cada um.

---

## 2. Diferenças entre as duas versões

As duas versões têm **a mesma interface, os mesmos recursos, as mesmas configurações e as mesmas atualizações** (é o mesmo repositório publicado em dois lugares). Pesquisa de filmes e séries, escolha de capas, banners, vídeos MP4, qualidades, marca d'água e personalização dos boxes funcionam nas duas.

| | GitHub Pages | Cloudflare Pages |
|---|---|---|
| Criar banners (PNG) | ✅ | ✅ |
| Criar vídeos (MP4) | ✅ | ✅ |
| Pesquisa TMDB, capas e galeria de capas | ✅ | ✅ |
| Todas as configurações e personalização | ✅ | ✅ |
| **Compressão otimizada de MP4** | ❌ não disponível (limitação da hospedagem) | ✅ quando o navegador permite |

A **única diferença principal** é a compressão otimizada. O GitHub Pages não permite enviar os cabeçalhos de segurança que ela exige; o Cloudflare Pages permite (arquivo `_headers`, já incluído). Isso **não é erro**: no GitHub Pages o sistema avisa com clareza e gera o vídeo normalmente.

---

## 3. Tutorial rápido: qual versão usar?

Funciona igual no computador, no Android e no iPhone (abra pelo navegador).

1. **Só quero criar banners e vídeos** → abra o endereço do **GitHub Pages**, use as ferramentas normalmente e baixe o arquivo.
2. **Quero comprimir o vídeo MP4** (reduzir o tamanho antes de enviar) → abra o endereço do **Cloudflare Pages**, crie o banner/vídeo e deixe a qualidade **"Redes Sociais"** selecionada; a compressão acontece sozinha no final.
3. **Não sei qual escolher** → comece pelo **GitHub Pages**: ele atende ao uso normal. O **Cloudflare Pages** é o recomendado para quem precisa reduzir o tamanho dos vídeos antes de compartilhar.
4. **A compressão não está disponível** → veja o rodapé ou **Configurações → Compressão otimizada**:
   - se diz **GitHub Pages**, é normal: use o endereço do Cloudflare Pages;
   - se diz **Cloudflare Pages** e mesmo assim está "indisponível", atualize o navegador ou tente outro (no computador, Chrome ou Edge); no iPhone, abra pelo Safari atualizado e sem modo privado. Se continuar, gere o vídeo sem a compressão (ele sai normalmente).
5. **A compressão falhou ou demorou demais** → use o botão **"Pular compressão e usar o vídeo direto"** (aparece durante a compressão) para ficar com o vídeo original, que é entregue na hora. Se o compressor travar, o sistema interrompe sozinho e entrega o vídeo original com um aviso.

> Quem não sabe o endereço do Cloudflare Pages deve pedi-lo a quem administra o site. O administrador pode deixar um botão para ele dentro do site (veja o passo 4.7).

---

## 4. Instalação passo a passo (para quem vai publicar o próprio site)

### 4.1 O que você vai precisar
- Uma conta gratuita no **GitHub**: https://github.com
- Uma conta gratuita no **TMDB** (chave da API): https://www.themoviedb.org
- *(Opcional, para a compressão)* uma conta gratuita no **Cloudflare**: https://dash.cloudflare.com

### 4.2 Pegar sua chave da API (TMDB)
1. Crie sua conta em https://www.themoviedb.org/signup e confirme o e-mail.
2. Acesse https://www.themoviedb.org/settings/api e solicite uma chave de API (tipo "Developer"; preencha o formulário com os dados do seu uso).
3. Copie a **Chave da API** (32 caracteres) — ou o **Token de Leitura da API** (começa com `eyJ...`). Os dois funcionam.

> Dica: você pode usar até 3 chaves. O sistema alterna entre elas nas buscas e troca sozinho se uma falhar, ficar lenta ou atingir o limite de uso.

### 4.3 Copiar o projeto para o seu GitHub
1. No GitHub, clique em **New repository**. Dê um nome (ex.: `banners`) e deixe como **Public**. Clique em **Create repository**.
2. Na página do repositório, clique em **uploading an existing file** (ou *Add file → Upload files*).
3. **Descompacte o ZIP** do projeto e arraste **todo o conteúdo** da pasta `banner-generator-pro` para a página do GitHub. Os arquivos precisam ficar na **raiz** do repositório (não dentro de outra pasta):
   - `index.html`, `banner-app.js`, `site-config.js`, `tailwind.js`, `manifest.webmanifest`
   - `favicon.ico`, `apple-touch-icon.png`, `apple-touch-icon-precomposed.png`
   - as pastas `vendor` e `assets`
   - `_headers` (necessário para a compressão no Cloudflare; o GitHub Pages simplesmente o ignora)
   - `.htaccess` e `nginx-headers.conf.example` (só servem para hospedagem própria Apache/Nginx; podem ficar)
   > Arquivos que começam com ponto ou sublinhado (`.htaccess`, `_headers`) podem ficar **ocultos** no seu computador. Ative "mostrar arquivos ocultos" (Mac: `Cmd + Shift + .`) e confira se foram enviados.
4. Clique em **Commit changes**.
   > O envio pelo navegador aceita até 25 MiB por arquivo. O maior arquivo do projeto (`vendor/ffmpeg-core.wasm`, ≈ 23 MiB) cabe, mas se o navegador recusar o envio use o aplicativo **GitHub Desktop** ou o Git.

### 4.4 Publicar a versão GitHub Pages
1. No repositório: **Settings → Pages**.
2. Em *Build and deployment*, escolha **Deploy from a branch**, branch **main**, pasta **/ (root)** e clique em **Save**.
3. Aguarde 1 a 2 minutos. O seu endereço aparece no topo da página Pages (formato de exemplo: `https://usuario.github.io/repositorio/`).

### 4.5 (Opcional) Publicar a versão Cloudflare Pages — com compressão
Use o **mesmo repositório** do GitHub (não crie outro):
1. No painel do Cloudflare: **Workers & Pages → Create → Pages → Connect to Git** e autorize o acesso ao seu GitHub.
2. Escolha o repositório do projeto.
3. Deixe o **comando de build vazio** e o **diretório de saída como `/`**.
4. Clique em **Save and Deploy**. (O limite do Cloudflare Pages é 25 MiB por arquivo; o `ffmpeg-core.wasm`, ≈ 23 MiB, cabe.)
5. Ao terminar, o Cloudflare mostra o seu endereço (formato de exemplo: `https://nome-do-projeto.pages.dev/`).

> Os nomes dos botões podem variar no painel. O ponto importante: o Cloudflare precisa estar **conectado ao repositório** e o arquivo `_headers` precisa estar na raiz.

### 4.6 Configurar dentro de cada site
1. Abra o seu endereço e clique na **engrenagem** (canto superior direito).
2. Em **Chaves da API TMDB**, cole sua(s) chave(s) (até 3) e clique em **Testar chaves** — deve aparecer "✓ Chave válida".
3. Configure o que quiser (opcional): **logo / marca d'água**, e os **Box Esquerdo / Central / Direito** (texto livre, cores, ícone próprio, ocultar).
4. Clique em **Salvar**.
5. Se publicou os dois endereços, **repita nos dois** (as configurações ficam salvas por endereço).

### 4.7 (Opcional) Botão para a outra versão dentro do site
Abra o arquivo `site-config.js` e preencha **os seus próprios** endereços entre aspas, por exemplo:

```js
githubPagesUrl: 'https://usuario.github.io/repositorio/',     // EXEMPLO DE FORMATO — use o seu
cloudflarePagesUrl: 'https://nome-do-projeto.pages.dev/',     // EXEMPLO DE FORMATO — use o seu
```
Com isso, o GitHub Pages passa a mostrar um link *"Abrir a versão com compressão"* e o Cloudflare Pages um link para a versão GitHub. **Deixando vazio, nenhum link aparece** e tudo continua funcionando. Se você usa **domínio próprio**, informe-o em `githubHosts` ou `cloudflareHosts` para o site mostrar os textos certos.

### 4.8 Qual endereço usar em cada situação
| Situação | Use |
|---|---|
| Só criar banners e vídeos | GitHub Pages |
| Reduzir o tamanho do MP4 | Cloudflare Pages |
| Publicou só o GitHub Pages | O endereço do GitHub Pages (a compressão não estará disponível) |
| Publicou os dois e está em dúvida | GitHub Pages para o dia a dia; Cloudflare Pages quando precisar comprimir |

### 4.9 Teste rápido do seu site (5 minutos)
Faça em **cada** endereço que você publicou:
1. O site abre e o rodapé mostra a **versão** e a **hospedagem** corretas.
2. Em **Configurações**, as chaves passam em **Testar chaves**.
3. Em **Filmes e Séries**, pesquise um título: aparecem os resultados **com as capas**; ao escolher, aparecem a **prévia** e a **galeria de capas**.
4. Baixe um banner (PNG) e gere um vídeo curto.
5. No Cloudflare Pages: o painel de vídeo mostra *"Compressão otimizada de MP4 disponível"* e o resultado indica a conversão. No GitHub Pages: o aviso explica que a compressão está no Cloudflare Pages.

---

## 5. Atualizações: como manter as duas versões iguais

As duas versões **saem do mesmo repositório**. Você atualiza **uma vez só**, no GitHub, e as duas publicações se atualizam sozinhas — não é preciso repetir a alteração em dois lugares.

1. Baixe o novo ZIP e descompacte.
2. No repositório do GitHub: **Add file → Upload files**, envie os arquivos novos **por cima** (mesmos nomes; mantenha as pastas) e clique em **Commit changes**.
3. Aguarde:
   - **GitHub Pages:** republica sozinho em 1 a 2 minutos (acompanhe em **Actions**).
   - **Cloudflare Pages:** gera uma nova publicação a cada alteração enviada ao GitHub (acompanhe em **Deployments** no painel).
4. Confira: abra os dois endereços e veja se o **número da versão no rodapé** é o mesmo.
5. Se continuar aparecendo a versão antiga, recarregue sem cache (**Ctrl + Shift + R**; no Mac **Cmd + Shift + R**; no celular, feche e reabra a aba).

> Suas configurações (chaves, logo, cores) **não são apagadas** por uma atualização: ficam no navegador.
> Se você publicou só o GitHub Pages, siga os mesmos passos (a etapa do Cloudflare não existe).
> Evite editar arquivos diretamente no Cloudflare: sempre altere pelo GitHub, para as duas versões não ficarem diferentes.

---

## 6. Sobre o projeto e funcionalidades

**Finalidade:** criar rapidamente banners e vídeos de divulgação de filmes e séries, com as suas informações de contato, prontos para compartilhar.

**Geradores:** **Filmes e Séries** (banner PNG) · **Trailers em Vídeo** (MP4 a partir de um vídeo seu) · **Vídeo com Texto Livre** (MP4 com um texto seu no lugar dos dados do filme).

| Gerador | Formatos |
|---|---|
| Banner (imagem) | Post 1080x1350 · Story 1080x1920 · Status WhatsApp 1230x2050 |
| Vídeo (MP4) | Post 1080x1080 · Story 1080x1920 · Status WhatsApp 1230x2050 |

**Principais recursos**
- Pesquisa de filmes e séries no TMDB (com até 3 chaves em rodízio).
- **Escolha da capa** (galeria em português ou sem idioma) e prévia da capa selecionada.
- **Plataforma** detectada automaticamente (ou texto livre) e cor do texto da plataforma.
- **Três boxes** (Esquerdo, Central, Direito) com texto livre, cores, ícone próprio e opção de ocultar.
- **Logo / marca d'água:** sem marca, canto superior direito, ou canto + fundo.
- Vídeos por etapas (Preparar → Gravar → Comprimir → Concluir) e qualidades *Redes Sociais*, *Alta*, *Média* e *Baixa*.
- Arquivos baixados com nome + categoria (ex.: `Speed_Racer_Filme.mp4`).
- "Adicionar à tela inicial" no celular (ícone de aplicativo).

**Melhorias relevantes das versões anteriores:** geração e compressão de vídeos MP4 mais rápidas e estáveis (1.7 a 1.9.3), correção das capas do TMDB com os cabeçalhos de segurança do Cloudflare (1.9.4), compatibilidade com as duas hospedagens e avisos claros (1.9.2 e 1.10.0). Detalhes no [histórico](#9-histórico-de-versões).

**Importante:** as configurações ficam salvas **no navegador** (inclusive as chaves da API, que nunca são enviadas a ninguém além da TMDB). Ao limpar os dados do navegador ou trocar de aparelho, é preciso configurar de novo.

---

## 7. Compressão otimizada de MP4 (detalhes técnicos)

Nos geradores de vídeo, a qualidade **"Redes Sociais (Full HD otimizado)"** vem selecionada por padrão (recompressão H.264 para Telegram, WhatsApp e Instagram).

- **Requisitos:** o endereço precisa enviar `Cross-Origin-Opener-Policy: same-origin` e `Cross-Origin-Embedder-Policy: require-corp`, e o navegador precisa oferecer `SharedArrayBuffer`. O sistema verifica isso sozinho e mostra o resultado em **Configurações → Compressão otimizada**.
- **Cloudflare Pages / Netlify:** o arquivo `_headers` (já incluído) aplica os cabeçalhos. **Apache/cPanel:** `.htaccess`. **Nginx:** `nginx-headers.conf.example`. Publique também a pasta `vendor` (incluindo `ffmpeg-core.wasm`, ≈ 23 MiB).
- **GitHub Pages não permite esses cabeçalhos** — por isso a compressão não existe lá. Os vídeos são gerados normalmente: em navegadores que gravam MP4 direto, o arquivo sai em alta qualidade (≈ 14 Mbps), sem a etapa de compressão.
- **Cabeçalhos de segurança e imagens externas:** com os cabeçalhos ativos, o navegador só aceita imagens externas (capas do TMDB) carregadas com `crossorigin="anonymous"` e liberadas pelo servidor da imagem (CORS). O sistema já faz isso; **não apague o `_headers` para "consertar" capas** — isso desliga a compressão e não é necessário.
- **Alternativas se a compressão falhar:** botão *"Pular compressão e usar o vídeo direto"*, interrupção automática do compressor se travar (entrega o MP4 original com aviso) e, sem compressão disponível, geração normal.
- **Dica ao enviar:** no WhatsApp, envie como **Documento** (sem compressão) ou escolha a opção de qualidade HD; no Telegram, desmarque a compressão / envie como arquivo; o Instagram sempre recomprime, por isso o texto pequeno do rodapé do banner é o primeiro a sofrer.
- Vídeos grandes podem passar do limite de 100 MB do WhatsApp em HD: use a qualidade *Média* ou *Baixa*.

---

## 8. Solução de problemas

**Aparece "Configure sua chave da API" / "Chave inválida" / "Limite de uso atingido"**
Abra a engrenagem, cole a chave inteira (sem espaços), clique em **Testar chaves** e **Salvar**. Se o limite de uso for atingido, aguarde um instante ou adicione uma 2ª/3ª chave. Lembre-se: cada endereço guarda as suas próprias configurações.

**As capas não carregam (aparece um ícone 🎬 no lugar)**
1. Confira a internet e recarregue sem cache (Ctrl/Cmd + Shift + R).
2. Verifique se alguma extensão, rede de empresa/escola ou bloqueador de anúncios bloqueia `image.tmdb.org`; teste em outra rede ou aba anônima.
3. Teste a **outra versão** (GitHub ↔ Cloudflare). Se funciona em uma e não na outra, anote qual e avise o suporte.
4. Não apague `_headers`/`.htaccess` por causa das capas (veja a seção 7).

**A pesquisa de filmes e séries não mostra resultados**
Veja a mensagem exibida abaixo do campo de pesquisa (ela informa se o problema é chave, limite de uso ou conexão). Confira as chaves em Configurações, tente outro título e aguarde alguns segundos se a rede estiver lenta.

**Falha ao gerar banner ou vídeo**
Recarregue a página e tente de novo. Use **Chrome/Edge** no computador ou o **Safari atualizado** no iPhone, fora do modo privado, com espaço livre no aparelho. Para vídeos muito longos ou pesados, use a qualidade *Média* ou *Baixa*. Se o problema só acontece em uma hospedagem, experimente a outra.

**A compressão não inicia ou não termina**
Confirme se está no endereço do **Cloudflare Pages** (veja o rodapé). Se estiver e continuar "indisponível", veja o motivo em **Configurações → Compressão otimizada** (cabeçalhos do `_headers` não aplicados, pasta `vendor` não publicada ou navegador sem os recursos). Se iniciou mas demora, clique em **"Pular compressão e usar o vídeo direto"**.

**Funciona num endereço e no outro não / diferenças entre hospedagens**
A única diferença esperada é a compressão otimizada (somente no Cloudflare Pages). Se houver outras diferenças, confira se os dois estão com o **mesmo número de versão** no rodapé — se não, a atualização ainda não foi publicada em um deles (seção 5).

**Página em branco ou erro 404**
Confirme que o GitHub Pages está ativado (seção 4.4) e que o `index.html` está na raiz do repositório (não dentro de outra pasta).

**Nada mudou depois de atualizar**
Recarregue sem cache e confira se a nova versão aparece no rodapé.

---

*Este produto usa a API do TMDB, mas não é endossado ou certificado pelo TMDB. Não remova esse aviso do sistema.*

---

## 9. Histórico de versões
A cada atualização: altere o número e a data no rodapé do `index.html` (`appVersion` / `appUpdated`) e o `?v=` dos arquivos, **revise este LEIA-ME** (acessos, tutoriais, diferenças entre as versões, requisitos de hospedagem e esta lista) e registre aqui a versão com a lista dos **arquivos alterados** (os que não mudaram não entram na lista). O LEIA-ME deve sempre refletir o código publicado.

### 1.10.0 — 23/10/2026
Hospedagem identificada automaticamente (GitHub Pages × Cloudflare Pages), avisos claros sobre a compressão e documentação reorganizada. Nenhum endereço fixo no código: cada comprador usa os próprios.
- **Identificação automática da hospedagem:** o site reconhece `*.github.io`, `*.pages.dev` ou outro endereço e ativa/desativa a compressão otimizada conforme os cabeçalhos e o navegador. A limitação do GitHub Pages passa a ser explicada (sem aparência de erro) no painel dos vídeos, no resultado, em **Configurações → Compressão otimizada de vídeos MP4** e no rodapé.
- **`site-config.js` (novo, opcional e vazio):** permite ao comprador informar os próprios endereços para exibir um link para a outra versão e declarar domínio próprio. Endereços inválidos (ex.: `javascript:`) são ignorados.
- **Capas do TMDB:** capa que não carrega mostra um ícone no lugar da imagem quebrada (resultados, galeria e prévia) e a prévia volta ao escolher outra capa. A abordagem `crossorigin="anonymous"` da 1.9.4 foi mantida e verificada contra servidor de imagens com CORS ligado e desligado, com e sem os cabeçalhos do Cloudflare.
- Não é mais feita a sondagem de `/health` nos endereços `*.github.io` e `*.pages.dev` (evita erro 404 no console).
- Correção do texto de tamanho após a compressão quando o arquivo final fica maior que o original (aparecia "--9%"; agora "+9%").
- `LEIA-ME.md` reorganizado: acessos e como achar o seu endereço, diferenças entre as versões, tutorial para escolher a versão, instalação passo a passo (GitHub Pages e Cloudflare Pages), como manter as duas versões iguais, solução de problemas e histórico.
- Arquivos alterados: `banner-app.js`, `index.html`, `LEIA-ME.md`
- Arquivos novos: `site-config.js`

### 1.9.4 — 23/10/2026
Correção das capas (posters) que não apareciam nas listas e na seleção quando os cabeçalhos COOP/COEP estão ativos (Cloudflare/Netlify): imagens externas agora são carregadas com `crossorigin="anonymous"`.
- Arquivos alterados: `banner-app.js`, `index.html`, `LEIA-ME.md`

### 1.9.3 — 23/10/2026
Correção da compressão que ficava em 0%: progresso real por quadros (o vídeo gravado não traz duração), interrupção automática se o compressor travar (entrega o MP4 nativo com aviso), botão "Pular compressão", preset mais rápido (superfast) e remoção do `-vsync cfr`.
- Arquivos alterados: `banner-app.js`, `index.html`, `LEIA-ME.md`

### 1.9.2 — 23/10/2026
Aviso de compressão adaptado para quem usa GitHub Pages (explica a limitação em vez de indicar erro) e guia de como ativar a compressão avançada.
- Arquivos alterados: `banner-app.js`, `index.html`, `LEIA-ME.md`

### 1.9.1 — 23/10/2026
Histórico do LEIA-ME passa a informar os arquivos alterados em cada versão.
- Arquivos alterados: `LEIA-ME.md`, `index.html` (versão no rodapé)

### 1.9.0 — 23/10/2026
Gerador de vídeo por etapas (Preparar → Gravar → Comprimir → Concluir) com indicador visual e aviso quando a compressão avançada não está disponível.
- Arquivos alterados: `banner-app.js`, `index.html`, `LEIA-ME.md`

### 1.8.0 — 23/10/2026
Arquivos baixados com nome + categoria (ex.: `Speed_Racer_Filme.mp4` / `.png`); ícone do iPhone embutido no HTML (data URI) para a tela de início.
- Arquivos alterados: `banner-app.js`, `index.html`, `LEIA-ME.md`

### 1.7.0 — 23/10/2026
Nova qualidade "Redes Sociais (Full HD otimizado)" nos vídeos: recompressão H.264 (30 fps constante, High Profile, faststart, leve nitidez para o texto) e bitrate maior. Compressor FFmpeg incluído em `vendor/`.
- Arquivos alterados: `banner-app.js`, `index.html`, `LEIA-ME.md`
- Arquivos novos: `vendor/ffmpeg-core.js`, `vendor/ffmpeg-core.wasm`, `vendor/ffmpeg-core.worker.js`, `.htaccess`, `_headers`, `nginx-headers.conf.example`

### 1.6.1 — 22/10/2026
Nos vídeos Story e Status (trailer e texto livre) a logo fica centralizada ACIMA do vídeo, sem cobrir a imagem.
- Arquivos alterados: `banner-app.js`, `index.html`, `LEIA-ME.md`

### 1.6.0 — 22/10/2026
Vídeos Story e Status (trailer e texto livre) com a logo centralizada no topo do vídeo, mesmo padrão nos dois.
- Arquivos alterados: `banner-app.js`, `index.html`, `LEIA-ME.md`

### 1.5.0 — 22/10/2026
Correção do ícone ao adicionar na tela de início do iPhone (apple-touch-icon na raiz, sem parâmetro de versão).
- Arquivos alterados: `index.html`, `LEIA-ME.md`
- Arquivos novos: `apple-touch-icon.png`, `apple-touch-icon-precomposed.png`

### 1.4.0 — 22/10/2026
Aviso em vermelho nas Configurações sobre os dados ficarem salvos apenas no navegador.
- Arquivos alterados: `index.html`, `LEIA-ME.md`

### 1.3.0 — 22/10/2026
Favicon e ícone de aplicativo (Android/iOS) com a logo; manifest para "Adicionar à tela inicial".
- Arquivos alterados: `index.html`, `LEIA-ME.md`
- Arquivos novos: `favicon.ico`, `manifest.webmanifest`, `assets/icons/` (apple-touch-icon, favicon-16, favicon-32, icon-192, icon-512, icon-maskable-192, icon-maskable-512)

### 1.2.0 — 22/10/2026
Logo movida para a pasta `assets/` e botão "Canal Oficial de Atualizações" (Telegram) no rodapé.
- Arquivos alterados: `index.html`, `LEIA-ME.md`
- Arquivos movidos: `logo.png` → `assets/logo.png`

### 1.1.0 — 22/10/2026
Logo no lugar do título principal, rodapé com versão e botão "Ajuda e Suporte" (Telegram).
- Arquivos alterados: `index.html`, `LEIA-ME.md`
- Arquivos novos: `logo.png`

### 1.0.0
Versão inicial.

---

## Qualidade para redes sociais (Telegram, WhatsApp, Instagram)
Nos geradores de vídeo, a qualidade **"Redes Sociais (Full HD otimizado)"** vem selecionada por padrão.

- **Com otimização completa:** o servidor precisa enviar os cabeçalhos `Cross-Origin-Opener-Policy: same-origin` e `Cross-Origin-Embedder-Policy: require-corp`. Já deixei prontos: `.htaccess` (Apache/cPanel), `_headers` (Netlify/Cloudflare Pages) e `nginx-headers.conf.example` (Nginx). Suba os arquivos da pasta `vendor` (incluindo `ffmpeg-core.wasm`, ~24 MB). Quando ativo, aparece "otimização para redes sociais" no painel do gerador.
- **GitHub Pages não permite esses cabeçalhos.** Para ativar a compressão mantendo o GitHub como origem do código, publique o **mesmo repositório** em um serviço gratuito que aceita o arquivo `_headers` (já incluído):
  - **Cloudflare Pages:** Workers & Pages → Create → Pages → Connect to Git → escolha o repositório → deixe o comando de build vazio e o diretório de saída como `/` → Save and Deploy. (O limite é 25 MB por arquivo; o `ffmpeg-core.wasm` tem ~24 MB e cabe.)
  - **Netlify:** Add new site → Import from GitHub → escolha o repositório → sem comando de build e sem pasta de publicação → Deploy.
  - A cada alteração enviada ao GitHub, o site é atualizado sozinho. O endereço muda, e as configurações salvas no navegador (chaves, logo, cores) precisam ser refeitas no novo endereço.
- **Sem os cabeçalhos:** o sistema continua funcionando e grava o MP4 direto do navegador, agora com bitrate maior (14 Mbps).
- Se após ativar os cabeçalhos alguma imagem externa deixar de carregar, apague o `.htaccess`/`_headers`: o sistema volta ao modo MP4 nativo.
- **Dica ao enviar:** no WhatsApp, envie como **Documento** (sem compressão) ou escolha a opção de qualidade HD; no Telegram, desmarque a compressão / envie como arquivo; o Instagram sempre recomprime, por isso o texto pequeno do rodapé do banner é o primeiro a sofrer.
