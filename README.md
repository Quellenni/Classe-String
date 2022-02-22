## java.lang.String 
É utilizada para representar textos através de uma cadeia de caracteres,
todos literais em string são implementados com essa classe no Java, após atribuídos não
podem ser alterados.

**Alternativas de instanciação de objetos com construtor ou métodos singleton:**

Utilizando construtor para instanciar um Objeto String: String texto = **new**

String("Instanciando um novo objeto tipo String");

Utilizando método Singleton para Instanciar :

A implementação consiste em um construtor privado e um campo para armazenar seu
resultado, além de um método de acesso estático com o nome **getInstance()**.

O campo privado pode ser atribuído de dentro de um bloco inicializador estático ou usando
um inicializador. O método **getInstance()**, que deve ser público, retorna a esta instância.

public class Singleton {

private static Singleton singleton = new Singleton();

//Um construtor privado impede que a classe seja instanciada

private Singleton() {}

public static Singleton getInstance() {

return singleton;

}

// Método protegido pela instância da classe

protected static void imprimeMensagem() {

String mensagem = "Hello Word";

System.out.println (mensagem);

}

}

Para executar o método **imprimeMensagem()**, que está protegido na classe Singleton,
devemos pegar uma instância da classe para poder ter acesso:


public class ExemploSingleton {

public static void main (String [] args) {

Singleton singleton = Singleton.getInstance ();

singleton.imprimeMensagem();

}

}


O resultado da execução acima será: “Hello, Singleton” e toda vez que o método for
executado, a JVM utilizará a mesma instância da classe para responder e nenhum novo
objeto do tipo será instanciado.


**Métodos:**

a) compareToIgnoreCase(String exemplo) - Método compara duas strings ignorando
se é maiuscula ou minuscula. Retorna um int sendo 0 verdadeiro -1 falso;

b) format(String exemplo, “argumento”) - Método formata a string a partir de
argumentos, retorna o valor do argumento a string

c) concat(String exemplo) - Método concatena a string especificada ao final da string
onde método foi chamado.

d) split(String exemplo ) - Método Divide esta string em várias substrings a partir de
um delimitador indicado pelo usuário;

**Método sobrecarregado:**

@Override
public String toString(){

return "Esse é meu objeto Random";

}

**Demonstração adaptando o uso dos métodos:**

- Verificação de Banco de dados : login.compareToIgnoreCase(String exemplo) -
Método compararia se o login corresponde a string que usei no ao logar site.
- Realizar cadastro no banco de dados: nome.format(String exemplo, “argumento”)
para atribuir um dados para operação do crud.
- Também no cadastro e banco de dados : nome.concat(sobrenome) para concatenar
nomes, endereço ou qualquer outra informação de cadastro;
- Caso eu tenha um cadastro e CPF e precise transformar as informações num array
posso usar o método split, basta aplicar o método Split da seguinte forma: cpf.split("
. ");



## StringJoiner
StringJoiner é usado para construir uma sequência de caracteres separados por um _delimitador_ e, opcionalmente, começando com um _prefixo_ fornecido e terminando com um _sufixo_ fornecido.

_Delimitador_ a sequência de caracteres a ser usada entre
cada elemento adicionado ao valor StringJoiner
_Exemplo:_ ( " , "  )

_Prefixo_  a sequência de caracteres a ser usada no início _Exemplo:_ ( " [ ")

_Sufixo_ a sequência de caracteres a ser usada no final   _Exemplo:_( " ] " )

![Captura_de_tela_de_2022-02-22_11-51-10 readme](https://user-images.githubusercontent.com/86434650/155159138-bd63975a-e13e-4db5-8330-d4cc302473e7.png)



**CONSTRUTORES:**

**StringJoiner (CharSequence delimiter)**
Constrói um StringJoiner sem caracteres, sem prefixo ou sufixo e uma cópia do delimitador fornecido.

**StringJoiner(CharSequence delimiter, CharSequence prefix, CharSequence suffix)** Constrói um StringJoiner sem caracteres usando cópias do prefixo, delimitador e sufixo fornecidos.

Exemplos:

A String " [ Miguel:Pedro]" pode ser construída da seguinte forma:


>StringJoiner nome  = new StringJoiner( ":" , "[" ,"]");
>
>nome.add("Miguel");
>
>nome.add("Pedro");

**Saída:**
>[Miguel:Pedro]




**MÉTODOS:**

__toString()__
é usado para converter StringJoiner em String. Ele retorna o valor atual, consistindo no prefixo, os valores adicionados até agora separados pelo delimitador e o sufixo, a menos que nenhum elemento tenha sido adicionado.

>Sintaxe:
public String toString()


Retorna: Este método retorna a representação de string deste StringJoiner.

import java.util.StringJoiner;

    public class testes {
        public static void main(String[] args) {

        StringJoiner nome  = new StringJoiner(",","[","]");
            
            nome.add("Miguel");
            nome.add("Pedro");

            System.out.println("Nomes: "
                    + nome.toString());


**Saída:**
>Nomes: [Miguel,Pedro]




__merge()__
adiciona o conteúdo do StringJoiner fornecido sem prefixo e sufixo como o próximo elemento se não estiver vazio. Se o StringJoiner fornecido estiver vazio, a chamada não terá efeito.


>Sintaxe:
public StringJoiner merge(StringJoiner other)



Parâmetros: Este método aceita um parâmetro obrigatório outro que é o StringJoiner cujo conteúdo deve ser mesclado com este

Retorna: Este método retorna este StringJoiner

Exceção: este método lança **NullPointerException** se o outro StringJoiner for nulo

import java.util.StringJoiner;

    public class testes {
        public static void main(String[] args) {

          StringJoiner nome  = new StringJoiner(",","[","]");

            nome.add("Miguel");
            nome.add("Pedro");

            System.out.println("Nomes: "
                    + nome.toString());

            // criamos uma nova cadeia de caracteres
            StringJoiner country = new StringJoiner(",","{","}");
            country.add("Peru");
            country.add("Brasil");

            System.out.println("Cidades: "
                    + country.toString());

            // Podemos mesclar dois joiners usando merge().
            
            StringJoiner merged = nome.merge(country);

            System.out.println(merged.toString());


        }

    }

**Saída:**

>Nomes: [Miguel,Pedro]
>
>Cidades: {Peru,Brasil}
>
>[Miguel,Pedro,Peru,Brasil]




__lenght()__
é usado para descobrir o comprimento do StringJoiner em caracteres. Ele retorna o comprimento da representação String deste StringJoiner.


import java.util.StringJoiner;

    public class testes {
        public static void main(String[] args) {

           StringJoiner nome  = new StringJoiner(",","[","]");
            
            nome.add("Miguel");
            nome.add("Pedro");

            System.out.println("Nomes: "
                    + nome.toString());

            System.out.println(nome.length());

**Saída:**

>Nomes: [Miguel,Pedro]
>
>14




**REFERÊNCIAS:**

* [Documentação Oracle](https://docs.oracle.com/javase/8/docs/api/java/util/StringJoiner.html#toString--)

* [Site Acervo Lima](https://acervolima.com/java-util-stringjoiner-em-java8/)




