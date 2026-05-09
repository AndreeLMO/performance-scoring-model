# performance-scoring-model
Modelo Logístico de desempenho para equipe de processamento de imagens odontológicas  
# 📊 Modelo de Avaliação de Desempenho — Equipe de Processamento de Imagem

> Modelo quantitativo, estruturado e auditável para avaliação comparativa de desempenho  
> Versão 2.3 | Autor: André Luiz Magalhães de Oliveira

[![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=flat-square&logo=python&logoColor=white)](https://python.org)
[![Pandas](https://img.shields.io/badge/Pandas-2.x-150458?style=flat-square&logo=pandas&logoColor=white)](https://pandas.pydata.org)
[![Scikit-learn](https://img.shields.io/badge/Scikit--learn-1.x-F7931E?style=flat-square&logo=scikit-learn&logoColor=white)](https://scikit-learn.org)
[![Status](https://img.shields.io/badge/Status-Concluído-brightgreen?style=flat-square)](.)
[![License](https://img.shields.io/badge/License-MIT-blue?style=flat-square)](LICENSE)

---

## 📌 Visão Geral

Este projeto implementa um **modelo de scoring baseado em função logística** para avaliação comparativa de desempenho de equipes de processamento de imagem médica (com foco em endodontia).

O score final (0–100) integra quatro dimensões de desempenho e incorpora normalizações robustas a outliers, ajustes por complexidade de exame e um fator de confiança baseado em volume. O modelo é **auditável e parametrizável**, permitindo calibração gerencial.

> O modelo tem caráter **comparativo e de desenvolvimento**, sem finalidade punitiva.

---

## 🧮 Metodologia

### Função Logística

O score final é calculado por uma função logística calibrada que combina quatro sub-scores:

```
Score = f_logística(α·Produtividade + β·Qualidade + γ·Eficiência + δ·Complexidade)
```

### Sub-scores

| Dimensão | Descrição |
|---|---|
| **Produtividade** | Volume processado (fluxos) normalizado de forma robusta |
| **Qualidade** | Retrabalho excedente ao esperado para a complexidade técnica |
| **Eficiência** | Tempo médio de execução ajustado pela complexidade dos exames |
| **Complexidade** | Perfil de endodontia processada, ponderado por número de dentes |

### Parâmetros do Modelo

| Parâmetro | Valor | Descrição |
|---|---|---|
| ALPHA | 1.0 | Peso da produtividade |
| BETA | 0.8 | Peso do retrabalho |
| GAMMA | 0.6 | Peso do tempo |
| DELTA | 0.8 | Peso da complexidade |
| K_WEIGHT | 0.5 | Peso do fator k_z |
| Sensibilidade logística | 0.9 | Inclinação da curva logística |
| FATOR_AJUSTE_TEMPO_ENDO | 0.8 | Ajuste de tempo para endodontia |
| RETRAB_EXPONENTE | 1.2 | Expoente da penalização de retrabalho |
| CONF_N0 | 30.0 | Volume mínimo para fator de confiança pleno |

### Pesos por Tipo de Endodontia

| Tipo | Peso |
|---|---|
| Até 3 dentes | 0.3 |
| 4 a 6 dentes | 0.6 |
| 7 dentes ou mais | 1.0 |

---

## 📈 Resultados (dados anonimizados)

### Estatísticas Gerais

| Indicador | Valor |
|---|---|
| Total de colaboradores avaliados | 22 |
| Score médio | 44.6 |
| Score mediano | 40.9 |
| Score mínimo | 6.2 |
| Score máximo | 87.1 |
| Desvio padrão | 21.8 |

### Distribuição dos Sub-scores

O modelo gera distribuições para cada dimensão, permitindo identificar padrões de desempenho individual e comparativo:

- **Distribuição do Score Geral** — histograma dos scores ajustados
- **Boxplot por dimensão** — variação de Produtividade, Qualidade, Eficiência e Complexidade
- **Distribuição de Complexidade Endo** — perfil de exames processados
- **Fluxo × Retrabalho** — relação entre volume e penalização por retrabalho

---

## 🔍 Análise de Sensibilidade

O modelo inclui análise de sensibilidade dos parâmetros (variação de ±20%):

| Parâmetro | Variação média (pontos) |
|---|---|
| ALPHA | **2.63** (maior impacto) |
| BETA | 1.75–1.78 |
| GAMMA | 1.30–1.34 |
| DELTA | 0.93–0.94 |

> O parâmetro **ALPHA** (produtividade) apresenta o maior impacto no score final, exigindo atenção especial em calibrações futuras.

---

## 🗂️ Estrutura do Repositório

```
performance-scoring-model/
│
├── notebook/
│   └── performance_model.ipynb     # Pipeline completo do modelo
│
├── data/
│   └── README_data.md              # Instruções para uso com dados próprios
│
├── results/
│   ├── score_distribution.png      # Distribuição dos scores
│   ├── subscore_boxplot.png        # Boxplot por dimensão
│   └── rankings.png                # Rankings visuais
│
├── requirements.txt
└── README.md
```

---

## 🚀 Como Executar

```bash
# 1. Clone o repositório
git clone https://github.com/seu-usuario/performance-scoring-model.git
cd performance-scoring-model

# 2. Instale as dependências
pip install -r requirements.txt

# 3. Adicione seus dados (veja data/README_data.md)

# 4. Execute o notebook
jupyter notebook notebook/performance_model.ipynb
```

---

## 🔭 Aplicações e Extensões

- Adaptável para qualquer equipe com métricas de volume, qualidade e tempo
- Parâmetros configuráveis via arquivo de configuração para diferentes contextos
- Possível integração com dashboards (Power BI, Streamlit)
- Extensível para séries temporais (evolução de desempenho ao longo do tempo)

---

## 📬 Contato

**André Luiz Magalhães de Oliveira**  
Graduação em Física Médica — USP Ribeirão Preto  
📧 andreluizmoliveira7@gmail.com  
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0077B5?style=flat-square&logo=linkedin)](https://linkedin.com/in/seu-perfil)
[![GitHub](https://img.shields.io/badge/GitHub-Portfolio-181717?style=flat-square&logo=github)](https://github.com/seu-usuario)
