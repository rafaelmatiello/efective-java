# Efective-java

Exemplos dicas sobre o livro Effect Java 3

## Preferir contrutores staticos
 + Não necessáriamente precisa criar um objecto toda vez que for invocado, pode usar cache se for imutavel.
 + Pode retornar qualquer subtipo ou implementação;
 + Permite variar a quantidade de parâmetros informados, assim decidir qual a melhor implementação retornar.
 + Permite centralizar as criações, como o DriverManger.getConnection(), DriverManager.registerDriver.
 
 - Não é possível ter um contrutor privado em um subclasse, 
 - Difícil entrar as referências como criar as classes e também o padrão para nomes de criação de classes.
 
### Pasta exemplo:

<incluir exemplo>

### Exemplo:

 - Date.from() 
 - EnumSet.of()
 - Boolean.valueOf()
 - X.getInstance()
 - Array.newInstance()
 - Collections.list()


## Evitar métodos/costrutor com muitos parâmentros.

 + Build deve validar se todos os parâmetros foram informados
 + Valores obrigatórios, devem estar no construtor.
 + Cada atributo retorna this.
 + Utilizar valor default dentro do builder.
 + Os parâmetros devem ser imutaveis.
 

### Pasta exemplo:

<incluir exemplo>

### Exemplo:

Problema:
```java
BO.calcular(String id, String numemp, String tipCol, String numCad, LocalDate dataInicial, LocalDate dataFinal,Boolean enviarEmail, Boolean gerarPendencia);
```

Solução:
```java
// dataFinal = hoje;
// dataInicial = hoje;
// enviarEmail = false;
// gerarPendencia = false;


CalcularParametros parametros = new CalcularParametros(String id, String numemp, String tipCol, String numCad);
parametros.dataInicial('').enviarEmail(false).build();

calcular(calcularParametros);
```

## intem 3 -Singletons

 - Singletons são dificeis de testar.
 - Prefira métodos como getInstance() a disponibilizar public static, evita alteração de instancia.
 - Facilidade se precisar alterar a implementação.
 - cuidado com serialização de dados de singleton, se não for serializar colocar transient, 
 - Enum com um único item é a melhor forma de implementar um singleton,
 
 ### Pasta exemplo:
 
 public enum Elvis {
   INSTANCE;
   public void leaveTheBuilding() { ... }
   }
 }
 
 
 ## Item 4 - Construtor privado
  - bom para utilizar em classe que não podem ser instanciadas, como utilitários.
  - gerar uma exception caso alguém tentar utilizar o construtor indevidamente.
  
 ## pasta exemplo:
 
 // Noninstantiable utility class
public class UtilityClass {
// Suppress default constructor for noninstantiability
private UtilityClass() {
throw new AssertionError();
}
... // Remainder omitted
}
 
 
  stop page 51.
 https://github.com/echoJava/book/blob/master/Java/Effective%20Java%2C%20Third%20Edition.pdf
