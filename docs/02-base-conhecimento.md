# Base de Conhecimento

## Dados Utilizados

Descreva se usou os arquivos da pasta `data`, por exemplo:

| Arquivo | Formato | Utilização no Agente |
|---------|---------|---------------------|
| `historico_atendimento.csv` | CSV | Contextualizar interações anteriores |
| `perfil_investidor.json` | JSON | Personalizar recomendações |
| `produtos_financeiros.json` | JSON | Sugerir produtos adequados ao perfil |
| `transacoes.csv` | CSV | Analisar padrão de gastos do cliente |

---

## Adaptações nos Dados

> Você modificou ou expandiu os dados mockados? Descreva aqui.

Não houve alteração nos dados. Foram utilizados os dados oferecidos no desafio.

---

## Estratégia de Integração

### Como os dados são carregados?
> Descreva como seu agente acessa a base de conhecimento.

Os dados serão carregados via código Python ao ler os arquivos CSV e JSON na pasta '''/data'''. Estes dados são estruturados de forma que não seja utilizados dados incompletos ou inúteis para a resposta final.

### Como os dados são usados no prompt?
> Os dados vão no system prompt? São consultados dinamicamente?

O prompt se divide em quatro camadas:
1. **System Prompt**: Define permanentemente o comportamento.
2. **Contexto da sessão**: São inseridas informações relevantes para aquela conversa.
3. **Dados recuperados**: Os dados necessários para responder à pergunta são consultados dinamicamente ao sistema de consulta do banco de dados.
4. **Processamento de resposta**: As informações obtidas são estruturadas da forma mais adequada a partir das características do agente definida no System Prompt.

---

## Exemplo de Contexto Montado

> Mostre um exemplo de como os dados são formatados para o agente.

```
Dados Cadastrais e Perfil:
- Nome: João Silva
- Perfil: Moderado
- Objetivo: Construir reserva de emergência - R$15.000,00 || Entrada do Apartamento - R$50.000,00
- Saldo disponível: R$15.000,00

Resumo Financeiro:
- Patrimônio Total: R$25.000,00
- Média de saída mensal: R$2.488,90
- Total de saída do último mês: R$2.112,85

Produtos Disponíveis para consulta:
- Tesouro Selic (risco baixo)
- CDB Liquidez Diária (risco baixo)
- LCI/LCA (risco baixo)
- Fundo Multimercado (risco médio)
- Fundo de Ações (risco alto)

Resumo de Consultas:
- Última Consulta (19/07/2026): Concluído (Dúvida sobre corte de gastos)

---------------------------------------------------------------------------
[MENSAGEM DO USUÁRIO]: "Quais os gastos impactaram mais na minha renda mensal durante o ultimo ano?"
```
