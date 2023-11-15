# Enunciado exemplo do Projeto 2

_**Atenção**: Este enunciado não é para implementar no Projeto 1! É apenas um
exemplo do tipo de perguntas que poderão surgir no Projeto 2 (_live coding_)._

**Certifiquem-se que nos _Settings_ do projeto do grupo a opção `Include Git LFS
objects in archives` está ativada!**

## Questões


1. Cria um um novo repositório **privado** tua conta pessoal de GitHub para
   realizares este Projeto 2 / *live coding*. Em particular:

    1. Cria um novo repositório **privado** vazio no GitHub, com o nome
       p2_aXXXXXXX (substituir XXXXXXXX pelo número de aluno).
    2. Toma nota do URL deste novo repositório. *Não podes partilhar
       este URL com ninguém além do docente\!*
    3. Faz `Download ZIP` do projeto original para o teu computador, descomprime
       o projeto para uma pasta, e no terminal faz `cd` para dentro dessa pasta.
    4. Nessa pasta, inicializa um novo repositório Git, e adiciona o repositório
       privado criado no ponto i. como novo repositório remoto (`git remote
       add...`).
    5. Faz `add` do estado atual do repositório e depois `push` para o novo
       o repositório remoto.

2.  Adiciona no início (topo) do `README.md` a seguinte informação na
    forma de *lista Markdown*:

    1.  *Código* no topo deste enunciado (código só será fornecido no enunciado
        real).
    2.  O teu *nome* e *número de aluno*.

3.  Convidar o docente para colaborar no novo repositório.

4.  No Projeto 1 era pedido que criasses 5 botões, numerados de 1 a 5,
    que ao serem clicados apresentassem um painel com a mensagem “For
    the future 1”, etc. Deves substituir a mensagem em cada painel pela
    seguinte informação, **usando obrigatoriamente Linq**:

    1. **Painel 1**: O peso total de todos os itens no inventário.
    2. **Painel 2**: O número total de _Action items_ (i.e., cujo tipo não seja
       `Container`) no inventário.
    3. **Painel 3**: Número de _Container items_ com mais do que 2 _Weapons_
       diretamente lá contidas (i.e., que não).
    4. **Painel 4**: O valor médio dos _Container items_ com mais de 2 _Weapon
       items_ lá contidos, incluindo possivelmente contidos em sub-contentores.
    5. **Painel 5**: O valor total de todas as _Coins_ diretamente colocadas em
       _pouches_.

## Notas adicionais

- Este projeto é com consulta. Podes utilizar livros ou qualquer recurso na
  Internet exceto IAs generativas. Não podes comunicar com ninguém (incluindo
  IAs generativas), e a quebra desta regra equivale automaticamente a nota zero
  neste projeto.
- Este projeto tem um peso de 3 valores na nota final.
- A realização com sucesso das alíneas 1 a 3 deste enunciado vale 0.5 valores.
- A alínea 4 vale 2.5 valores, e cada uma dos respetivas sub-alíneas
  vale por sua vez 0.5 valores.
