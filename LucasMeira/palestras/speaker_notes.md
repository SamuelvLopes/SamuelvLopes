# Roteiro da Palestra

Palestra: Integrando Segurança no S-SDLC com uma Pipeline Open Source e IA

Use ← / → para navegar, S para notas e F para tela cheia.

Conteúdo adaptado de DevSecOps.pdf ao visual atual. Capturas são registros históricos da demonstração; blocos de IA do HTML foram preservados.

## Slide 1 — Capa

Olá a todos. Meu nome é Lucas Renan e sou Especialista em Segurança de Aplicações. A proposta de hoje é mostrar como integrar segurança ao ciclo de desenvolvimento sem criar um novo gargalo — usando automação open source e IA para ganhar escala e contexto.

## Slide 2 — Quem sou eu

Antes de entrar no tema: sou formado pelo IFPE, tenho sete anos de experiência em tecnologia e cinco dedicados a AppSec. Minha rotina passa por automação, análise estática e dinâmica, modelagem de ameaças e testes de invasão. Gosto também de compartilhar conhecimento em eventos e comunidades.

## Slide 3 — DevOps para DevSecOps

DevOps acelerou a entrega, mas por muito tempo a segurança continuou no modelo de esperar o software ficar pronto para testar. DevSecOps muda isso: a segurança participa desde o início e precisa ser automatizada. O objetivo não é instalar mais um portão manual; é colocar controles no fluxo de engenharia.

## Slide 4 — Por que integrar segurança?

  Encontrar problemas enquanto a equipe ainda está projetando e desenvolvendo.  Reduzir retrabalho e encurtar o caminho entre descoberta e correção.  Entregar com rapidez, com segurança como responsabilidade compartilhada.

## Slide 5 — S-SDLC

No S-SDLC, cada fase tem controles adequados. No planejamento, modelamos ameaças. No código, analisamos vulnerabilidades e segredos. No build, olhamos dependências e imagens. Em staging, fazemos testes dinâmicos. Em operação, monitoramos e aprendemos. O ponto central é reduzir o tempo entre introduzir um risco e receber feedback útil.

## Slide 6 — Referências para o trabalho

O material antigo reúne ASVS, MASVS e WSTG como referências para orientar requisitos, revisões e testes.

## Slide 7 — Quem participa?

   AppSec:  orienta requisitos, modelagem e validação de segurança.   Desenvolvimento:  implementa controles e corrige vulnerabilidades.   SRE e DBRE:  colaboram na operação, infraestrutura e dados.   PO:  participa da priorização e dos critérios de aceitação.

## Slide 8 — Modelagem de ameaças

No PDF, esse bloco se conecta a Insecure Design, A04 do OWASP Top 10 de 2021. A modelagem acontece antes de depender apenas de scanners.

## Slide 9 — Modelagem com STRIDE

Exemplo de documentação de modelagem de ameaças. Registro da apresentação original; resultados e versões retratam aquela demonstração.

## Slide 10 — Do modelo ao requisito

Exemplo de análise da tela de login no material original. Registro da apresentação original; resultados e versões retratam aquela demonstração.

## Slide 11 — SCA · dependências

O slide original relaciona SCA a A06:2021 — Vulnerable and Outdated Components. SCA analisa componentes; é uma atividade distinta da revisão manual de código.

## Slide 12 — SAST · código-fonte

O material também cita SonarQube, Snyk e Fortify. Aqui mantemos o foco na ferramenta usada na parte prática.

## Slide 13 — Exemplo: “pingue” um IP

Apresentar o trecho original como exemplo vulnerável. O objetivo é acompanhar o caminho da entrada até a execução.

## Slide 14 — Command injection

Demonstração original do problema no programa de ping. Registro da apresentação original; resultados e versões retratam aquela demonstração.

## Slide 15 — Perguntas para a revisão

  Qual tipo de dado a função deveria aceitar?  A entrada é validada antes de chegar a uma operação sensível?  Existem senhas ou outros segredos em texto claro?  A complexidade dificulta compreender e testar o comportamento?

## Slide 16 — Validação manual

Tentativa de validação de endereço sem uma biblioteca de parsing. Registro da apresentação original; resultados e versões retratam aquela demonstração.

## Slide 17 — Validar o IP e evitar o shell

A versão foi adaptada: além da validação com ipaddress apresentada no PDF, passamos argumentos separados ao subprocess, sem shell. No Windows, a opção de contagem do ping é -n.

## Slide 18 — DAST · aplicação em execução

O PDF também apresenta Nessus, Nmap e Nuclei como ferramentas de análise. O escopo de cada ferramenta varia; o exemplo de DAST da pipeline usa ZAP.

## Slide 19 — Resultados da análise dinâmica

Painel de achados exibido na apresentação antiga. Registro da apresentação original; resultados e versões retratam aquela demonstração.

## Slide 20 — Ferramentas

Aqui entram ferramentas open source. Threat modeling começa antes do código. Na pipeline, podemos usar Bandit para Python/SAST, TruffleHog ou Gitleaks para segredos e Trivy para containers, pacotes e repositórios. Depois, no ambiente de teste, scripts e scanners dinâmicos ampliam a cobertura.

## Slide 21 — Pipeline

Este é o desenho que conecta a palestra. O pull request dispara scanners de segredos e SAST. Depois vêm dependências, imagem e build. Em staging, fazemos DAST. O diferencial é o passo de IA: ela recebe os achados e adiciona contexto antes do gate. A IA não substitui a regra nem o especialista; ela ajuda a decidir o que merece atenção primeiro.

## Slide 22 — CI/CD: integrar e entregar

   Integração contínua:  integrar mudanças com frequência e executar build e testes automatizados.   Entrega contínua:  manter um artefato validado e pronto para implantação.  A pipeline conecta essas etapas e inclui verificações de segurança.

## Slide 23 — GitHub Actions

  Automatizar build, testes e deploy a partir de eventos do repositório.  Organizar a execução em  workflows, jobs e steps .  Também automatizar labels, issues e outras tarefas do repositório.

## Slide 24 — Um primeiro workflow

Exemplo transcrito do PDF com indentação YAML preservada. A versão da action é a do material original.

## Slide 25 — Onde os jobs executam?

   GitHub-hosted:  ambiente hospedado pelo GitHub, pronto para executar o workflow.   Self-hosted:  ambiente provisionado e administrado pela própria equipe.  A escolha considera manutenção, personalização e acesso aos ambientes necessários.

## Slide 26 — Vamos pôr a mão na massa

  Disparar o workflow com uma alteração no repositório.  Executar  Trivy  para dependências e  Bandit  para Python.  Guardar os relatórios e inspecionar os achados.  Executar  ZAP  contra a aplicação no ambiente de teste.

## Slide 27 — Workflow em execução

Registro da execução no GitHub Actions. Registro da apresentação original; resultados e versões retratam aquela demonstração.

## Slide 28 — Trivy: achado de dependência

Exemplo de vulnerabilidade encontrada na demonstração original. Registro da apresentação original; resultados e versões retratam aquela demonstração.

## Slide 29 — Bandit: achado no código

Exemplo de segredo em código apontado na demonstração. Registro da apresentação original; resultados e versões retratam aquela demonstração.

## Slide 30 — Publicar os relatórios

Etapas de análise estática e envio dos resultados SARIF. Registro da apresentação original; resultados e versões retratam aquela demonstração.

## Slide 31 — ZAP na pipeline

Configuração da análise dinâmica apresentada no PDF. Registro da apresentação original; resultados e versões retratam aquela demonstração.

## Slide 32 — Bônus: IA comenta no PR

Comentário produzido pela integração experimental de IA. Registro da apresentação original; resultados e versões retratam aquela demonstração.

## Slide 33 — Evolução do experimento

Os próximos passos do PDF são apresentados como planos do experimento original, sem afirmar que já foram concluídos.

## Slide 34 — SDLC nativo de IA

Com IA generativa, escrever código ficou muito mais rápido. O número 10× aqui é visual e representa a mudança de ordem de grandeza — não uma métrica universal. O ponto é: se a produção de código acelera e a revisão humana permanece linear, o gargalo se move. Precisamos aplicar automação e contexto também na análise dos achados.

## Slide 35 — Triagem com IA

Imagine 120 achados vindos de vários scanners. Em vez de colocar 120 itens na fila humana, podemos correlacionar os resultados com a alteração, a exposição da aplicação e o contexto do ativo. O 120 para 5 é um exemplo didático, não uma promessa de redução fixa. A revisão humana continua essencial nos casos relevantes.

## Slide 36 — Como a IA muda o S-SDLC

No planejamento, artefatos de intenção podem carregar contexto tanto para humanos quanto para agentes. No desenvolvimento, a IA pode ajudar a gerar testes e cenários negativos. Na governança, scanners continuam produzindo sinais objetivos, enquanto a IA auxilia a triagem. A pessoa deixa de gastar tempo igualmente com tudo e foca nos casos mais críticos.

## Slide 37 — Scripts usados

Referências dos repositórios mostrados no material original. Registro da apresentação original; resultados e versões retratam aquela demonstração.

## Slide 38 — Encerramento

Em resumo: segurança precisa fazer parte do fluxo, não aparecer só no final. Ferramentas open source continuam sendo a base técnica da automação. A IA pode ajudar a transformar volume em contexto e prioridade, mas decisões de risco importantes continuam pedindo julgamento humano. Muito obrigado. Perguntas?
