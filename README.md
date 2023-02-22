# ApplicationInsights-Queries-PaisRegiao

// Documentação sobre Kusto Query Language https://docs.microsoft.com/en-us/azure/data-explorer/kusto/query/

// Query com quantidade de requisições por país/região de origem,

// incluindo o uso de Alias para os campos de retorno
requests

  | summarize Qtde=count() by AreaOrigem=client_CountryOrRegion

// Gráfico do tipo pizza com requisições por país/região origem
requests

  | summarize Qtde=count() by CidadeOrigem=client_CountryOrRegion 

  | render piechart

# ApplicationInsights-Queries-CidadeOrigem

 // Query simples com quantidade de requisições por cidade de origem
requests

  | summarize count() by client_City 

// Query com quantidade de requisições por cidade de origem,

// incluindo o uso de Alias para os campos de retorno
requests

  | summarize Qtde=count() by CidadeOrigem=client_City 

// Gráfico do tipo pizza com requisições por cidade origem
requests

  | summarize Qtde=count() by CidadeOrigem=client_City 
  
  | render piechart

# ApplicationInsights-Queries-Containers

// Query simples com quantidade de requisições por container
requests

  | summarize count() by cloud_RoleInstance 

// Query com quantidade de requisições por container,

// incluindo o uso de Alias para os campos de retorno
requests
  
  | summarize Qtde=count() by Container=cloud_RoleInstance 

// Query com quantidade de requisições e tempo médio de resposta por container,
 
// incluindo o uso de Alias para os campos de retorno
requests

  | summarize Qtde=count(), TempoMedio=avg(duration) by Container=cloud_RoleInstance 

// Gráfico do tipo pizza com requisições por container
requests

  | summarize Qtde=count() by Container=cloud_RoleInstance 

  | render piechart
