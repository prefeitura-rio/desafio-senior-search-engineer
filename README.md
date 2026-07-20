# Desafio Técnico: Descoberta de Serviços Públicos

## Contexto

Você receberá um catálogo com cerca de 50 serviços públicos, extraídos de um universo maior de mais de 1200 serviços reais. Cada serviço terá, no mínimo, os seguintes campos:

- nome do serviço
- descrição curta
- descrição longa
- categoria ou secretaria responsável

O objetivo deste desafio é avaliar como você estrutura um problema aberto, escolhe uma arquitetura, mede qualidade e sustenta tecnicamente as suas decisões.

Na prática, cidadãos raramente sabem o nome exato do serviço que precisam. Muitas vezes a necessidade começa vaga, incompleta ou ambígua — e pode emergir ao longo de uma conversa, não em uma única query. Queremos entender como você desenharia um sistema em que um agente conversacional ajuda o cidadão a encontrar o serviço certo e descobrir caminhos relacionados.

## Objetivo

Construir um sistema composto por:

- um **agente conversacional** que recebe mensagens do cidadão em linguagem natural, mantém o contexto da conversa (multi-turn) e usa ferramentas para encontrar e apresentar serviços relevantes
- uma **ferramenta de busca** que o agente invoca internamente — retornando serviços relevantes para a necessidade do usuário com técnicas modernas de recuperação de informação e IA
- uma **camada de recomendação** que sugere serviços relacionados que façam sentido naquele contexto
- uma **interface web** com dois modos: chat com o agente e busca direta no catálogo

## O Problema

Partindo apenas do catálogo fornecido, desenvolva uma solução que resolva três problemas:

### 1. Busca

A ferramenta de busca deve, dada uma consulta em linguagem natural, retornar serviços relevantes. Você decide como implementá-la — ela é um componente que o agente usa, não o produto final. Ainda assim, precisa ser tecnicamente sólida: uma solução puramente por palavra-chave, sem componente moderno de IA, não atende ao espírito do desafio.

### 2. Recomendação

Além dos resultados principais, o sistema deve sugerir serviços relacionados que façam sentido naquele contexto. Você decide onde essa lógica vive — pode ser outra ferramenta que o agente chama, lógica embutida no próprio agente, ou outro arranjo que você consiga defender.

A recomendação pode considerar, por exemplo, a intenção inferida da conversa, relações semânticas entre serviços, ou contexto de jornada (ex: quem precisa gerar um boleto provavelmente vai precisar pagá-lo depois).

### 3. Agente conversacional

O agente é o ponto central da solução. Ele recebe a mensagem do cidadão, decide quando e como invocar a busca, mantém o contexto ao longo de múltiplas mensagens e formula respostas úteis. Deve ser capaz de lidar tanto com necessidades vagas ("minha rua está com um buraco") quanto com necessidades diretas ("quero agendar o CadÚnico"). O agente é informacional — encontra e apresenta serviços, não os executa.

## Grau de Abertura

Este desafio é intencionalmente aberto. Não esperamos uma implementação "certa" ou aderência a uma stack específica. Queremos ver como você pensa.

Você deve tomar e defender decisões sobre pontos como:

- arquitetura do agente: framework escolhido (LangGraph, LangChain, implementação própria, etc.) e por quê
- como a busca é estruturada e exposta como ferramenta para o agente
- estratégia de recuperação e ranking: embeddings, busca vetorial, lexical, híbrida, reranking
- forma de gerar recomendações relacionadas
- estratégia de memória e contexto conversacional
- como avaliar qualidade — tanto da busca quanto das respostas do agente
- critérios de trade-off entre qualidade, complexidade, custo, latência e simplicidade operacional

Não é necessário implementar múltiplas arquiteturas completas; uma abordagem bem defendida é suficiente.

## O Que Esperamos Ver

- agente conversacional funcional, com suporte a múltiplos turnos de conversa
- ferramenta de busca integrada ao agente, funcionando sobre o catálogo
- camada de recomendação de serviços relacionados
- interface web com dois modos: chat com o agente e busca direta no catálogo
- clareza sobre as decisões arquiteturais e seus trade-offs
- estratégia de avaliação que cubra tanto a busca quanto o agente
- preocupação com observabilidade: capacidade de entender o que o agente está fazendo e por quê

## O Que Não Vamos Fornecer

Para manter o desafio aberto, não serão fornecidos:

- consultas de exemplo
- gabarito de relevância ou qualidade de resposta
- estratégia de avaliação pronta
- arquitetura de referência

Parte importante do desafio é justamente decidir como transformar o catálogo e o comportamento do agente em algo avaliável.

## Entregáveis

Esperamos receber:

1. Uma aplicação funcional

Interface web com chat (interação com o agente) e busca direta no catálogo.

2. Código-fonte

Organizado da forma que você considerar adequada, com instruções claras de execução.

3. Documento curto de arquitetura

Pode estar no próprio README do projeto ou em um arquivo separado. Esse documento deve explicar:

- qual problema você entendeu estar resolvendo
- como você estruturou o agente e suas ferramentas
- quais decisões arquiteturais tomou e por quê
- quais alternativas considerou e por que não as seguiu
- quais limitações a solução possui hoje

4. Estratégia de avaliação e análise de qualidade

Queremos ver como você mediu qualidade — tanto da ferramenta de busca quanto do agente como um todo. Isso pode incluir, por exemplo:

- criação de queries de teste para a ferramenta de busca
- criação de cenários de conversa com intenção e resultado esperados
- uso de LLM-as-Judge para avaliar a qualidade das respostas do agente
- análise qualitativa de acertos e falhas

Não existe método obrigatório. O importante é a coerência entre problema, método e conclusão.

5. Testes e observabilidade

Inclua o que você considerar suficiente para demonstrar qualidade de engenharia. Para o agente, observabilidade inclui entender o fluxo de cada interação: o que foi buscado, o que o agente decidiu fazer e o que foi retornado ao usuário. Não buscamos volume artificial de testes, e sim boas escolhas.

6. Seção obrigatória: como eu escalaria isso

Explique como sua solução evoluiria em dois eixos:

- **Catálogo**: de 50 para 1200 serviços — como sua solução de busca e recomendação escala em qualidade, custo e manutenção?
- **Agente**: em volume de conversas simultâneas, variedade de intenções e operação contínua — como você garantiria qualidade e estabilidade ao longo do tempo?

## Diferenciais

Não são obrigatórios, mas agregam sinal:

- agente capaz de fazer perguntas de clarificação quando a necessidade é ambígua
- tratamento explícito de queries fora de escopo (o agente reconhece o que não sabe responder)
- rastreamento de traces do agente para fins de observabilidade e debug
- streaming de respostas na interface de chat
- análise de falhas mais profunda — onde o agente erra e por quê
- mecanismos para monitorar regressões de qualidade ao longo do tempo

## Critérios de Avaliação

Vamos avaliar principalmente:

- clareza na formulação do problema
- qualidade e coerência da arquitetura escolhida — tanto para o agente quanto para a busca
- capacidade de justificar trade-offs
- qualidade dos resultados e da análise produzida
- maturidade na estratégia de avaliação
- qualidade do código, testes e organização da solução
- capacidade de pensar a evolução da solução para um cenário real

## Escopo Esperado

Este é um desafio de take-home pensado para algo em torno de 1 a 2 dias de trabalho. Não esperamos acabamento de produto, cobertura exaustiva ou infraestrutura de produção completa. Preferimos uma solução focada, coerente e bem defendida a uma implementação extensa com pouca clareza técnica.

## Observação Final

Estamos menos interessados em verificar se você já faz exatamente este trabalho hoje e mais interessados em entender se você tem repertório, autonomia e rigor para propor bons caminhos, avaliar qualidade e elevar a discussão técnica do time.
