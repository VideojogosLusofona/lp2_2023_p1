<!--
Projeto 1 de Linguagens de Programação II 2023/24 (c) by Nuno Fachada

Projeto 1 de Linguagens de Programação II 2023/24 is licensed under a
Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License.

You should have received a copy of the license along with this
work. If not, see <http://creativecommons.org/licenses/by-nc-sa/4.0/>.
-->

# Projeto 1 de Linguagens de Programação II 2023/24

## Introdução

Os grupos devem implementar, em Unity 2022.3 LTS, um gestor de inventário
multi-nível para posterior utilização num jogo RPG.

O projetos têm de ser desenvolvidos por **grupos de 2 a 3 alunos** (não são
permitidos grupos individuais). Até **31 de outubro** é necessários que:

* Indiquem a composição do grupo.
* Indiquem o URL do repositório **privado** do projeto no GitHub.
* Convidem o [docente][Nuno Fachada] para ter acesso a este mesmo repositório
  privado.

Os projetos serão automaticamente clonados às **23h00 de 19 de novembro** sendo
a entrega feita desta forma, sem intervenção dos alunos. Repositórios e/ou
projetos não funcionais nesta data não serão avaliados.

## Funcionamento da aplicação

### Resumo

A aplicação deve (1) abrir um ficheiro indicando os conteúdos do inventário, (2)
mostrar o inventário no ecrã, e (3) permitir que o utilizador selecione um item
de modo a mostrar mais informação sobre o mesmo.

### Detalhes

#### Items

Os itens tem três características obrigatórias (podem ter mais para efeitos de
_game design_ e visualização, embora isso não seja obrigatório):

* _Name_
* _Type_
* _Weight_
* _Value_

Existem dois tipos gerais de items:

* _Action items_
* _Container items_
  * Além das três características anteriores, os _container items_ têm uma
    característica _MaxWeight_, que indica o peso máximo que podem transportar
    (além do seu próprio peso).

##### _Action Items_

O programa deve reconhecer os seguintes _action items_:

| Item               | Código no ficheiro | Type       | Weight | Value |
|--------------------|--------------------|------------|-------:|------:|
| Sword              | `sword`            | Weapon     | 5.5    | 10.3  |
| Axe                | `axe`              | Weapon     | 5.5    | 10.3  |
| Shield             | `shield`           | Apparel    | 7.0    | 8.6   |
| Ring of Protection | `ring_protection`  | Apparel    | 0.5    | 3.9   |
| Scroll of Attack   | `scroll_attack`    | Scroll     | 0.4    | 2.9   |
| Scroll of Defense  | `scroll_defense`   | Scroll     | 0.4    | 2.9   |
| Health potion      | `potion_health`    | Consumable | 0.5    | 4.8   |
| Food               | `food`             | Consumable | 0.8    | 3.5   |
| Water              | `water`            | Consumable | 0.5    | 1.0   |
| Coin               | `coin`             | Coin       | 0.3    | 1.0   |

##### _Container Items_

O programa deve reconhecer os seguintes _container items_:

| Item               | Código no ficheiro | Type      | Weight | Value | Max. Weight |
|--------------------|--------------------|----------:|-------:|------:|------------:|
| Pouch              | `pouch`            | Container | 0.2    | 0.6   | 8.0         |
| Bag                | `bag`              | Container | 0.8    | 1.9   | 16.5        |
| Backpack           | `backpack`         | Container | 2.3    | 4.9   | 24.8        |

#### Abrir ficheiro

A aplicação começa por pedir ao utilizador o ficheiro descrevendo o inventário.
Estes ficheiros devem ter a extensão `rpginv`. Por exemplo, `coisas.rpginv`,
`stuff.rpginv` ou `tralha.rpginv` são nomes válidos para ficheiros que descrevem
inventários. A secção [Formato dos ficheiros de inventário] contém mais detalhes
sobre o formato interno destes ficheiros.

Para simplificar, a aplicação procura apenas mapas na pasta `inventory` (tudo
em minúsculas), localizada no _Desktop_/ambiente de trabalho do utilizador
atual. Atenção que esta procura deve funcionar em qualquer computador e sistema
operativo. A aplicação apresenta ao utilizador uma lista rolável (_scrollable_)
com os ficheiros `rpginv` existentes nessa pasta, e o utilizador seleciona um
deles. Quem quiser fazer uma aplicação mais avançada, com bonificação na nota,
pode tentar usar um _asset_ como o [UnitySimpleFileBrowser] que consiga abrir
ficheiros `rpginv` em qualquer parte do disco.

#### Mostrar o inventário no ecrã

Após abrir um ficheiro válido, a aplicação mostra o inventário no ecrã na forma
de uma lista rolável, indicando o peso e o valor de cada item. Os _container
items_  devem ser mostrados (mas não os seus conteúdos), sendo que o respetivo
peso e o valor devem corresponder ao peso e valor do _container item_ **mais** o
peso e valor de todos os itens lá guardados.

<!-- A renderização de cada _tile_ pode ser feita com as _sprites_ básicas fornecidas
pelo Unity. Cada tipo de terreno deve ser representado por uma _sprite_ quadrada
cuja cor deve ser apropriada ao terreno em questão. Por cima da _sprite_ do
terreno devem ser colocadas as _sprites_ dos recursos existentes nesse _tile_.
Sugiro que usem _sprites_ do tipo círculo ou triângulo, cada uma representando
um recurso diferente (usem cores/formas para diferenciar entre recursos). Mesmo
que o _tile_ tenha todos os recursos possíveis, deve ser sempre visível a
_sprite_ de fundo que representa o tipo de terreno base.

Se tiverem tempo podem melhorar a apresentação e usar _tilesets_ gráficos mais
apelativos, embora isso não seja muito valorizado na nota final, uma vez que a
principal componente aqui a ser avaliada é a programação. Em qualquer dos casos,
deve ser sempre possível distinguir o terreno base e eventuais recursos nele
existentes.

Se o utilizador clicar num _tile_, deve ser apresentada informação detalhada
sobre o mesmo, como descrito na próxima secção. -->

#### Ver informação detalhada sobre um item

Ao clicar num _action item_ deve ser mostrado um painel de informação detalhado
sobre o mesmo...

O painel pode ser fechado pelo utilizador, voltando a aplicação a mostrar o
inventário.

Para os _container items_ ...

#### Funcionalidade futura

O UI da aplicação deve ter 5 botões, claramente marcados de 1 a 5. Ao clicar num
destes botões, deve aparecer um painel praticamente vazio, apenas com a mensagem
"For the future 1" para o botão 1, "For the future 2" para o botão 2, etc.

O painel pode ser fechado pelo utilizador, voltando a aplicação a mostrar o
mapa.

Esta funcionalidade será implementada individualmente para o Projeto 2, durante
a sessão de avaliação de _live coding_ agendada para dia 28 de novembro. Por
esta razão será muito difícil fazerem o Projeto 2 (_live coding_) caso não
tenham completado com sucesso este projeto.

Exemplos do tipo de perguntas que poderão surgir no Projeto 2 estão disponíveis
[aqui](livecoding.md).

#### Outros

<!-- * Poderá ser útil existir uma legenda relacionando as _sprites_ com os tipos
  de terreno e diferentes recursos que representam. -->
* A aplicação não deve _crashar_ com exceções, mas sim mostrar ao utilizador, de
  forma elegante, possíveis erros que possam ocorrer (por exemplo, na leitura do
  ficheiro caso este tenha um formato inválido, ou existam _container items_
  com peso superior ao seu _MaxWeight_).

### Formato dos ficheiros de inventário

O formato dos ficheiros é exemplificado pela seguinte amostra auto-explicativa:
<!--  (`<componente>` significa um componente
obrigatório e `[componente]` representa um componente opcional):-->

```text
weapon_sword
weapon_sword
container_backpack
    drink_health
    food
    pouch
        coin
        coin
        coin
food
scroll_defense
scroll_attack
pouch
    drink_water
    drink_water
    drink_health
    apparel_ring_protection
apparel_shield
```

A pasta `exemplos` contém alguns ficheiros de exemplo. Ficheiro cujo nome
termina em _invalid_ indicam ficheiros inválidos, ou porque contêm conteúdos
inválidos, ou porque algum item não-contentor contém outros items, ou porque
existe excesso de peso num dos itens contentores especificados. O UI deve
claramente indicar o erro concreto em cada um dos casos, e não _crashar_.

## Dicas e sugestões

### Organização do projeto e estrutura de classes

O projeto deve estar devidamente organizado, seguindo a fazendo uso de classes,
`struct`s e/ou enumerações, conforme seja mais apropriado. Cada tipo (i.e.,
classe, `struct` ou enumeração) deve ser colocado num ficheiro com o mesmo nome.
Por exemplo, uma classe chamada `Item` deve ser colocada no ficheiro `Item.cs`.
Por sua vez, a escolha da coleção ou coleções a usar também deve ser adequada
ao problema.

A estrutura de classes deve ser bem pensada e organizada de forma lógica,
fazendo uso de *design patterns* quando apropriado. Em particular, o projeto
deve seguir uma abordagem [MVC] (discutida em LP1, ver _slides_ do semestre
passado), e ser desenvolvido tendo em conta os princípios de programação
orientada a objetos, como é o caso, entre outros, dos princípios [SOLID].
Estes princípios devem ser balanceados com o princípio [KISS], crucial no
desenvolvimento de qualquer aplicação.

## Objetivos e critério de avaliação

Este projeto tem os seguintes objetivos:

* **O1** - Programa deve funcionar como especificado.
* **O2** - Projeto e código bem organizados, nomeadamente:
  * Estrutura de classes bem pensada (ver secção
    [Organização do projeto e estrutura de classes][orgclasses]).
  * Inexistência de código "morto", que não faz nada, como por exemplo
    variáveis, propriedades ou métodos nunca usados.
  * Projeto compila e executa sem erros e/ou _warnings_.
* **O3** - Código devidamente indentado, comentado e documentado. Documentação
  deve ser feita com [comentários de documentação XML][XML].
* **O4** - Repositório Git deve refletir boa utilização do mesmo, com
  _commits_ de todos os elementos do grupo e mensagens de _commit_ que sigam
  as melhores práticas para o efeito (como indicado
  [aqui](https://chris.beams.io/posts/git-commit/),
  [aqui](https://gist.github.com/robertpainsi/b632364184e70900af4ab688decf6f53),
  [aqui](https://github.com/erlang/otp/wiki/writing-good-commit-messages) e
  [aqui](https://stackoverflow.com/questions/2290016/git-commit-messages-50-72-formatting)).
  Quaisquer _assets_ binários, tais como imagens, devem ser integrados
  no repositório em modo Git LFS (atenção que este último ponto é **muito
  importante**).
* **O5** - Relatório em formato [Markdown] (ficheiro `README.md`),
  organizado da seguinte forma:
  * Título do projeto.
  * Autoria:
    * Nome dos autores (primeiro e último) e respetivos números de aluno.
    * Informação de quem fez o quê no projeto. Esta informação é
      **obrigatória** e deve refletir os _commits_ feitos no Git.
  * Legenda dos _itens_, ou seja, que _sprite_ representa cada _item_.
  * Arquitetura da solução:
    * Descrição da solução, com breve explicação de como o programa foi
      organizado, indicação dos _design patterns_ utilizados e porquê, bem como
      dos cuidados tidos ao nível dos princípios [SOLID].
    * Um diagrama UML de classes simples (i.e., sem indicação dos
      membros da classe) descrevendo a estrutura de classes (**obrigatório**).
  * Referências, incluindo trocas de ideias com colegas, sugestões dadas por IAs
    generativas (e.g., ChatGPT), código aberto reutilizado (e.g., do
    StackOverflow) e bibliotecas de terceiros utilizadas. Devem ser o mais
    detalhados possível.
  * **Nota:** o relatório deve ser simples e breve, com informação mínima e
    suficiente para que seja possível ter uma boa ideia do que foi feito.
    Atenção aos erros ortográficos e à correta formatação [Markdown], pois
    ambos serão tidos em conta na nota final.

O projeto tem um peso de 3.5 valores na nota final da disciplina e será avaliado
de forma qualitativa. Isto significa que todos os objetivos têm de ser
parcialmente ou totalmente cumpridos. A cada objetivo, O1 a O5, será atribuída
uma nota entre 0 e 1. A nota do projeto será dada pela seguinte fórmula:

_N = 3.5 x O1 x O2 x O3 x O4 x O5 x D_

Em que _D_ corresponde à nota da discussão e percentagem equitativa de
realização do projeto, também entre 0 e 1. Isto significa que se os alunos
ignorarem completamente um dos objetivos, não tenham feito nada no projeto ou
não comparecerem na discussão, a nota final será zero.

## Entrega

O projeto é entregue de forma automática através do GitHub. Mais concretamente,
o repositório do projeto será automaticamente clonado às **23h00 de 19 de
novembro de 2023**. Certifiquem-se de que a aplicação está funcional e que todos
os requisitos foram cumpridos, caso contrário o projeto não será avaliado.

O repositório deve ter:

* Projeto Unity 2022.3 LTS funcional.
* Ficheiros `.gitignore` e `.gitattributes` adequados para projetos Unity.
* Ficheiro `README.md` contendo o relatório do projeto em formato [Markdown].
* Ficheiros de imagens, contendo o diagrama UML de classes e outras figuras
  que considerem úteis. Estes ficheiros devem ser incluídos no repositório em
  modo Git LFS (assim como todos os _assets_ binários do Unity).

Em nenhuma circunstância o repositório pode ter _builds_ ou outros ficheiros
temporários do Unity (que são automaticamente ignorados se usarem um
`.gitignore` apropriado).

## Honestidade académica

Nesta disciplina, espera-se que cada aluno siga os mais altos padrões de
honestidade académica. Isto significa que cada ideia que não seja do
aluno deve ser claramente indicada, com devida referência ao respetivo
autor. O não cumprimento desta regra constitui plágio.

O plágio inclui a utilização de ideias, código ou conjuntos de soluções
de outros alunos ou indivíduos, ou quaisquer outras fontes para além
dos textos de apoio à disciplina, sem dar o respetivo crédito a essas
fontes. Os alunos são encorajados a discutir os problemas com outros
alunos e devem mencionar essa discussão quando submetem os projetos.
Essa menção **não** influenciará a nota. Os alunos não deverão, no
entanto, copiar códigos, documentação e relatórios de outros alunos, ou dar os
seus próprios códigos, documentação e relatórios a outros em qualquer
circunstância. De facto, não devem sequer deixar códigos, documentação e
relatórios em computadores de uso partilhado.

**Sobre IAs generativas (e.g. ChatGPT):** podem usar este tipo de ferramentas
para esclarecer dúvidas, ou até para obterem uma ou outra sugestão de código,
desde de que as ideias e organização geral do projeto sejam originais. Código
completamente fornecido por uma IA generativa será facilmente detetável pelas
ferramentas de deteção de plágio, pelo que sugerimos muito cuidado no uso deste
tipo de ferramentas. De qualquer forma, todo o código gerado através de IA
(parcialmente ou totalmente) deve ser indicado em forma de comentário e nas
referências do relatório.

Nesta disciplina, a desonestidade académica é considerada fraude, com
todas as consequências legais que daí advêm. Qualquer fraude terá como
consequência imediata a anulação dos projetos de todos os alunos envolvidos
(incluindo os que possibilitaram a ocorrência). Qualquer suspeita de
desonestidade académica será relatada aos órgãos superiores da escola
para possível instauração de um processo disciplinar. Este poderá
resultar em reprovação à disciplina, reprovação de ano ou mesmo suspensão
temporária ou definitiva da ULHT.

*Texto adaptado da disciplina de [Algoritmos e
Estruturas de Dados][aed] do [Instituto Superior Técnico][ist]*

## Referências

* \[1\] Whitaker, R. B. (2022). **The C# Player's Guide** (5th Edition).
  Starbound Software.
* \[2\] Albahari, J., & Johannsen, E. (2020). **C# 8.0 in a Nutshell**. O’Reilly
  Media.
* \[3\] Freeman, E., Robson, E., Bates, B., & Sierra, K. (2020). **Head First
  Design Patterns** (2nd edition). O'Reilly Media.
* \[4\] Dorsey, T. (2017). **Doing Visual Studio and .NET Code Documentation
  Right**. Visual Studio Magazine. Retrieved from
  <https://visualstudiomagazine.com/articles/2017/02/21/vs-dotnet-code-documentation-tools-roundup.aspx>.

## Licenças

* Este enunciado é disponibilizado através da licença [CC BY-NC-SA 4.0].
* O código que acompanha este enunciado é disponibilizado através da licença
  [MIT].

## Metadados

* Autor: [Nuno Fachada]
* Curso:  [Licenciatura em Videojogos][lamv]
* Instituição: [Universidade Lusófona de Humanidades e Tecnologias][ULHT]

[CC BY-NC-SA 4.0]:https://creativecommons.org/licenses/by-nc-sa/4.0/
[MIT]:http://opensource.org/licenses/MIT
[lamv]:https://www.ulusofona.pt/licenciatura/videojogos
[Nuno Fachada]:https://github.com/nunofachada
[ULHT]:https://www.ulusofona.pt/
[aed]:https://fenix.tecnico.ulisboa.pt/disciplinas/AED-2/2009-2010/2-semestre/honestidade-academica
[ist]:https://tecnico.ulisboa.pt/pt/
[Markdown]:https://guides.github.com/features/mastering-markdown/
[SOLID]:https://en.wikipedia.org/wiki/SOLID
[KISS]:https://en.wikipedia.org/wiki/KISS_principle
[XML]:https://docs.microsoft.com/dotnet/csharp/codedoc
[orgclasses]:#organização-do-projeto-e-estrutura-de-classes
[objetivos]:#objetivos-e-critério-de-avaliação
[UnitySimpleFileBrowser]:https://github.com/yasirkula/UnitySimpleFileBrowser
[Formato dos ficheiros de inventário]:#formato-dos-ficheiros-de-inventario
[MVC]:https://www.geeksforgeeks.org/mvc-design-pattern/
[.NET SDK 6.0]:https://dotnet.microsoft.com/download/dotnet/6.0