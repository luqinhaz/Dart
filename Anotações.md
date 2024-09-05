# DART E FLUTTER

Anotações das aulas sobre Dar e Flutter.

## Tipos de Dados

- Number
    > Super tipo, aceita double ou int;

- String
    > Tipo que armazena cadeia de caracteres;

- Boolean
    > Tipo lógico (true ou false);

- Function
    > Trecho de código, processo, rotina responsável pela execução de uma tarefa;

- List
    > Arrays, variáveis com valores identificados através de index;

- Map
    > Estrutura similar ao List, porém com chave :valor;

- dynamic
    > Tipo de dados genérico, aceita valores de todos os outros tipos;

- var
    > Utilizado para criar variáveis sem tipo de dados definidos.

## Modificador de imutabilidade

- const e final
    > Tem o propósito de não permitir a alteração de uma variável, função, atributos e/ou métodos.

- static
    > Indica que um método ou atributo de uma classe é estático, ou seja, pode ser acessado sem uma instância de classe criada previamente.

## const X final

- const
    > Atribuição única para variáveis no momento da declaração da variável;

    > Não permite a declaração sem valor pré definido.

- final
    > Atribuição única para variáveis;

    > Permite a declaração sem valor pré definido

## Interpolation

    // BAD
    print(name + " " + lastname);

    // GOOD
    print('${name} ${lastname}');

    // PERFECT
    print('$name $lastname');

## Dart Null Safety

- Se bem aplicado previne o tão famoso: NullPointerException;

- Por padrão as variáveis não podem ser nulas, ao menos que seja dito de forma explicita.

## Operadores

- ?
- ??
- ??=
- ...?

## Exemplos

    String? name;
    print(name);

    ------------------------------------------------

    Class Client {
        String? name;

        String? getName() {
            return name?.toUpperCase();
        }
    }

    void main() {
        var client = Client();
        name = "Lucas";
        print(client.name);
    }

    ------------------------------------------------
    ## Validação para não apresentar "null" ao usuário
    String? showName(String? name) {
        return name ?? "Nome não definido";
    }

    void main() {
        print(showName(null));
    }

    ## Validação mais simples para print
    String? text;
    print(text ?? "sem texto");

    ------------------------------------------------

    ## Spreed Operator

    void main() {
        List? list1 = ["b", "c", "d"];
        List? list2 = ["a",...list1, "e", "f"];

        print(list1);
        print(list2);

        Map? m1 = {"name":"John", "age": 21};
        Map? m2 = {"birthday":"1989-05-10", "weight": 89.9, ...m1};

        print(m1);
        print(m2);
    }

## Métodos

- Ação
    > Métodos que não tem retorno, apenas executam ação determinada.

- Retorno
    > Métodos que executam determinada ação e após, retornam algum valor para quem chamou o método.

### Arrow Function

- Com a utilização de arrow function, conseguimos simplificar métodos de retorno único com declaração em apenas 1 linha.

> Exemplo com chaves:

    showName() {
        return "Lucas";
    }

> Exemplo com arrow:

    showName() => "Lucas";

### Parâmetros Opcionais

> Não nomeados: [ ]

    // Parâmetros opcionais não nomeados
    String getName(String name, [String? lastname]) {
        return '$name ${lastname ?? ""}';
    }

    void main() {
        print(getName("Lucas", "Maia"));
        print(getName("Lucas"));
    }

> Nomeados: { }

    // Parâmetros opcionais nomeados
    String getName(String name, {String? lastname}) {
        return '$name ${lastname ?? ""}';
    }

    void main() {
        print(getName("Lucas", lastname: "Maia"));
        print(getName("Lucas"));
    }

### Programação Assíncrona

#### async

> Determina que uma função retornará algo de forma assíncrona, ou seja, o aplicativo pode continuar a execução de outras tarefas sem precisar esperar pelo retorno.

#### await

> O await serve para indicar para a aplicação que ela deve esperar até a conclusão da função, ou seja, não pode executar nenhuma tarefa enquanto a função não estiver concluída.

#### Future

> Determina que uma função retorna algo de forma assíncrona, ou seja, pode demorar para que esse retorno ocorra.

    void hello() => print("oi");
    void bye() => print("tchau");

    Future message() {
        final duration = Duration(seconds: 3);
        return Future.delayed(duration).then((value) => "Eita!");
    }

    void main() async {
        hello();

        await message().then((status) {
            print(status)
        });
    }

    ------------------------------------------------

        -- Sem usar o async
        void main() {
        hello();

        message().then((status) {
            print(status)
        });
    }

### Class hero

    class Hero {
        String? name;
    }

    void main() {
        final hero = Hero();

        hero.name = "Lucas";
    }
