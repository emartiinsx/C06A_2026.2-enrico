Enrico Lima Martins Pereira
GES
595

IA utilizada: Gemini

Prompts usados:

"Analise o exercicio a seguir e use os power points das aulas como base para me explicar detalhadamente o que preciso fazer e como posso fazer"

Resposta obtida:

"Para resolver o exercício da loja PC Mania, você precisará construir um sistema em Java aplicando os conceitos de Programação Orientada a Objetos abordados em aula. Abaixo está um guia detalhado do que deve ser feito e como conectar os requisitos aos conteúdos dos slides:

**1. Organização do Projeto (Pacotes)**

* O exercício exige que você organize o seu código utilizando pacotes.


* Como visto na Aula 06, os pacotes no Java funcionam como diretórios para organizar seus arquivos de código.


* Você deve criar pacotes usando a convenção de nome invertido da empresa/instituição (por exemplo, `br.inatel.cdg.pcmania`) e salvar todas as classes do projeto dentro dessa estrutura.



**2. Criação das Classes e Encapsulamento**

* Baseando-se no diagrama UML fornecido, você deve criar as classes: `Cliente`, `Computador`, `HardwareBasico`, `SistemaOperacional` e `MemoriaUSB`.


* A regra do exercício é clara: **todos os atributos de todas as classes devem ser privados** (`private`). A Aula 07 explica que o modificador `private` encapsula a classe, escondendo os detalhes da implementação e garantindo que apenas a própria classe altere seu estado diretamente.


* Consequentemente, você deve criar os métodos *getters* e *setters* **apenas se for estritamente necessário** expor ou alterar uma variável de fora da classe, pois a criação inútil de *getters/setters* resultará em perda de pontos.


* Você também deve criar construtores em todas as classes para inicializar as variáveis corretamente.



**3. Modelando os Relacionamentos e Arrays**

* O diagrama UML exibe relacionamentos de Composição (losango preenchido) entre o `Computador`, o `HardwareBasico` e o `SistemaOperacional`. Segundo a Aula 04, a Composição significa que essas instâncias são parte integrante do computador e devem ser criadas e gerenciadas por ele (a existência das partes não faz sentido sem o "todo").


* A relação com `MemoriaUSB` é uma Agregação (losango vazio), onde o objeto é vinculado externamente através do método `addMemoriaUSB`.


* O cliente pode realizar a compra de vários computadores (indicado por `2..*` no UML). Como o uso de bibliotecas como o `ArrayList` é proibido, você deve declarar um Array tradicional de objetos `Computador` dentro do `Cliente`.


* Ao percorrer esse Array de objetos usando um `for` ou `for-each` para calcular os valores ou imprimir os dados, é fundamental verificar primeiro se a posição atual possui um objeto ou se é igual a `null`, para não gerar falhas na execução.



**4. Lógica de Menus e Promoções**

* O sistema não pedirá que o usuário digite peças e nomes. Todos os dados de configuração das Promoções 1, 2 e 3 (como "Core i5", "8 Gb", "macOS Sequoia") devem ser criados e preenchidos de forma estática pelo seu código.


* Os nomes das peças de hardware básico serão seus tipos (ex: "Processador", "Memória RAM") e a capacidade será o seu valor em `int` (ex: 2200, 8).


* Os preços dos PCs são derivados exclusivamente da sua matrícula: o PC da Promoção 1 custa o exato valor da matrícula, o da Promoção 2 custa matrícula + 1, e o da Promoção 3 custa matrícula + 2.


* A interface com o usuário ocorrerá apenas para a seleção da compra. Como abordado na Aula 03, você deve importar o pacote `java.util.Scanner` para efetuar a leitura dos dados do teclado.


* Utilize uma estrutura de laço como `while` ou `do-while` para manter a interface de compra repetindo até o momento que o cliente digite o código de saída (0).


* Dentro do laço, use blocos de seleção `switch-case` para tratar os códigos 1, 2 ou 3. Em cada caso, instancie o respectivo computador da promoção e adicione-o ao array de compras do `Cliente`.



**5. Classe Utilitária e Fechamento**

* Após o usuário digitar 0 para encerrar as compras, o seu sistema deve invocar os métodos necessários para imprimir as informações do cliente, a lista detalhada de PCs que ele comprou e o valor total devido.


* Crie uma classe adicional separada chamada `ProcessarPedido`. Nela, crie um método utilitário (helper) que receberá o array de computadores do cliente por parâmetro e executará a impressão da mensagem "Pedido enviado...".



**6. Padrões de Entrega**

* Finalizado o código, o envio deve ser feito por meio do link de um repositório público.


* No arquivo README do repositório, você precisará preencher seus dados de identificação, como a sua matrícula, seu nome, Enrico, e o seu curso, Engenharia de Software.


* Se você utilizar o auxílio de alguma inteligência artificial para realizar o trabalho, o README deverá obrigatoriamente descrever os prompts utilizados, qual foi o modelo de IA empregado e se o resultado obtido com ela foi satisfatório."

Segundo Prompt:

"Agora gere um codigo exemplo para este exercicio e me explique passo a passo a construção do código"

Reposta obtida:

"A compreensão de cada classe do sistema é fundamental para consolidar a aplicação prática dos conceitos de Programação Orientada a Objetos no desenvolvimento de software. Abaixo está o detalhamento técnico do funcionamento de cada bloco de código estruturado.

**Classes Base: HardwareBasico, SistemaOperacional e MemoriaUSB**

* **Encapsulamento Estrito:** Todos os atributos (como `nome`, `capacidade`, `tipo`) são declarados como `private`. Isso impede que outras partes do sistema alterem os dados diretamente, protegendo o estado interno de cada componente.
* **Construtores Obrigatórios:** Não há construtores vazios. Quando uma dessas classes é instanciada, é obrigatório passar os valores iniciais (ex: `new MemoriaUSB("Pen-drive", 16)`). Isso garante que nenhum componente exista sem suas definições fundamentais.
* **Acesso Controlado:** Os métodos `get` (como `getNome()`) servem exclusivamente para permitir a leitura controlada desses dados no momento em que o recibo for impresso na tela.

**Classe Computador**

* **Relação de Composição:** No construtor da classe `Computador`, o objeto `SistemaOperacional` e o array `HardwareBasico` recebem o comando `new` internamente. Isso cria uma dependência existencial: a memória RAM e o Windows não existem soltos no sistema; eles são criados no exato momento em que o PC é fabricado e seriam destruídos se o objeto do PC fosse apagado da memória.
* **Relação de Agregação:** O método `addMemoriaUSB(MemoriaUSB musb)` recebe um objeto que foi criado externamente. O pen-drive é um periférico independente acoplado ao computador.
* **Prevenção de Falhas (`mostraPCConfigs`):** O laço `for` varre o array de hardware. A verificação `if (hw != null)` é crucial para evitar um erro de `NullPointerException` caso o computador tenha espaços vazios no array de peças.

**Classe Cliente**

* **Gerenciamento de Array:** O cliente possui um array tradicional `Computador[] pcs = new Computador[10]`. Como o uso de coleções dinâmicas está restrito, o tamanho 10 atua como um limite físico de itens no carrinho.
* **Inserção Segura (`adicionarCompra`):** Um laço de repetição percorre o array procurando a primeira posição `null` (vazia). Assim que encontra, insere o objeto `Computador` recém-comprado e executa um `break` para interromper o laço imediatamente, evitando duplicidades.
* **Cálculo Financeiro (`calculaTotalCompra`):** Acumula o valor retornado pelo método `getPreco()` de cada posição ocupada do array de computadores, resultando no valor devido.

**Classe ProcessarPedido**

* **Método Estático:** A declaração `public static void` permite que a função `enviarPedido` seja chamada diretamente pelo nome da classe (`ProcessarPedido.enviarPedido()`), sem a necessidade de instanciar um objeto `ProcessarPedido` com o comando `new` previamente.

**Classe Main (Executável)**

* **Loop de Interface (`do-while`):** Mantém o menu de vendas rodando continuamente na tela do terminal. Só é interrompido quando a variável `opcao` recebe o valor `0`.
* **Instanciação via Switch-Case:** É o núcleo da lógica de negócios. Para cada opção escolhida (1, 2 ou 3), o código aciona os construtores das classes passando os dados exatos (strings e números inteiros/flutuantes) previstos nas tabelas de promoção, incluindo a variável `matricula` para a definição dos preços.
* **Validação Final:** Ao encerrar o laço, um bloco `if` verifica se o total de compras é maior que zero antes de chamar os métodos de impressão de recibo, evitando a exibição de notas fiscais vazias."

Codigo gerado é semelhante ao enviado, porém, com comentários sobre a construção do código.



Achei que a resposta obtida pela IA foi satizfatória pos consegui entender alguns conceitos mais abstratos sobre a matéria de POO e isso fez com que eu sanasse práticamente todas as minhas dúvidas. 
