# Banner Generator Pro — Guia de instalação (GitHub Pages)

Gerador de banners (imagem) e vídeos (MP4) de filmes e séries, pronto para WhatsApp, Instagram e Status.
Roda 100% no navegador, hospedado de graça no GitHub. **Não precisa de servidor, Render nem variáveis de ambiente.**

---

## O que você vai precisar
- Uma conta gratuita no **GitHub**: https://github.com
- Uma conta gratuita no **TMDB** (para a chave da API): https://www.themoviedb.org

---

## Passo 1 — Pegar sua chave da API (TMDB)
1. Crie sua conta em https://www.themoviedb.org/signup e confirme o e-mail.
2. Acesse https://www.themoviedb.org/settings/api e solicite uma chave de API (tipo "Developer"; preencha o formulário com os dados do seu uso).
3. Copie a **Chave da API** (32 caracteres) — ou o **Token de Leitura da API** (começa com `eyJ...`). Os dois funcionam.

> Dica: você pode criar até 3 chaves (use contas diferentes ou a mesma) e colocar todas no sistema. Ele alterna entre elas nas buscas e troca sozinho se uma falhar, ficar lenta ou atingir o limite de uso.

## Passo 2 — Publicar o site no GitHub Pages
1. No GitHub, clique em **New repository** (Novo repositório). Dê um nome (ex.: `banners`) e deixe como **Public**. Clique em **Create repository**.
2. Na página do repositório, clique em **uploading an existing file** (ou *Add file → Upload files*).
3. **Descompacte este ZIP** e arraste para a página do GitHub **todo o conteúdo da pasta** `banner-generator-pro`:
   `index.html`, `banner-app.js`, `tailwind.js`, `favicon.ico`, `apple-touch-icon.png`, `apple-touch-icon-precomposed.png`, `manifest.webmanifest` e as pastas `vendor` e `assets`. (Os arquivos devem ficar na raiz do repositório, não dentro de outra pasta.)
4. Clique em **Commit changes**.
5. Vá em **Settings → Pages**. Em *Build and deployment*, escolha **Deploy from a branch**, branch **main**, pasta **/ (root)** e clique em **Save**.
6. Aguarde 1 a 2 minutos. O endereço do seu site aparece no topo da página Pages, no formato:
   `https://SEU-USUARIO.github.io/NOME-DO-REPOSITORIO/`

## Passo 3 — Configurar dentro do site
1. Abra o endereço do seu site e clique na **engrenagem** (canto superior direito).
2. Em **Chaves da API TMDB**, cole sua(s) chave(s) (até 3) e clique em **Testar chaves** — deve aparecer "✓ Chave válida".
3. Configure também (opcional):
   - **Logo / marca d'água** e como ela aparece (sem marca, canto superior direito, ou canto + fundo do banner)
   - **Box Esquerdo / Central / Direito**: texto livre de cada box (Instagram, WhatsApp, chamada, site...), com cor de fundo, cor do texto, ícone próprio e opção de ocultar
4. Clique em **Salvar**.

Pronto! Escolha **Filmes e Séries**, **Trailers em Vídeo** ou **Vídeo com Texto Livre** na tela inicial.

---

## Formatos disponíveis
| Gerador | Formatos |
|---|---|
| Banner (imagem) | Post 1080x1350 · Story 1080x1920 · Status WhatsApp 1230x2050 |
| Vídeo (MP4) | Post 1080x1080 · Story 1080x1920 · Status WhatsApp 1230x2050 |

Nos geradores você também escolhe a **capa** (em português ou sem idioma), pode digitar a **plataforma** em texto livre (se deixar vazio, o sistema detecta automaticamente) e mudar a cor do texto da plataforma.

---

## Observações importantes
- **Suas configurações ficam salvas no navegador** (inclusive as chaves da API). Se limpar os dados do navegador ou trocar de aparelho, é preciso configurar de novo. As chaves nunca são enviadas para ninguém além da TMDB.
- **Vídeos MP4:** Chrome/Edge atuais e Safari geram MP4 direto. Em navegadores que só gravam WebM (ex.: Firefox), o arquivo sai em WebM, pois o GitHub Pages não permite a compactação extra por FFmpeg. Recomendamos Chrome ou Edge.
- Vídeos grandes podem ultrapassar o limite de 100 MB do WhatsApp em HD; use a qualidade *Média* ou *Baixa* nesses casos.
- **Atualizações:** para atualizar o sistema, substitua os arquivos no repositório (*Add file → Upload files*, enviando por cima).

## Problemas comuns
- **"Configure sua chave da API"**: abra a engrenagem, cole a chave e salve.
- **"Chave inválida"**: confira se copiou a chave inteira, sem espaços, e se ela foi aprovada no TMDB.
- **"Limite de uso atingido"**: aguarde um instante ou adicione uma 2ª/3ª chave.
- **Página em branco ou 404**: confirme que o GitHub Pages está ativado (Passo 2) e que `index.html` está na raiz do repositório.
- **Nada mudou depois de atualizar**: pressione Ctrl+Shift+R (ou Cmd+Shift+R) para recarregar sem cache.

---

*Este produto usa a API do TMDB, mas não é endossado ou certificado pelo TMDB. Não remova esse aviso do sistema.*

---

## Histórico de versões
A cada atualização: altere o número e a data no rodapé do `index.html` (`appVersion` / `appUpdated`) e o `?v=` dos arquivos, e registre aqui a versão com a lista dos **arquivos alterados** (os que não mudaram não entram na lista).

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
- **Sem os cabeçalhos:** o sistema continua funcionando e grava o MP4 direto do navegador, agora com bitrate maior (14 Mbps).
- Se após ativar os cabeçalhos alguma imagem externa deixar de carregar, apague o `.htaccess`/`_headers`: o sistema volta ao modo MP4 nativo.
- **Dica ao enviar:** no WhatsApp, envie como **Documento** (sem compressão) ou escolha a opção de qualidade HD; no Telegram, desmarque a compressão / envie como arquivo; o Instagram sempre recomprime, por isso o texto pequeno do rodapé do banner é o primeiro a sofrer.
