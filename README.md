## StringJoiner
StringJoiner é usado para construir uma sequência de caracteres separados por um _delimitador_ e, opcionalmente, começando com um _prefixo_ fornecido e terminando com um _sufixo_ fornecido.

_Delimitador_ a sequência de caracteres a ser usada entre
cada elemento adicionado ao valor StringJoiner
_Exemplo:_ ( " , "  )

_Prefixo_  a sequência de caracteres a ser usada no início _Exemplo:_ ( " [ ")

_Sufixo_ a sequência de caracteres a ser usada no final   _Exemplo:_( " ] " )




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




