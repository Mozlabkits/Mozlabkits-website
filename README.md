Mozlabkits — Site institucional

Site institucional completo, responsivo, bilíngue (PT/EN) e pronto para publicação gratuita, construído apenas com **HTML, CSS e JavaScript puros** (sem frameworks, sem etapa de build). Isso o torna muito rápido e fácil de publicar em qualquer hospedagem estática.

> **Sobre o conteúdo:** este projeto usa "Mozlabkits", uma ONG fictícia, como exemplo funcional e completo. Troque textos, imagens, PDFs, e-mails, telefones e links por dados reais antes de publicar — veja a seção **"O que trocar antes de publicar"**.

---

## 1. Estrutura de pastas

```
projeto/
├── index.html                 # Página única (todas as seções, com âncoras)
├── 404.html                   # Página de erro 404
├── robots.txt                 # Indexação para buscadores
├── sitemap.xml                # Mapa do site para SEO
├── netlify.toml                # Configuração opcional para Netlify
├── assets/
│   ├── css/
│   │   └── style.css          # Todo o design do site (tokens, layout, componentes)
│   ├── js/
│   │   ├── main.js            # Menu, busca, galeria, vídeos, formulários, modal
│   │   └── i18n.js            # Sistema de tradução PT/EN
│   ├── i18n/
│   │   ├── pt.json            # Todos os textos em Português
│   │   └── en.json            # Todos os textos em Inglês
│   ├── img/
│   │   ├── logo.svg, favicon.svg, hero-art.svg
│   │   ├── gallery-1.svg … gallery-6.svg   (fotos de exemplo)
│   │   ├── video-1.svg … video-3.svg        (miniaturas de vídeo de exemplo)
│   │   └── icons.svg          # Sprite com todos os ícones do site
│   └── docs/
│       ├── relatorio-anual-2025.pdf
│       ├── estatuto-social.pdf
│       └── balanco-financeiro-2025.pdf
└── scripts/
    └── gerar_pdfs_exemplo.py  # Script Python que gerou os PDFs de exemplo
```

Todas as imagens de exemplo são ilustrações vetoriais (SVG) originais, leves e sem dependência de fotos de terceiros — troque-as por fotos reais quando desejar (instruções abaixo).

---

## 2. Recursos incluídos

- Menu profissional (desktop fixo + menu mobile em tela cheia)
- Banner inicial com ilustração e chamadas para ação
- Botões de chamada para ação (voluntariado, programas, doação)
- Formulário de contato, formulário de voluntários e formulário de parceiros
- Botão de doação com modal explicando as formas de doar
- Busca interna do site (filtra as seções por palavra-chave)
- Galeria de fotos com lightbox (ampliar imagem, navegar com setas/teclado)
- Galeria de vídeos (carregamento do player só ao clicar — melhora a velocidade)
- Download de documentos em PDF
- Mapa incorporado (Google Maps)
- Ícones modernos em SVG (sem bibliotecas externas)
- Rodapé completo com links institucionais, redes sociais e newsletter
- Links para Facebook, LinkedIn, Instagram, YouTube e WhatsApp (+ botão flutuante de WhatsApp)
- Site 100% responsivo (celular, tablet, desktop)
- Bilíngue PT/EN com troca instantânea, sem recarregar a página
- Preparado para novos idiomas (basta adicionar um novo arquivo JSON — ver seção 6)

---

## 3. Sistema de design (resumo)

- **Paleta:** verde-floresta `#1B3A2B`/`#0E1F16`, papel esverdeado `#EFF2EC`, dourado-nascer-do-sol `#E8B84B`/`#C98A2C`, terracota discreto `#B45338`.
- **Tipografia:** títulos em `Fraunces` (serifada, com personalidade), corpo em `Inter` (alta legibilidade), rótulos/dados em `IBM Plex Mono`.
- **Elemento de assinatura:** "anéis de crescimento" (círculos concêntricos, como anéis de árvore) usados como divisores de seção — remete às "raízes" do nome e da missão do instituto.
- Todo o CSS está em `assets/css/style.css`, organizado por componente e comentado por blocos.

---

## 4. Como testar localmente

Como o site usa `fetch()` para carregar os textos (`pt.json`/`en.json`) e ícones SVG externos, **não funciona 100% se você apenas der duplo-clique no `index.html`** (restrição de segurança dos navegadores para arquivos locais). Use um servidor local simples:

**Com Python (já vem instalado na maioria dos sistemas):**
```bash
cd projeto
python3 -m http.server 8000
```
Depois abra `http://localhost:8000` no navegador.

**Com Node.js:**
```bash
cd projeto
npx serve .
```

---

## 5. O que trocar antes de publicar

| Onde | O que fazer |
|---|---|
| `assets/i18n/pt.json` e `en.json` | Revisar todos os textos institucionais (missão, programas, endereço, etc.) |
| `assets/img/gallery-*.svg`, `video-*.svg`, `hero-art.svg` | Substituir pelas fotos e miniaturas de vídeo reais (mesmo nome de arquivo ou ajuste os `src` no `index.html`) |
| `index.html` → seção `#videos` | Trocar `data-video-id="dQw4w9WgXcQ"` pelos IDs reais dos vídeos no YouTube |
| `index.html` → seção `#mapa` | Trocar o endereço no link do Google Maps (`src` do `iframe`) pelo endereço real |
| `index.html` → seção `#doar` / modal | Substituir chave Pix e dados bancários fictícios pelos reais |
| `index.html` → rodapé e `#contato` | Atualizar e-mail, telefone, WhatsApp, endereço e links das redes sociais |
| `assets/docs/*.pdf` | Substituir pelos documentos reais (relatório, estatuto, balanço) |
| `assets/img/favicon.svg`, `logo.svg` | Ajustar para a identidade visual real, se necessário |
| `index.html` (`<head>`) | Atualizar `<link rel="canonical">`, URLs de Open Graph e o JSON-LD de dados estruturados |
| `robots.txt` e `sitemap.xml` | Atualizar a URL final do site |

### Sobre os formulários

Os três formulários (voluntariado, parceiros, contato) já estão marcados com `data-netlify="true"`, prontos para funcionar **automaticamente e de graça no Netlify** (veja seção 7). Se for publicar apenas no **GitHub Pages**, que não processa formulários, você tem duas opções simples e gratuitas:
1. Usar um serviço como **Formspree** ou **Web3Forms**: crie uma conta gratuita, troque o atributo `action` de cada `<form>` pela URL fornecida pelo serviço.
2. Publicar no **Netlify** (recomendado), que já resolve isso sem nenhuma configuração extra.

---

## 6. Como adicionar um novo idioma no futuro

O site já foi criado pensando em crescer para outros idiomas:

1. Duplique `assets/i18n/en.json` para, por exemplo, `assets/i18n/es.json` e traduza os valores.
2. Abra `assets/js/i18n.js` e adicione `"es"` ao array `SUPPORTED_LANGS`.
3. Adicione um botão ou seletor extra no lugar do atual botão PT/EN (`#langToggle`) chamando `IA_I18N.setLang("es")`.

Nenhuma outra alteração é necessária — todos os textos do site usam `data-i18n="chave"` e são atualizados automaticamente.

---

## 7. Publicar gratuitamente — passo a passo

### Opção A — Netlify (recomendado, formulários já funcionam)

1. Crie uma conta gratuita em https://www.netlify.com (pode entrar com sua conta do GitHub).
2. Na página inicial do painel, clique em **"Add new site" → "Deploy manually"**.
3. Arraste a pasta inteira do projeto (`projeto/`) para a área indicada — o Netlify publica o site em segundos.
4. Pronto! Você recebe uma URL gratuita do tipo `https://nome-aleatorio.netlify.app`.
5. (Opcional) Em **Site settings → Domain management**, você pode trocar para um domínio próprio ou personalizar o subdomínio gratuito.
6. Os formulários (voluntariado, parceiros, contato, newsletter) aparecerão automaticamente em **Site settings → Forms**, com notificações por e-mail configuráveis.

**Publicação contínua (opcional):** se preferir conectar direto a um repositório do GitHub em vez de arrastar a pasta, escolha **"Import an existing project"**, autorize o GitHub, selecione o repositório, deixe o campo "Build command" vazio e "Publish directory" como `.` (ponto).

### Opção B — GitHub Pages (100% gratuito, formulários precisam de serviço externo — ver seção 5)

1. Crie uma conta gratuita em https://github.com, se ainda não tiver.
2. Crie um novo repositório (por exemplo `instituto-amanhecer-site`), público.
3. Envie todos os arquivos do projeto para esse repositório. Duas formas:
   - **Pela interface web:** abra o repositório → "Add file" → "Upload files" → arraste todos os arquivos e pastas do projeto → "Commit changes".
   - **Pelo terminal (Git):**
     ```bash
     cd projeto
     git init
     git add .
     git commit -m "Primeira publicação do site"
     git branch -M main
     git remote add origin https://github.com/SEU-USUARIO/instituto-amanhecer-site.git
     git push -u origin main
     ```
4. No repositório, vá em **Settings → Pages**.
5. Em "Source", selecione a branch `main` e a pasta `/ (root)`, depois clique em **Save**.
6. Aguarde 1–2 minutos. O GitHub mostrará a URL pública, algo como:
   `https://SEU-USUARIO.github.io/instituto-amanhecer-site/`
7. Sempre que você enviar (`push`) novas alterações para a branch `main`, o site é atualizado automaticamente.

---

## 8. Acessibilidade e SEO — o que já está pronto

- HTML semântico (`header`, `nav`, `main`, `section`, `footer`), hierarquia de títulos consistente.
- Link "Pular para o conteúdo principal" para quem navega por teclado.
- Estados de foco visíveis (`:focus-visible`) em todos os elementos interativos.
- Contraste de cores testado para leitura confortável.
- `alt` descritivo em todas as imagens de conteúdo; imagens decorativas marcadas como `aria-hidden`.
- Suporte a `prefers-reduced-motion` (reduz animações para quem configurou isso no sistema).
- Meta tags de SEO, Open Graph, `sitemap.xml`, `robots.txt` e dados estruturados (Schema.org / JSON-LD) para melhor indexação em buscadores.
- Carregamento tardio (`loading="lazy"`) de imagens fora da primeira tela e de vídeos (carregados só ao clicar), o que mantém o site muito rápido.

---

## 9. Licenças

- Fontes `Fraunces`, `Inter` e `IBM Plex Mono` são gratuitas e de uso livre (Google Fonts / Open Font License).
- Ícones e ilustrações deste projeto são originais, criados especificamente para este site.
