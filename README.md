# Desafio Técnico: Descoberta de Serviços Públicos

## Contexto

Você receberá um catálogo com cerca de 50 serviços públicos, extraídos de um universo maior de mais de 1200 serviços reais. Cada serviço terá, no mínimo, os seguintes campos:

- nome do serviço
- descrição curta
- descrição longa
- categoria ou secretaria responsável

O objetivo deste desafio é avaliar como você estrutura um problema aberto, escolhe uma arquitetura, mede qualidade e sustenta tecnicamente as suas decisões.

Na prática, cidadãos raramente sabem o nome exato do serviço que precisam. Muitas vezes a busca começa com uma necessidade mal formulada, incompleta ou ambígua. Queremos entender como você desenharia uma solução que combine busca e recomendação para ajudar uma pessoa a encontrar o serviço certo e descobrir caminhos relacionados.

## Objetivo

Construir uma solução de descoberta de serviços que:

- permita buscar serviços usando linguagem natural
- retorne resultados relevantes para a intenção do usuário
- recomende serviços relacionados que possam ajudar na jornada do cidadão
- use técnicas modernas de busca e IA, com escolhas tecnicamente justificadas

## O Problema

Partindo apenas do catálogo fornecido, desenvolva uma solução que resolva dois problemas centrais:

1. Busca

Dada uma consulta em linguagem natural, o sistema deve retornar serviços relevantes.

2. Recomendação

Além dos resultados principais de busca, o sistema deve sugerir serviços relacionados que façam sentido naquele contexto.

Você decide como estruturar essa recomendação. Ela pode, por exemplo, considerar a intenção inferida da query, os resultados retornados, relações semânticas entre serviços, proximidade temática, contexto de jornada (primeiro a pessoa precisa de um serviço e depois de outro ex. gerar boleto e pagar boleto) ou outro critério que você considere adequado.

## Grau de Abertura

Este desafio é intencionalmente aberto. Não esperamos uma implementação "certa" ou aderência a uma stack específica. Queremos ver como você pensa.

Você deve tomar e defender decisões sobre pontos como:

- arquitetura da solução
- estratégia de recuperação e ranking
- papel de embeddings, busca vetorial, busca lexical, busca híbrida, reranking, LLMs ou outros componentes
- forma de gerar recomendações relacionadas
- estratégia de avaliação de qualidade
- critérios de trade-off entre qualidade, complexidade, custo, latência e simplicidade operacional

Uma solução puramente básica de busca por palavra-chave, sem componente moderno de busca ou IA, não atende ao espírito do desafio. Não é necessário implementar múltiplas arquiteturas completas; uma abordagem bem defendida é suficiente.

## O Que Esperamos Ver

- uma solução funcional de busca sobre o catálogo
- uma camada de recomendação de serviços relacionados
- uma interface visual simples que permita demonstrar a experiência proposta
- clareza sobre as decisões arquiteturais e seus trade-offs
- preocupação com qualidade de resultado, testes e observabilidade
- capacidade de criar um método de avaliação mesmo com pouco dado disponível

## O Que Não Vamos Fornecer

Para manter o desafio aberto, não serão fornecidos:

- consultas de exemplo
- gabarito de relevância
- estratégia de avaliação pronta
- arquitetura de referência

Parte importante do desafio é justamente decidir como transformar o catálogo em um problema avaliável.

## Entregáveis

Esperamos receber:

1. Uma aplicação funcional

Pode ser uma aplicação web simples, desde que permita demonstrar com clareza a busca e as recomendações relacionadas.

2. Código-fonte

Organizado da forma que você considerar adequada, com instruções claras de execução.

3. Documento curto de arquitetura

Pode estar no próprio README do projeto ou em um arquivo separado. Esse documento deve explicar:

- qual problema você entendeu estar resolvendo
- quais decisões arquiteturais tomou
- por que escolheu essa abordagem
- quais alternativas considerou e por que não as seguiu
- quais limitações a solução possui hoje

4. Estratégia de avaliação e análise de qualidade

Queremos ver como você definiu e mediu qualidade. Isso pode incluir, por exemplo:

- criação de queries de teste
- definição de critérios de relevância
- construção de algum conjunto de avaliação, mesmo pequeno
- métricas que façam sentido para o problema
- análise qualitativa de acertos e falhas

Não existe uma métrica obrigatória. O importante é a coerência entre problema, método e conclusão.

5. Testes e observabilidade

Inclua o que você considerar suficiente para demonstrar qualidade de engenharia. Não buscamos volume artificial de testes, e sim boas escolhas. Observabilidade pode ser simples, desde que ajude a entender o comportamento do sistema.

6. Seção obrigatória: como eu escalaria isso de 50 para 1200 serviços

Explique como sua solução evoluiria ao sair de um catálogo reduzido para um cenário real mais amplo. Queremos entender como você pensa sobre escala, manutenção, custo, qualidade e operação.

## Diferenciais

Não são obrigatórios, mas agregam sinal:

- sugestão ou reformulação de queries
- comparação controlada entre variantes de ranking ou recomendação
- análise de falhas mais profunda
- cuidado especial com explainability ou inspeção de resultados
- mecanismos explícitos para monitorar regressões de qualidade

## Critérios de Avaliação

Vamos avaliar principalmente:

- clareza na formulação do problema
- qualidade e coerência da arquitetura escolhida
- capacidade de justificar trade-offs
- qualidade dos resultados e da análise produzida
- maturidade na estratégia de avaliação com pouco dado
- qualidade do código, testes e organização da solução
- capacidade de pensar a evolução da solução para um cenário real

## Escopo Esperado

Este é um desafio de take-home pensado para algo em torno de 1 a 2 dias de trabalho. Não esperamos acabamento de produto, cobertura exaustiva ou infraestrutura de produção completa. Preferimos uma solução focada, coerente e bem defendida a uma implementação extensa com pouca clareza técnica.

## Observação Final

Estamos menos interessados em verificar se você já faz exatamente este trabalho hoje e mais interessados em entender se você tem repertório, autonomia e rigor para propor bons caminhos, avaliar qualidade e elevar a discussão técnica do time.
