# Roteiro da Palestra

**Palestra:** Integrando Segurança no S-SDLC com uma Pipeline Open Source e IA  
**Evento:** XibéSec 26 — Belém  
**Palestrante:** Lucas Renan Meira dos Santos  

> No HTML, pressione **S** para abrir a visão do palestrante com as notas do slide atual e cronômetro. Use **← / →** para navegar e **F** para tela cheia.

---

## Slide 1 — Capa

Olá a todos, bom dia/boa tarde! Meu nome é Lucas Renan e sou Especialista em Segurança de Aplicações. Hoje nós vamos falar sobre um desafio que toda equipe de tecnologia moderna enfrenta: como integrar segurança no ciclo de vida de desenvolvimento de software sem se tornar o gargalo do time de engenharia. E melhor ainda: como fazer isso com ferramentas open source e adaptadas para a nova era da Inteligência Artificial.

## Slide 2 — Quem sou eu

Antes de entrarmos no assunto principal, uma breve apresentação: sou formado pelo IFPE, com 7 anos na área de tecnologia e 5 dedicados a AppSec. Tenho experiência prática com SAST, DAST, modelagem de ameaças e testes de invasão. Além do trabalho técnico, gosto de compartilhar conhecimento em eventos como TDC e Rec'n'Play.

## Slide 3 — De DevOps para DevSecOps

Para entendermos onde estamos, precisamos olhar para como o desenvolvimento mudou. DevOps revolucionou a capacidade de entrega, mas a segurança muitas vezes continuou no modelo de esperar o código ficar pronto para testar. Daí vem o Shift-Left: fazer a segurança nascer junto com o código. Isso exige automação em tempo real, porque processos manuais e aprovações demoradas não acompanham pipelines cada vez mais rápidas e complexas.

## Slide 4 — S-SDLC

S-SDLC é segurança integrada ao ciclo inteiro, e não uma auditoria no final. No planejamento entram threat modeling e requisitos; no código entram análises e prevenção de secrets; no build entram dependências e containers; em testes entram DAST e validações; e em operação entram observabilidade, vulnerabilidades e resposta. O ponto principal é fornecer feedback acionável no momento em que a equipe ainda consegue corrigir barato e rápido.

## Slide 5 — Ferramentas Open Source

A segurança começa no design com modelagem de ameaças. Quando o código é escrito, a pipeline precisa ter motores de detecção: Trivy para containers, pacotes e repositórios; Bandit para SAST em Python; TruffleHog ou Gitleaks para segredos. Scripts automatizados podem complementar varreduras dinâmicas. A ideia é montar uma malha contínua de segurança sem depender de licenças muito caras.

## Slide 6 — Pipeline Open Source + IA

Aqui está a visão prática. O commit entra e passa por secret scanning, SAST, análise de dependências, container scanning, build, staging e DAST. A diferença é onde a IA entra: não para substituir scanners determinísticos, mas para correlacionar os findings, considerar o contexto da mudança e priorizar o que merece atenção. O gate continua baseado em política e, quando necessário, decisão humana. Isso reduz gargalo sem transformar IA em fonte única de verdade.

## Slide 7 — SDLC Nativo de IA

Depois de evoluirmos para DevSecOps, o paradigma mudou novamente com IA. A geração de código acelerou muito. A equipe de segurança, mesmo automatizada, pode virar gargalo quando o volume de mudanças e findings cresce. O risco é criar filas enormes de revisão ou, no extremo oposto, deixar código passar sem análise por pressão de negócio. Precisamos mudar não apenas as ferramentas, mas a forma de fazer triagem e governança.

## Slide 8 — IA na triagem

A IA pode funcionar como uma camada de triagem. Ela recebe findings dos scanners, correlaciona com o diff e o contexto do componente, ajuda a explicar impacto e prioriza o que realmente merece ação. O exemplo de 120 para 5 é conceitual: a mensagem é que a revisão humana precisa concentrar energia no que é crítico, ambíguo ou regulado. A IA apoia a decisão; não deve ser tratada como scanner ou gate infalível.

## Slide 9 — Como a IA muda o S-SDLC

Se a IA alterou o modelo tradicional, usamos IA para adaptar o ciclo. No planejamento, artefatos vivos como `intent.md` podem carregar a intenção da mudança para humanos e agentes. No desenvolvimento, a IA ajuda a elaborar testes rigorosos e incorporar conhecimento de segurança. Na governança, os scans continuam operando em tempo real, enquanto IA ajuda a triar falsos positivos e direcionar a revisão humana para código crítico ou altamente regulado.

## Slide 10 — Encerramento

Em resumo, a automação open source continua sendo o pilar do CI/CD, mas a forma como planejamos e conduzimos revisões de segurança precisa abraçar IA com responsabilidade. Scanners fazem detecção, IA ajuda a organizar contexto e prioridade, e pessoas continuam responsáveis pelas decisões importantes. Muito obrigado pela atenção. Foi um prazer apresentar em Belém. Alguém tem alguma dúvida ou gostaria de compartilhar alguma experiência?
