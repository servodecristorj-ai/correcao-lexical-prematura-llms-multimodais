# Correção Lexical Prematura em LLMs Multimodais via Contexto Diferido

**Status:** Em andamento | **Paper:** PDF em preparação - submissão arXiv planejada para Jul 2026

## Resumo
Este repositório documenta uma falha sistêmica em LLMs multimodais: aplicação de correção lexical automática ao texto antes do processamento de imagens anexadas, causando falsos positivos em termos raros mas semanticamente válidos.

Apresentamos estudo de caso reproduzido em 4 LLMs de produção e propomos três estratégias de mitigação.

## Evidências Experimentais

Testamos o caso em 4 LLMs multimodais principais. Todas apresentaram correção prematura.

**[📄 Baixar PDF com todos os testes](/evidencias/printevidencecat.pdf)**

### LLMs Testadas:
1. Claude Sonnet 5 - Anthropic
2. Meta AI - Meta 
3. Gemini - Google
4. ChatGPT - OpenAI

### Relatório Técnico Gerado pela Claude
A própria Claude documentou a falha arquitetural e propôs mitigações.

**[📝 Ver transcrição completa](/relatorios/relatorio_claude.txt)**

## Mitigações Propostas
1. **Correção com Consciência de Incerteza**: Questionar usuário quando confiança em hipótese de "erro de digitação" é baixa.
2. **Julgamento Diferido**: Postergar correção lexical até contexto multimodal estar completo.
3. **Calibração Lexical**: Reduzir penalidade para termos raros mas gramaticalmente válidos.

## Estrutura do Repositório
