# 📊 Dashboard Portfólio — Emissário Leão Dourado

> Dashboard estático de controle e acompanhamento de obra da Viana & Moura Construções, desenvolvido como portfólio de projeto para o Emissário Leão Dourado.

---

## 📋 Sobre o Projeto

O **Emissário Leão Dourado** é uma obra de infraestrutura urbana subterrânea executada pela **Viana & Moura Construções**, envolvendo o assentamento de tubulação em três trechos distintos na cidade de Recife/PE.

Este repositório contém o arquivo `dashboard_portfolio.html` — uma **aplicação web estática, offline e autocontida** que registra e apresenta o histórico completo de execução da obra, desde o início até a conclusão em **30/04/2026**.

---

## 🏗️ Escopo da Obra

| Trecho | Período | Cor |
|---|---|---|
| Trecho 1 | 05/03/2026 – 24/04/2026 | `#8B1A1A` |
| Trecho 2 | 31/03/2026 – 30/04/2026 | `#6d1414` |
| Trecho 3 | 17/04/2026 – 29/04/2026 | `#5e1010` |

### Atividades controladas por trecho:
- **RPA** — Remoção de Pavimento Asfáltico (m²)
- **ESC** — Escavação (m³)
- **ATU** — Assentamento de Tubulação (m)
- **REA** — Reaterro Compactado (m³)
- **DRO** — Desmonte de Rocha (m³)
- **IPV** — Implantação de Poço de Visita (und)
- **REPAS** — Reposição de Pavimento Asfáltico (m)

---

## ✅ Resultado Final da Obra

| KPI | Valor |
|---|---|
| Avanço Físico Médio | **102,5%** |
| IDP Global | **1,03** |
| Tubulação assentada | **701 m** (100,4%) |
| Reposição asfáltica | **701 m²** (concluída) |
| Prazo contratual | **30/04/2026** ✅ |

---

## 🖥️ Funcionalidades do Dashboard

### Telas / Módulos

| Tela | Descrição |
|---|---|
| **Visão Geral** | KPIs globais, progresso geral, IDP Global, simulação de conclusão e alertas |
| **Trechos** | Detalhe por trecho com IDP individual, progresso por atividade e barras de progresso |
| **Cronograma** | Gráfico Gantt interativo com linhas planejado vs. realizado |
| **Diário** | Registros dos diários de obra com linha do tempo |
| **Análise IA** | Diagnóstico executivo gerado por IA (Gemini 2.5 Pro — Google DeepMind) |
| **Mapa** | Localização georreferenciada dos trechos via Leaflet.js |
| **Exportar PDF** | Exportação de diário de obra preenchido via html2pdf.js |

---

## 🛠️ Tecnologias Utilizadas

| Tecnologia | Função |
|---|---|
| HTML5 + CSS3 + JavaScript | Core da aplicação (zero dependências de build) |
| [Chart.js](https://www.chartjs.org/) | Gráficos de progresso e Gantt |
| [Leaflet.js](https://leafletjs.com/) | Mapa interativo com georreferenciamento dos trechos |
| [html2pdf.js](https://ekoopmans.github.io/html2pdf.js/) | Exportação de diários em PDF |
| Google Fonts | Playfair Display, Crimson Pro, Barlow Condensed |
| PWA (manifest.json) | Suporte a instalação como app no mobile |

---

## 📁 Estrutura de Arquivos

```
emissario-leao-dourado/
├── dashboard_portfolio.html   # Aplicação principal (self-contained)
├── manifest.json              # Manifesto PWA
├── logo.png                   # Ícone da aplicação
└── c.diario.png               # Template de fundo para exportação do diário PDF
```

> **Nota:** toda a lógica, estilos, dados e scripts estão embutidos diretamente no `dashboard_portfolio.html`, garantindo funcionamento 100% offline e sem dependência de servidor.

---

## 🚀 Como Usar

### Opção 1 — Abrir diretamente no navegador

Basta abrir o arquivo `dashboard_portfolio.html` em qualquer navegador moderno:

```bash
open dashboard_portfolio.html
```

### Opção 2 — Servir via servidor local (recomendado para PWA)

```bash
# Com Python
python3 -m http.server 8080

# Com Node.js (npx)
npx serve .
```

Acesse: `http://localhost:8080/dashboard_portfolio.html`

### Opção 3 — Deploy estático (Vercel, Netlify, GitHub Pages)

O arquivo pode ser publicado diretamente em qualquer serviço de hospedagem estática. A versão ao vivo está disponível em:

🔗 **[https://emissario-ld.vercel.app](https://emissario-ld.vercel.app)**

---

## 📊 Dados da Obra (Estrutura Interna)

Os dados estão embutidos na variável `STATIC_DB` no início do arquivo HTML, com a seguinte estrutura:

```js
const STATIC_DB = {
  actuals: {
    "YYYY-MM-DD": { "TX_ATIVIDADE": valor_numerico }
  },
  trechos: [
    {
      id, nome, cor, inicio, fim,
      atividades: [{ id, nome, un, total, ini, fim, plano }]
    }
  ],
  diarios: [{ data, texto }],
  hhData: []
};
```

---

## 🤖 Análise Inteligente (IA)

O dashboard integra um módulo de **Análise Inteligente** baseado em IA generativa:

- **Modelo:** Gemini 2.5 Pro — Google DeepMind
- **Funcionamento:** No sistema ao vivo, a IA coleta todos os KPIs em tempo real (IDP, progresso físico, desvios por trecho, ritmo de produção, diários de obra) e gera um diagnóstico executivo contextualizado.
- **Neste portfólio:** exibe uma análise estática pré-gerada referente ao status final da obra (30/04/2026).

---

## 📱 PWA — Progressive Web App

O dashboard suporta instalação como aplicativo nativo no mobile (Android/iOS):

- Adicionar à tela inicial via navegador
- Funciona 100% offline após instalação
- Ícone e splash screen configurados via `manifest.json`
- Theme color: `#8B1A1A` (Viana & Moura)

---

## 🎨 Design System

| Token | Valor | Uso |
|---|---|---|
| `--vmc-red` | `#8B1A1A` | Cor primária (marca V&M) |
| `--vmc-gold` | `#E8A020` | Destaque e acentos |
| `--vmc-bg` | `#EDEAE3` | Fundo da aplicação |
| `--vmc-card` | `#FFFFFF` | Fundo dos cards |
| `--vmc-dark` | `#1E2740` | Textos e ícones |

**Tipografia:**
- `Playfair Display` — títulos e valores numéricos
- `Crimson Pro` — textos de corpo e interface
- `Barlow Condensed` — labels e etiquetas

---

## 📝 Diários de Obra (Destaques)

| Data | Ocorrência |
|---|---|
| 12/03/2026 | Incidência de rocha no Trecho 1 — desmonte com compressor e massa expansiva |
| 30/04/2026 | Finalização da reposição asfáltica — 141m executados no último dia, encerrando o emissário |

---

## 🏢 Créditos

**Construtora:** Viana & Moura Construções  
**Obra:** Emissário Leão Dourado  
**Período:** Março – Abril de 2026  
**Dashboard gerado em:** 30/04/2026
