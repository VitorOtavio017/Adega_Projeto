# 🍷 Vinho Fino — Adega & Empório

> Site de vendas de uma adega de vinhos, desenvolvido com **SDD (Spec Driven Development)** usando [OpenSpec](https://github.com/Fission-AI/OpenSpec) como framework de especificações.

---

## 📋 Sobre o Projeto

O **Vinho Fino** é um site de e-commerce para uma adega fictícia, criado como projeto de estudo da disciplina aplicando a metodologia **Spec Driven Development (SDD)**. O objetivo foi praticar como especificações bem definidas guiam o desenvolvimento de software de forma mais previsível e rastreável.

### Funcionalidades

- 🏠 **Landing page** com hero section e apresentação da adega
- 🍾 **Catálogo de vinhos** com cards de produtos e filtros visuais
- 🛒 **Carrinho de compras** com sidebar deslizante e controle de itens
- 📧 **Formulário de newsletter** para o Clube de Assinantes
- 📱 **Layout responsivo** para desktop e mobile
- ✨ **Animações** de scroll reveal e microinterações

---

## 🛠️ Tecnologias

| Tecnologia | Uso |
|---|---|
| **HTML5** | Estrutura semântica da página |
| **CSS3** | Estilização, animações e responsividade (puro, sem frameworks) |
| **JavaScript (Vanilla)** | Lógica do carrinho, toast, newsletter |
| **OpenSpec** | Framework de Spec Driven Development |
| **Node.js 20.19+** | Requisito para rodar o OpenSpec CLI |

---

## ⚙️ Pré-requisitos

- [Node.js](https://nodejs.org) **v20.19.0 ou superior**
- Um navegador moderno (Chrome, Firefox, Edge, Safari)
- Editor de código (**Cursor** ou **Antigravity** — recomendado para uso com OpenSpec)

Verifique sua versão do Node:
```bash
node --version
```

---

## 🚀 Como Configurar e Rodar

### 1. Clone o repositório

```bash
git clone https://github.com/VitorOtavio017/adega-vinho-fino.git
cd adega-vinho-fino
```

### 2. Instale o OpenSpec CLI (globalmente)

```bash
npm install -g @fission-ai/openspec@latest
```

Confirme a instalação:
```bash
openspec --version
```

### 3. Inicialize o OpenSpec no projeto

Escolha **uma** das opções conforme seu editor:

**Para Cursor:**
```bash
openspec init --tools cursor
```

**Para Antigravity:**
```bash
openspec init --tools antigravity
```

### 4. Rode o projeto no navegador

Como o projeto é HTML/CSS/JS puro, basta abrir o arquivo:

```bash
# macOS
open index.html

# Windows (PowerShell)
Start-Process index.html

# Linux
xdg-open index.html
```

Ou instale um servidor local simples:

```bash
# Opção 1: com npx
npx serve .

# Opção 2: com Python (se tiver instalado)
python3 -m http.server 8080
```

Acesse em: **http://localhost:8080** (ou porta indicada)

---

## 📁 Estrutura de Arquivos

```
adega-vinho-fino/
│
├── index.html              # Página principal do site
│
├── openspec/               # Gerado pelo OpenSpec
│   ├── specs/              # Especificações consolidadas do projeto
│   └── changes/            # Histórico de mudanças (proposals, tasks)
│
├── .cursor/                # (se usar Cursor)
│   ├── skills/
│   └── commands/
│
├── .agent/                 # (se usar Antigravity)
│   ├── skills/
│   └── workflows/
│
├── README.md               # Este arquivo
└── README-SPECS.md         # Reflexão sobre Spec Driven Development
```

---

## 🔄 Fluxo de Desenvolvimento com OpenSpec

O projeto foi desenvolvido seguindo o fluxo core do OpenSpec:

```
/opsx:explore → /opsx:propose → /opsx:apply → /opsx:archive
```

### Comandos utilizados

| Comando | Descrição |
|---|---|
| `/opsx:explore` | Investigar escopo e alinhar requisitos antes de propor |
| `/opsx:propose add-product-catalog` | Gerou spec do catálogo de produtos |
| `/opsx:propose add-cart-sidebar` | Gerou spec do carrinho lateral |
| `/opsx:propose add-newsletter` | Gerou spec da seção de newsletter |
| `/opsx:apply` | Implementou cada mudança conforme a spec |
| `/opsx:archive` | Consolidou as specs e arquivou cada mudança |

### Inspecionar specs pelo terminal

```bash
# Listar todas as mudanças
openspec list

# Ver detalhes de uma mudança
openspec show add-product-catalog

# Validar uma spec
openspec validate add-cart-sidebar

# Visualizar spec consolidada
openspec view
```

---

## 💡 Exemplos de Uso

### Adicionar um vinho ao carrinho
1. Acesse a seção **"Destaques da Semana"**
2. Passe o mouse sobre qualquer card de vinho
3. Clique em **"+ Adicionar ao Carrinho"**
4. O carrinho lateral abre automaticamente com o item
---

## 🔧 Atualizar o OpenSpec

```bash
npm install -g @fission-ai/openspec@latest
openspec update
```

