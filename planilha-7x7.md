Para preencher experiências:
Para níveis 3 e 4, comece pelas evidências. As evidências devem mencionar a situação (projeto e momento) onde os exemplos ocorreram, com objetivo de demonstrar consistência.
Para atingir consistência, espera-se cerca de ~6 meses de atuação.

Nível inicial: Nível exploratório -  esperado que a pessoa esteja no momento de absorção de conhecimento, não é necessário marcar o item.
Nível 1: Nível aprendiz, ou nível de domínio teórico - esperado que a pessoa tenha profundidade teórica (de ponta a ponta)  sobre o que está sendo pedido.
Nível 2: Nível de capacidade, ou nível de conhecimento prático - esperado que a pessoa tenha consistência em praticar o que está sendo pedido, com suporte.
Nível 3: Nível de proficiência - esperado que a pessoa tenha consistência em praticar o que está sendo pedido sem nenhum suporte.
Nível 4: Nível expert - esperado que a pessoa tenha experiência em praticar o que está sendo pedido em cenários complexos. Cenários válidos a serem usados de exemplo abaixo:
    1 - Escala - Os seus exemplos demonstram que você atuou em maior escala (Múltiplos times ou projetos)
    2 - Adversidade - Os seus exemplos demonstram que você atuou em cenários adversos (cliente ou situação complicada e/ou atenuada, requerendo energia extra em comunicação e alinhamentos ou escalações frequentes)
    3 - Complexidade técnica - Os seus exemplos demonstram atuação em uma tecnologia diferente da que habitualmente trabalha, que seja peculiar, com poucos profissionais especialistas, e/ou muito nova no mercado, com nenhum ou pouquíssimo suporte externo e interno."
___

## pergunta: Identifico e implemento/oriento a melhoria de pontos prioritarios do codigo, como desempenho ou manutenibilidade

### L3


### **L4**

___

## pergunta: Investigo e aplico diferentes métodos de análise, identificando e solucionando problemas técnicos

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

## pergunta: Avalio e defino padrões para codificação garantindo que sejam seguidos por todo o time

### L3

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

### L4

- [2016~2018 Luxfacta Projeto Modulação Fabril]:
  - [ESCALA] Minha participação no projeto envolvei mais de 2 equipes, tanto interna Luxfacta quando externa (cliente), onde os treinamentos necessários foram feitos para manter o padrão do projeto.
  - [ADVERSIDADE] Os times eram contrários à escolha das tecnologia [knockoutjs] por falta de conhecimento da ferramenta, onde os conflitos foram solucionados com sessões de treinamentos intensivos.
- [2019~2020 Dextra Cliente Dafiti]:
  - [ADVERSIDADE] Nenhum time sabia como funcionava a API, e os devs da época não via com bons ólhos PHP por serem de outra stacks (python, golang). Com isso muitas discuções surgiram no refactor da [mobile-api] na tentativa de trocar além do mecanismo de pesquisa, a stack também. Embora o prazo para migração era curto, não estava 100% justificado migrar a stack somente porque os devs não sabiam aquela stack/framework, e os conflitos foram solucionados com constantes comunicações da área de gestão Dextra-Dafiti para conseguir "acalmar" os ânimos.
  - [ESCALA] Também foi necessário envolver muitos times de outros contextos para tentar remapear toda trajetória da API para criar documentação que não existia
- [2020~2021 Dextra Cliente Dafiti]:
  - [COMPLEXIDADE TÉCNICA] Ambas as stacks [golang nodejs] foram aprendidas para poder criar as bibliotecas e criar os padrões para o cliente.
- [2021~2022 Dextra-CI&T Dafiti]:
  - [COMPLEXIDADE TECNICA] Entrando no mundo DevOps para conseguir padronizar as pipelines do cliente, estou aprendendo [kubernetes, argocd, helm] para melhorar meu entendimento das stacks para melhorar a qualidade das entregas do cliente.

___

## pergunta: Codifico de forma clara e objetiva utilizando as melhores práticas

### L3

Embora muito se prega em utilizar-se de [design-patterns] como [SOLID, DDD, TDD, STRATEGY, etc], todos tem o objetivo de 

- [2016-2017 - luxfacta Projeto Modulação fabril]
  Fui responsável por definir padrão de projeto para implementação de nova ferramenta para AMBEV-Brasil para gestão de produção de cervejas , atuando como lider técnico e arquiteto.
  Como lider técnico tive a missão de aprender para poder ensinar uma equipe de 12 desenvolvedores uma nova tecnologia (na época) de front-end chamada KNOCKOUT-JS para construção de um front-end reativo com padrão MVVM onde maior desafio foi conseguir ter precisão arbitrária de 20 decimais para contas complexas de fórmulas matemáticas para gestão do sistema. Já para back-end o desafio foi criar integrações com sitemas legados de gestão, para extração de dados automatizados para preencher a estrutura básica de dados da nova aplicação para facilitar o processo de migração de ferramenta.

- [2017-2018 - Luxfacta Projeto Interactionlog]
  Como lider de equipe, fui responsável por entrar no projeto já em andamento, onde a estrutura base estava desorganizada, minha missão foi aprender/organizar todos os escopos do histórico do projeto e realizar um Refactor da aplicação para melhoria tanto de performance quanto de usabilidade, que na época estava cheio de bugs e débitos técnicos. A tecnica usada para melhorar o projeto foi de adequação com padrão DDD na separação bem clara dos domínios e responsabilidades, trazendo uma melhora de 70% na velocidade de processamento (média caiu de 5s para 800ms). No processo, fui responsável em treinar a equipe para poder manter o padrão e boas práticas.

- [2019-2020 Dextra Projeto Mobile-api]
  Fui responsável por migrar o mecanismo de pesquisa de SOLR para Datajet, onde o maior desafio foi aprender um novo framework PHP para poder fazer a documentação que não existia da API, fazer um refactor para tirar a implementação acoplada com todos os conponentes da API para conseguir criar uma factory de mecanismos de pesquisas, separando as responsabilidades com padrão DDD.

- [2020-2021 Dextra Projeto FINDING-TEAN]
  Fiquei encarregado da manutenção e gestão da API principal de catálogo que era em uma stack que eu não dominava, aprendi GOLANG, fiz um package publicado em <https://pkg.go.dev/github.com/gritzkoo/golang-health-checker/pkg/healthcheck> que é usado como componente instalado em muitas aplicações no cliente e na comunidade.

- [2021 Dextra Iniciativa PCI Dafiti]
  Fui incumbido da responsabilidade de fazer correções de segurança em aplicação PCI em uma stack que eu não sabia (scala). Tive de aprender para ensinar time pequeno de 2 devs. Maior desafio foi aprender a stack, a estruturação do projeto para poder fazer pequenos refactores, usando DDD para entregar os ajustes solicitados de segurança sem comprometer a plataforma de pagamentos!

### L4

Consigo constantemente engajar os times ao qual faço suporte a melhorarem as entregas com qualidade, mesmo que o cenário não é propício para isso, as vezes sendo o pivô de alguns conflitos, mas sempre com a qualidade em primeiro lugar
Exemplo das iniciativas:

[2015~2019 Luxfacta Cliente:Ambev~ABInbev]
- [COMPLEXIDADE TÉCNICA] Aprender para poder ensinar uma equipe de 12 pessoas a usar tecnologia de front-end chamada [knockout-js] para construir uma aplicação reativa para gestão de produção.
- [ADVERSIDADE] Ao enfatizar que a aplicação não estava usando boas práticas de código ao qual iriam prejudicar a entrega da funcionalidade solicitada, foi usado todos os meios de comunicação possíveis (gestores, coordenadores e devs) porém não surtiu efeito. Foi necessário uma escalada para o C-Level passando os pontos negligenciados aos demais ao qual resultou em uma demissão em massa no cliente! [Brasil Pré Pagos (BPP)].

[2019~2022 Dextra-CI&T Cliente:Dafiti]
- [ESCALA] Migração eks sofia (refatoração da aplicação para conversão de boas práticas em apps para containers) foi uma iniciativa de suporte para outro time [cross] que estava com um desafio de fazer ajustes em uma stask ao qual não dominavam, e ensinar [docker, docker-compose, helm, argo-cd, gitops, kubernetes] para
- [COMPLEXIDADE TECNICA] aprender para poder ensinar [golang] para dar manutenção e refactor de microserviço de catálgo. Também fui responsável em ensinar a stack de [golang] para outra consultoria [ESCALA] para poder incluir novas funcionalidades no microserviço [ADVERSIDADE] onde os devs de lá tinham problemas de comunicação o que dificultou a entrega da inclusão de ADS.
- [ESCALA] Ajuda contexto de Payment em aplicações legadas PHP para melhoria de código e boas práticas (iniciativa do bacen)
- [ADVERSIDADE] Mapeamento global das APIs dafiti para ajuda na estratégia para nova arquitetura de new app backend.









------------


## trashed

- [2018-2019 - Luxfacta Projeto Atendimentos]
  Fui responsável por organizar a migração da aplicação de servidores on-premisse para cloud(azure), e fazer o plano de rollout da aplicação.
___

Consigo constantemente engajar os times ao qual faço suporte a melhorarem as entregas com qualidade, mesmo que o cenário não é propício para isso, as vezes sendo o pivô de alguns conflitos, mas sempre com a qualidade em primeiro lugar
Exemplo das iniciativas:

[2015~2019 Luxfacta Cliente:Ambev~ABInbev]

- [COMPLEXIDADE TÉCNICA] Aprender para poder ensinar uma equipe de 12 pessoas a usar tecnologia de front-end chamada [knockout-js] para construir uma aplicação reativa para gestão de produção.
- [ADVERSIDADE] Ao enfatizar que a aplicação não estava usando boas práticas de código ao qual iriam prejudicar a entrega da funcionalidade solicitada, foi usado todos os meios de comunicação possíveis (gestores, coordenadores e devs) porém não surtiu efeito. Foi necessário uma escalada para o C-Level passando os pontos negligenciados aos demais ao qual resultou em uma demissão em massa no cliente! [Brasil Pré Pagos (BPP)].

[2019~2022 Dextra-CI&T Cliente:Dafiti]

- [ESCALA] Migração eks sofia (refatoração da aplicação para conversão de boas práticas em apps para containers) foi uma iniciativa de suporte para outro time [cross] que estava com um desafio de fazer ajustes em uma stask ao qual não dominavam, e ensinar [docker, docker-compose, helm, argo-cd, gitops, kubernetes] para
- [COMPLEXIDADE TECNICA] aprender para poder ensinar [golang] para dar manutenção e refactor de microserviço de catálgo. Também fui responsável em ensinar a stack de [golang] para outra consultoria [ESCALA] para poder incluir novas funcionalidades no microserviço [ADVERSIDADE] onde os devs de lá tinham problemas de comunicação o que dificultou a entrega da inclusão de ADS.
- [ESCALA] Ajuda contexto de Payment em aplicações legadas PHP para melhoria de código e boas práticas (iniciativa do bacen)
- [ADVERSIDADE] Mapeamento global das APIs dafiti para ajuda na estratégia para nova arquitetura de new app backend.










Embora eu sou conhecido entre os devs como uma pessoa que é dura na review de PRs, sempre tendo compartilhar meu conhecimento adquirido ao logo da carreira para ajudar os demais a evoluir na carreira, mas com uma segunda inteção de tentar manter um padrão.