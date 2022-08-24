# Para preencher experiências

Para níveis 3 e 4, comece pelas evidências. As evidências devem mencionar a `situação` (projeto e momento) onde os `exemplos ocorreram`, com objetivo de demonstrar `consistência`.

Para atingir consistência, espera-se cerca de `~6 meses de atuação`.

- `Nível inicial: Nível exploratório` -  esperado que a pessoa esteja no momento de absorção de conhecimento, não é necessário marcar o item.
- `Nível 1: Nível aprendiz, ou nível de domínio teórico` - esperado que a pessoa tenha profundidade teórica (de ponta a ponta)  sobre o que está sendo pedido.
- `Nível 2: Nível de capacidade, ou nível de conhecimento prático` - esperado que a pessoa tenha consistência em praticar o que está sendo pedido, com suporte.
- `Nível 3: Nível de proficiência` - esperado que a pessoa tenha consistência em praticar o que está sendo pedido sem nenhum suporte.
- `Nível 4: Nível expert` - esperado que a pessoa tenha experiência em praticar o que está sendo pedido em cenários complexos. Cenários válidos a serem usados de exemplo abaixo:
  - 1 - **Escala** - Os seus exemplos demonstram que você atuou em maior escala (Múltiplos times ou projetos)
  - 2 - **Adversidade** - Os seus exemplos demonstram que você atuou em cenários adversos (cliente ou situação complicada e/ou atenuada, requerendo energia extra em comunicação e alinhamentos ou escalações frequentes)
  - 3 - **Complexidade técnica** - Os seus exemplos demonstram atuação em uma tecnologia diferente da que habitualmente trabalha, que seja peculiar, com poucos profissionais especialistas, e/ou muito nova no mercado, com nenhum ou pouquíssimo suporte externo e interno."

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

## Coding Excellence: Investigo e aplico diferentes métodos de análise, identificando e solucionando problemas técnicos

### L3

Sou considerado no cliente onde trabalho hoje, uma referência no quesito de resolver problemas complexos em ambiente produtivo to tipo top-down.
Constantemente estou envonvido em salas de warroon para ajudar a fazer análise de problemas e atuando na solução dos mesmos. Meu processo de investigação consiste em:

- Analisar logs da aplicação em elasticsearch (graylog ou kibana)
- Analisar graficos de telemetria de hardware (usando APM Instana ou Newrelic) como consumo de memória/cpu/rede
- Analisar saúde de cluster k8s analisando recursos reservados vs utilizados usando APM Instana
- Criação de dashboards customizados em grafana para trace de problemas customizados, com auxilio de logs aprimorados em aplicações.
- Criação de aplicações simples para ajudar a fazer troubleshooting de forma agnostica as aplicações, como por exemplo a ferramenta `php-memcache-toolkit` feita para ajudar a validar e verificar dados no servidor memcache e migrar dados cross ambientes.

Essa habilidade foi aprimorada em muitos projetos que atuei em minha carreira e não somente aqui na CI&T. A baixo irei listar alguns exemplos:

- [2017 Luxfacta projeto Interactionlog]
  - Consegui identificar, através da análise dos logs da aplicação, problemas de compatilidade das bibliotecas instaladas na aplicação e a integração com banco de dados SQL-Server. O ambiente de desenvolvimento era Windows, e o ambiente produtivo era Linux (open susy), e por conta disso todos os dados da integração com um banco de dados especívico do cliente foi comprometida. Na época a solução mais rápida foi migrar o ambiente produtivo para Windows, e com isso o problema foi mitigado.
- [2018 Luxfacta projeto Atendimento]
  - Através de investigação dos logs e com validação de execução no banco de dados da aplicação, consegui identificar problemas nas consultas geradas no banco de dados que estavam gerando gargalos de execução da aplicação. Com essa análise e os dados em mãos, foi possível fazer uma lista de tarefas a serem feitas no projeto para melhorar as consultas à base de dados. Fui o protagonista no sentido de puxar as informações e montar uma estratégia junto ao time para realizar as tarefas.
- [2019 Dextra cliente Dafiti blackfriday 19]
  - Durante a blackfriday de 2019, atuei diretamente no time de suporte para manter a loja no ar validando boards de telemetria do grafana e newrelic. Um problema muito específico aconteceu com os servidores de memcache onde parte da navegação do catalog estava comprometida por falta de dados no servidor memcache. Eu criei uma aplicação separada da API para tirar metricas e dados do servidor memcache, a `php-memcache-toolkit` para validar, analisar e injetar dados nos servidores memcache. Com isso conseguimos identificar o gap entre servidores
- [2020 Dextra cliente Dafiti projeto mobile-api]
  - Com meus conhecimentos em PHP consegui corrigir problemas de escalabilidade da API, fazendo análise dos dados do APM (Newrelic), e realizando ajustes nos parâmetros do php-fpm, nginx e limites do K8s. Também fiz ajustes nas multi-camadas da imagem Docker para conseguir usar de forma mais aprimorada um container mais enxuto, utilizando imagem oficial da stack. Isso melhorou a performance da aplicação em mais de 20%.
- [2021 Dextra cliente Dafiti projeto catalog-search]
  - Investigação de problemas de comunicação entre a API da Dafiti catalog-search e o serviço de catálogo Datajet estavam gerando perda de vendas do cliente. O método de análise utlilizado foi usar o cloudwatch da aws e tirar core-dump das máquinas para ter insumos de dados sobre comunicação entre os clusters k8s para validação de rotas. O problema consiste até hoje na Dafiti, pois o problema está do lado da Datajet, mas foi resolvido parcialmente o problema, adicionando um API GATEWAY entre a comunicação das APIs para que mais métricas fossem registradas para gerar dashboards mais elaborados no grafana para ajudar no troubleshooting do problema. Foi incluido no API GATEWAY também uma camada extra de cache para evitar solicitações multiplas para a API e mitigar ainda mais o problema.
- [2022 fevereiro CI&T Cliente Dafiti servidores de Mencached]
  - Investigação relacionada à falhas constantes nos servidores de memcache que perdiam dados e tiravam a loja, parcialmente, do ar. O problema foi identificado analizando as configurações de ingraestrutura dos servidores, que estavam usando mapeamento de DNS de forma errada para multiplos servidores, ao invés de usar o serviço de NLB(network load balancer). Após diagnosticado, a atuação foi repassar todas as configurações das máquinas EC2, definindo DNS, tirando confiugração de IPs chumbados no código, e redirecionando as aplicações de consulta, para passarem a usar o NLB. O problema foi solucionado e até o momento estamos sem mais incidentes com esse componente.

### L4

A habilidade de investigar problemas e solucioná-los está sempre vinculada com algum tipo de complexidade, e nos exemplos que eu citei não é diferente!

- [2017 Luxfacta projeto Interactionlog]
  - [ADVERSIDADE] Nesse projeto, o cliente Ambev já estava muito alterado com a cituação, pois o sistema era a plataforma oficial de avaliação de desempenho dos funcionários e também uma plataforma de log de trabalho, como se fosse um checkbox diário de atividades, e como o sistema estava constantemente dando problemas, várias pessoas foram prejudicadas pela instabilidade do sistema, e os animos estavam muito exaltados. Atuar em um ambiente perturbado é bem mais complexo e exigiu muita energia extra para manter a calma da equipe, gerentes e analistas para encontrar a solução e entregar para o cliente
- [2018 Luxfacta projeto Atendimento]
  - [COMPLEXIDADE TÉCNICA] Nesse desafio foi necessário aprender muito sobre banco de dados para poder solucionar o problema, e como essa não era uma skill muito evoluida minha na época, foi onde tive a oportunidade de estudar muito e fazer a aplicação de tudo que aprendi para solucinar o problema
- [2019 Dextra cliente Dafiti blackfriday 19]
  - [COMPLEXIDADE TECNICA] Foi quando eu consolidei meu conhecimento em ferramentas como GRAYLOG, GRAFANA KIBANA para conseguir ter telemetria de sistema em tempo real, e como em toda minha carreira eu não tinha tido a oportunidade de atuar com esse ferramental, foi necessário um esforço extra para conseguir aprender para poder ensinar a usar essas ferramentas e conseguir diagnosticar problemas com mais eficiência.
  - [ADVERSIDADE] Durante essa blackfriday, os servidores de memcache falharam, e por conta disso, a navegação do catálogo de produtos dos aplicativos foram prejudicadas. Como minha atuação naquele ano foi a substituição do mecanismo de pesquisa, o problema foi vinculado com a entrega do novo catálogo na API, e deveras não era esse o problema, e a complexidade gerada pelo cliente foi encontrar energia para explicar que, o problema era nos servidores de memcache e não na implementação da API do catálgo foi grande. Depois de explicada, eu criei uma ferramenta para auxiliar a análise do memcache na Dafiti, o `php-memcache-tool-kit` e conseguimos realizar os ajustes necessários em tempo record e voltar o catálogo no ar!
- [2020 Dextra cliente Dafiti projeto mobile-api]
  - [COMPLEXIDADE TÉCNICA] Para conseguir atingir esses objetivos, foi necessário evoluir a versão do php de 5.5 para 7.3(versão top-1 da época) para ter acesso à algumas funcionalidades novas que viabilizariam os ajustes. A migração de versão iria acarretar em um refactor em 100% das classes de teste, uma vez que o phpunit teria de subir de 2.9 para 8.5 e nenhuma ferramenta automatizada para isso existe. A migração de versão foi um sucessso!
  - [ADVERSIDADE] Embora a migração tenha ocorrido sem problemas, os engenheiros da Dafiti da época não queriam continuar a dar suporte à aplicações escritas em PHP, e estavam pregando o discurso de que não era possível migrar a versão do php para uma mais recente e que não valia a pena o esforço, e que era melhor usar esse tempo e esforço para mudar a tecnologia da API, que na época estavam cogitando em mudar para python. Foi necessário energia extra para conseguir explicar e provar que era possível fazer a migração na aplicação sem a necessidade de big-bang mudando a stack do projeto, mas como isso era contra os princípios do responsável pela API no cliente, foi necessário realizar essa migração escondida do cliente e entregar os resultados mesmo assim.
- [2021 Dextra cliente Dafiti projeto catalog-search]
  - [COMPLEXIDADE TÉCNICA] Tive de aprender para a stack de GOLANG para poder conseguir atuar nesse projeto, e junto a stack, componentes de cloud como API GATEWAY, CLOUDWATCH, ATHENA. Como o desafio à ser resolvido era muito complexo para minha hardskill da época, foi necessário uma energia extra nos estudos para conseguir atender as espectativas do cliente na solução desse problema.
- [2022 fevereiro CI&T Cliente Dafiti servidores de Mencached]
  - [COMPLEXIDADE TÉCNICA] Aqui nesse desafio foi necessário consolidar meus conhecimentos em servidores memcache para conseguir definir qual seria a forma correta de confiurações tanto de aws quanto de aplicações para resolver o problema. Minha atuação foi em conjuto com o time de SRE da Dafiti, mas tive papel de protagonismo nas sugestão das ações de melhorias, e minhas sugestões foram muito bem aceitas nos planejamentos, e na execução, todos funcionaram e trouxeram o resultado esperado, redução de incidentes com servidores de memcache e downtime de catálogo.

___

## Coding Excellence: Identifico e implemento/oriento a melhoria de pontos prioritarios do codigo, como desempenho ou manutenibilidade

### L3

- [2015 - Luxfacta projeto PMT]
  - Levantamento de códigos duplicacos com auxilio da ferramenta sonarqube para montar lista de backlog para inclusão nas tarefas das sprints.
  - Atuei como referência na inciativa dos refactors da aplicação atuando diretamente nos pontos sinalizados pelo sonarqube
  - redução de mais de 20% no tamanho total do pejeto utilizando as melhorias proprostas na ferramenta sonarqube
- [2016 - Luxfacta projeto mofab]
  - Como líder técnico da equipe de desenvolvimento, fui o protagonista na organização do projeto para viabilizar a implementação das fórmulas matemáticas complexas para reaproveitamento em todo sistema de forma unificada para facilitar testes
- [2017 - Luxfacta projeto Interactionlog]
  - Identifiquei oportunidade de melhorias no módulo de formulários dinâmicos da aplicação, levantando os pontos que poderiam estar mais performaticos. Atuei junto ao time no refactor fazendo uma mudança de mais de 30% na experiência do usuário do front-end no tempo de resposta da aplicação.
  - Identifiquei códigos duplicados com auxilio do sonarqube para montagem de lista de backlog de débtos técnicos do projeto, ajudando o time projetar no tempo, as tarefas para realizar os ajustes necessários
- [2018 Luxfacta projeto mofab Africa do sul]
  - Como o projeto estava sendo convertido para multi-linguas, foi aproveitado para os refactors de:
    - atualização do código base, passando de PHP-5.6 para php-7.1.3
    - migrado o framework báse de laravel 4.2 para laravél 5.8
    - Criado sistema proprietário de gestão de traduções do framework em banco de dados, viabilizando planilhas excel para exportar e importar traduções para 7 linguas
    - inclusão de autenticação api via ssl com geração e cadastro de API via painel admin
- [2019 Dextra Dafiti mobile-api]
  - Refactor completo de todo módulo de catálogo da API dos aplicativos android ios para tirar código de catálogo acoplado e separar em contextos separados usando DDD
  - Refactor de toda base de testes do catálogo passando framework base de testes phpunit-2.8.9 para phpunit-8.4 para
  - Refactor do booststrap da aplicação para viabilizar a migração de versão do php de 5.5 para 7.3
- [2020 Dextra Dafiti catalog-search]
  - Identificado problemas de conexão entre apis de dependências externas usando graylog com métricas de redes coletadas do prometeus e cloudwatch, e com os insumos gerados foi possível mitigar problemas do catálogo da loja para BF 2020 fazendo uso do API-GATEWAY como intermediador das requisições entre os microserviços Dafiti vs Datajet
  - Refactor da aplicação, melhorando o boostrap no start dos pods em eks, diminuindo o tempo de startup de 2min para 30s
  - Fui protagonista na iniciativa de Dafiti ADS para montar a estratégia de implementação da nova integração com a catalog-search, viabilizando testes e métricas no grafana
- [2021~2022 Dextra Dafiti Plataforma]
  - Identifiquei melhorias que poderiam beneficiar a Dafiti em relação à padrões de esteira e deployment de aplicações EKS e EC2, montando junto ao meu gerente Direto Willian Lopes a estratégia para compania Dafiti para implamentar as mudanças sugeridas, e ajudar a fazer sunset de ferramentas sub-utilizadas
  - Fui protagonista fazendo refactor de 2 grandes componentes do cliente (bob alice) tirando de ferramentas legadas o deploy para pipelines modernas (circle ci) melhorando o time to market dos times de engenharia nos sitemas citados

### L4

Para simplificar a descrição, vou consolidar de forma resumida uma trajetório de N projetos!
Os pontos mais impactantes nas aplicações, no quesito melhoria de código e resiliência das aplicações, eu fui o protagonista da implementação do padrão de health-check da stack nodejs e golang, que foi incluida em larga escala no cliente Dafiti, para melhoar a vizibilidade das aplicações.
Os projetos de início da carreira, o foco foi muito em "arrumar a casa" fazendo refactors usando TDD DDD como guias e ferramenta de qualidade como sonarqube como validador.
Muitos projetos do cliente atual tiveram impactos enormes nos times, sendo hoje uma referência em grande parte do cliente como sinônimo de qualidade.
___

## Coding Excellence: Identifico a necessidade e construo PoCs no meu contexto quando necessário, fazendo uso de frameworks ou linguagens modernas

### L3

No meu histórico de atuação do cliente atual, faço POCs para resolver todos os problemas, entre elas, algumas viraram soluções reais como

- Package golang, nodejs e PHP de health-check que nasceram de forma singela para aliviar uma dor por falta de padrões, e hoje são packages publicados oficialmente na comunidade
  - <https://github.com/gritzkoo/nodejs-health-checker>
  - <https://github.com/gritzkoo/php-health-checker>
  - <https://github.com/gritzkoo/golang-health-checker>
  - <https://github.com/gritzkoo/golang-health-checker-lw>
- POC de estudos de AWS APIGATEWAY que virou solução de BF 2020 Dafiti que segurou audiência do catálogo da loja!
- POC de estudos de gitops que está sendo utilizada de guidelines para branch estrategy, organização dos argo cds e nomenclaturas gerais de deployments na atuação do time atual. Esses guidelines estão sendo usados para estruturação da documetação técnica de onboarding do time de engenharia e de sre. Abaixo a lista dos repositórios usados como POCS e a minha certificação de gitops fundamentals para consolidar o conhecimento no contexto.
  - <https://github.com/gritzkoo/gitops>
  - <https://github.com/gritzkoo/helm-charts>
  - <https://github.com/gritzkoo/argo-class/blob/main/instalando-argocd.md>

### L4

Como as POCS citadas no L3 foram largamente utilizadas na Dafiti trazendo uma grande mudança nos processos de desenvolvimento (atual e em progresso), as ações se caracterizam no contexto de [ESCALA] pois o impacto é grande e cross times e torres da dafiti.

Já outros exemplos como do API Gateway, foi necessário mais um esforço no contexto de [ADVERSIDADE] pois existiu uma resistência tênue dos engenheiros de sre que não dominavam a tecnologia e não queriam deixar usar a solução. Foi necessário um esforço extra, tanto para aprender para poder ensinar, qunato mostrar as melhorias com métricas de cloudwatch, prometeus e grafana na solução dos problemas de comunicação usando a ferramenta como intermediadora.

As atividades recentes referentes à gitops, helm charts, cluster kubernetes, estão sendo desafioadores no contexto de [COMPLEXIDADE TÉCNICA] pois essas tecnologias eu não conhecia, e estou estudando elas para poder agregar valor na experiência dos desenvolvedores da Dafiti, para trazer padrões e automações que viabilizam uma experiência melhor no dia-a-dia da engenharia da Dafiti
___

## Coding Excellence: Apoio a melhoria do código de outras pessoas colaboradoras, fornecendo feedback por meio de revisões de código

### L3

- [2021 Dafiti customer-api]
  - Auxiliei o time de customer para conceber/configurar o start do projeto junto ao Eduardo Judici, passando conhecimento sobre a stack de nodejs. Também fiz acomanhamento do ramp da evolução do time no aprendizado de boas práticas no desenvolvimento para poder contemplar pipeline agnostica, padrão de liveness/readiness para k8s. Para k8s também foi passado o conhecimento sobre finetuning de pods utilizando como ferramenta o instana para companhar os gráficos de consumo de recursos de cpu/mem.
- [2022 Dafiti carmen]
  - Auxiliei time de wallet para migração da aplicação carmen web e api para container. Minha participação nesse movimento foi de intrutor para o Michel Vivaldini instruindo em como construir a Dockerfile, criar os deployments no repositório de gitops (argo), e revisão dos códigos no github, sempre apontando pontos de melhorias do código como escrita de logs em stdout, padrão de log em json, pipeline agnostica à stack usando docker-compose.
- [2022 Dafiti new app]
  - Auxiliei time de new app para criação dos dashboards no grafana para monitoria dos microserviços do novo app.

### L4

___

## Continuous Delivery: Defino e configuro um ambiente de Integração Contínua com todas as suas práticas/fases

### L3

- [2019 Dafiti mobile-api]
  - Fiz o discovery do processo de CI/CD da API, pois não havia mais ninguém na Dafiti que conhecia os processos de delivery da mesma. Após o rediscovery, foi identificados pontos de melhoria da aplicação para que a pipeline fosse migrada da ferramenta desenvolvida em casa da Dafiti para CircleCI
- [2020 Dafiti]
  - Fiz a reestruturação dos deploys dos microserviços do ecosistema de PWA, para utlizar CircleCI e gitops, tirando da ferramenta feita em casa da Dafiti Py_Deployer, utilizando as melhores práticas do mercado. os microserviços migrados foram:
    - discovery-venus
    - discovery-mars
    - ms-cms
    - ms-catalog
  - Fiz refactor de toda pipeline e steps de deploy da aplicação CORE de catálogo da Dafiti, a catalog-search. O refactor consistil de, remover a stack de go da pipeline, transformando os passos da pipeline agnostica à stack, utilizando docker-compose e boas práticas de Docker, criando uma imagem muitl-estágios com responsabilidades distintas e definidas, migrando configurações via arquivo `.env` para variáveis de ambiente do container no deployment.

### L4

- [2022 Dafiti DevXP]
  - [ESCALA] Desenhei novo fluxo de trabalho para toda compania, chamado de `branch strategy` onde o principal objetivo é deixar as pipelines padronizadas por meio de um ORB da CircleCI que funciona como um sitema de template de pipelines. O branch strategy consite de separar passos de pipelines adequados para cada fase de desenvolvimento, onde não irá ocorrer execuções desnecessárias gastando créditos da pipeline por falta de planejamento. O padrão consite da nomenclaruta de branchs hotfix release feature, onde:
    - hotfix é a branch que passa por todos os passos da pipeline até chegar com o artefato (registry, package) em homologação ou stage passando por testes unitários, scans DAST SAST, build de artefato, deploy em ambiente de dev, espera interação humana para avançar o artefato para homolog. Ao fechar a PR da hotfix na main, o artefato de homolog é promovido para live
    - release é a branch principal que representa uma história ou épico do JIRA, onde é criada a partir da main, ela não aceita comits direto, toda interação é realizada via Pull Requests de suas branchs filhas features, que são a representação das subtasks do JIRA. a branch de feature usa apenas os passos de testes e scans, que são utilizados como gates de qualidade na PR para release, e assim que fechado uma PR para release, a mesma inicia os passos de geração do artefato (registry ou package) para ser instalado no primeiro ambiente (dev ou qa), que fica esperando interação humana para promover para (homolog ou stage) para testes de fumaça. Uma vez fechada a PR da release na main, o artefato de homolog é promovido para live.
  Esse processo diminui em 60% o tempo de uso dos runners e time to market pois não é passado por todas as etapas na pipeline para entregas em live.

___

## Continuous Delivery: Defino ou customizo a estratégia de versionamento de código adequada ao meu contexto, e a utilizo corretamente

### L3

Fui o protagonista da padronização de N pipelines de projetos cross com objetivo de definir para compania Dafiti Group, o modelo mais adequado de versionamento de código para microserviços que são deployados em EKS.

Para projetos que não são do tipo package, o versionamento dos artefatos usa os 7 primeiros dígitos do hash do commit, para evitar que fique poluido o repositório no GitHub com infundadas tags e semantic versioning erradas apenas do "porque sim" de entregas de apps que não faz sentido usar semantic.

Para repositórios que são do tipo PACKAGE, desenhei e padronizei a pipeline para execução de testes e publicação automática no gerenciador interno NEXUS da Dafiti para stack de node, NPM.

Documentei os processos, no Confluense, para que novos desenvolvedors saibam os passos necessários para criar novos packages e dar manutenção nos atuais sem maiores problemas.

### L4

No contexto de estratégia de versionamento, fui o protagonista da escrita do CIRCLECI-ORB da dafiti <https://circleci.com/developer/orbs/orb/dafiti-group/orb-standard-pipeline> onde foi estruturado todas as melhores práticas de versionamento de código de forma organizada para poder replicar a mesma estratégia para toda Dafiti.
Com o Orb, foi lançada uma iniciativa de modernização de todas as aplicações da dafiti para o uso do mesmo, sendo assim, acredito que essa iniciativa se enquadra em [ESCALA] na régua de 7x7
___

## Continuous Delivery: Defino e automatizo o pipeline de entrega adequado para o meu contexto, e garanto que o time o utilize corretamente

### L3

Tenho proficiência em 2 tecnologias de pipelines, Github Actions e Circleci.
Para meus projetos pessoais que são packages de código aberto na comunidade, uso a pipeline Github Actions como nos links de exemplo abaixo:

- <https://github.com/gritzkoo/nodejs-health-checker/blob/master/.github/workflows/main.yml>
- <https://github.com/gritzkoo/golang-health-checker/blob/master/.github/workflows/main.yaml>
- <https://github.com/gritzkoo/golang-health-checker-lw/blob/main/.github/workflows/test.yaml>
- <https://github.com/gritzkoo/php-health-checker/blob/main/.github/workflows/test.yml>

Todas usam padrão de execução de testes com coverage que é enviado para o `coveralls.io` para geração dos badges de quality-gates dos packages

Já para CircleCI, eu adquiri o `known-how` na Dafiti nos últimos 3 anos, e venho aprimorando à cada novo desafio.
Entre os exemplos de pipelines mais relevantes, tenho um histórico de protagonismo em ajudar a criar os padrões da Dafiti, ao invés de apenas usá-los.
Os projetos mais conceituados e cross eu eu ajudei a padronizar a pipeline, e modernização, é os componentes BOB ALICE MOBILE-API MOBILE-CHECKOUT-API CATALOG-SEARCH CATALOG-FRONT, a maioria deles eram EC2 e foram midradas para k8s.

### L4

Acredito que como a padronização da Dafiti como um todo como meio do CircleCI ORB seja um exemplo de L4, pois é uma ação que padroniza para toda corporação os padrões de pipeline, e junto com a documentação no confluense, é uma metodologia adequada para garantir que todos da corporação utilizem desse novo paradigma!
___

## Continuous Delivery: Automatizo o provisionamento de ambientes através de ferramentas

### L3

### L4

___

## Continuous Delivery: Identifico métricas técnicas ou de negócio e implanto o monitoramento das mesmas, dando ciência delas ao cliente ou ao time

### L3

Tenho proficiencia em geração de dashboards com APM instana e Grafana.
Nos projetos que eu vivi na dafiti, como mobile-api mobile-checkout-api, alice, sofia, customer-api, entre outros, todos receberam padronização de health-checks para montar os dashboards de monitoria de alertas no Grafana. Embora no ZABIXX não tenha cido eu especificadamente que criei os alertas, foi a partir da padronização dos logs que eu fiz nas aplicações citadas anteriormente que viabilizou a criação dos alertas.

O dashboard de maior peso que eu fiz para dafiti foi o de monitoria de chaves do memcache da aplicação mobile-api, que é a fonte de dados para todos os troubleshootings envolvendo esse componente.

Outro dashboard que foi muito utilizado, foi o do catalog-search que criou visualizações de tráfego por loja/país, com status de cache hit/miss das configurações do API-GATEWAY da aws
### L4

___

## Continuous Delivery: Desenho e aplico arquiteturas em processos que habilitam a entrega contínua e a testabilidade da solução

### L3

- [MobileAPI]
  - Na migração de ferramenta de consulta de catálogo de SOLR para DATAJET, implementei a solução de forma estruturada para que somente com FEATURE-TOOGLE fosse possível utilizar o novo modelo de catálogo dos APPs. Também nos testes foi utilizado estrutura de Mocks para testar todo módulo de catálogo e garantir transparência para virada da implementação. No delivery, acompanhei com o time de business a virada do tipo canary do catálogo, usando a feature-toogle no firebase dos applicativos, liverando de forma gradativa o novo catálogo.
- [Sofia catalog-front]
  - Na migração de EC2 para EKS, além de modernizar vários items da aplicação, foi utilizado modelo BLUE/GREEN para virada do tráfego em ambiente produtivo
- [Catalog Serarch]
  - Nesse microserviço, que era exclusivamente de finding no tempo que estive por lá, migrei a forma de desenvolvimento para TRUNK BASED DEVELOPMENT para conseguir fazer entregas mais confiáveis e rápidas, eliminando as branchs acumulativas, deixando mais limpo o histórico no github da solução.
### L4

___

## Quality: Defino e implanto a estratégia de teste automatizado para garantia da qualidade

### L3

- [Meus projetos OpenSource de health-checks]
  - Utilizo da estratégia de TDD nos meus packages de health-check para garantir que toda nova versão, todos os critérios de qualidade sejam seguidos garantindo uma entrega saudável e segura nas stacks de PHP NODE GOLANG
- [Mobile-API]
  - Na migração do módulo de catálogo, utilizei TDD para garantir que sempre que novos ajustes sejam feitos no catálogo da API, todos os cenários de testes deem cobertura suficiente para dar segurança para novos desenvolvedores que hoje fazem manutenção no módulo. Os testes unitários é passo obrigatório na Pipeline e é utilizado como quality-gate para habilitar merge button na PR
- [Mobile-checkout-api]
  - Fui o protagonista na migração da versão de php de 5.5 para 7.3, e nessa virada, foi necessário reescrever toda base de testes unitários da API migrando phpunit da versão 2.9 para 8.5. Durante a fase de refactor dos testes, reescrevi boa parte dos mesmo para que mocks gatantissem as respostas das integrações externas de forma correta e garantir integridade dos testes e removi testes que estavam na base do código sem motivo ou inválidos
- [Alice]
  - Na implemnetação do módulo de feeds integrado com datajet, escrevi testes unitários utilizando padrão TDD e MOCS para garantir que as entregas dessa funcionaliade tivessem um alto nível de confiabilidade
- [PWA]
  - Integração com feeds foi precursora da implementação de testes usando JEST e providers de testes escrevendo todos senários possíveis garantindo qualidade na entrega do módulo. Embora hoje esse projeto tenha sido descontinuado pelo cliente, serviu de base de conhecimento para implemnetação do mesmo paradígma em outros projetos utlizando a stack de NODE
### L4

___

## Quality: Planejo e executo testes adicionais (acessibilidade, desempenho ou segurança), interpretando os resultados e comunicando sugestões de próximos passos

### L3

Fui protagonista na iniciativa de finetuning da mobile-api, para utilizar ferramentas de testes automatizados como Gatling e Vegeta, para simular teste de stress, para poder pegar metricas de consumo de CPU e MEM, usando Newrelic ou Instana APM, dos pods em K8S, para ajustar os recursos do deployment para melhorar o tempo de resposta e o consumo de recurso do cluster.
Meu conhecimento foi lapidado nessa iniciativa, e com o conhecimento adquirido, consegui realizar em outras aplicações do cliente, como catalog-search, catalog-front, alice, bob, ms-catalog, ms-cms, discovery-venus, entre outras.
Hoje sou considerado tanto pela equipe de dev quando pela equipe de sre, uma referência no quesito finetunning, e estou envolvido em muitas iniciativas de SRE ajudando a planejar e executar tarefas de melhorias contínuas nos ajustes das aplicações.
### L4

___

## Quality: Participo e/ou lidero o assunto qualidade no meu escopo através de governança dos processos

### L3

Atualmente no cliente, sou considerado uma referência no quesito de governança de processos de qualidade. 

Os principais processos ao qual fui protagonista, o que mais se destaca foi a implementação de um sonarqube padronizado, que antes estava segmentado em mais de uma instância e não era todos os projetos que estavam sendo gerenciados, para um novo e centralizado, criando um template padrão de pipeline, que da ferramenta de circleci se chama ORB, e escrevi a documentação técnica de como fazer o ingresso de qualquer projeto, seja novo ou legado, para a utilização desse processo.
Também sou o protagonista da padronização dos health checks de 3 stacks, PHP NODE GOLANG e estou constantemente acompanhando o time de engenharia para manter esse padrão, fazendo apresentações explicando a importancia desse processo.

### L4

___

## Quality: Defino metas de qualidade e apoio o time a alcançá-las usando o resultado das ferramentas de análise do código

### L3

Na iniciativa de ingresso de SSC para utilização da API catalog-search, fazendo a virada de catálodo de solr para datajet, fui o protagonista em criar dashboards no grafana, para servir de metricas de índice de erros e tempos de respostas, e com esses dados, fiz os alinhamentos de expectativas entre time Brasil, Argentina, Colombia e Chile, para definir qual seria os critérios de acetie do índice de falha e SLA da API. Com as métricas foi possível fazer a migração da API do cluster Brasil para um compartilhado com SSC e com isso, identificamos problemas de comunicação entre regiões da AWS deixando a aplicação fora dos padrões estabelecidos com o time SSC. Com a inclusão de um API GATEWAY, foi possível não somente corrigir o problema do SLA da API como também viabilizar muitas outras métricas, por meio do CLOUD-WATCH, que por meio deste, foi possível fazer uma ação conjunta com time da Alemanhã Datajet, para fazer troubleshooting de rede e ajustar as configurações de VPC PEARING entre clusters e melhorar o tempo de resposta da API, deixando abaixo de 300ms. Nessa iniciativa as métricas dos dashboards eram cruciais e serviram como parâmetros de entrega de qualidade na iniciativa.

Na minha atuação no time de finding, utilizei métricas extraídas do Google GMT e Google Analítics para ajudar na tomada de decisão junto a P.O da época (Drielli) para validar as hipóteses de melhorias no catálogo, e junto aos indicadores, eu era o protagonista para mapear as ações junto com o time para realização dos ajustes e melhorias necessários para atingir as metas necessárias de negócio.

Para meus packages publicados na comunidade, de padronização de health-check escritos em PHP NODE GOLANG, utilizo code coverage junto ao COVERALLS.IO para servir de quality-gate das pipelines de automação para garantir 100% de coverage dos packages.

Embora eu tenha sido um protagonista na Dafiti na implementação do servidor sonarqube, padronização das pipelines de muitros projetos, ainda essa iniciativa não está contemplando o code coverage sendo gerenciado pelo sonarqube, mas estou puxando esse tópico em meu time de DevXP para inclusão da padronização de como extrair coverage de forma agnostica na pipeline e usá-los como parâmetro de quality-gate para servir de travas nas PRs do Github e dar mais visibilidade dos problemas que as aplicações da Datifi tem atualmente. Como o parque de aplicações é composto quase na totalidade por aplicações obsoletas e legados, optei por não incluir esse íncide na abordagem inicial do sonarqube para não travar toda engenharia e passar, inicialmente um extrato do cenário atual de muitas aplicações.

### L4

___

## Quality: Planejo e faço testes exploratórios / manuais de forma eficiente e garantindo a execução do fluxo completo

### L3

- [2019 mobile-api]
  - Planejei testes da API para contemplar todo o processo de compras no APP da Dafiti, e escrevi o senário em GATLING para virar um teste de stress da estrutura, para servir de insumo para ajustes da infraestrutura para realizar ajustes necessários para conseguir aguentar a audiência da BlackFriday. Com as telemetrias geradas com os testes, nas ferramentas de observabilidade da época [newrelic, grafana, kibana], foi possivel ajustar o tamanho do pool de conexões do php-fpm, tamanho de recursos dos pods tanto de memória quanto de cpu, e com esses ajustes, foi possível passar a BF sem downtime da estrutura
- [2020 catalog-search]
  - Para viabilizar testes que simulassem uma navegação organica para teste de stress da estrutura, estudei o uso da ferramenta https://github.com/tsenart/vegeta (vegeta) e com os logs da API, que foi resgatado da ferramenta de log kibana da época, foi possível contruir uma massa de 200k querys únicas que simulavam a navegação no catálogo da loja, e junto com a automação dos testes, usando argo workflows, foi possível definir o amanho da autiência e tempo dos testes. Os resultados eram apresentados por tempo de respostas e status code, e com os dados coletados das ferramentas de observabilidade [newrelic graylog, grafana], foi possível fazer ajustes no deployment do kubernetes de HPA e melhorar o tempo de autoscaling da aplicação e durante a BF 2022 não teve downtime do componente

Embora meu conhecimento em testes abrangem desde testes unitários e até testes de stress automatizados, atualmente não estou usando mais esse conhecimento, pois minha atuação no cliente não está direatamente ligada às iniciativas que demandem esse tipo de atuação.
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

## Process: Mobilizo o time e participo de agendas para melhoria contínua, criando uma lista de ações futuras utilizando métricas de processo como referência

### L3

### L4

___

## Teamwork: Dou feedback de forma efetiva (com exemplos) aos membros do time, dando visibilidade dessa ação aos líderes

### L3

### L4

___

## Teamwork: Identifico e formo sucessores, diminuindo as dependências de pessoas específicas ou para viabilizar crescimento

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
