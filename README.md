# Sakibites Bot Portfolio - Guia de Deployment

## 📋 Visão Geral

Este é um portfólio web profissional dos bots Discord **Modi** e **Musicat**, desenvolvido em React com Tailwind CSS e otimizado para GitHub Pages.

## 🚀 Funcionalidades

### Modi - Moderação Automática
- Filtragem automática de mensagens (Mídia, Texto, Link, Regex)
- Mensagens de aviso temporárias para usuários infratores
- Configurações persistentes por servidor (Firebase)
- Comandos administrativos via Slash Commands
- Suporte a múltiplos tipos de filtro por canal

### Musicat - Bot de Música
- Reprodução de música de alta fidelidade
- Suporte a múltiplas fontes (YouTube, SoundCloud, etc.)
- Gerenciamento de fila de reprodução
- Comandos de controle de mídia (Play, Pause, Stop, Skip)
- Baixa latência e estabilidade

## 📁 Estrutura do Projeto

```
sakibites-portfolio/
├── client/
│   ├── public/
│   │   ├── bots_data.json       # Dados dos bots
│   │   └── ...
│   ├── src/
│   │   ├── pages/
│   │   │   ├── Home.tsx         # Página inicial
│   │   │   ├── BotPortfolio.tsx # Página de portfólio individual
│   │   │   └── NotFound.tsx     # Página 404
│   │   ├── components/
│   │   │   ├── Header.tsx       # Componente de header
│   │   │   ├── Footer.tsx       # Componente de footer
│   │   │   └── ...
│   │   ├── App.tsx              # Componente principal com roteamento
│   │   ├── index.css            # Estilos globais
│   │   └── main.tsx             # Entrada da aplicação
│   └── index.html               # Template HTML
├── dist/                         # Build otimizado
├── package.json                 # Dependências do projeto
├── vite.config.ts              # Configuração do Vite
└── README.md                    # Este arquivo
```

## 🛠️ Instalação e Desenvolvimento

### Pré-requisitos
- Node.js 18+ 
- pnpm (recomendado) ou npm

### Instalação

```bash
# Clone o repositório
git clone https://github.com/sakibites/portfolio.git
cd sakibites-portfolio

# Instale as dependências
pnpm install
# ou
npm install
```

### Desenvolvimento

```bash
# Inicie o servidor de desenvolvimento
pnpm dev
# ou
npm run dev

# O servidor estará disponível em http://localhost:3000
```

### Build para Produção

```bash
# Crie o build otimizado
pnpm build
# ou
npm run build

# Visualize o build localmente
pnpm preview
# ou
npm run preview
```

## 🌐 Deployment no GitHub Pages

### Opção 1: Usando GitHub Actions (Recomendado)

1. **Configure o repositório:**
   - Vá para Settings → Pages
   - Selecione "GitHub Actions" como source
   - Salve as alterações

2. **Crie o arquivo `.github/workflows/deploy.yml`:**

```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches: [ main ]

jobs:
  build-and-deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      
      - name: Setup Node.js
        uses: actions/setup-node@v3
        with:
          node-version: '18'
          cache: 'pnpm'
      
      - name: Install dependencies
        run: pnpm install
      
      - name: Build
        run: pnpm build
      
      - name: Deploy
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./dist/public
```

3. **Faça push para o repositório:**
   ```bash
   git add .
   git commit -m "Add GitHub Pages deployment"
   git push origin main
   ```

### Opção 2: Deploy Manual

1. **Gere o build:**
   ```bash
   pnpm build
   ```

2. **Faça upload dos arquivos:**
   - Copie o conteúdo de `dist/public/` para a branch `gh-pages`
   - Ou use uma ferramenta como `gh-pages` package

3. **Configure o repositório:**
   - Vá para Settings → Pages
   - Selecione a branch `gh-pages` como source

## 🔧 Configuração

### Variáveis de Ambiente

O projeto utiliza variáveis de ambiente injetadas automaticamente:

- `VITE_APP_TITLE` - Título da aplicação
- `VITE_APP_LOGO` - Logo da aplicação
- `VITE_ANALYTICS_ENDPOINT` - Endpoint de analytics (opcional)
- `VITE_ANALYTICS_WEBSITE_ID` - ID do website para analytics (opcional)

### Customização

#### Alterar Domínio

Se você estiver usando um domínio customizado (como `sakibites.space`):

1. Crie um arquivo `CNAME` em `client/public/`:
   ```
   sakibites.space
   ```

2. Configure o DNS do seu domínio para apontar para GitHub Pages

#### Alterar Tema

O projeto usa tema dark por padrão. Para alterar:

1. Edite `client/src/App.tsx`:
   ```tsx
   <ThemeProvider defaultTheme="light">
   ```

2. Customize as cores em `client/src/index.css`

## 📱 Roteamento

O portfólio utiliza roteamento baseado em arquivo com Wouter:

- `/` - Página inicial com lista de bots
- `/p/Modi` - Portfólio do bot Modi
- `/p/Musicat` - Portfólio do bot Musicat
- `/404` - Página não encontrada

## 🎨 Design

- **Framework CSS:** Tailwind CSS 4
- **Componentes UI:** shadcn/ui
- **Tema:** Dark mode por padrão
- **Responsivo:** Mobile-first design
- **Animações:** Framer Motion (opcional)

## 📦 Dependências Principais

- **React 19** - Framework UI
- **Tailwind CSS 4** - Styling
- **Wouter** - Roteamento
- **Lucide React** - Ícones
- **shadcn/ui** - Componentes UI
- **Vite** - Build tool

## 🔐 Segurança

- Tokens de bots são ignorados via `.gitignore`
- Dados sensíveis não são commitados
- Arquivos de configuração privada são excluídos

## 📝 Licença

MIT

## 🤝 Contribuições

Contribuições são bem-vindas! Por favor, abra uma issue ou pull request.

## 📞 Suporte

Para suporte, junte-se ao servidor Discord: https://discord.gg/sakibites

---

**Desenvolvido com ❤️ para a comunidade Sakibites**
