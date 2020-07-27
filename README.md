## TDD baseado no Desafio abaixo:

## Problema:

* Um determinado produto financeiro recolhe imposto de renda apenas quando o cliente faz o seu resgate. O cálculo do IR segue a seguinte lógica abaixo:
* Até 1 ano de aplicação: 22,5% sobre o lucro
* De 1 a 2 anos de aplicação: 18,5% sobre o lucro
* Acima de 2 anos de aplicação: 15% sobre o lucro
* A aplicação não pode ser igual ou menor que zero
* A data de resgate não pode ser menor que a data de aplicação

### Instruções:

1. Criar um projeto de classes chamado “Aliquota.Domain”;
2. Criar um projeto de testes chamado “Aliquota.Domain.Test”
3. Modelar a(s) entidade(s) que resolvem o problema abaixo;
4. Mapear as entidades no Entity Framework Core;
5. Criar um projeto de frontend para permitir a persistência de dados (console, webapp, etc.);
4. Testar a(s) entidade(s) de forma que garantam as regras de negócio;
5. Utilizar os conceitos de DDD, OO, POCO e SOLID que você julgar necessário;
6. Use inglês ou português no seu código. Como achar melhor. Isso não será critério de avaliação.


### Pré-requisitos:

* Utilizar C# e framework .NET Core;
* Utilizar xUnit para os testes;
* O projeto deve compilar;
* Os testes devem rodar pelo Test Explorer do VS e via console (dotnet test);

### Solução do Desafio:

Foram criadas APIs expostas via **Swagger** como interface, é possível aplicar novos investimentos e resgata-los. É possivel acessar ao executar a aplicação e acessar:
**https://\<URI-APP\>/swagger/index.html**

As **informações só são validas durante a exceção da aplicação**, como não existe sessão de usuário, decidi utilizar **Entity Framework in Memory** para essa abordagem.
APIs:

GET
* /investimento/Aplicacao/{id} **(Obtem uma aplicação por Id)**
* /investimento/Aplicacao **(Obtem todas aplicações)**
* /investimento/Aplicacao/{AplicacaoId}/resgate **(Obtem um resgate especifico de uma aplicação)**

POST
* /investimento/Aplicacao **(Cria uma aplicação)**
* /investimento/Aplicacao/{AplicacaoId}/resgate **(Resgata determinada aplicação)**
* /investimento/Aplicacao/resgate/disponiveis **(Resgata todas que tem data de aplicação menor que data de resgate)**
