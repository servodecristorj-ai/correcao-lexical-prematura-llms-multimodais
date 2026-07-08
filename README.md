# Correção Lexical Prematura em LLMs Multimodais via Adicionamento Postergado de Contexto

Uma avaliação sistêmica de como os vieses de decodificação autorregressiva causam uma autocorreção agressiva em inputs raros, mas gramaticalmente válidos, antes que o processamento multimodal ocorra.

---

## 📌 Resumo
Este repositório documenta uma falha sistêmica em modelos de linguagem multimodais de última geração (LLMs): a **correção lexical prematura**. Quando expostos a sequências textuais de baixa probabilidade estatística, mas perfeitamente válidas, os modelos aplicam uma autocorreção agressiva baseada em vieses puramente textuais antes de realizar o alinhamento cruzado (*cross-modal grounding*) com imagens enviadas em turnos subsequentes da conversa.

Demonstramos esse comportamento por meio de um estudo de caso controlado utilizando a construção em língua portuguesa *"O gato subscreveu na telha"*.

## 🗂️ Estrutura do Repositório
*   `premature_lexical_correction_paper.pdf`: O artigo científico oficial formatado em LaTeX (padrão arXiv).
*   `printevidencecat.pdf`: Registro visual cronológico e prints completos dos testes em todas as plataformas avaliadas.
*   `relatorio_tecnico_claude.md`: Parecer técnico de engenharia reversa gerado diretamente pelo modelo Claude 3.5 Sonnet.

## 🔬 Metodologia e Experimento Central
O experimento foi desenhado para testar a resiliência dos modelos contra clichês linguísticos previsíveis. Embora a sequência *"O gato subiu no telhado"* esteja massivamente presente nas bases de treinamento, substituímos o verbo por um termo raro e formal, porém totalmente legítimo:

1.  **Turno 1 (Apenas Texto):** *"O gato subscreveu na telha"*
2.  **Turno 2 (Token Visual):** Uma imagem do personagem *Gato Félix* escrevendo e assinando fisicamente um bilhete sobre uma superfície de telhas.

### Sistemas Testados (Julho de 2026)
*   **Claude 3.5 Sonnet** (Anthropic) - *Estudo de Caso Principal*
*   **ChatGPT-4o** (OpenAI)
*   **Gemini** (Google)
*   **Meta AI** (Meta)

Todos os modelos exibiram 100% de reprodutibilidade da falha durante o Turno 1, afirmando categoricamente que a frase do usuário continha um erro de digitação ou semântica, recuando apenas após a introdução da imagem no Turno 2.

## 🛠️ Mitigações Propostas
Conforme detalhado no relatório técnico, propõem-se três atualizações arquiteturais nas pipelines multimodais:
1.  **Verificação de Incerteza antes de Correção:** Ativação de hipóteses consultivas ao usuário em vez de corrupção silenciosa do texto.
2.  **Retenção de Julgamento (*Deferred Judgment*):** Postergar a normalização lexical até que o grafo de input multimodal esteja totalmente carregado.
3.  **Calibração Lexical:** Atenuar as penalidades probabilísticas para termos válidos no dicionário quando integrados a sintaxes coerentes.

## ⚖️ Licença
Distribuído sob a **Licença Apache 2.0**. Consulte o arquivo `LICENSE` para obter mais informações.
