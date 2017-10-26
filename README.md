# Simulador de Renda Fixa Pré e Pós
Existem vários simuladores de Renda Fixa Pré e Pós fixados no mercado. Mas a maioria deles não tem as taxas atualizadas automaticamente ou não fazem a projeção do CDI futuro da maneira correta. Esse projeto foi criado pelos desenvolvedores da Easynvest, onde o objetivo é entregar um simulador de Renda Fixa para o mercado, projetando o CDI futuro com taxas atualizadas diretamente da Anbima.

![simulador easynvest](https://raw.githubusercontent.com/easynvest/simulador-rendafixa/40-screenshotsimulador/screenshot.png)

Você pode ver esse simulador funcionando aqui:
[https://easynvest.github.io/simulador-rendafixa/](https://easynvest.github.io/simulador-rendafixa/)

## Para rodar esse projeto
Execute o famoso
`npm install && npm start`
e tudo pronto para começar. :D


## Consumindo o serviço de cálculo
A API que calcula o os valores futuros se encontram em [outro projeto Open Source, aqui](https://github.com/easynvest/api-simulator-calc). Abaixo segue algumas informações sobre como utilizamos esse serviço no nosso simulador.

 - **URL**: https://easynvestsimulatorcalcapi.azurewebsites.net/calculator/simulate
 - **Method**: GET
 - **URL Params**:
    ```javascript
        investedAmount = 32323.0                 // Valor a investir em reais
        index = "CDI"                            // Índice, por enquanto só CDI disponível
        rate = 123                               // Percentual do papel
        isTaxFree = false                        // Isento de IR, por enquanto só falso
        maturityDate = "2023-03-03"              // Data do vencimento, no formato ano-mes-dia
    
    ```
 - **Response**
    ```javascript
    {
        "investmentParameter": {
            "investedAmount": 32323.0,                      // O valor a ser investido
            "yearlyInterestRate": 9.5512,                   // Rentabilidade anual
            "maturityTotalDays": 1981,                      // Dias corridos
            "maturityBusinessDays": 1409,                   // Dias úteis
            "maturityDate": "2023-03-03T00:00:00",          // Data de vencimento
            "rate": 123.0,                                  // Percentual do papel
            "isTaxFree": false                              // Isento de IR
        },
        "grossAmount": 60528.20,                            // Valor bruto do investimento
        "taxesAmount": 4230.78,                             // Valor do IR
        "netAmount": 56297.42,                              // Valor líquido
        "grossAmountProfit": 28205.20,                      // Rentabilidade bruta
        "netAmountProfit": 23974.42,                        // Rentabilidade líquida
        "annualGrossRateProfit": 87.26,                     // Rentabilidade bruta anual
        "monthlyGrossRateProfit": 0.76,                     // Rentabilidade bruta mensal
        "dailyGrossRateProfit": 0.000445330025305748,       // Rentabilidade bruta diária
        "taxesRate": 15.0,                                  // Faixa do IR (%)
        "rateProfit": 9.5512,                               // Rentabilidade no período
        "annualNetRateProfit": 74.17                        // Rentabilidade líquida anual
    }
    ```

# Lint
Nós usamos o ESLint para apontar erros de padrão de escrita no JS. Para rodar o teste, execute o comando `npm run lint`.

# Contribuindo
Fique à vontade para contribuir da maneira que for, seja escrevendo issues ou clonando o projeto para submeter Pull Requests.

Se você for escrever código, por favor, preste atenção aos detalhes do `.editorconfig` e do padrão de JS descrita nas regras do `eslinrc`.

Se você encontrar um problema e se empolgar para fazer um Pull Request, por favor, crie uma Issue para que seu Pull Request fique atrelado à ele, assim teremos um histórico saudável de problemas reportados + soluções enviadas.

# Licença - Apache 2.0
Esse projeto é OpenSource e aberto para qualquer um contribuir sob a licença *Apache 2.0*, que é compatível com a licença GPL de software livre.

Copyright 2017 Easynvest - Título Corretora de Valores SA, inscrita sob o CNPJ 62.169.875/0001-79

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
