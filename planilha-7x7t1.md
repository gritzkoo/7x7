# Para preencher experiências:

Para níveis 3 e 4, comece pelas evidências. As evidências devem mencionar a `situação` (projeto e momento) onde os `exemplos ocorreram`, com objetivo de demonstrar `consistência`.

Para atingir consistência, espera-se cerca de `~6 meses de atuação`.

- `Nível inicial: Nível exploratório` -  esperado que a pessoa esteja no momento de absorção de conhecimento, não é necessário marcar o item.
- `Nível 1: Nível aprendiz, ou nível de domínio teórico` - esperado que a pessoa tenha profundidade teórica (de ponta a ponta)  sobre o que está sendo pedido.
- `Nível 2: Nível de capacidade, ou nível de conhecimento prático` - esperado que a pessoa tenha consistência em praticar o que está sendo pedido, com suporte.
- `Nível 3: Nível de proficiência` - esperado que a pessoa tenha consistência em praticar o que está sendo pedido sem nenhum suporte.
- `Nível 4: Nível expert` - esperado que a pessoa tenha experiência em praticar o que está sendo pedido em cenários complexos. Cenários válidos a serem usados de exemplo abaixo:
  - 1 - Escala - Os seus exemplos demonstram que você atuou em maior escala (Múltiplos times ou projetos)
  - 2 - Adversidade - Os seus exemplos demonstram que você atuou em cenários adversos (cliente ou situação complicada e/ou atenuada, requerendo energia extra em comunicação e alinhamentos ou escalações frequentes)
  - 3 - Complexidade técnica - Os seus exemplos demonstram atuação em uma tecnologia diferente da que habitualmente trabalha, que seja peculiar, com poucos profissionais especialistas, e/ou muito nova no mercado, com nenhum ou pouquíssimo suporte externo e interno."

___

## Coding Excellence: Codifico de forma clara e objetiva utilizando as melhores práticas

### L3

Embora muito se prega em utilizar-se de [design-patterns] como [SOLID, DDD, TDD, STRATEGY, etc], todos tem o objetivo de padronizar e organizar projetos, embora pessoalmente não os sigo à risca, pois teoria e prática nem sempre andam juntas. Eu os uso como base de norteamento e os uso da forma que melhor resolve cada problema.

- [2016-2017 - luxfacta Projeto Modulação fabril]
  Atuei como lider de projeto e arquiteto. Criei front-end reativo usando MVVM e FACTORY com libjs knowkout-js. Já no backend, usando framework LARAVEL, foi utilizado padrão misto de DDD com MVC

- [2017-2018 - Luxfacta Projeto Interactionlog]
  Também atuando como lider técnico e arquiteto, fiz migração do projeto legado para usar MVVM com FACTORY no front-end, refactor do back-end para usar DDD FACTORY MVC

- [2019-2020 Dextra Projeto Mobile-api]
  Fui responsável por fazer refactor mecanismo de pesquisa usando FACTORY DDD, também fiz refactor e update da aplicação para evoluir de PHP 5.5 para 7.3 reescrevendo boa parte dos testes unitários migrando PHP-Unit de 3.5 para 8.9.

- [2020-2021 Dextra Projeto FINDING-TEAN]
  Fui responsável pelo refactor da catalog-search para melhoria de:
  - performance: reduzindo tempo de respostas de 1.4s para < 500ms, reduzindo código legado e passos que não faziam mais sentido, separando responsabilidades usando DDD
  - melhoramento de monitoria, usando lib compartilhada de health-check criando dashboards mais específicos para tracing de rede, implementando um API GATEWAY para mitigar problemas de comunicação com Datajet
  - padronização de logs, usando padrão JSON

- [2020-2021 Dextra Projeto CATALOG-FRONT SOFIA]
  Fui responsável por fazer migração de ec2 para eks. Essa app passou por um refactor para ficar compatível com environments, padronização de logs, monitoria.
  Para padronizar essa app, e criar um padrão para Dafiti, desenvolvi um padrão não comunm no merdado de padrão de imagem Docker multilayer, onde em conjunto do Docker compose foi possível deixar a pipeline agnostica a stack, e com isso, conseguimos definir um padrão para migração de outras apps utilizando a mesma abordagem.

### L4

- [2016-2017 - luxfacta Projeto Modulação fabril]

  [COMPLEXIDADE TÉCNICA] Tive de aprender para poder ensinar KNOCKOUTJS, lib pouco conhecida na época de front-end, com documentação pouco intuitiva.

- [2020~presente]
  - [ESCALA]
    - Criei uma aplicação template na Dafiti escrita em GOLANG para padronizar tanto o padrão de pipeline agnóstica, quando padrão de imagem Docker multi-layer com camadas com responsabilidades únicas para viabilizar uma chamada de CI apenas na pipeline. Esse projeto também padroniza a estrutura básica de deployment usando helm com gfg-application-web chart da dafiti, padroniza também resposta de health-check. Esse template também é utilizado como guide-line para outras stacks na geração de novos projetos de template e documentação dos processos de criação de novas aplicações na Dafiti.
    - Jutno à migração do SOFIA, o padrão madurecido nessa iniciativa é utilizado em vários outros projetos seguindo os mesmos guide-lines de padrão de [pipeline, docker, docker-compose, helm]. Esses padrões hoje estão documentados no cliente no Confluense para iniciar novas APPS

___

## Coding Excellence: Avalio e defino padrões para codificação garantindo que sejam seguidos por todo o time

### L3

Entre os padrões que eu identifiquei na minha carreira, as de maior relevância para compartilhar aqui seria

- Padronização de probes de liveness e readiness onde sou autor de duas bibliotecas OpenSouce para ser usada tanto nas aplicações do cliente quanto para toda comunidade dev
  - <https://github.com/gritzkoo/golang-health-checker>
  - <https://github.com/gritzkoo/nodejs-health-checker>
- Padronização do desenho de pipelines deixando elas agnosticas à stack do projeto, essa padronização visa a utilização de Dockerfile com multilayer bem definidos com estratégia de CI interna, junto à implementação do Docker Compose com um serviço de nome CI, que é apenas chamado na pipeline `docker-compose run --rm ci` para que tudo o que é necessário para configurar, instalar e subir seja feito em apenas 1 step
- Padronização do branch strategy (ainda não apresentado apra toda engenharia até o momento) para mudar a forma como a Dafiti faz suas entregas. Esse padrão visa deixar igual a nomenclatura de branchs e configurações do github/circle-ci para que não tenha branchs que ficam acumulando um histórico muito grande de alterações, forçando ter vida curta. Já na pipeline, o padrão visa diminuir o uso dos runners fazendo a execução de tasks somente quando ela é mais relevante, como por exemplo, rodar testes somente nas features branchs, e da release branch para frente, não rodar mais esses passos. A branch release é a única que gera o artefato (seja registry ou qualquer outra coisa), e a publicação no 1º ambiente, seguindo apenas com a promossão desse artefato de ambiente para outro, garantindo a entrega explícita do que foi testado. Junto a essa estratégia, toda uma documentação está sendo feita para se tornar material de treinamento da engenharia para garantir que todos sigam esse novo modelo de trabalho.

<!-- 
- [2016~2018 Luxfacta Projeto Modulação Fabril]
Defini o padrão para implementação de contas automáticas usando [knockoutjs], com auxílio da lib [bignumberjs] para conseguir precisão arbitraria de 20 decimais. O padrão definido tirava a responsabilidade de validações numerais como [não nulo, diferente de zero, é numero, !NaN] de todos os parametros para chamada dos cálculos, deixando o código mais limpo, e criando uma [factory] para chamada dos cálculos, centralizando em um único ponto, a entrada dos argumentos para tratativa e manutenção das fórmulas matemáticas.
Ainda no mesmo projeto, criei uma interface de cadastro de clientes para API onde era gerado um par de chaves ssh ao qual era utilizado para fazer criptografia dos dados de comunicação de cada cliente da API(serviço) com sistema de monitoria para cada cliente isolado.

- [2019~2020 Dextra Cliente Dafiti]
Implementei o padrão [factory] no mecanismo de pesquisa da [mobile-api] e fiz tranferência de conhecimento para todos os envolvidos com a API da época para explicar o padrão.

- [2020~2021 Dextra Cliente Dafiti]
Criei duas libs para padronizar chamadas de [health-check liveness e readiness] em [golang] e [nodejs] e implementei em vário microserviços do cliente.
<https://github.com/gritzkoo/golang-health-checker>
<https://github.com/gritzkoo/nodejs-health-checker>

- [2021~2022 Dextra-CI&T Dafiti]
Criei projeto [golang] de template para criação de novos microserviços que além de padronizar o código/estrutura do projeto, padroniza pipeline agnostica e com observabilidade.
Atualmente estou criando novos padrões de projetos e pipelines para padronizar também os projetos legados.
-->
### L4

Nos todos os exemplos citados no L3 se enquadrão no quesito [ESCALA], pois eles envolvem atividades cross, impactando não somente 1 time ou projeto mas sim o cliente como um todo.
<!-- - [2016~2018 Luxfacta Projeto Modulação Fabril]:
  - [ESCALA] Minha participação no projeto envolvei mais de 2 equipes, tanto interna Luxfacta quando externa (cliente), onde os treinamentos necessários foram feitos para manter o padrão do projeto.
  - [ADVERSIDADE] Os times eram contrários à escolha das tecnologia [knockoutjs] por falta de conhecimento da ferramenta, onde os conflitos foram solucionados com sessões de treinamentos intensivos.
- [2019~2020 Dextra Cliente Dafiti]:
  - [ADVERSIDADE] Nenhum time sabia como funcionava a API, e os devs da época não via com bons ólhos PHP por serem de outra stacks (python, golang). Com isso muitas discuções surgiram no refactor da [mobile-api] na tentativa de trocar além do mecanismo de pesquisa, a stack também. Embora o prazo para migração era curto, não estava 100% justificado migrar a stack somente porque os devs não sabiam aquela stack/framework, e os conflitos foram solucionados com constantes comunicações da área de gestão Dextra-Dafiti para conseguir "acalmar" os ânimos.
  - [ESCALA] Também foi necessário envolver muitos times de outros contextos para tentar remapear toda trajetória da API para criar documentação que não existia
- [2020~2021 Dextra Cliente Dafiti]:
  - [COMPLEXIDADE TÉCNICA] Ambas as stacks [golang nodejs] foram aprendidas para poder criar as bibliotecas e criar os padrões para o cliente.
- [2021~2022 Dextra-CI&T Dafiti]:
  - [COMPLEXIDADE TECNICA] Entrando no mundo DevOps para conseguir padronizar as pipelines do cliente, estou aprendendo [kubernetes, argocd, helm] para melhorar meu entendimento das stacks para melhorar a qualidade das entregas do cliente. -->
___

## Coding Excellence: Investigo e aplico diferentes métodos de análise, identificando e solucionando problemas técnicos.

### L3

- [2017 Luxfacta Projeto Interactionlog]
  O projeto foi migrado para servidor linux (antes windows) onde muitos problemas de publicação foram encontrados. Os métodos para identificação dos problemas foram acompanhar os dashboards de métricas e os logs da aplicação para identificação dos erros, mas todos os problemas levantados eram referentes à configuração do sistema operacional da máquina EC2 com apache. Na época eu não sabia nem linux nem apache, foi necessário aprender ambos para poder solucionar os problemas sozinhos, embora existia um time de infra do cliente AMBEV da UOLDIVEL ao qual se negou a ajudar solucionar os problemas na época. Os ajustes foram realizados com sucesso.
- [2018 Luxfacta projeto atendimento]
  Problemas de performance da aplicação, foi necessário acompanhamento das métricas do banco de dados (SQL-server) para entender onde os problemas estam acontecendo. Após encontrados, tive de estudar banco de dados mais aprofundadamente para poder lidar com a iniciativa dos ajustes de performance junto ao time do projeto.
- [2019~Atualmente Dafiti]
  Hoje sou considerado pelo cliente a referência em troubleshooting, sendo constantemente solicitado para acompanhar os incidentes da loja em produção para ajudar tanto na tomada de decisões quando na soluções (paleativas ou definitivas) dos problemas. Os componentes ou projetos que sou mais considerado referência hoje são [bob mobile-api memcache catalog-search catalog-front alice docker-dafiti shared bootstrap php-memcache-toolkit]

### L4

Consigo facilmente passar do contexto de engenharia para infraestrutura sabendo investigar cross contexto problemas nas plataformas do cliente, mesmo quando C-level está junto nas warroons.
Em grande parte das investigações assumo posição de protagonismo puxando o racional junto ao time de engenharia e SRE.
Uso nas investigações ferramentas como GRAFANA, GRAYLOG, INSTANA, NEWRELIC, CLOUDWATCH.
Em alguns casos, crio logs específicos para montagem de dashboards customizados para tracking de pontos já conhecidos, o mais famoso no cliente é o dashboard das Mobiles onde é possivel rastrear problemas relacionados ao MEMCACHED, ponto de maior falha da engenharia do cliente.
Outro dash de troubleshooting muito usado foi de problemas relacionados à comunicação da API de catálogo do cliente para a API do 3º que entrega o conteúdo mapeando e evidenciando problemas relacionados à rede.
Complementando os pontos citados no L3 com profundidade.

- [2017 Luxfacta Projeto Interactionlog]
  - [COMPLEXIDADE TÉCNICA] Foi necessário aprender em tempo record sistema operacional LINUX(red hat), servidor web APACHE, para conseguir solucionar os problemas técnicos
  - [ADVERSIDADE] Todos os envolvidos no projeto estavam com os animos exaltados, a comunicação não estava fluindo, o dono da Luxfacta na época foi incluido na iniciativa para "prestações de contas" sobre o projeto não estar sendo "entregue" no "esparado/planejado". A cultura do cliente não era das melhores, o principal amago era achar os culpados achar pretestos para sanar os pagamentos. A pressão na entrega desse projeto em específico foi grande, mas ajudou a melhorar bastante as softskills de comunicação.
- [2018 Luxfacta projeto atendimento]
  - [COMPLEXIDADE TÉCNICA] Foi necessário aprender com profundidade os conseitos de banco de dados SQL-server para conseguir resolver esse problema técnico, embora não era o objetivo da minha carreina naquele momento, aceitei o desafio, e conseguir aprender e resolvi os problemas da iniciativa com qualidade.
- [2019~Atualmente Dafiti]
  - [ADVERSIDADE] A comunicação em alguns projetos nunca foram fluidos, algumas escalações eram constantes. 
    - [mobile-api] Para migrar a versão do PHP da mobile-api de 5.5 para 7.3 na época foi complexa porque o engenheiro "responsável" da Dafiti na época já tinha feito um discurso dizendo que era impossível fazer por retro-compatibilidade do framework da aplicação, ao qual não era verdade, ele apenas não queria (pessoalmente) migrar a versão por querer forçar migrar a stack de PHP para python na época. Minha posição nesse cenário foi realizar mesmo assim a migração da versão, e entregar a melhoria sem o aval do responsável, apenas escalando que os discursos não eram verdadeiros, e consegui entregar a melhoria.
    - [catalog-search] Implementação da feature Dafiti ADS, a consultoria responsável(envilha) não era proficiente em golang, e muitos discursos de falácias de dificuldades aleatórias eram usadas para mitigar a entrega da feature. Eu entrei e desenvolvi sozinho a feature não só na catalog-search, como também na [mobile-api] apenas para servir de exemplo em como fazer a feature. Os desenvolvedores envolvidos eram muito juniors, e não entendiam a complexidade ao qual o desafio pedia, a comunicação era muito falha, foi necessário fazer muitas escalações e até pedidos de substituição dos envolvidos por falta de proficiência.
    - [new-app] Embora a iniciativa é para um novo app[front-end], eu fui o protagonista que puxou junto ao coordenador da época [will lopes] para evidênciar os problemas de toda a plataforma, não se limitando apenas em front-end. Todo um mapeamento foi feito de mehorias de back-end foi feito para deixar explicito que era necessário "arrumar a casa" para dar suporte para iniciativa do novo app, porém, muita coisa conteceu durante o processo, e toda a camada da gestão/C-Level mudou no meio da iniciativa, e todo o mapeamento foi descreditado pelo gerente atual [braz] com o discurso que "a dafiti não tem problemas no back-end". Foi extremamente complicado explicar para ele sobre o engano que ele estava fazendo, mas infelizmente essa batalha eu não conquistei, e lamentavelmente fui designado apra outra iniciativa sem conseguir conquistar o espaço necessário para fazer as ações mapeadas.
    - [incidentes no geral] Várias vezes eu fui protagonista nas salas de warroom, quando C-Level estava presente tanto para esplicar as problemáticas quanto para mapear as ações com time de SRE/Engenharia para solução de problemas.
  - [COMPLEXIDADE TÉCINICA]
    - [apps no geral] Aprendi kubernetes argo-cd helm, aws, docker, ecr, ec2, golang, nodejs, scala para conseguir melhorar minha hardskill para ser considerado hoje a referência nos troubleshootings da plataforma como um todo.

___

## Coding Excellence: Identifico e implemento/oriento a melhoria de pontos prioritarios do codigo, como desempenho ou manutenibilidade

### L3

### L4

___

## Coding Excellence: Identifico a necessidade e construo PoCs no meu contexto quando necessário, fazendo uso de frameworks ou linguagens modernas

### L3

### L4

___

## Coding Excellence: Apoio a melhoria do código de outras pessoas colaboradoras, fornecendo feedback por meio de revisões de código

### L3

### L4

___

## Continuous Delivery: Defino e configuro um ambiente de Integração Contínua com todas as suas práticas/fases

### L3

### L4

___

## Continuous Delivery: Defino ou customizo a estratégia de versionamento de código adequada ao meu contexto, e a utilizo corretamente

### L3

### L4

___

## Continuous Delivery: Defino e automatizo o pipeline de entrega adequado para o meu contexto, e garanto que o time o utilize corretamente

### L3

### L4

___

## Continuous Delivery: Automatizo o provisionamento de ambientes através de ferramentas

### L3

### L4

___

## Continuous Delivery: Identifico métricas técnicas ou de negócio e implanto o monitoramento das mesmas, dando ciência delas ao cliente ou ao time.

### L3

### L4

___

## Continuous Delivery: Desenho e aplico arquiteturas em processos que habilitam a entrega contínua e a testabilidade da solução

### L3

### L4

___

## Quality: Defino e implanto a estratégia de teste automatizado para garantia da qualidade

### L3

### L4

___

## Quality: Planejo e executo testes adicionais (acessibilidade, desempenho ou segurança), interpretando os resultados e comunicando sugestões de próximos passos

### L3

### L4

___

## Quality: Participo e/ou lidero o assunto qualidade no meu escopo através de governança dos processos

### L3

### L4

___

## Quality: Defino metas de qualidade e apoio o time a alcançá-las usando o resultado das ferramentas de análise do código

### L3

### L4

___

## Quality: Planejo e faço testes exploratórios / manuais de forma eficiente e garantindo a execução do fluxo completo.

### L3

### L4

___

## Quality: Planejo e executo os planos de ação oriundos da análise de causas-raízes melhorando a qualidade

### L3

### L4

___

## Architecture & Design: Desenho e valido em fórum técnico soluções / arquiteturas baseadas no negócio e sob restrições técnicas

### L3

### L4

___

## Architecture & Design: Proponho soluções prevendo efeitos colaterais, defendendo-a e explicando as razões de decisões técnicas ao cliente e lideranças

### L3

### L4

___

## Architecture & Design: Incentivo e garanto que todo o time faça uso das melhores práticas de desenvolvimento de software

### L3

### L4

___

## Architecture & Design: Realizo o refinamento técnico absorvendo rapidamento o contexto do cliente e transfiro o conhecimento para o time durante o desenvolvimento

### L3

### L4

___

## Architecture & Design: Crio e mantenho roadmap em colaboração com os gestores, gerindo dívidas técnicas e priorizando itens técnicos no roadmap do projeto

### L3

### L4

___

## Architecture & Design: Elaboro uma estratégia para modernização tecnológica da plataforma do cliente, validando com as lideranças e comunicando-a efetivamente ao cliente

### L3

### L4

___

## Process: Colaboro ativamente durante reuniões de planejamento incentivando o meu time ao compromisso coletivo com as estimativas

### L3

### L4

___

## Process: Identifico e implanto melhorias de processo usando como base métricas coletadas da operação

### L3

### L4

___

## Process: Explico efetivamente todo o contexto / história do projeto, sempre me valendo de métricas durante a apresentação

### L3

### L4

___

## Process: Utilizo as ferramentas de acordo com o processo definido pelo time dando plena visibilidade das minhas atividades e do time

### L3

### L4

___

## Process: Monitoro, priorizo e alimento o backlog ajudando o time a ter conhecimento claro das próximas tarefas, técnicas ou não

### L3

### L4

___

## Process: Mobilizo o time e participo de agendas para melhoria contínua, criando uma lista de ações futuras utilizando métricas de processo como referência.

### L3

### L4

___

## Teamwork: Dou feedback de forma efetiva (com exemplos) aos membros do time, dando visibilidade dessa ação aos líderes

### L3

### L4

___

## Teamwork: Identifico e formo sucessores, diminuindo as dependências de pessoas específicas ou para viabilizar crescimento.

### L3

### L4

___

## Teamwork: Planejo e viabilizo a capacitação de todo o time para cobrir eventuais lacunas de conhecimento técnico identificados

### L3

### L4

___

## Teamwork: Contagio todo o time pelo exemplo e postura ao encarar desafios de forma positiva fazendo-os enxergar as eventuais oportunidades

### L3

### L4

___

## Teamwork: Incentivo, através do exemplo, revisões técnicas (ex: Solution Review) canalizando a experiência coletiva na produção de uma nova solução de melhor qualidade

### L3

### L4

___

## Teamwork: Compartilho conhecimentos regularmente em canais apropriados aumentando o conhecimento do time, área ou comunidade

### L3

### L4

___

## Soft skills: Comunico de forma efetiva e negocio propostas e soluções técnicas com o cliente

### L3

### L4

___

## Soft skills: Entrego de forma consistente tarefas sob minha responsabilidade sendo reconhecido como alguém que se pode contar

### L3

### L4

___

## Soft skills: Me comunico de forma eficaz e escalo qualquer tipo de necessidade em tempo hábil evitando que ocorram crises no projeto

### L3

### L4

___

## Soft skills: Construo e mantenho credibilidade com o cliente, time e liderança

### L3

### L4

___

## Soft skills: Crio e mantenho um relacionamento com o cliente, sendo visto e colocando a CI&T como referência

### L3

### L4

___

## Soft skills: Viabilizo e estimulo o time a participar de iniciativas corporativas, mobilizando dentro da área de atuação condizente com meu nível

### L3

### L4
