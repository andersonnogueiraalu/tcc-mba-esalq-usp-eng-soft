# Vulnerabilidades em Código Java/Spring Gerado por IA: Um Estudo Empírico com Replit AI e OWASP Top 10 2025

> **Trabalho de Conclusão de Curso (TCC)**  
> MBA em Engenharia de Software — USP/Esalq  
> Autor: Anderson de Franklin Freitas Nogueira  
> Ano: 2025–2026

---

## Sobre esta pesquisa

Este repositório reúne todos os artefatos produzidos durante a pesquisa empírica realizada como Trabalho de Conclusão de Curso do MBA em Engenharia de Software da USP/Esalq.

A investigação parte de uma constatação que tem preocupado a comunidade de segurança: ferramentas de inteligência artificial generativa são amplamente adotadas no desenvolvimento de software, mas o código que elas produzem carrega vulnerabilidades em proporção significativamente maior do que o código escrito por humanos. O relatório da Veracode (2025), baseado na avaliação de mais de 100 LLMs, apurou que o código gerado por IA apresenta 2,74 vezes mais falhas de segurança e que Java, especificamente, lidera a taxa de insegurança entre as linguagens avaliadas, com 72% das amostras comprometidas.

**Pergunta central da pesquisa:**

> *Em que medida o código back-end Java/Spring gerado pelo Replit AI apresenta vulnerabilidades mapeáveis pelo OWASP Top 10 2025?*

Para responder a essa pergunta, foram construídos cenários padronizados de desenvolvimento back-end, submetidos ao Replit AI sem diretrizes explícitas de segurança. O código gerado foi então analisado por um pipeline automatizado de análise estática de segurança (SAST), utilizando Semgrep e SpotBugs/Find Security Bugs. As vulnerabilidades detectadas foram classificadas segundo as categorias do OWASP Top 10 em sua edição de 2025.

A pesquisa caracteriza-se como **aplicada, experimental-descritiva e de natureza mista**: quantitativa na contagem e distribuição das vulnerabilidades, qualitativa na interpretação dos padrões identificados e na formulação de recomendações práticas de mitigação.

---

## Estrutura do repositório

```
tcc-replit-owasp/
│
├── docs/                          # Documentação acadêmica do TCC
│   ├── introducao.docx
│   ├── revisao_bibliografica.docx
│   ├── metodologia.docx
│   ├── resultados.docx
│   ├── conclusao.docx
│   └── tcc_completo_vFinal.docx
│
├── prompts/                       # Catálogo de prompts utilizados
│   ├── catalog_prompts.md         # Descrição e critérios de elaboração
│   ├── P01_autenticacao.md
│   ├── P02_autorizacao.md
│   ├── P03_manipulacao_dados_sensiveis.md
│   ├── P04_validacao_entrada.md
│   ├── P05_operacoes_banco_dados.md
│   ├── P06_gestao_sessoes.md
│   ├── P07_tratamento_excecoes.md
│   └── P08_logging.md
│
├── projects/                      # Projetos gerados pelo Replit AI
│   ├── P01_autenticacao/
│   │   ├── src/
│   │   ├── pom.xml
│   │   └── README.md
│   ├── P02_autorizacao/
│   │   ├── src/
│   │   ├── pom.xml
│   │   └── README.md
│   ├── P03_manipulacao_dados_sensiveis/
│   │   ├── src/
│   │   ├── pom.xml
│   │   └── README.md
│   ├── P04_validacao_entrada/
│   │   ├── src/
│   │   ├── pom.xml
│   │   └── README.md
│   ├── P05_operacoes_banco_dados/
│   │   ├── src/
│   │   ├── pom.xml
│   │   └── README.md
│   ├── P06_gestao_sessoes/
│   │   ├── src/
│   │   ├── pom.xml
│   │   └── README.md
│   ├── P07_tratamento_excecoes/
│   │   ├── src/
│   │   ├── pom.xml
│   │   └── README.md
│   └── P08_logging/
│       ├── src/
│       ├── pom.xml
│       └── README.md
│
├── analysis/                      # Pipeline de análise SAST
│   ├── pipeline/
│   │   ├── run_semgrep.sh
│   │   ├── run_spotbugs.sh
│   │   └── consolidate_results.py
│   ├── rules/
│   │   ├── semgrep_java_spring.yml
│   │   └── spotbugs_config.xml
│   └── raw/                       # Saídas brutas das ferramentas (JSON/XML)
│       ├── semgrep/
│       │   ├── P01_semgrep.json
│       │   └── ...
│       └── spotbugs/
│           ├── P01_spotbugs.xml
│           └── ...
│
├── results/                       # Dados consolidados e visualizações
│   ├── consolidated_findings.csv  # Base de dados unificada de vulnerabilidades
│   ├── owasp_mapping.csv          # Mapeamento achados → categorias OWASP
│   ├── dashboard/                 # Dashboard de resultados
│   │   └── index.html
│   └── charts/                    # Gráficos exportados
│       ├── distribuicao_owasp.png
│       ├── severidade_por_projeto.png
│       └── comparativo_ferramentas.png
│
└── references/                    # Referências bibliográficas e materiais de apoio
    ├── bibliography.bib
    └── papers/
        ├── veracode_2025.pdf
        ├── owasp_top10_2025.pdf
        └── ...
```

---

## Tecnologias utilizadas

| Componente | Ferramenta |
|---|---|
| Geração de código | Replit AI |
| Linguagem analisada | Java 17+ com Spring Boot 3.x |
| SAST — análise semântica | Semgrep OSS |
| SAST — taint analysis | SpotBugs + Find Security Bugs |
| Referência de segurança | OWASP Top 10 2025 |
| Versionamento | Git / GitHub |

---

## Como reproduzir a análise

```bash
# 1. Clone o repositório
git clone https://github.com/<seu-usuario>/tcc-replit-owasp.git
cd tcc-replit-owasp

# 2. Execute a análise com Semgrep em todos os projetos
bash analysis/pipeline/run_semgrep.sh

# 3. Execute a análise com SpotBugs
bash analysis/pipeline/run_spotbugs.sh

# 4. Consolide os resultados
python analysis/pipeline/consolidate_results.py

# 5. Abra o dashboard
open results/dashboard/index.html
```

> **Pré-requisitos:** Java 17+, Maven 3.8+, Semgrep OSS, SpotBugs 4.x, Python 3.10+

---

## Resultados finais

> *Esta seção será preenchida ao término da coleta e análise de dados. Os resultados preliminares serão atualizados progressivamente conforme o pipeline for executado.*

### Sumário executivo

| Métrica | Valor |
|---|---|
| Total de projetos analisados | — |
| Total de vulnerabilidades detectadas | — |
| Categorias OWASP identificadas | — |
| Categoria OWASP mais frequente | — |
| Taxa de detecção Semgrep | — |
| Taxa de detecção SpotBugs | — |
| Vulnerabilidades confirmadas (revisão manual) | — |

### Distribuição por categoria OWASP Top 10 2025

| # | Categoria OWASP | Ocorrências | % do total |
|---|---|---|---|
| A01 | Broken Access Control | — | — |
| A02 | Cryptographic Failures | — | — |
| A03 | Injection | — | — |
| A04 | Insecure Design | — | — |
| A05 | Security Misconfiguration | — | — |
| A06 | Vulnerable and Outdated Components | — | — |
| A07 | Identification and Authentication Failures | — | — |
| A08 | Software and Data Integrity Failures | — | — |
| A09 | Security Logging and Monitoring Failures | — | — |
| A10 | Server-Side Request Forgery (SSRF) | — | — |

### Principais achados qualitativos

> *A ser preenchido após análise.*

### Recomendações de mitigação

> *A ser preenchido após análise.*

---

## Referências principais

- OWASP. *OWASP Top 10 2025*. Open Worldwide Application Security Project, 2025. Disponível em: https://owasp.org/Top10/
- VERACODE. *GenAI Code Security Report*. Burlington: Veracode, 2025.
- APIIRO. *AI-Generated Code Security Research*. Tel Aviv: Apiiro, 2025.
- CYCODE. *ASPM State of Software Supply Chain Security*. 2026.
- HINTZBERGEN, J. et al. *Fundamentos de Segurança da Informação: com base na ISO 27001 e ISO 27002*. Rio de Janeiro: Brasport, 2018.
- CHEN, M. et al. Evaluating Large Language Models Trained on Code. *arXiv*, 2021. Disponível em: https://arxiv.org/abs/2107.03374
- BARKE, S. et al. Grounded Copilot: How Programmers Interact with Code-Generating Models. *OOPSLA*, 2023.

---

## Licença

Este repositório está licenciado para uso **exclusivamente acadêmico e não comercial**.

É permitido:
- Consultar, citar e referenciar o conteúdo deste repositório em trabalhos acadêmicos, desde que com atribuição adequada ao autor.
- Reproduzir trechos para fins educacionais, respeitando as normas de citação.

É vedado:
- Utilizar o código, os dados ou os documentos deste repositório para fins comerciais, diretos ou indiretos.
- Redistribuir ou sublicenciar o conteúdo sem autorização expressa do autor.
- Usar os resultados da pesquisa como insumo para produtos, serviços ou soluções comerciais sem negociação prévia.

```
© 2025–2026 Anderson de Franklin Freitas Nogueira
Todos os direitos reservados para uso comercial.
Para autorizações, contato: andersonfreitas21@usp.br
```

> Este trabalho foi desenvolvido como requisito parcial para obtenção do título de MBA em Engenharia de Software pela USP/Esalq. O conteúdo representa exclusivamente as opiniões e conclusões do autor, não refletindo posicionamento oficial da instituição ou das ferramentas avaliadas.
