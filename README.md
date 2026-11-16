# ARTOOLS Pigmentum — Experiência Digital de Alta Precisão

Landing page interativa cinematográfica e institucional da **ARTOOLS Pigmentum 0.1**, construída sob os fundamentos do **Aura Design System** e padrões de engenharia de software da Apple e Gemini.

---

## 📁 Estrutura de Pastas do Projeto

O projeto foi organizado para máxima eficiência, compatibilidade e facilidade de implantação (*deploy*) em qualquer CDN ou hospedagem estática:

```text
artools/
├── index.html                      # Ponto de entrada canônico de produção
├── index2.html                     # Espelho sincronizado para desenvolvimento
├── vercel.json                     # Headers de cache e segurança para Vercel
├── netlify.toml                    # Configurações de cache e segurança para Netlify
├── .gitignore                      # Exclusão de arquivos de SO (.DS_Store), logs e temporários
├── README.md                       # Documentação técnica do projeto
│
├── assets/
│   ├── images/                     # Fotografias e diagramas em alta resolução
│   │   ├── pen_architecture_dark.jpg
│   │   ├── pen_architecture_uncapped.jpg
│   │   ├── pen_real_photo.jpg
│   │   └── artools_tech_feature.png
│   │
│   ├── videos/                     # Vídeos otimizados para produção
│   │   └── video2.mp4              # Coreografia 360° em alta fidelidade
│   │
│   ├── video_frames/               # Sequência de 192 frames para modo Canvas GPU
│   │   ├── frame_0001.jpg
│   │   └── ...
│   │
│   ├── templates/                  # Referências arquitetônicas e design systems
│   │   ├── design_system.html      # Guia de tokens e componentes Aura
│   │   ├── digital-architect.aura.build/
│   │   ├── animations-gemini/
│   │   └── animations-gemini2/
│   │
│   └── raw_files/                  # Arquivos originais e fontes de mídia
│
└── backups/                        # Histórico de versões prévias arquivadas
    └── index_backup.html
```

---

## ⚡ Tecnologias e Bibliotecas

- **Tailwind CSS v3 (CDN):** Estilização utilitária baseada nos tokens de design do Aura (`#EAEAE5`, `#1C1917`, `#0A0A0D`).
- **GSAP 3 + ScrollTrigger:** Orquestração de animações baseadas no scroll, pinned stages e transições com blur out.
- **Lenis Scroll:** Suavização inercial de rolagem (*smooth scroll*).
- **Dual Engine Scrubber:**
  - **Motor Primário (Vídeo MP4):** Controle instantâneo de tempo do `video2.mp4` via `currentTime` com interpolação contínua (*lerp* 0.28).
  - **Motor Secundário (Canvas GPU):** Renderização direta em `<canvas>` com cálculo de aspect ratio adaptativo para telas ultra-wide e mobile.
- **Iconify Design:** Ícones vetoriais solares sob demanda sem impacto no carregamento.

---

## 🛠️ Como Executar Localmente

Como a aplicação faz carregamento dinâmico de vídeo e canvas, recomenda-se servi-la via servidor HTTP local (para evitar bloqueios de CORS por protocolo `file://`):

### Opção 1: Via VS Code (Recomendado)
Instale a extensão **Live Server** e clique em **Go Live** no arquivo `index.html`.

### Opção 2: Via Node.js (npx)
```bash
npx serve .
```

### Opção 3: Via Python
```bash
# Python 3
python -m http.server 8080
```
Acesse `http://localhost:8080` no navegador.

---

## 🚀 Como Fazer Deploy

O projeto é 100% estático (HTML/CSS/JS) e está pronto para produção:

### 1. Vercel
1. Conecte o repositório no [Vercel](https://vercel.com).
2. Deixe o diretório raiz como `.` e framework como **Other**.
3. O arquivo `vercel.json` configurará automaticamente os cabeçalhos de cache imutável para as mídias.

### 2. Netlify
1. Arraste a pasta para o [Netlify Drop](https://app.netlify.com/drop) ou conecte via Git.
2. O arquivo `netlify.toml` já define a pasta de publicação como raiz (`.`).

### 3. GitHub Pages
1. Acesse **Settings > Pages** do seu repositório.
2. Selecione a branch `main` e a pasta `/ (root)`.
3. Salve para gerar o link público.

---

## ⚙️ Configuração de Compra / Checkout

Para direcionar os botões **COMPRAR AGORA** e **ADQUIRIR SÉRIE 01** diretamente para sua página de checkout, altere a propriedade `buyUrl` no início da tag `<script>` em `index.html`:

```javascript
const CONFIG = {
    renderEngine: 'video',
    buyUrl: "https://sua-loja.com.br/checkout", // Insira a URL real aqui
    // ...
};
```
*Se deixada vazia, um modal de instrução elegante e acessível será exibido ao usuário.*
