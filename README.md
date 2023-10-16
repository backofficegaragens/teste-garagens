# Estapar Backoffice - Teste Garagens


## Contexto

A [Estapar](https://www.estapar.com.br) é uma empresa com muitos produtos. Um deles é a estadia de carros em garagens.

Para este exemplo, a estadia de carros pode ser: 

__Estadia Avulsa__ 

Onde o pagamento segue a lógica de cobrança: 1) Valor da Primeira hora + 2) Valor das demais horas. 

A estadia mínima é a primeira hora e não existe carência. 
Para as demais horas a carência é de 30 minutos, ou seja passados 30 minutos é feita a cobrança da hora cheia, caso não passe de 30 minutos é feito a cobrança de 50% do valor para as demais horas da Garagem.


__Estadia de Mensalista__

O cliente paga o valor mensal estipulado para a Garagem e pode fazer múltiplas entradas e saídas na garagem contratada bem como deixar o carro durante a noite na garagem sem custo adicional (per noite).




## Requerimentos


__Pontos de Atenção__

- Consumir os serviços para obter dados de `Garagens`, `Formas de Pagamentos` e `Passagens`
- Salvar os dados localmente. 
    - ORM: `Entity Framework` ou `Dapper`
    - Banco de dados SQL Server
- Todo o código deve ser executado através do comando: `docker compose up`
- APIs devem estar disponíveis no `Swagger` da aplicação
- Todas as APIs devem ter parâmetro: Código da Garagem. Seja via autenticação ou via parametro.
- Saída deve ser no formato JSON em tela e armazenado em um Blob Storage
    - Pode utilziar o Azurite
- Arquivo `Postman` para teste das APIs.



__Documentação__ 

Escreva a documentação que achar necessária com as orientações de como rodar o projeto, como testar o projeto, items que podem servir de melhorias de performance, técnicas ou de arquitetura dando como exemplo cenários que suportem as argumentações.



__APIs__

O valor (`PrecoTotal`) de todas as passagens devem ser calculados levando em consideração: 1) Tempo de estadia; 2) Preço da primeira hora + preço das demais horas de cada Garagem.

Forma de Pagamento como `Mensalista` deve ter o falor zerado (0)


- __Lista de Carros__
    - Carros no período (Data e Hora inicial e Data e Hora final)
    - Carros que ainda estão na garagem (Data Final = Null)
    - Carros que passaram, e não estão mais na garagem.
- __Fechamento__
    - Dado um período, 1) quantidade total e valor por forma de pagamento incluindo mensalistas.
- __Tempo Médio__
    - Dado um período, 1) Calcular tempo médio de estadia de mensalistas; 2) Calcular o tempo médio de estaria de clientes não mensalistas




## Sugestões para o projeto

- Organizar a solução em projetos, 1) Projeto Teste; 2) Projeto API; 3) Projeto de Dominio 
- Valores (`PrecoTotal`) deve ser arredondado para baixo utilizando duas casas decimais, sempre que possível.





## Bônus

- __Autenticação__ Implementar autenticação garantindo que apenas usuários logados consigam acessar as APIs.
- __Autorização__ Garantir que apenas usuários associados a uma garagem tenha acesso aos dados daquela garagem específica.
- __Cache__ Verificar se a consulta já foi feita anteriormente e obter o resultado a partir do `Blob Storage` ao invés do `SQL Server`
- __Testes__ Testes unitários



## Finalizando


Quando seu código estiver pronto, compartilhe via Github com o usuário: `backoffice.garagens` e envie um email para `backoffice.garagens@gmail.com`




## Referencias

- [Entity Framework](https://learn.microsoft.com/pt-br/ef/)
- [Dapper](https://dappertutorial.net/)
- [Docker](https://docs.docker.com/)
    - [docker compose up](https://docs.docker.com/engine/reference/commandline/compose_up/)
- [Azure Storage Emulator](https://learn.microsoft.com/en-us/azure/storage/common/storage-use-emulator)
    - [Azurite](https://learn.microsoft.com/en-us/azure/storage/common/storage-use-azurite?tabs=docker-hub)
    - [Storage Explorer](https://azure.microsoft.com/pt-br/products/storage/storage-explorer/)