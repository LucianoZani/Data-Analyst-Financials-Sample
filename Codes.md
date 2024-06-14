# Tabela Calendário Dinâmica
## Construída em liguagem M no Power Query
- Retorna a data mais antiga de uma coluna. Após a criação,  mo editor avançado, renomear a função para DateMin 
```
= List.Min(financials[Date])
```
- Retorna a data mais atual de uma coluna. Após a criação, renomear a função mo painel etapas aplicadas para DateMax
```
= List.Max(financials[Date])
```
- Retorna a quantidade de dias entre a data mínima e a data máxima, renomear no painel etapas aplicadas para QtdDays
 ```
= Duration.Days(DateMax-DateMin)+1
```
- Retorna uma lista com todas as datas iniciando pela mais antiga até a mais atual, neste caso, renomear é opcional.
```
= List.Dates(DateMin,QtdDays, #duration(1,0,0,0))
```
- modifica a lista em tabela. Lembre se trocar o "Personalizar1" caso tenha renomeado a lista no passo anterior
```
= Table.FromList(Personalizar1, Splitter.SplitByNothing(), null, null, ExtraValues.Error)
```
