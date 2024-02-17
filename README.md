# IntroDatabases
Portfolio de projetos durante a aprendizagem de sistemas de gerenciamento de banco de dados

1o. Projeto -- Refinar um modelo ER de um E-Commerce.

Foi desenvolvido diagrama no MySQL Workbench do modelo desenvolvido durante o curso.
O objetivo foi refinar o modelo ao acrescentar entidades ao modelo. 
"Para modelar um banco de dados para uma plataforma de E-Commerce, foram estabelecidas
algumas entidades e relacionamentos básicos.
Objetivo é refinar o modelo apresentado acrescentando os seguintes pontos:
Cliente PJ e PF – Uma conta pode ser PJ ou PF, mas não pode
ter as duas informações;
Pagamento – Pode ter cadastrado mais de uma forma de pagamento;
Entrega – Possui status e código de rastreio;
"

Proposta de solução do 1o. Projeto:
Mapear clientes separando CPF de CNPJ?
A opção ideal seria criar uma especialização de entidades, 
ao definir as entidades ClienteCPF e ClienteCNPJ. Eles
herdam os dados Nome, Endereço da superentidade Cliente.
Será feito de forma correspondente ao feito no exemplo da Universidade.
Foi usada a "New 1:1 Non-identifying Relationship" para replicar o exemplo
da Universidade, apesar de não ter ficado claro a razão da escolha. O
atributo Identificação no Ente original Cliente será suprimido, e serão
criadas subclasses de cliente como CNPJ e CPF, mutuamente excludentes.

Informação Entrega é atributo de alguma entidade ou é nova entidade?
Para um pedido ser completado, tem que ser feito, pago,
entregue ao endereço do cliente. Depois disso, deve passar o periodo 
de carência para devolução de produto. Será definido que a entrega 
será uma nova entidade, porque ele existirá apenas depois de o estado 
de pagamento for "pagamento concluído". Além disso, a entidade 
Entrega tem como atributos o status de entrega (aguardando envio, 
enviado, entregue, aguardando devolução e devolvido) e de devolução
de parte ou todos os produtos do pedido, se for o caso

E sobre as formas de pagamento, foi decidido modelar essa informação
como atributo de cada cliente, pois trata-se de informação exclusiva de
cada cliente. Além disso, será possível cadastrar até 3 formas diferentes 
de pagamento, para que seja possível manter uma quantidade de 
informação razoável sobre o cliente.
