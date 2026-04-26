# ifpr-web3-lista-0 

## 1.​ Quais protocolos (os principais) são usados em uma comunicação realizada na web? Descreva muito brevemente o papel de cada um deles.​

HTTP/HTTPS (Camada de Aplicação): Responsáveis pela comunicação entre o software (navegador) e o servidor web. O HTTPS adiciona uma camada de criptografia via TLS/SSL. 

DNS (Camada de Aplicação): Converte nomes de domínio (como www.exemplo.com) em endereços IP. 

TCP (Camada de Transporte): Garante que os dados cheguem completos e na ordem correta através de um processo de conexão chamado handshake

IP (Camada de Internet): Responsável por rotear os pacotes de dados pela rede até o servidor de destino correto.

## 2. Alguns autores usam o termo “arquitetura da web” para se referir a como as camadas tecnológicas da web estão organizadas e aos princípios que definem a troca de informações entre essas camadas. Por questões didáticas e de simplificação, convencionou-se chamar essa arquitetura de “arquitetura cliente x servidor” ou arquitetura “requisição x resposta”. Explique de forma simplificada como funciona essa arquitetura. 

Essa arquitetura, funciona de forma que a comunicação é sempre iniciada pelo cliente (como um navegador). O processo básico consiste em: O cliente solicita um recurso específico (uma página, uma imagem, etc.) <-> O servidor recebe essa solicitação, processa e responde devolvendo o recurso solicitado ou uma mensagem de erro.

## 3.​ Em uma arquitetura web, qual o papel desempenhado pelo protocolo HTTP?​

O HTTP (Hyper Text Transfer Protocol) é o protocolo padrão para a troca de mensagens na web. Ele atua como uma interface bem definida que estabelece regras para a comunicação, sendo orientado a recursos e operando no modelo de requisição e resposta. Ele define como as mensagens de solicitação devem ser estruturadas e como os códigos de estado devem ser interpretados.

## 4.​ O HTTP possui padrões uniformes para requisição e para resposta. 
### a)​ Dê ao menos três exemplos métodos de requisição e suas características; 

- GET: Utilizado para solicitar um determinado dado ou recurso do servidor. 
- POST: Indica ao servidor o envio de dados do cliente para serem processados (como dados de um formulário de login). 
- DELETE: Utilizado para solicitar a exclusão de um recurso específico. 

### b)​ Dê ao menos três exemplos status de respostas e quando ocorrem; 

- 200 OK: Indica que a requisição foi bem-sucedida e o recurso está sendo entregue. 
- 404 Not Found: Ocorre quando o servidor não consegue encontrar o recurso solicitado na URL informada. 
- 500 Internal Server Error: Indica que ocorreu um erro genérico no servidor ao tentar processar a requisição.

## 5.​ Em uma arquitetura web é sempre o cliente quem inicia o processo de comunicação: o cliente requisita, o servidor responde. Contudo, aplicações web como Gmail ou Instagram, “empurram” informações novas ao cliente, tais como um novo e-mail ou uma “curtida” em uma determinada publicação. Hipoteticamente, quais estratégias poderiam ser empregadas para se chegar a esse resultado? 

WebSockets: Fornece comunicação bidirecional em tempo real entre cliente e servidor. 
Long Polling (Pool de espera): O cliente faz uma requisição e o servidor a mantém aberta até que haja uma nova informação para enviar. 
Periodic Ping (Ajax): O cliente "pergunta" ao servidor periodicamente se há novidades através de APIs assíncronas.

### SOBRE O FRAMEWORK SPRING​

## O Spring Framework é um framework Java que fornece uma infraestrutura completa para o desenvolvimento de aplicações, especialmente aplicações web e corporativas, com foco em: i) Baixo acoplamento; ii) Alta coesão; ii) Organização da arquitetura​

## 6.​ Em uma aplicação web baseada no Spring MVC, o desenvolvedor cria classes anotadas com @Controller (ou @RestController no futuro) e define métodos para responder a URLs específicas. Entretanto, quando um usuário acessa uma URL no navegador (por exemplo, digitando /produtos), o navegador não “chama diretamente” o método do controller. Faça uma pesquisa e considerando a arquitetura do Spring MVC explique como o Spring consegue interceptar a requisição HTTP, decidir qual controller e qual método devem ser executados e, por fim, gerar a resposta ao cliente. 

Embora o navegador não chame o método do controller diretamente, o Spring intercepta a requisição através de um fluxo coordenado:
- **Interceptação: Um servidor web (como o Tomcat) recebe a requisição HTTP bruta.
- **Conversão: Os dados da requisição são convertidos para objetos Java (como o HttpServletRequest).
- **Roteamento (DispatcherServlet): O Spring utiliza um "mapeador de rotas" que analisa a URL (ex: /produtos) e o verbo HTTP para decidir qual classe anotada com @Controller e qual método (anotado com @GetMapping, por exemplo) deve tratar aquele pedido.
- **Execução e Resposta: O Spring invoca o método, passa os parâmetros necessários e o retorno do método é processado para gerar a resposta final ao cliente.

## 7.​ Em Java, é comum encontrarmos códigos que utilizam anotações como @Override, @Deprecated ou @SuppressWarnings. Diferentemente de comentários, essas marcações não servem apenas para documentação, mas podem influenciar o comportamento do compilador, das ferramentas e até da execução do programa. Considerando esse contexto, explique o que são anotações em Java e qual é o seu papel no desenvolvimento de aplicações modernas. 

Anotações são metadados usados para fornecer informações sobre o código sem alterar diretamente sua lógica de execução. No desenvolvimento moderno, elas desempenham um papel crucial na configuração e gerenciamento de aplicações, permitindo que o compilador ou o próprio framework (como o Spring) saiba como tratar determinada classe ou método (ex: definir permissões, persistência ou injeção de dependência).

## 8.​ Em aplicações baseadas no Spring Framework, é comum criar classes simples, sem código explícito de configuração, apenas utilizando anotações como @Component, @Controller, @Service ou @Repository. Mesmo assim, o Spring consegue instanciar objetos, injetar dependências e organizar a aplicação automaticamente. Considerando esse cenário, explique como as anotações do Spring permitem que o framework identifique, gerencie e conecte os componentes da aplicação sem que o desenvolvedor precise criar objetos manualmente. 

O Spring consegue gerenciar componentes sem configuração manual através do seu Container e das anotações de especialização:Identificação: Ao usar anotações como @Component, @Controller, @Service ou @Repository, o desenvolvedor sinaliza que aquela classe deve ser um Bean gerenciado pelo Spring.Ciclo de Vida: O Spring Container assume a responsabilidade de instanciar o objeto, configurar seus atributos iniciais e destruí-lo quando necessário.Injeção de Dependência: O framework identifica quais objetos uma classe precisa e os "injeta" automaticamente (passa os objetos necessários para o bean), eliminando a necessidade do desenvolvedor usar o operador new manualmente.
