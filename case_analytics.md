# Case: Estudo de rentabilidade

## Parte 1 - Análise

A planilha em anexo contém dados fictícios de cerca de 5 mil clientes. Nela você vai encontrar dados transacionais de alguns meses, assim como as receitas e custos associados a esse cliente nos respectivos meses. Além disso, também existem informações cadastrais, tais quais a cidade em que ele atua, seu MCC (Merchant Category Code), seu canal de vendas, e quando ele entrou na empresa.

A partir desses dados, faremos um estudo para indicar quais os diferentes perfis de clientes, e listar algumas estratégias que podemos adotar com relação a cada perfil para melhorar a lucratividade da empresa no curto, médio, e longo prazo.

Como uma empresa de receita recorrente, um dos principais indicadores de rentabilidade de um cliente é o tempo esperado que o cliente use o nosso produto. Isso está associado ao Índice de evasão de clientes de um mês para outro, o que chamamos de "Churn".

O Índice de evasão mensal (ou "churn") no mês de novembro, por exemplo, pode ser calculado como:


            [Churn do mês de novembro] = [Número de clientes inativos* em novembro que estavam ativos* em 
            outubro] / [Número de clientes ativos* em outubro];


* Pode-se considerar um cliente ativo como aquele que fez ao menos uma transação no mês de referência. Consequentemente, inativo é aquele que não fez nenhuma transação.


Generalizando, para um determinado mês "M", com relação ao mês anterior "M-1".

            [Churn de "M"] = [Número de clientes que não transacionaram em "M", mas que transacionaram em "M-1”] 
            / [Número de clientes que transacionaram em "M-1"];


A partir do índice de evasão mensal, pode-se estimar o tempo médio que um cliente fica ativo, que chamamos de "Tempo de vida médio", como:

            [Tempo de vida médio, em meses] = 1 / [Churn]


Naturalmente, outro indicador de rentabilidade muito importante é o lucro médio por cliente nos meses em que o cliente esteve ativo, em consequência a receita e custo desse cliente.


### A partir dos dados fornecidos:


 - Utilizando alguma técnica de clusterização da sua escolha, identifique diferentes perfis de clientes, apontando, para cada grupo: a receita, o custo, o lucro, índice de evasão e tempo de vida médio. Como você descreveria qualitativamente os perfis traçados? (Ex. "Clientes de alto faturamento", "Clientes do ramo de alimentação" etc.).

 - Assumindo que o custo da atividade comercial (campanhas de marketing, comissão de vendedores) para adquirir um novo cliente varie unicamente com o "canal", quais perfis de cliente você indicaria a empresa ter mais foco em vendas (novos clientes), visando o resultado de longo prazo? Consequentemente, em qual o "canal" devemos focar (escolha um)?

[Tabela para consulta](https://gist.github.com/Isabelarrodrigues/0060f97128c4304111c6c1f68531163d#gistcomment-3396413)


- Pensando agora nos clientes que já contrataram o produto, em que canal de clientes você focaria os esforços para aumentar a rentabilidade (escolha um)? Que estratégias você adotaria para alcançar esse ganho de rentabilidade?

- A partir das suas conclusões sobre as perguntas anteriores, faça um forecast de Receita e Lucro da empresa para os próximos 3 meses. Assuma que as premissas de crescimento de vendas e rentabilização dos clientes sigam a tabela abaixo de acordo com os canais escolhidos nas perguntas anteriores:

[Tabela para consulta](https://gist.github.com/Isabelarrodrigues/0060f97128c4304111c6c1f68531163d#gistcomment-3396415)


Assuma que as únicas linhas de Receita e Custo que incidem sobre o valor transacionado são as de MDR e Pré-pagamento e que essas linhas variem linearmente com o valor transacionado.

Realize a análise e monte uma apresentação com ferramentas de sua escolha, mostrando sua linha de raciocínio, premissas e recomendações.


### Dicas:

- Existe muita informação sobre o mercado de adquirência e sobre a Stone na internet, pesquise! Sugestão de material: releases de resultado da Stone e concorrentes (IPO filing e releases trimestrais), notícias em geral.

- Pesquise também sobre o fluxo de pagamentos e receitas em uma adquirente, isso ajuda a entender os dados da planilha.

<br />
<br />
 

## Parte 2 - Questões de lógica SQL

Imagine que a tabela do google sheets, usada na primeira parte do desafio, seja uma cópia fiel de uma tabela do banco de dados da Stone chamada *"clientes_custos_receitas"* .
Também considere que as colunas nomeadas na planilha refletem as colunas da tabela, que por sua vez estão em ***snake_case***.
Ex:

        Nome na Planilha: Quantidade de Transações 
        Nome na Tabela:   quantidade_de_transacoes

### Usando a linguagem ***standard SQL*** escreva a lógica de uma query que:

1) Conte o número de cidades distintas em que cada tipo de canal de venda atua.

2) Retorna a soma da margem final por cidade e ano de apuração de clientes que não entraram pelo 'Canal 1'.

3) Retorne os 10 clientes com maior média de ***net_mdr*** para o último trimestre de 2021.

4) Retorne para cada ***numero_do_cliente*** e mês de apuração o ***volume_transacionado*** naquele mes e o quanto esse volume representa em percentual 
em relação ao volume total histórico que esse mesmo cliente transacionou.
Ex: Para um cliente de código 12345 que só teve 3 registros na tabela, a query retornaria os seguintes resultados:

```
      numero_do_cliente | data_apuracao | Total Transacionado no mes | %
      12345             |  '2021-01-01' |           100              | 20%
      12345             |  '2021-02-01' |           250              | 50%
      12345             |  '2021-03-01' |           150              | 30%
```
