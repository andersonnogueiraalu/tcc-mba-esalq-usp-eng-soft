# Catálogo de Prompts — Critérios de Elaboração

## Objetivo

Este catálogo documenta os oito prompts padronizados submetidos ao Replit AI durante a coleta de dados da pesquisa. Cada prompt simula um cenário realista de desenvolvimento back-end Java/Spring Boot, sem incluir qualquer diretriz explícita de segurança — condição necessária para observar o comportamento padrão da ferramenta.

## Critérios de design dos prompts

| Critério | Descrição |
|----------|-----------|
| **Naturalidade** | O prompt deve soar como uma solicitação real de desenvolvedor, sem termos de segurança (OWASP, vulnerabilidade, injeção, etc.) |
| **Especificidade técnica** | Deve nomear o stack (Java 17, Spring Boot 3, Maven) para eliminar ambiguidade de linguagem/framework |
| **Completude funcional** | Deve pedir uma feature completa (controller + service + repository + testes) para maximizar a superfície de código gerado |
| **Domínio isolado** | Cada prompt foca em um único domínio de segurança para facilitar o mapeamento OWASP |
| **Replicabilidade** | O texto é fixo; não há variação entre execuções — qualquer pesquisador pode reproduzir a coleta |

## Condição experimental controlada

Os prompts foram submetidos ao Replit AI **sem** as seguintes informações:
- Referências a vulnerabilidades ou boas práticas de segurança
- Instruções sobre OWASP, SANS, NIST ou frameworks de segurança
- Pedidos explícitos de validação de entrada, sanitização, criptografia ou controle de acesso
- Contexto sobre o caráter de pesquisa de segurança

Essa condição reproduz o uso típico de IA por desenvolvedores que buscam velocidade de entrega sem foco explícito em segurança.

## Mapeamento prompt × OWASP Top 10 2025

| Prompt | Domínio | Categorias OWASP primárias probing | Categorias secundárias |
|--------|---------|-------------------------------------|------------------------|
| P01 | Autenticação | A07 — Identification & Authentication Failures | A02 Cryptographic Failures |
| P02 | Autorização | A01 — Broken Access Control | A05 Security Misconfiguration |
| P03 | Dados Sensíveis | A02 — Cryptographic Failures | A01, A09 |
| P04 | Validação de Entrada | A03 — Injection | A04 Insecure Design |
| P05 | Banco de Dados | A03 — Injection | A04, A05 |
| P06 | Sessões | A07 — Identification & Authentication Failures | A01, A05 |
| P07 | Exceções | A09 — Security Logging & Monitoring Failures | A05 |
| P08 | Logging | A09 — Security Logging & Monitoring Failures | A02, A03 |

## Procedimento de submissão

1. Abrir uma sessão limpa no Replit AI (sem histórico de conversa anterior)
2. Submeter o texto do prompt exatamente como registrado no arquivo P0X correspondente
3. Aceitar a primeira resposta completa sem solicitar revisões
4. Copiar o código gerado para `projects/P0X_<dominio>/src/` sem modificações
5. Registrar data/hora, versão da ferramenta e identificador da sessão no cabeçalho do arquivo de resultado bruto

## Convenção dos arquivos de prompt

Cada arquivo `P0X_<dominio>.md` contém:
- **Metadados**: ID, domínio, categorias OWASP alvo, data de elaboração
- **Prompt** (bloco `prompt`): texto exato submetido ao Replit AI
- **Vulnerabilidades esperadas**: hipóteses levantadas antes da execução (para controle de viés confirmatório)
- **Notas de coleta**: campo livre para observações durante a submissão
