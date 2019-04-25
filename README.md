# Efective-java

Exemplos dicas sobre o livro Effect Java 3

## Evitar métodos/costrutor com muitos parâmentros.

 - Build deve validar se todos os parâmetros foram informados
 - Valores obrigatórios, devem estar no construtor.
 - Cada atributo retorna this.
 - Utilizar valor default dentro do builder.

### Pasta exemplo:

### Exemplo:

Problema:

calcular(String id, String numemp, String tipCol, String numCad, LocalDate dataInicial, LocalDate dataFinal,Boolean enviarEmail, Boolean gerarPendencia);

Solução:

CalcularParametros parametros = new CalcularParametros(LogId)
parametros.numEmp(1).tipCol(2).numCad(3).build();

calcular(calcularParametros);
