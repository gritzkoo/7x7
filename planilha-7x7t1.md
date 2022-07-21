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
Minha stack principal é PHP, mas tenho autonomia também em NODEJS GOLANG. Faço pocs constantemente na Dafiti para poder provar conseitos de ajustes antes de alterar aplicações legadas!
### L4
Os pontos mais impactantes nas aplicações, no quesito melhoria de código e resiliência das aplicações, eu fui o protagonista da implementação do padrão de health-check da stack nodejs e golang, que foi incluida em larga escala no cliente Dafiti, para melhoar a vizibilidade das aplicações.
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

## Continuous Delivery: Identifico métricas técnicas ou de negócio e implanto o monitoramento das mesmas, dando ciência delas ao cliente ou ao time

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

## Quality: Planejo e faço testes exploratórios / manuais de forma eficiente e garantindo a execução do fluxo completo

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
