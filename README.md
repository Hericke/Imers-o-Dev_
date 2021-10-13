# Imers-o-Dev_
Livro de treinamento HTML-CSS-Javascript
lógica do jogo

7.3 ESCREVENDO O CÓDIGO 67

ou empate (ambos os valores são iguais).
Já praticamos anteriormente com as ferramentas para
comparar valores e também como passar condições ao JavaScript:
se tal condição se cumprir, vá por tal caminho; caso contrário, siga
por outro caminho. Vamos reaproveitar tudo aqui:
function jogar() {
var atributoSelecionado = obtemAtributoSelecionado()
if (cartaJogador.atributos[atributoSelecionado] > cartaMaquina
.atributos[atributoSelecionado]) {
alert('Venceu. A carta do computador é menor')
} else if (cartaJogador.atributos[atributoSelecionado] < carta
Maquina.atributos[atributoSelecionado]) {
alert('Perdeu. A carta do computador é maior')
} else {
alert('Empatou!')
}
console.log(cartaMaquina)
}
E como exatamente o JavaScript consegue obter o valor de
cada atributo para comparar? Através da sintaxe
objeto[“nomeDaPropriedade”] quando sabemos exatamente o
nome da propriedade ou objeto[variavel] (sem aspas) quando
não temos como passar o nome da propriedade ou será feita uma
iteração.
Faça os seguintes testes no seu código, logo abaixo da variável
cartaSeiya :
//usamos colchete e aspas quando sabemos exatamente o nome da pro
priedade e queremos acessar o valor correspondente
console.log(cartaPaulo.atributos["ataque"])
//usamos colchete e uma variável quando não sabemos exatamente ou
não temos como fixar o nome da propriedade, por exemplo em caso
de iteração, para acessar o valor correspondente a cada proprieda

68 7.3 ESCREVENDO O CÓDIGO

de
for (atributo in cartaPaulo.atributos) {
console.log(cartaPaulo.atributos[atributo])
}

Dica: agora é possível acessar os VALORES de cada propriedade
(ou seja, cada “poder” das cartas) e aí sim fazer a comparação
entre o valor do “poder” na carta sorteada para o jogador e
para o computador. O fluxo do código que deve ser executado
para cada resultado da comparação pode ser resolvido com
if/else if/else .

Observe um detalhe na execução deste código: separamos o
código em funções para que só sejam executados no momento
certo e podemos ver um exemplo disso na função
obtemAtributoSelecionado() ; esta função está sendo
chamada/executada a partir da execução da função jogar() .
Como a própria função jogar() não é executada antes do
jogador clicar no botão, não há o risco da função
obtemAtributoSelecionado() ser executada sem os dados
necessários, ou em um momento errado.
Esta primeira versão do Super Trunfo já tem bastante código,
então vamos parar por aqui e respirar um pouco.

Os temas que estamos vendo nestas aulas vão te acompanhar
durante toda sua trajetória no desenvolvimento web. Abaixo
seguem alguns temas interessantes para você já ir se
7.4 PARA SABER MAIS

7.4 PARA SABER MAIS 69

aprofundando:
escopo
a palavra-chave return
manipulação de arrays (iteração, filtros, etc)
manipulação de objetos (iteração, acesso a propriedades,
acesso a valores)
Tudo certo? Então é hora de praticar!

Vamos repassar todos os passos do programa:
Criar as cartas do jogo e definir seus atributos;
Desenvolver uma função para sortear uma carta para o
jogador e outra para a máquina;
Exibindo os atributos das cartas na tela para o jogador;
Obter o atribudo escolhido pelo jogador e comparar com a
carta da máquina;
Comparar o atributo de ambas as cartas e definir um
vencedor.
Clique neste link para acessar o código completo no Codepen.
7.5 RESUMO

70 7.5 RESUMO

CAPÍTULO 8

Além de resolver problemas de forma lógica, trabalhar com
programação também envolve a integração de ferramentas. Para
esta Imersão, utilizamos o JavaScript em conjunto com o HTML e
CSS, que são a base para o que chamamos de desenvolvimento
web front end.
O código da aula inicial para você acompanhar está aqui:
https://codepen.io/imersao-dev/pen/GREGPNb
Não se esqueça de fazer o fork desse projeto para a sua conta, e
de marcar a hashtag da #imersaodev e #alura.
Nesta aula, vamos evoluir o que já criamos para o Super
Trunfo, focando justamente na integração da lógica com a tela.

Como das vezes anteriores, vamos começar pelo fluxo do
programa. O jogo já está fazendo o mínimo necessário para que o
SUPER TRUNFO:
MONTAGEM DAS CARTAS

8.1 OBJETIVO DA AULA

8.2 PASSO A PASSO

8 SUPER TRUNFO: MONTAGEM DAS CARTAS 71

fluxo lógico do Super Trunfo funcione, então podemos pensar em
incrementar a experiência de jogo, adicionando alguns passos:
após o sorteio das cartas, extrair de cada objeto a imagem
da carta e o valor de cada “poder”;
exibir na tela estas informações, fazendo com que
apareçam no local correto (ou seja, dentro da tag esperada).

Vamos pegar estas imagens da internet, como fizemos com os
pôsteres do AluraFlix:
var cartaSeiya = {
nome: "Seiya de Pégaso",
imagem: "https://i.pinimg.com/originals/c2/1a/ac/c21aacd5d092b
f17cfff269091f04606.jpg",
atributos: {
ataque: 80,
defesa: 60,
magia: 90
}
}
var cartaPokemon = {
nome: "Bulbasauro",
imagem: "http://4.bp.blogspot.com/-ZoCqleSAYNc/UQgfMdobjUI/AAA
AAAAACP0/s_iiWjmw2Ys/s1600/001Bulbasaur_Dream.png",
atributos: {
ataque: 70,
defesa: 65,
magia: 85
}
}
var cartaStarWars = {
nome: "Lorde Darth Vader",
imagem: "https://images-na.ssl-images-amazon.com/images/I/51VJ
BqMZVAL._SX328_BO1,204,203,200_.jpg",
atributos: {
Adicionando imagens para as cartas

72 8.2 PASSO A PASSO

ataque: 88,
defesa: 62,
magia: 90
}
}
Note que acrescentamos em cada objeto de carta um atributo a
mais, o atributo imagem , cada um com um valor de string
correspondente ao link da imagem.

Você pode escolher outras imagens se quiser, mas não
esqueça de conferir se o link termina com .jpg ou .png .

Por enquanto, o programa está exibindo na tela somente uma
lista dos “poderes”, que pegamos a partir da carta sorteada para o
jogador — estávamos mostrando só a lista, sem valores! Hora de
exibir também os valores, para que o jogador possa escolher
melhor em qual poder quer apostar.
Para isso, precisamos:
localizar um elemento HTML específico na tela, usando o
getElementById() ou o getElementsByName() , de
acordo com o caso;
adicionar novas informações formatadas como tags de
HTML, utilizando JavaScript;
descobrir como incluir estilos CSS a estas novas
informações que estão sendo adicionadas.
Vamos começar criando a função exibeCartaJogador() e
Exibindo as informações adicionais na tela

8.2 PASSO A PASSO 73

usando o document.getElementById(“carta-jogador”) para
localizar o elemento com o identificador id=”carta-jogador”
no HTML e salvar este “endereço” em uma variável.
function exibeCartaJogador() {
var divCartaJogador = document.getElementById("carta-jogador")
}
Para testar esse código, substitua a chamada da função
exibirOpcoes() na úlfima linha da função sortearCarta()
por esta que estamos começando a criar agora:
exibeCartaJogador() .
Agora, quando o jogador clica no botão sortear carta ,
além da lógica do sorteio que já vimos anteriormente, o JavaScript
também tem que “injetar” pedaços de código em HTML e em CSS
para que os dados apareçam nos locais corretos da tela e com a
aparência que esperamos.
Tanto o HTML quanto o CSS têm suas próprias sintaxes, que
são diferentes do JavaScript. Porém, o JavaScript tem ferramentas
que utilizam strings (caracteres entre aspas ” ” ) combinados
com variáveis para criar novos trechos de código em HTML e CSS,
fazendo com que o navegador reconheça as instruções. Já fizemos
um pouco disso nos projetos anteriores, toda vez que utilizamos a
palavra-chave innerHTML para inserir tags HTML no formato de
string.
O HTML inicial deste projeto já conta com imagem pronta
para ser a base de todas as cartas, e o jogo já inicia com esta
imagem aplicada na <div> de carta do jogador e de carta do
computador:

74 8.2 PASSO A PASSO

<div>
<div id="carta-jogador">
<img src="https://www.alura.com.br/assets/img/imersoes/dev
-2021/card-super-trunfo-transparent-ajustado.png"
style=" width: inherit; height: inherit; position: abs
olute;">
<h3></h3>
</div>
</div>
<div>
<div id="carta-maquina" class="carta"><img
src="https://www.alura.com.br/assets/img/imersoes/dev-2021/ca
rd-super-trunfo-transparent-ajustado.png"
style=" width: inherit; height: inherit; position: abs
olute;"></div>
</div>
Já temos a base, mas como exibir as informações nela?
Lembrando que, nessa hora, só devemos mostrar a carta sorteada
para o jogador!
As informações são:
nome da carta;
imagem;
poderes e seus valores.
Quando queremos adicionar estilo ao HTML, utilizamos as
chamadas propriedades de CSS; por exemplo, trocar as cores dos
textos, alinhar elementos, entre muitas outras coisas.
É possível atribuir estas propriedades a tags HTML de algumas
formas. Vamos ver um exemplo baseado no código do primeiro
projeto da Imersão:
No arquivo HTML atribuímos class a um elemento:
<h1 class="page-title">
Conversor de moedas

8.2 PASSO A PASSO 75

</h1>
E no CSS utilizamos o nome de class para mudar
propriedades; no exemplo abaixo, a cor do texto:
.page-title {
color: #ffffff;
margin: 0 0 5px;
}
O exemplo acima é uma forma bastante utilizada. Mas também
é possível passar estilos direto na tag HTML do elemento,
dispensando o arquivo CSS. O exemplo acima ficaria, então, da
seguinte forma:
<h1 class="page-title" style="color: #ffffff; margin: 0 0 5px;">
Conversor de moedas
</h1>
O JavaScript consegue manipular tags HTML e adicionar
style a uma tag, e é esta ferramenta que vamos utilizar para
adicionar a imagem correspondente:
function exibeCartaJogador() {
var divCartaJogador = document.getElementById("carta-jogador")
divCartaJogador.style.backgroundImage = `url(${cartaJogador.im
agem})`
}
No código acima, utilizamos
divCartaJogador.style.backgroundImage
= url(${cartaJogador.imagem}) ` para adicionar um
atributo style ao elemento que já estava salvo na
variável divCartaJogador . Além de style adicionamos também
qual é a propriedade de estilo que queremos adicionar e
seu valor, uma url (um caminho de um link) que estamos
obtendo do objeto cartaJogador.imagem`.

76 8.2 PASSO A PASSO

Se precisar, relembre o processo de acessar dados de um
objeto no material da aula anterior.

Quando o JavaScript processar esse trecho de código, o HTML
gerado vai ser semelhante ao abaixo:
<div id="carta-jogador" style="background-image: url('https://[en
dereço da sua imagem].jpg');">
</div>
Ainda temos que exibir o nome da carta e os poderes com
valores. Ou seja, também temos que utilizar o JavaScript para
gerar código HTML destes elementos.
Podemos pegar o nome no mesmo objeto cartaJogador e
criar uma tag <p> (tag genérica de texto) com esta informação:
function exibeCartaJogador() {
var divCartaJogador = document.getElementById("carta-jogador")
divCartaJogador.style.backgroundImage = `url(${cartaJogador.im
agem})`
var nome = `<p class="carta-subtitle">${cartaJogador.nome}</p>
`
}
O nome ainda não está aparecendo na tela, pois ainda não
atualizamos o valor de divCartaJogador com mais este trecho
de código HTML.
function exibeCartaJogador() {
var divCartaJogador = document.getElementById("carta-jogador")
divCartaJogador.style.backgroundImage = `url(${cartaJogador.im
agem})`
var nome = `<p class="carta-subtitle">${cartaJogador.nome}</p>
`

8.2 PASSO A PASSO 77

divCartaJogador.innerHTML += nome
}
Para atualizar uma variável com um novo valor sem substituir
totalmente o que já está salvo nela, podemos usar o operador += ,
como já vimos nos exercícios com iteradores.
Imagem e nome da carta estão na tela, hora de lidar com a lista
de poderes e os valores. Também temos que usar o JavaScript para
criar tags HTML e inserir tudo no código; a diferença é que, nesse
caso, temos que fazer isso para cada um dos poderes que está
dentro de um objeto.
No estágio inicial deste projeto, vimos como percorrer objetos
utilizando for... in . Podemos reutilizar este método para criar
tags HTML de forma automatizada com cada poder e valor.
function exibeCartaJogador() {
var divCartaJogador = document.getElementById("carta-jogador")
divCartaJogador.style.backgroundImage = `url(${cartaJogador.im
agem})`
var nome = `<p class="carta-subtitle">${cartaJogador.nome}</p>
`
var opcoesTexto = ""
for (var atributo in cartaJogador.atributos) {
opcoesTexto += "<input type='radio' name='atributo' value=
'" + atributo + "'>" + atributo + " " + cartaJogador.atributos[at
ributo] + "<br>"
}
divCartaJogador.innerHTML += nome + opcoesTexto
}
Para cada um dos poderes, temos que criar uma string com
a sintaxe do HTML e as informações que vamos acessar do objeto
JavaScript referente à carta do jogador. Então, a primeira coisa a
fazer é criar uma variável para salvar todas essas tags, começando

78 8.2 PASSO A PASSO

com um valor de “vazia”:
var opcoesTexto = ""

A estrutura do for... in é a mesma que fizemos para a fase
anterior deste projeto! Você pode consultar o material caso
precise relembrar o que foi feito.

for (var atributo in cartaJogador.atributos) {
// código aqui
}
O que será feito em cada iteração é que muda. Além disso, já
vimos o input type=”radio” na fase anterior do projeto, e
também como acessar os valores em um objeto, e não apenas as
propriedades:
for (var atributo in cartaJogador.atributos) {
opcoesTexto += "<input type='radio' name='atributo' value='" +
atributo + "'>" + atributo + " " + cartaJogador.atributos[atribu
to] + "<br>"
}
Agora o JavaScript vai unir cada atributo (ou seja, cada item
dentro do objeto cartaJogador.atributos ) com strings que
representam código HTML, salvando o resultado de cada iteração
na variável opcoesTexto — repare que estamos usando o
operador += novamente para atualizar a variável ao invés de
substituir seu valor.
Temos que atualizar também o valor que será enviado para a
variável divCartaJogador : isso está sendo feito com a linha
divCartaJogador.innerHTML += nome + opcoesTexto ... Mas

8.2 PASSO A PASSO 79

se tentarmos atualizar a tela neste momento, perceberemos que os
poderes não estão aparecendo na parte da tela onde deveriam.
Aqui vamos entrar um pouco mais em como HTML e CSS
trabalham juntos para que todas as partes da tela estejam onde
deveriam estar. Para este projeto, nosso time de front end já deixou
algumas propriedades de CSS criadas no arquivo style.css ,
prontas para serem acessadas pelo HTML... Só precisamos criar o
código para isso!
divCartaJogador.innerHTML += "<div id='opcoes' class='carta-st
atus'>" + nome + opcoesTexto + "</div>"
A classe class=’carta-status’ vai cuidar do alinhamento,
o que precisamos fazer é inserir uma tag para agrupar tudo. No
caso, vamos criar uma tag de elemento do tipo <div> , adicionar
as variáveis com o código HTML que acabamos de criar, sem
esquecer de fechar a tag no final da linha, com </div> .
O resultado final desta função fica da seguinte forma:
function exibeCartaJogador() {
var divCartaJogador = document.getElementById("carta-jogador")
divCartaJogador.style.backgroundImage = `url(${cartaJogador.im
agem})`
var nome = `<p class="carta-subtitle">${cartaJogador.nome}</p>
`
var opcoesTexto = ""
for (var atributo in cartaJogador.atributos) {
opcoesTexto += "<input type='radio' name='atributo' value=
'" + atributo + "'>" + atributo + " " + cartaJogador.atributos[at
ributo] + "<br>"
}
divCartaJogador.innerHTML += "<div id='opcoes' class='carta-st
atus'>" + nome + opcoesTexto + "</div>"
}

80 8.2 PASSO A PASSO

HTML e CSS são competências à parte da lógica de
programação em si! Durante a Imersão decidimos não focar
muito em conceitos destas linguagens, pois seria muita coisa
para ver ao mesmo tempo! Mas se você gostar, pode se
aprofundar também nestes assuntos e revisitar este código
mais tarde para ver como estas partes estão trabalhando
juntas.

Uma boa parte do código que fizemos na versão anterior pode
ser aproveitada neste trecho.
A função obtemAtributoSelecionado() não vai ser
modificada, pois a lógica de obter a lista de elementos <input
type=’radio’ name=’atributo’> para verificar qual está
selecionado ( .checked ) é a mesma.
Na função jogar() — a função que usamos, entre outras
coisas, para chamar/executar obtemAtributoSelecionado() —,
vamos manter a lógica de verificação usada no if (valor maior/
valor menor/ empate), porém agora substituindo o alert por
uma mensagem na tela:
function jogar() {
var atributoSelecionado = obtemAtributoSelecionado()
var htmlResultado = “”
if (cartaJogador.atributos[atributoSelecionado] > cartaMaquina
.atributos[atributoSelecionado]) {
htmlResultado = '<p class="resultado-final">Venceu</p>'
} else if (cartaJogador.atributos[atributoSelecionado] < carta
Exibir a carta do computador

8.2 PASSO A PASSO 81

Maquina.atributos[atributoSelecionado]) {
htmlResultado = '<p class="resultado-final">Perdeu</p>'
} else {
htmlResultado = '<p class="resultado-final">Empatou</p>'
}
var divResultado = document.getElementById("resultado")
divResultado.innerHTML = htmlResultado
exibeCartaMaquina()
}
Começamos com a variável htmlResultado vazia, e para cada
uma das condições do if , salvamos uma string com a tag
HTML e a informação de acordo com a comparação (jogador
perdeu, jogador ganhou, etc).
Os passos seguintes, como nas outras funções que criamos, é
localizar o elemento ”resultado” no HTML e inserir no
.innerHTML deste elemento a string que o JavaScript salvou na
variável htmlResultado de acordo com o caminho seguido pelo
if .
Agora que já temos o resultado dessa rodada do jogo, podemos
passar para o último passo, que é revelar a carta do computador. Já
vamos deixar esta função sendo chamada na última linha,
exibeCartaMaquina() .

Já temos a função exibeCartaJogador() , e se formos pensar
na lógica do que precisamos fazer para exibir a carta do
computador, podemos identificar coisas semelhantes:
acessar objeto da carta sorteada;
exibir nome e imagem a partir deste objeto;
Exibindo a carta do computador

82 8.2 PASSO A PASSO

percorrer (iterar) o objeto cartaMaquina.atributos
para acessar a lista de poderes;
exibir estes atributos da forma correta na tela (nesse caso,
não precisamos dos botões type=”radio” para
selecionarmos uma opção).
Assim, a função final fica da seguinte forma:
function exibeCartaMaquina() {
var divCartaMaquina = document.getElementById("carta-maquina")
divCartaMaquina.style.backgroundImage = `url(${cartaMaquina.im
agem})`
var nome = `<p class="carta-subtitle">${cartaMaquina.nome}</p>
`
var opcoesTexto = ""
for (var atributo in cartaMaquina.atributos) {
opcoesTexto += "<p type='text' name='atributo' value='" +
atributo + "'>" + atributo + " " + cartaMaquina.atributos[atribut
o] + "<br>"
}
divCartaMaquina.innerHTML += "<div id='opcoes' class='carta-st
atus --spacing'>" + nome + opcoesTexto + '</div>'
}
As diferenças entre as funções exibeCartaJogador() e
exibeCartaMaquina() são:
o momento em que são chamadas: exibimos na tela a carta
do jogador quando o usuário clica no botão para sortear
sua carta. Já a carta do computador só pode ser exibida
após o usuário escolher um poder e clicar no botão
jogar . Afinal de contas, não podemos deixar o usuário
ver os poderes da carta do computador antes de fazer a
escolha e confirmar clicando no botão!
o HTML gerado no for... in : na carta do jogador, temos

8.2 PASSO A PASSO 83

que criar uma tag do tipo <input type=”radio”> para o
usuário selecionar o poder que quer comparar. Para a carta
do computador, podemos criar uma tag de texto normal do
HTML ( <p> ) já que o jogador não vai fazer nenhuma
escolha nesse caso, só acompanhar os resultados.

VOCÊ JÁ OUVIU FALAR EM “REAPROVEITAMENTO DE CÓDIGO”?
Quando utilizamos partes de código similares, como no caso
das funções exibeCartaJogador() e
exibeCartaMaquina() é normal tentarmos escrever de uma
forma que tenha o melhor aproveitamento possível. Ou seja,
tentamos escrever somente um trecho de código que sirva
para várias situações; afinal de contas, o código para exibir
cartas na tela deveria funcionar independente de ser a carta
do jogador, do computador, ou qualquer outra situação. Você
vai se deparar muito com esta questão durante seus estudos, e
vai ter a oportunidade de estudar situações em que isso pode
inclusive não ser vantajoso... No código que acabamos de
fazer, você consegue pensar em como reaproveitar a função
de exibir cartas para o mesmo código funcionar nos dois
casos, sem precisar ser reescrito?

8.3 PARA SABER MAIS

84 8.3 PARA SABER MAIS

Lembre-se que quase sempre existe mais de uma forma de
fazer qualquer tarefa de programação. À medida em que você
for aprendendo novos métodos, pode voltar neste projeto e
praticar nele!

Abaixo, algumas questões que você pode usar para direcionar
seus estudos:
por que os trechos de código que estamos adicionando ao
HTML direto pelo JavaScript já aparecem nos lugares
certos?
quais são as formas de se trabalhar com código CSS e
quando cada caso é melhor, ou mais utilizado?
Tudo certo? Então é hora de praticar!

Adicionando o campo imagem nos objetos com o caminho
da imagem;
Criar uma função que exibe a carta do jogador após o
sorteio das cartas;
Adicionar a moldura da carta;
Escrever o resultado na tela após o duelo das cartas
informando se o jogador venceu ou perdeu;
Criar uma função que exibe a carta da máquina;
Exibir os atributos e pontos da carta da máquina.
Clique neste link para acessar o código completo no Codepen.
8.4 RESUMO

8.4 RESUMO 85

86 8.4 RESUMO

CAPÍTULO 9

Nesta nona aula da Imersão Dev, desscobriremos como usar o
Figma para um layout em código HTML e CSS para o nosso
portfólio! Dessa vez, o código da aula será montado a partir do
zero, então para isso você deve criar um novo pen em branco no
codepen, clicando na sua imagem do perfil e selecionando new
pen .
Hoje veremos muita coisa legal. Não somente com
JavaScript, mas também com HTML e CSS, três tecnologias
principais para o desenvolvimento front-end na web.
Vamos um portfólio com todos os projetos que fizemos ao
longo da Imersão Dev, que foram sete.

Figma é a plataforma que a galera de design utiliza para
desenhar como será a página que queremos desenvolver. Depois, o
pessoal de front-end pega esse design já pronto, da equipe de
designers, e começa a investigar tudo que tem na página que
teremos que transformar em código.
FIGMA, HTML E CSS

9.1 OBJETIVO DA AULA

9.2 FIGMA

9 FIGMA, HTML E CSS 87

Neste link, você encontra o projeto do Figma

Para começar o nosso código, vou digitar o <body> , todo o
conteúdo da nossa página estará dentro dele. Repare na sintaxe que
estou usando, sempre colocando o sinal de menor e depois o sinal
de maior. Para fechar a tag <body> , fazemos a mesma coisa mas
com uma barra, </body> .
Nossa página será dividida em duas estruturas. A primeira é o
<header> , que no nosso projeto vai ser esse espaço que tem a
foto da Rafa, o nome dela e o texto descrevendo o trabalho dela.
Além disso, outra tag importante é a <main> , que vai ter o
conteúdo com os links dos projetos de cada aula.
<body>
<header>
</header>
<main>
</main>
</body>
Temos uma imagem, um texto com uma fonte maior e a
descrição em fonte menor. Vou colocar essas propriedades dentro
do nosso <header> . Primeiro colocaremos um <img> , que
representa a imagem, note que antes de fechar a tag aparece
algumas coisas aqui no autocompletar, que podemos usar como
propriedades para essa imagem que queremos colocar. Esse src
significa "source" e indica qual é o caminho da imagem que
queremos utilizar.
9.3 HTML - ESTRUTURA DA PÁGINA

88 9.3 HTML - ESTRUTURA DA PÁGINA

Vamos usar a imagem está no meu perfil de uma plataforma
chamada GitHub, que é uma plataforma em que você consegue
armazenar seus códigos, nela você consegue subir seus códigos e
fazer diferentes versões dele. É uma plataforma que usaremos ao
longo do tempo e é essencial para quem quer trabalhar na área de
desenvolvimento.
Estamos na minha conta do GitHub. Uma coisa que eles
fizeram e é muito legal é que basta colocar um .png no final da
URL do meu perfil e já conseguimos acessar a minha foto.
Por exemplo:
Este é o Github do Gui
https://github.com/guilhermeonrails
Para exibir a foto dele usamos o mesmo endereço e
adicionamos o .png
A url será https://github.com/guilhermeonrails.png
Estamos utilizando o GitHub agora apenas para pegar o
caminho da foto, a foto de vocês se já tiverem uma conta no
GitHub. Recomendo que vocês já criem uma conta lá para achar
tranquilamente a sua foto simplesmente colocando .png no final
da URL do seu perfil.
9.4 INCLUINDO UMA IMAGEM

9.4 INCLUINDO UMA IMAGEM 89

Por questão de segurança, quando colocamos o .png e
pressionamos "Enter", a URL muda. Não é essa URL que
pegaremos. Nós vamos pegar a URL do perfil mesmo,
adicionando o .png no final. No caso do perfil da Rafaella,
essa é a URL que pegaremos:
https://github.com/rafaballerini.png. Vou colar a URL no
nosso código e fechar a tag de imagem com barra e o sinal de
maior (/>).

<body>
<header>
<img class="perfil-foto" src="https://github.com/rafaballer
ini.png" />
</header>
<main>
</main>
</body>

O elemento div do HTML (ou Elemento de Divisão de
Documento HTML) é usado para agrupar elementos para fins de
estilo (usando os atributos class ou id). Vamos colocar uma
<div> para dividir o nosso header para ficar fácil de
conseguirmos manter. Dentro dessa <div> vou colocar aquele
texto em uma tag <h1> .
Usamos muito o <h1> para título da página, para o que vai
ser o texto principal da nossa página. Nesse caso, o título é o nosso
9.5 CONTEÚDO DO HTML

90 9.5 CONTEÚDO DO HTML

próprio nome no portfólio. por exemplo "Rafaella Ballerini".
Podemos incluir outro texto que aparece embaixo. Você pode
usar um <h2> ou <h3> . O <h1> normalmente utilizamos
apenas uma vez na página. Vamos inserir um <h3> com trecho
"Instrutora e desenvolvedora front-end".
<body>
<header>
<img src="https://github.com/rafaballerini.png" />
<div>
<h1>Rafaella Ballerini</h1>
<h3>Instrutora e desenvolvedora front-end #imersaodev</h3
>
</div>
</header>
//código omitido
Nós colocamos a imagem, o <h1> e <h3> , mas ainda não
está muito bonito. Nós sabemos que podemos usar o CSS para
deixar isso mais bonito.

No CSS, normalmente, utilizamos as próprias tags. Existem
três tipos de seletores principais que podemos utilizar para estilizar
o HTML, por exemplo, se utilizamos a tag <div> vai ser aplicado
para todas as divs do nosso projeto; a classe vai ser para os
elementos que tiverem a classe que escreveremos, pode ser uma
classe "perfil", uma classe "título", e os elementos que que
colocarmos essa classe terão isso aplicado; e o id sempre utilizamos
para estilizar apenas um elemento específico. Quando queremos
apenas aquele elemento, daquela forma, colocamos um id nele que
vai ser único e não será aplicado em nenhum outro elemento.
9.6 CSS

9.6 CSS 91

Nesse caso, vamos utilizar muito mais o class e as tags para
estilizar nossa página. Então, vamos começar a estilizar?
Primeiro começamos estilizando as coisas maiores, começando
pelo fundo e depois vamos para os elementos. Vamos começar pela
tag <body> , que é essa que vai pegar todos os elementos. No CSS
você escreve:
body {
}
Vamos escrever todas as coisas que queremos estilizar, por
exemplo, o fundo, a cor da fonte, etc. Vamos lá para o Figma
pensar qual é o mais externo de todos os elementos da nossa
página. A primeira coisa que podemos pegar é essa cor azul-escura
de fundo, que vai ser o nosso background. E como conseguimos
descobrir qual é a cor exata? Aliás, ela tem também um efeito
gradiente. Para descobrir qual é a cor utilizaremos o próprio
Figma.
Podemos clicar em cima da cor e lá na lateral direita tem uma
aba vertical chamada "Inspect", de inspecionar, nela conseguimos
ver alguma informação como a "colors", as cores, que nos informa
que é um "Linear Gradient" (Gradiente Linear) e tem duas cores
diferentes. Ele já nos informa quais cores estamos utilizando. Mas
além disso, conseguimos ter o código CSS desse fundo. Nessa
mesma aba, abaixo de "Colors", tem o "Code CSS" que passa a
posição, largura, altura, e o nosso background que é exatamente o
que queremos.
Preciso fazer uma observação: às vezes não é legal usar o
posicionamento informado pelo Figma porque ele pode ter um

92 9.6 CSS

posicionamento dependente de elementos de uma forma diferente.
É importante termos controle do posicionamento ao estilizarmos o
CSS, então não recomendo utilizar essa parte de posicionamento,
altura e largura do Figma. Até porque no CodePen tem um
tamanho diferente.
Mas faremos isso aos poucos, vou mostrar como
recomendamos que isso seja feito. O que vamos pegar agora é
apenas o trecho do código CSS do background. Podemos copiar
esse trecho, voltar para o CodePen e colar dentro do body do CSS.
body {
background: linear-gradient(236.85deg, #041832 27.26%, #3468A7
96.03%);
}
Vamos salvar e rodar para ver o que vai acontecer. Agora nosso
fundo está com a cor certa e com o gradiente linear que vimos no
design do Figma.

Quem quiser pode mudar a cor também. Mexer nesses
números do código de cor e testar.

Vamos voltar ao Figma e buscar a fonte certa. É a mesma para
a página inteira, desde o nome até os nomes dos projetos. Na aba
"Inspect" ao lado, temos a parte de tipografia chamada
"Typography", e encontraremos a fonte "Roboto".
Para podermos trazer fontes para o nosso projeto, podemos
9.7 FONTES

9.7 FONTES 93

utilizar uma plataforma chamada Google Fonts, basta procurar no
buscador. Acessando-a, veremos que existem muitas opções e
podemos escrever texto para testar se gostamos, e escolher.
Fiquem à vontade para explorar outras fontes, mas por

enquanto usaremos a Roboto que é bem conhecida. Encontrando-
a na plataforma, clicaremos sobre esta e selecionaremos os pesos

ou estilos que queremos, o que também já está no nosso Figma.
O nome está com o número "700" no campo "weight", e o texto
de descrição da nossa página está com peso "400", então vamos
usar esses dois valores. Quando acessamos os pesos da fonte
Roboto no Google Fonts, teremos uma lista com textos de
exemplos e seus respectivos valores de peso e estilo no canto
superior esquerdo de cada item.
Escolheremos o "Regular 400" e clicaremos no botão de "select
this style" nesta opção. Depois, encontraremos o "Bold 700" e
selecionaremos este estilo também.
Existe a possibilidade de importarmos a fonte em nosso HTML
ou no CSS, pois o Google Fonts oferece a opção de "link" e
"import" na opção "Use on the web" na aba "Selected family".
Usaremos no CSS, já que estamos aprendendo como estilizar.
Selecionaremos a opção "import", copiaremos o código a partir da
tag <style> até o final e depois colocaremos no início do nosso
código CSS.
É como se estivéssemos de fato importando algo para usarmos
ao longo do nosso código, então é importante colocarmos no topo
do projeto para usarmos quando quisermos.

94 9.7 FONTES

@import url('https://fonts.googleapis.com/css2?family=Roboto:wght
@400;700&display=swap');
body {
background: linear-gradient(236.85deg, #041832 27.26%, #3468A
7 96.03%);
}
De volta ao Google Fonts, também encontraremos a
informação de como utilizá-la, pois apenas a importamos para o
nosso projeto, mas não a estamos usando ainda.
Para isso, iremos na aba lateral de "Selected family" e
encontraremos o campo de "CSS rules to specify families" com
font-family: 'Roboto', sans-serif;, que é a forma como falamos ao
CSS que queremos utilizar esta fonte.
Então copiaremos essa linha e a colocaremos dentro do body,
porque de fato vamos usar esta fonte para todos os elementos da
página.
Vamos salvar e rodar para ver se a fonte está diferente.
Assim já temos nosso fundo e nossa fonte correta.

Vamos estilizar o nosso cabeçalho, para isso, podemos
primeiro criar uma nova classe para esse conjunto de coisas -
imagem, título e subtítulo -, porque sempre estilizaremos do maior
para o menor.
Por exemplo, poderíamos puxar a tag <header> que é a única
que estamos utilizando, mas começaremos usar de fato as classes.
9.8 ESTILIZANDO UMA DIV

9.8 ESTILIZANDO UMA DIV 95

Primeiramente, dentro do <header> do HTML, criaremos
uma class para este conjunto do cabeçalho. Após o sinal de
igualdade e entre aspas, escreveremos container.
O "container" é um agregado de elementos que temos, então
essa classe representará o nosso cabeçalho.
Para chamarmos uma tag no CSS, só precisaremos escrevê-la,
mas para chamarmos uma class, colocamos um ponto antes do
nome, obtendo .container neste caso. Isso para quando quisermos
estilizar uma classe.
.

Se tivéssemos escrito somente header, só usaríamos essas
características para o <header> , mas como fizemos usando a
classe, todos os elementos que tiverem a .container, e talvez
não seja somente o <header> mesmo, também pegarão essas
características.

Agora já temos o nosso body todo estilizado, ainda que não
possamos ver muitas coisas na página ainda. Mas já temos
estilizadas as coisas que usaremos nela inteira.
Vamos voltar ao Figma para sabermos o próximo passo. temos
um fundo azul e um retângulo de fundo branco, o qual contém o
cabeçalho do <header> e o <main> , que é o conteúdo principal.
Então precisaremos criar algo que englobe esses dois conjuntos
de elementos. De volta ao nosso código, veremos o que podemos
fazer para colocar este retângulo branco.

96 9.8 ESTILIZANDO UMA DIV

Temos o <body> com o <header> e o <main> separados
no HTML, e precisamos englobá-lo em alguma divisão. Criaremos
uma nova <div> que engloba desde antes do <header> até após
o </main> .
Assim, poderemos estilizar essa <div> para termos o fundo
branco do retângulo, pois se estilizarmos o <body> , será a parte
mais externa do fundo azul. Portanto precisamos de uma divisão
interna.
Em seguida, precisaremos criar uma nova classe para esta nova
<div> . Podemos ter as tags para elementos no geral, mas as
classes podem ser definidas para quando quisermos reutilizar a
estilização ou definir estilizações diferentes, afinal estamos usando
outras <div> .
Se estilizarmos a <div> da segunda linha do HTML, as linhas
de <h1> e <h3> da <div> seguinte receberão essa mesma
estilização, e não é o que queremos.
Portanto, criaremos uma nova class que terá o nome igual a
"container" para o conjunto. Para estilizarmos uma classe, faremos
de forma um pouco diferente em relação às tags.
<body>
<div class="container">
<header>
<img src;"https://github.com/rafaballerini.png" />
<div>
<h1>Rafaella Ballerini</h1>
<h3>Instrutora e desenvolvedora front-end #imersa
odev</h3>
</div>
</header>
<main>

9.8 ESTILIZANDO UMA DIV 97

</main>
</div>
</body>

Se colocássemos uma div e depois abríssemos chaves,
funcionaria também, porém todas as outras divisões
mudariam o estilo para este mesmo, e não é isso que
precisamos, pois queremos estilizar somente as div que
"carimbamos" com as características do container, com
especial, título e outra classe que faça sentido.

Começaremos colocando a cor de fundo branca. Então vamos
verificar qual é o valor desta cor para nosso background no
"Rectangle 1" da aba "Inspect".
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght
@400;700&display=swap');
body {
background: linear-gradient(236.85deg, #041832 27.26%, #3468A
7 96.03%);
font-family: 'Roboto', sans-serif;
}
.container {
}
Há várias cores brancas diferentes, por incrível que pareça.
Poderíamos escrever background com dois pontos e white apenas,
mas a equipe de design que fez este Figma já falou que este branco
não é puro, é mais um cinza super claro, então temos que buscar a
informação lá no Figma.

98 9.8 ESTILIZANDO UMA DIV

Então pegaremos a cor que já está no nosso "Inspect" e
colaremos no nosso código. Ela não tem um gradiente como a do
fundo, então é mais tranquilo.
Podemos tanto copiar do código CSS que já vem com a
propriedade do background, quanto escrever a propriedade e
colocar a cor.
Vamos incluir no .container , seguido do valor #ECF4FF da
cor de fundo que pegamos do Figma.
Em seguida, vamos salvar e rodar para vermos como nossa
página ficou.
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght
@400;700&display=swap');
body {
background: linear-gradient(236.85deg, #041832 27.26%, #3468A
7 96.03%);
font-family: 'Roboto', sans-serif;
}
.container {
background: #ECF4FF;
}

Para aumentarmos essa área do fundo e diminuirmos o
retângulo branco, podemos criar uma margem com a distância que
queremos entre o elemento anterior e o atual.
Então aplicaremos a propriedade margin: com uns 64
pixels (no CSS, escrevemos apenas px) de espaço. Agora
9.9 POSICIONAMENTO

9.9 POSICIONAMENTO 99

começamos de fato a trabalhar com tentativa e erro do CSS, pois
temos que ir testando se a distância colocada é satisfatória.
Tem algumas dessas informações no Figma, mas às vezes é
interessante termos o controle das posições dos elementos em
nosso código.
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght
@400;700&display=swap');
body {
background: linear-gradient(236.85deg, #041832 27.26%, #3468A
7 96.03%);
font-family: 'Roboto', sans-serif;
}
.container {
background: #ECF4FF;
margin: 64px;
}
Parece que a margem ficou boa com esse espaço entre o fundo
azul e o branco, mas podemos alterar se quisermos. A medida em
pixels é o tamanho que usamos para distâncias no código.

Na aba "Inspect" do Figma, encontraremos no código CSS as
propriedades box-shadow: e border-radius: . Para
entendermos essas palavras, começaremos pelo border-radius:, que
em uma tradução livre do inglês seria o "raio da borda".
O utilizamos para fazermos a borda arredondada do nosso
elemento. Quanto maior for o valor deste raio, mais curvados
serão os vértices deste elemento.
9.10 SOMBRA E BORDA

100 9.10 SOMBRA E BORDA

Para um exemplo, colocaremos o border-radius: igual a vinte
pixels. Vamos salvar nosso arquivo e rodar para vermos a
diferença.
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght
@400;700&display=swap');
body {
background: linear-gradient(236.85deg, #041832 27.26%, #3468A
7 96.03%);
font-family: 'Roboto', sans-serif;
}
.container {
background: #ECF4FF;
margin: 64px;
border-radius: 20px;
}
A "borda" da nossa divisão .container já ficaram
arredondadas com vinte pixels.
Voltando ao CSS do Figma para entendermos a propriedade
box-shaddow: , a qual faz a "sombra" por debaixo do nosso
elemento.
Podemos simplesmente copiar e colar no nosso código porque
já vem com algumas configurações de tamanho, cor e
transparência para aplicarmos.
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght
@400;700&display=swap');
body {
background: linear-gradient(236.85deg, #041832 27.26%, #3468A
7 96.03%);
font-family: 'Roboto', sans-serif;
}
.container {

9.10 SOMBRA E BORDA 101

background: #ECF4FF;
margin: 64px;
border-radius: 20px;
box-shadows: 6px 6px 6px #0E1D2F;
}
Feito isso, rodaremos para ver que há uma pequena sombra
sob o elemento de fundo branco, a qual é mais visível quando o
fundo azul está em tom mais claro, dando uma certa profundidade
para o elemento.

Agora precisaremos estilizar a cor da fonte. Às vezes a cor
defaut é a preta mesmo, mas como dissemos sobre a cor branca, há
vários tons de preto também.
Vamos voltar ao Figma para pegarmos o código da cor preta
utilizada na página, e levá-lo para nosso .container mudar em
todos os elementos que contém.
Escreveremos a propriedade color: que é a cor dos textos,
seguido do código #1C1C1C da cor preta, diferente do
background: que diz respeito à cor do fundo.
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght
@400;700&display=swap');
body {
background: linear-gradient(236.85deg, #041832 27.26%, #3468A
7 96.03%);
font-family: 'Roboto', sans-serif;
}
.container {
background: #ECF4FF;
color: #1C1C1C;
margin: 64px;
9.11 COR DA FONTE

102 9.11 COR DA FONTE

border-radius: 20px;
box-shadows: 6px 6px 6px #0E1D2F;
}

A mudança foi bem sutil, mas queremos que seja fiel ao
design!

Precisamos fazer é alterar a posição da foto, que está muito
grande e totalmente colada na borda do container, e queremos que
tenha algum espaçamento e fique mais para dentro.
Para isso, usamos o padding: que atua de uma forma
diferente do margin: que utilizamos para termos uma margem
do elemento externo de fundo azul para o elemento interno de
fundo branco que estamos estilizando.
Já o padding: faz diferente; dá uma margem do nosso container
para os elementos que estão dentro dele. Colocaremos um valor de
sessenta e quatro pixels para vermos como fica.
Vamos salvar e rodar para observar a página.
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght
@400;700&display=swap');
body {
background: linear-gradient(236.85deg, #041832 27.26%, #3468A
7 96.03%);
font-family: 'Roboto', sans-serif;
}
.container {
9.12 EDITANDO A FOTO

9.12 EDITANDO A FOTO 103

background: #ECF4FF;
color: #1C1C1C;
margin: 64px;
border-radius: 20px;
box-shadows: 6px 6px 6px #0E1D2F;
padding: 64px;
}
Já está melhorando!
A primeira coisa que vamos estilizar logo depois da <div> é o
nosso <header> no arquivo HTML. Também colocaremos uma
class para ele, a qual poderá ser igual a "perfil" por exemplo.
<body>
<div class="container">
<header class= "perfil">
<img src;"https://github.com/rafaballerini.png" />
<div>
<h1>Rafaella Ballerini</h1>
<h3>Instrutora e desenvolvedora front-end #imersa
odev</h3>
</div>
</header>
<main>
</main>
</div>
</body>
Rafaella: Para a estilizarmos, iremos ao arquivo CSS. e a
chamaremos com o ponto, .perfil e abre as chaves.
Vamos estilizar do nosso <header> , mas se formos ao Figma,
não encontraremos nenhum elemento entre o container, a imagem
e o cabeçalho que consigamos identificar apenas visualmente.
Precisaremos estilizar o posicionamento dos elementos que
irão estar dentro do cabeçalho. Para isso, criaremos uma nova

104 9.12 EDITANDO A FOTO

classe no nosso elemento-pai <header> que engloba a imagem e
os títulos, e então estilizaremos os elementos-filhos internos.
Queremos posicioná-los da forma correta, e para isso
utilizaremos o chamado FlexBox , que é uma forma de
conseguirmos estilizar dinamicamente os elementos dentro de
uma tag-pai, que neste caso é o cabeçalho <header> .
Por meio deste FlexBox conseguimos dizer se queremos os
elementos na horizontal, alinhados verticalmente, centralizados e
etc. É uma forma simples, mas há diversas outras de posicionar,
como usando position: absolute ou grid:.
Mas o FlexBox é algo que facilita muito a vida, pois só dizemos
se queremos centralizado, alinhado à direita e até se queremos um
espaço entre eles por exemplo, e ele faz "sozinho".

O Flexbox é uma "caixa flexível" e parece mágica. Podemos
colocar muitas coisas nessa caixa para termos resultados bem
diferentes e personalizados.

Neste caso utilizaremos bem pouco, então ficará bem simples
mesmo. Não precisaremos ter um elementos numa posição de "x" e
"y", pois o FlexBox já posiciona da forma que queremos, basta
dizer. Para o usarmos, precisaremos colocar um display: flex
em .perfil primeiro de tudo. Isso colocamos realmente no
elemento-pai, que é o cabeçalho <header> .
Feito isso, estamos dizendo que vamos usar o FlexBox de fato.
Em seguida, utilizaremos a propriedade align-items: que serve

9.12 EDITANDO A FOTO 105

para "alinhar os itens" com center para os alinharmos ao centro.
Salvaremos e rodaremos para vermos a diferença na página.
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght
@400;700&display=swap');
body {
background: linear-gradient(236.85deg, #041832 27.26%, #3468A
7 96.03%);
font-family: 'Roboto', sans-serif;
}
.container {
background: #ECF4FF;
color: #1C1C1C;
margin: 64px;
border-radius: 20px;
box-shadows: 6px 6px 6px #0E1D2F;
padding: 64px;
}
.perfil {
display: flex;
align-items: center;
}
Com isso, todos os nossos elementos ficaram centralizados na
página, e antes o nome e a descrição estavam embaixo da imagem.
Falamos para o cabeçalho que temos elementos internos que
devem ficar centralizados na página, então ficarão ao centro. Mas
notaremos que o nome "Rafaella Ballerini" está alinhado com a
descrição embaixo.
Para entendermos, iremos ao arquivo HTML novamente. Os
elementos-filhos do <header> não são a imagem, o título e o
subtítulo, e sim a imagem e a <div> , a qual engloba outros dois
elementos, os <h1> e <h3> .

106 9.12 EDITANDO A FOTO

Então temos na verdade dois elementos dentro do cabeçalho
que estamos estilizando, então este segundo tem duas coisas em
comum: o título e o subtítulo, e por isso estão juntos um acima do
outro e não centralizados lado a lado.
Estamos fazendo isso justamente porque este é o formato que
está no nosso Figma. Portanto é bom termos cuidado quando
formos utilizar o FlexBox, prestando atenção aos elementos-filhos
e ao pai, mas com o tempo fica mais fácil.
Já centralizamos a imagem e o texto da maneira como
queremos, e a primeira coisa que faremos depois será deixar a
borda da foto redonda, como vemos no Figma.
Como já vimos, existe a propriedade border-radius: que
arredonda os limites de um elemento, até o formato circular. Na
aba lateral de "Inspect" com a parte "CSS", encontraremos o valor.
Dentro da nossa tag img, criamos um class e, pode ser, por
exemplo, "perfil-foto", isto é, <img class="perfil-foto" .
Na verdade, por vezes, o Figma tem um formato diferente de
apresentar algumas informações. Ele está colocando a sombra
como um filtro e nós podemos pegar as informações que queremos
da nossa sombra, que são as que estão dentro dos parênteses e

colocar a propriedade que já conhecemos no CSS, que é o box-
shadow. Portanto, você pode copiar as informações que estão entre

parênteses e colocar, no código, o box-shadow .
.perfil-foto {
border-radius: 460px;
max-height: 160px;
box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
}

9.12 EDITANDO A FOTO 107

Depois da nossa foto, a próxima coisa que estilizaremos é, de
fato, os escritos. O nosso nome e, também, o nosso subtítulo.
Agora, vamos ao nosso HTML verificar como ele está. E, após o
img, temos a div, que engloba essas duas coisas. Podemos,
também, colocar uma classe para a div, a classe título, <div
class="titulo"> .
Seguindo, vamos ao CSS. Escreveremos, .titulo, para
estilizarmos nossa classe. No Figma, notaremos que uma das
únicas coisas que precisamos estilizar em conjunto, título e
subtítulo, é puxá-los um pouco para a esquerda, porque estão um
pouco grudados no nosso CodePen com a imagem. É interessante,
portanto, puxarmos um pouco a margem da foto, para o nosso
título ficar mais para a esquerda.
Voltando ao CodePen, é possível verificar como está essa parte.
Está muito grudado! Sendo assim, colocaremos margem, que é a
distância do elemento exterior para o que estamos estilizando.
Neste caso, margin-left, porque é apenas a da esquerda. Não
queremos colocar margem para cima, para baixo ou para a direita.
A nossa margem terá 16px.
.titulo {
margin-left: 16px;
}
Separou um pouco mais! Ficou melhor. Agora, estilizaremos o
nosso h1 e o h3. Nós não utilizaremos o h1 em outro lugar,
porque, normalmente, precisamos apenas de um, e h3 também
não. Portanto, mais abaixo, nós usaremos outros tipos de tags.
Podemos até usar a mesma tag para que vocês vejam usos distintos
9.13 ESTILIZANDO OS TEXTOS

108 9.13 ESTILIZANDO OS TEXTOS

do h1 e h3, mas, algo interessante é unir a classe do elemento pai,
exterior.
Por exemplo, no nosso h1 e h3, o elemento de cima é o div, isto
é, <div class="titulo"> , que é o título. Nós podemos utilizar a
classe desse elemento, dar um espaço e colocar a tag que queremos
estilizar. Assim, deixaremos um pouco mais específico que apenas
a tag h1 estará dentro da classe título.
<header class= "perfil">
<img class="perfil-foto" src="https://github.com/rafaballer
ini.png" />
<div class="titulo">
<h1>Rafaella Ballerini</h1>
<h3>Instrutora e desenvolvedora front-end #imersaodev</h3
>
</div>
</header>
No nosso CSS, faremos .titulo h1 { . Nós queremos
estilizar a tag h1, que está necessariamente dentro de um elemento
com classe título. Estamos especificando de uma forma um pouco
diferente do que quando colocamos apenas uma classe para ela. É
uma maneira bem interessante e amplamente utilizada.
Seguindo, vamos estilizar a nossa fonte, o nosso escrito.
Primeiro, nós havíamos separado dois pesos diferentes de fonte, a
400 e 700. A 700 era, justamente, a do nosso título. Podemos até
verificar no Figma. Portanto, a primeira coisa que faremos é o
font-weight: 700;. Nós também consultaremos o tamanho da nossa
fonte, porque, por padrão, existe um tamanho de fonte que o
próprio CSS deixa na nossa página.
É interessante conferir qual foi o tamanho escolhido pela/o
designer. Para isso, vamos ao Figma verificar o tamanho da fonte

9.13 ESTILIZANDO OS TEXTOS 109

também. O tamanho é 36px. Vamos colocar font-size:, que é
"tamanho da fonte", igual a 36 px, font-size: 36px;, salvar e
executar. O tamanho é 24px e o peso, 400px.
.titulo h3 {
font-weight: 400;
font-size: 24px;
}
Acho que, nesse, teremos alguma diferença, já que ele está bem
maior. Vamos ver? O peso mudou bastante e o tamanho também.
Ficou muito legal a parte do cabeçalho e temos ainda muitos
detalhes pela frente, para deixar bem mais bonita parte abaixo.
Vamos para a segunda parte!

No HTML. existe a ul , que é uma lista não ordenada e a ol ,
que é uma lista ordenada. Neste caso, não há ordem, o 1 e 2 não
são passos de uma receita que devemos seguir. Ou seja, ela não
precisa estar ordenada, por isso, usaremos ul .
Vamos dar o título da nossa lista, <ul>Projetos<ul> , e, cada
linha dessa nossa lista representará um projeto. Vamos colocar
uma <li></li> , sem esquecer de fechá-la. Ao lado, colocaremos
o view do projeto, para focarmos no HTML. A primeira coisa que
faremos é criar uma tag âncora. ncora se refere às questões que
estamos super acostumados a fazer, mas nunca paramos para
pensar no que de fato está acontecendo.
Quando selecionamos determinada palavra, que abre uma
outra tag, estamos selecionando uma "tag âncora", representada
pela letra "a". Essa tag a, nós também adicionaremos e fecharemos,
9.14 CRIANDO A LISTA DOS PROJETOS

110 9.14 CRIANDO A LISTA DOS PROJETOS

<li><a></a></li> . Nós abrimos a li, abrimos a tag a e fechamos
a li. Dentro, nós colocaremos texto. Repare que não estamos
colocando o texto dentro a, mas, sim, entre eles. Nós colocaremos
o nome do projeto que fizemos.
Vamos inserir dois projetos que desenvolvemos durante a
imersão, por isso os colocarei. Um deles é o "Conversor de moeda",
<li><a>Conversor de moeda</a></li> . Já é possível ver como
aparecerá na tela: "Projetos", e, na linha abaixo, um marcador em
formato de círculo e, à frente, "Conversor de moeda". Não consigo
clicar nele, porque ainda não adicionamos ainda o link para onde
queremos ir no projeto.
Dentro da nossa tag a, colocaremos outra propriedade para
indicar o link da tag âncora, que colocaremos com href="" e, entre
aspas, o endereço do projeto. Para isso, abriremos o CodePen e
pegaremos o link para que, ao clicar, a pessoa seja direcionada para
a página do CodePen. Nós selecionaremos, portanto, este endereço
com "Ctrl + C", o colocaremos no href, salvamos e rodamos.
<main class="projetos">
<ul>Projetos<ul>
<li><a href="https://codepen.io/imersao-dev/pen/39044b884
fd63387c4b075671051ce1a">Conversor de moeda</a></li>
</main>
</div>
</body>
Repare que a escrita "Conversor de moeda" aparece até de
outra cor. Quando apertamos o link, somos direcionados para a
aula do Conversor de Moeda. Vamos retornar, pois, não queremos
ficar naquela aula agora. Podemos fazer isso para todas as outras
aulas. A diferença desse código para a próxima aula, por exemplo,

9.14 CRIANDO A LISTA DOS PROJETOS 111

será apenas o link e o nome.
Vamos testar com o projeto do Aluraflix, que ficou bonito.
Basta copiar e colar o código dele, salvar e executar.
<main class="projetos">
<ul>Projetos<ul>
<li><a href="https://codepen.io/guilhermeonrails/pen/poPZ
Gov?editors=0111">Conversor de moeda</a></li>
<li><a href="https://codepen.io/imersao-dev/pen/XWpWrod"
> Aluraflix</a></li>
</main>
</div>
</body>
Ao selecionar o primeiro link com o botão direito, acessamos o
projeto da aula 2, "Conversor de Moeda". Selecionando o segundo
link, da mesma forma, acessamos a aula 5, "Aluraflix". Nós fizemos
a estrutura, mas, esteticamente, está feio. Especialmente se
comparado com a parte do nosso header, em que a imagem está
estilizada, circular, nossos links não estão com uma boa
apresentação.

A primeira coisa que conseguimos verificar é: no nosso Figma,
temos uma imagem para cada projeto que fizemos. Essas imagens
não são exatamente imagens, mas, sim, emojis, que podemos
utilizar no nosso sistema operacional. É como se estivéssemos
copiando e colando o texto. Ele é lido, não é uma imagem, como a
src, que precisávamos copiar e colar.
De fato, é algo que conseguimos copiar como texto e colar.
Para isso, temos o site bag emoji, que conta com uma grande
quantidade de emojis. Nós podemos usar, por exemplo, o emoji da
9.15 EMOJIS

112 9.15 EMOJIS

calculadora de notas. Vamos pesquisar por "number". Podemos
passar o mouse por cima e copiar o próprio emoji. Algo
interessante para quem usa o Windows é que, basta apertar a tecla
"windows" e o ponto para algo mágico acontecer. Testem em casa.

No Chrome, no "Menu Edit" também temos emojis, uma lista
com vários. No “Edit”, encontramos "Emojis e símbolos", é
possível escolhê-los e usá-los.

No Conversor de Moeda, coloquei um emoji de número, mas,
no Aluraflix, o que vocês acham que eu deveria colocar? Sinta-se a
vontade para incluir o emoji que preferir.
Essa foi a primeira coisa que colocamos para deixar um pouco
melhor esteticamente. Vamos rodar e ver como ficou. Está ótimo,
mas ainda padrão. Podemos estilizar, lembrando de sempre pensar
primeiro nas coisas mais externas e depois nas mais internas. Após
a nossa tag de header, o nosso cabeçalho, nós tínhamos, em
seguida, a tag main, que tem o conteúdo principal da nossa página.
Nós daremos uma classe para ela.
Para isso, voltaremos ao HTML e colocaremos a classe dentro
da main, uma classe="projetos" , que será, de fato, o conteúdo
dos projetos que temos.
<main class="projetos">
<ul>Projetos<ul>
<li><a
No CSS, nós estilizaremos o .projetos e temos muitas coisas
a pensar pela frente. A primeira delas é, de fato, o nosso flexbox,

9.15 EMOJIS 113

que estávamos usando para posicionar os elementos que estão
dentro dessa tag, que, no caso, formarão a nossa lista. Então, nós
usamos o display: flex; para indicarmos que queremos usar o
flexbox.
Seguindo, nós utilizaremos uma propriedade do flexbox que é
o flex-direction, a direção dos elementos que estarão dentro. Como
eu já havia comentado, pode ser horizontal, vertical, enfim,
existem várias propriedades e nós disponibilizamos o link de um
artigo para que vocês confiram todos.
Nesse caso, nós utilizaremos uma direção vertical, de coluna,
por isso, adicionaremos column, pois queremos que a nossa lista
fique estilizada nesse sentido, o display: flex normalmente vem
como horizontal, portanto, é importante ajustar o flex-direction
como column.
.projetos {
display: flex;
flex-direction: column;
}
Além disso, vamos alinhar todos os nossos elementos no
centro. Usaremos a propriedade do align-items: center;, para
deixá-los mais centralizados. Agora, basta salvar e rodar. Vamos
ver como ficará com essa estilização.

114 9.15 EMOJIS

É preciso cuidado, porque, pensando sobre o design, eu sei
que eles estudam muitas coisas, então, por trás existem
diversos motivos pelo qual é centralizado, por exemplo.
Motivos que nós não entendemos, mas que estão relacionados
com experiência do usuário e que, realmente, fazem muito
sentido. O ideal é sempre perguntar, "será que não seria legal
mudar?" e entender o motivo de estar de determinada
maneira.

A imagem, a questão de pegar um h3 e um h1 de uma
determinada class, ficou muito interessante. Nós fizemos esse
layout do zero.
Tudo certo? Então é hora de praticar!

Aprendemos a mexer no Figma e transformar o design em
código;
Entendemos melhor como funciona HTML e CSS;
Estruturamos o nosso portfólio com HTML, aprendendo
todas as tags necessárias pra isso;
Estilizamos o nosso portfólio com CSS, conhecendo os
seletores, propriedades e valores necessários para isso.
Clique neste link para acessar o código completo no Codepen.
9.16 RESUMO

9.16 RESUMO 115

CAPÍTULO 10

Estamos na nossa última aula da imersão! Eu sei que ainda
vamos nos ver por aqui, mas queria já deixar os parabéns por você
ter feito tudo durante essas duas semanas. Não é fácil aprender
programação, e o fato de você ter chegado até aqui já é muita coisa.

Vamos terminar o projeto que fizemos ontem, que foi nosso
portfólio. Enquanto fazemos isso, ainda vamos incluir outras
coisas bem legais.
A ideia dessa aula, vocês podem ver nessa tela do Figma. Ter
um botão para alterar o tema para claro ou escuro (dark mode) e
uma aba de projetos (que vamos evoluir ainda mais. Além disso,
nessa parte do projeto, conseguiremos visualizar trechos do código
e executar o projeto feito, como a calculadora, o mentalista e assim
por diante.

Portfólio é algo para ser bonito, não é? Precisa ser convidativo,
além de ter links para seu e-mail, seu Linkedin, algumas coisas que
PORTFÓLIO

10.1 OBJETIVO DA AULA

10.2 ESTILIZANDO A LISTA DE PROJETOS

116 10 PORTFÓLIO

passei no desafio. Inclusive, se você quiser estilizar com outras
cores, fique à vontade. No CSS, temos uma classe .projetos que
engloba toda a parte azul do Figma, onde temos os nossos projetos.
Atualmente temos nela um display: flex , que posiciona os

elementos filhos dentro dele (no caso a nossa lista), e o flex-
direction: column , que define a direção como colunas.

.projetos {
display: flex;
flex-direction: column;
}
Além de posicionar os elementos, precisamos colocar nosso
background. No Figma, vemos que a cor dessa parte é o azul
(linear-gradient), o mesmo que tínhamos usado no .
.projetos {
display: flex;
flex-direction: column;
background: linear-gradient(230.65deg, #499cfe 27.49%, #9cc8fc
83.19%);
}
Vamos salvar e rodar para verificarmos como está ficando.
Com essa alteração, a seção "Projetos" ganhará um fundo com um
gradiente azul. Uma coisa que está incomodando um pouco é que
nossa foto de perfil está muito "grudada" nessa caixa, e seria
interessante distanciarmos um pouco. Como vimos anteriormente,
isso é possível adicionando uma margem, nesse caso margin-top
para distanciarmos da parte de cima.
.projetos {
display: flex;
flex-direction: column;
background: linear-gradient(230.65deg, #499cfe 27.49%, #9cc8fc
83.19%);
margin-top: 32px;

10.2 ESTILIZANDO A LISTA DE PROJETOS 117

}
Legal, bem melhor. Também podemos ajustar os elementos
dentro de .projetos um pouco mais espaçados, algo que faremos
com o padding .
.projetos {
display: flex;
flex-direction: column;
background: linear-gradient(230.65deg, #499cfe 27.49%, #9cc8fc
83.19%);
margin-top: 32px;
padding: 32px;
}
Quando utilizamos apenas padding ou apenas margin, estamos
adicionando essa propriedade a todos os cantos. Já quando usamos
uma especificação, como margin-top, estamos aplicando a um
canto específico (cima, nesse caso). Vamos analisar o projeto no
Figma para entendermos o que mais podemos estilizar. Ainda
temos um link de redirecionamento para os projetos, mais tarde
faremos com que as telas do CodePen apareçam. Por enquanto
vamos focar na caixa azul dos nossos projetos. Ainda falta
incluirmos um border-radius, que deixa o elemento arredondado,
e o box-shadow, que faz uma sombra na parte inferior. Vamos
copiar esses elementos e incluir em nosso .projetos.
.projetos {
display: flex;
flex-direction: column;
background: linear-gradient(230.65deg, #499cfe 27.49%, #9cc8fc
83.19%);
margin-top: 32px;
padding: 32px;
box-shadow: 2px 2px 4px rgba(16, 16, 16, 0.42);
border-radius: 20px;
}
.projetos-titulo {

118 10.2 ESTILIZANDO A LISTA DE PROJETOS

list-style: none;
font-weight: 700;
font-size: 36px;
}
Já temos as bordas arredondadas e a sombra, e agora
precisamos estilizar os textos, tanto o título da lista quanto os
elementos dela. Primeiramente, criaremos uma classe para o título
da lista, que é a nossa
. No HTML, criaremos uma class="projetos-titulo"
<main class="projetos">
<ul class="projetos-titulo">Projetos<ul>
No CSS, incluiremos um .projetos-titulo e abriremos chaves
para começarmos a estilizar.
.projetos-titulo {
}
Primeiramente, removeremos o estilo dessa lista, o que inclui o
ponto e a indentação. Quando queremos estilizar e personalizar
um elemento, é interessante removermos a decoração padrão que
vem do HTML e do CSS, algo que fazemos com list-style: none (de
"nenhum").
.projetos-titulo {
list-style: none;
}
Em seguida, alteraremos o peso da fonte (font-weight) para
700, seguindo o nosso projeto do Figma. Além disso, alteraremos o
tamanho da fonte (font-size) para 36px.
.projetos-titulo {
list-style: none;
font-weight: 700;

10.2 ESTILIZANDO A LISTA DE PROJETOS 119

font-size: 36px;
}
Ficou mais ou menos, né? O título tá legal, mas os outros
elementos estão estranhos. Os outros ainda precisamos arrumar.
Agora adicionaremos uma classe para os itens da lista, que são
nossos
, chamada projetos-item. Vamos criar uma estrutura que será
reutilizada em outras partes.
Assim como fizemos ali em cima, colocar o
dentro de todos os projetos, por exemplo, como fizemos o

<main class="projetos">
<ul class="projetos-titulo">Projetos<ul>
<li class="projetos-item"><a
href="https://codepen.io/guilhermeonrails/pen/poPZGov?editors=011
DENTRO DE TODAS AS
DE PERFIL, MAS AMBOS
OS JEITOS FUNCIONAM.
AQUI VAMOS MOSTRAR
COMO UTILIZAR UMA
CLASSE PARA MAIS DE
UM ELEMENTO.

120 10.2 ESTILIZANDO A LISTA DE PROJETOS

11">Conversor de Moeda</a></li>
<li class="projetos-item"><a
href="https://codepen.io/guilhermeonrails/pen/yLbxpwm">Aluraflix<
/a></li>
</li>
Vamos estilizar o nosso item da lista. No CSS, criaremos um
.projetos-item e abriremos chaves. Para removermos os pontos
antes de cada elemento da lista, usaremos o list-style-type: none.
.projetos-item {
list-style-type: none;
}
Além disso, alteraremos o tamanho da fonte (font-size) e o

peso (font-weight). Por fim, temos também uma propriedade line-
height, que é a altura da linha, que é interessante adicionarmos.

Dessa forma, teremos mais distanciamento entre cada linha da
nossa lista.
.projetos-item {
list-style-type: none;
font-size: 24px;
font-weight: 400;
line-height: 48px;
}
Falta estilizarmos as "âncoras" dos nossos hiperlinks, que
deixam um sublinhado no texto. Para alterarmos isso, usaremos
uma classe .projetos-item a. Assim, toda tag que esteja dentro de
um elemento projetos-item terá essa estilização.
Adicionaremos um color: #1c1c1c para alterarmos a cor
do texto para a mesma dos outros elementos e removeremos a
decoração do texto com text-decoration: none.
.projetos-item a {
color: #1c1c1c;

10.2 ESTILIZANDO A LISTA DE PROJETOS 121

text-decoration: none;
}
Com isso, nosso projeto estará padronizado e poderemos clicar
sobre o link do "Conversor de Moeda" da nossa página.
Imediatamente já identifica como um link, e direciona para a
nossa página do Conversor de Moedas.
Rafaella: Exatamente, e poderíamos colocar links do LinkedIn,
Facebook e outras páginas, basta mudar o href que colocamos o
link do CodePen.

Ficou bem bacana este link sem o texto padrão que vem do
HTML. Mas para nosso projeto principal, abriremos uma lista com
caixinhas contendo os projetos que fizemos para visualizarmos.
Ou seja, queremos abrir apenas um pedaço do projeto que
estamos pegando do nosso projeto no CodePen para exibir. Para
isso, clicaremos com o botão direito sobre o retângulo que aparece
com os projetos no Figma e abriremos o Conversor de Moedas em
uma nova aba.
Neste projeto que fizemos, encontraremos um botão chamado
"Embed" na barra inferior, ao lado de "Fork". Clicando em
"Embed", abriremos uma caixa chamada "Embed This Pen" que
apresenta algumas opções, como a de "Theme" para escolhermos o
tema, que pode ser "Default", "Light", "Dark" ou "User Default".
Na aba de "HTML (Recommended)", encontraremos uma tag
com várias coisas, como o usuário, o tamanho que irá aparecer
10.3 ABRINDO OS PROJETOS NO PORTFÓLIO

122 10.3 ABRINDO OS PROJETOS NO PORTFÓLIO

e etc.
Copiaremos todo este conteúdo, que não é CSS nem JavaScript,
e sim um parágrafo HTML. Em nosso projeto, abriremos a parte
do HTML e tiraremos a tag-âncora .
Ao invés da tag , deixaremos a
ainda com o título de "Conversor de Moeda" para não o
perdermos, pois também temos isso no Figma.
Tiraremos o href também e colocaremos a tag
nas duas linhas de
.
//código omitido
<main class="projetos">
<ul class="projetos-titulo">Projetos"</ul>
<li class="projetos-item"><p> Conversor de moeda</p><
/li>
<li class"projetos-item"><p> Aluraflix</p></li>
</main>
</div>
</body>
De volta à caixa "Embed The Pen", copiaremos todo o
conteúdo da tag
com a classe "codepen" e todas as propriedades, e depois
colaremos embaixo da
que contém os títulos no nosso projeto.
Rafaella: Podemos pular uma linha se quisermos, e depois
salvamos.

10.3 ABRINDO OS PROJETOS NO PORTFÓLIO 123

//código omitido
<main class="projetos">
<ul class="projetos-titulo">Projetos"</ul>
<li class="projetos-item">
<p> Conversor de moeda</p>
<p class="codepen" data-height="300" data-theme-i
d="dark" data-default-tab="html,result" data-slug-hash="poPZGov"
data-user="guilhermeonrails" style="height: 300px; box-sizing: bo
rder-box; display: flex; align-items: center; justify-content: ce
nter; border2px solid; margin: 1em0; padding: 1em;">
<span> See the Pen <a href="https://codepen.i
o/guilhermeonrails/pen/poPZGov">
Conversor de moedas - ID3</a> by @guilima
dev (<a href="https://codepen.io/guilhermeonrails">@guilhermeonra
ils</a>)
on <a href="https:codepen.io">CodePen</a>.</s
pan>
</p>
<script async src="https://cpwbassets.codepen.io/
assets/embed/ei.js"></script>
</li>
<li class"projetos-item"><p> Aluraflix</p></li>
</main>
</div>
</body>
Na página, veremos que aparece o HTML, o CSS e o JavaScript
do projeto Conversor de Moeda. Ao centro e acima deste espaço
com o código, há o botão de "Result" para vermos a página do
Conversor de fato.
Se colocarmos um valor "10" no campo de "Insira o valor" por
exemplo, e depois clicarmos em "Converter", receberemos a
mensagem de que "o resultado em real é R$50".
Ou seja, estamos rodando o nosso projeto dentro do portfólio
direto pelo CodePen. Podemos escolher como queremos deixar o
título, o alinhamento, o tamanho, é interessante explorar!

124 10.3 ABRINDO OS PROJETOS NO PORTFÓLIO

Podemos estilizar o quanto quisermos, mas por enquanto está
bom.

Para vermos funcionando de verdade, abriremos o outro
projeto chamado "Aluraflix" feito no quinto dia da Imersão em
uma outra aba. Ao lado do botão "Fork", encontraremos o botão
"Embed" novamente.
Clicando sobre este, teremos a caixa "Embed This Pen"
também com a geração de um texto na tag
fornecido na aba "HTML (Recommended)". Copiaremos todo
este código da tag
e colaremos em nosso projeto, da mesma forma que fizemos
com o "Embed" do Conversor de Moeda.
Inclusive, esse botão "Embed" existe no YouTube e em outros
lugares quando quisermos colocar um vídeo, um CodePen mesmo,
uma postagem do Instagram ou Facebook e etc.
Usamos o termo "embedar" para fazer isso no dia a dia, ou seja,
colocamos algo dentro de outra coisa.
//código omitido
<main class="projetos">
<ul class="projetos-titulo">Projetos<ul>
<li class="projetos-item">
<p> Conversor de moeda</p>
<p class="codepen" data-height="300" data-theme-id="d
ark" data-default-tab="html,result" data-slug-hash="poPZGov" data
-user="guilhermeonrails" style="height: 300px; box-sizing: border

10.3 ABRINDO OS PROJETOS NO PORTFÓLIO 125

-box; display: flex; align-items: center; justify-content: center
; border: 2px solid; margin: 1em 0; padding: 1em;">
<span>See the Pen <a href="https://codepen.io/guilh
ermeonrails/pen/poPZGov">
Conversor de moedas - ID3</a> by @guilimadev (<
a href="https://codepen.io/guilhermeonrails">@guilhermeonrails</a
>)
on <a href="https://codepen.io">CodePen</a>.</spa
n>
</p>
<script async src="https://cpwebassets.codepen.io/ass
ets/embed/ei.js"></script>
</li>
<li class="projetos-item">
<p> Aluraflix</p>
<p class="codepen" data-height="300" data-theme-id="d
ark" data-default-tab="html,result" data-slug-hash="yLbxpwm" data
-user="guilhermeonrails" style="height: 300px; box-sizing: border
-box; display: flex; align-items: center; justify-content: center
; border: 2px solid; margin: 1em 0; padding: 1em;">
<span>See the Pen <a href="https://codepen.io/guilh
ermeonrails/pen/yLbxpwm">
Aluraflix - dia 5</a> by @guilimadev (<a href="
https://codepen.io/guilhermeonrails">@guilhermeonrails</a>)
on <a href="https://codepen.io">CodePen</a>.</spa
n>
</p>
<script async src="https://cpwebassets.codepen.io/ass
ets/embed/ei.js"></script>
</li>
</main>
</div>
</body>
Pronto, agora temos os dois projetos sendo carregados na
página, o Conversor de Moeda e o Aluraflix.

126 10.3 ABRINDO OS PROJETOS NO PORTFÓLIO

Não faremos para todas as aulas da imersão mas como o
processo é bem tranquilo e repetitivo, fica o desafio para
vocês!

Caminhamos um pouco nesta parte do "Embed", e ficou bem
legal. Mas ainda queremos saber como fazer um botão de alterar
tema para clicarmos e mudarmos a cor de fundo da página para
termos o tema "dark" por exemplo, parecido com o que há no
GitHub.
Para fazermos este botão no nosso cabeçalho, voltaremos ao
Figma para vermos como deve ser.
Ele ficará no canto superior direito do container com a legenda
"Alterar o tema". De volta ao código, acessaremos a tag
e criaremos uma outra
após o título.
Portanto serão três elementos principais no nosso cabeçalho: a
imagem, o título com o nome e o que fazemos, além do botão que
altera o tema.
Essa divisão terá uma classe chamada "tema" que iremos
estilizar. Dentro dela, colocaremos um botão de fato com a tag .
Depois, usaremos o onClick que vimos ao longo de todo o
10.4 DARK MODE

10.4 DARK MODE 127

curso. Sempre pegávamos o que já vinha no código feito por outra
pessoa no HTML e CSS com toda a função.
Desta vez criaremos a função que utilizaremos depois para
podermos alterar o tema, a qual pode ser chamada "mudaTema()".
Não faremos isso imediatamente porque vamos estilizar
primeiro, mas já deixaremos a função dentro do onClick no
JavaScript que usaremos.
Fecharemos essa tag
e depois colocaremos o texto "Alterar tema" para a

pessoa saber o que o botão faz.
Podemos salvar e rodar para vermos como está até agora.
<body>
<div class="container">
<header class="perfil">
<img class="perfil-foto" src="https://github.com/rafaball
erini.png" />
<div class="titulo">
<h1>Rafaella Ballerini</h1>
<h3>Instrutora e desenvolvedora front-end #imersaodev</
h3>
</div>
<div class="tema">
<button onclick="mudaTema()">Alterar Tema</button>
</div>
</header>
//código omitido
</div>
</body>
A primeira coisa que faremos é estilizar de fato. Vamos ao
arquivo com o código CSS no CodePen, e o ideal seria seguirmos

128 10.4 DARK MODE

uma linearidade dos elementos que vamos escrever para sabermos
onde podemos achá-los quando entrarmos no HTML.
Então é interessante irmos até a parte do cabeçalho e alterar de
lá mesmo. Temos o .perfil, o .perfil-foto, .titulo, .titulo h1 e o .título
h3.
Antes de .projetos, colocaremos a estilização da nossa classe de
.tema. Entre as chaves, colocaremos o button para estilizarmos
diretamente de dentro da classe, a qual é a
que engloba esse botão.
Precisaremos usar algumas propriedades novas, pois se trata da
estilização de um botão. Primeiro, vamos alinhá-lo de uma forma
diferente.
Os itens que já alinhamos estão todos à esquerda, e queremos
que só o botão fique sozinho à direita. Como estamos estilizando
com Flexbox, existe também a propriedade align-self: para isso,
sendo flex-end para deixarmos ao final no canto direito do
conjunto.
Vamos salvar e executar para vermos onde ficou.
//código anterior omitido
.titulo h1 {
font-weight: 700;
font-size: 36px;
}
.titulo h3 {
font-weight: 400;
font-size: 24px;
}

10.4 DARK MODE 129

.tema button {
aligh-self: flex-end;
}
.projetos {
display: flex;
flex-direction: column;
background: linear-gradient(230.65deg, #499cfe 27.49%, #9cc8fc
83.19%);
margin-top: 32px;
padding: 32px;
box-shadow: 2px 2px 4px rgba(16, 16, 16, 0.42);
border-radius: 20px;
}
//código posterior omitido
Ficou bem no canto direito mesmo.

O próximo passo é irmos ao Figma para vermos como o botão
está no projeto. Clicando sobre este, iremos até as configurações de
"Typography" na aba lateral e veremos qual é o tamanho da fonte
usada. O tamanho é vinte e quatro pixels com peso de
quatrocentos.
Então vamos estilizar isso. podemos copiar do Figma e colar no
nosso arquivo CSS também. Portanto o font-size: fica 24px e o
font-weight é 400.
Vamos rodar e ver o resultado na página.
//código anterior omitido
.titulo h1 {
font-weight: 700;
font-size: 36px;
}
10.5 AJUSTANDO A TIPOGRAFIA

130 10.5 AJUSTANDO A TIPOGRAFIA

.titulo h3 {
font-weight: 400;
font-size: 24px;
}
.tema button {
align-self: flex-end;
font-size: 24px;
font-weight: 400;
}
.projetos {
display: flex;
flex-direction: column;
background: linear-gradient(230.65deg, #499cfe 27.49%, #9cc8fc
83.19%);
margin-top: 32px;
padding: 32px;
box-shadow: 2px 2px 4px rgba(16, 16, 16, 0.42);
border-radius: 20px;
}
//código posterior omitido

Outra estilização que podemos fazer é darmos uma distância
um pouco melhor do escrito para as bordas do botão, para que o
texto fique um pouco mais centralizado.
Isso é o padding:, pois estamos alterando o elemento que
queremos e estamos colocando o que está dentro dele mais para
dentro.
Colocaremos esta propriedade no .tema button, e colocaremos
8px seguido de 16px. Estamos colocando duas informações nos
dois números, em que a primeira diz respeito à distância que há
entre o topo e o elemento interno, e entre a base e o elemento
10.6 BORDAS DO BOTÃO

10.6 BORDAS DO BOTÃO 131

interno.
Já a segunda informação é relativa às distâncias laterais entre os
limites laterais do botão e o elemento interno do texto. A mesma
coisa acontece para o margin:, então se quisermos dar uma
margem acima e embaixo e outra de um lado e de outro,
colocamos dois valores seguidos para cada um respectivamente.
Outra coisa é que o botão está com o fundo cinza, diferente do
projeto no Figma, então precisamos encontrar a cor certa para
usarmos. Ao selecionarmos o botão de "Alterar tema", teremos o
valor na parte "Colors" para copiarmos.
Portanto o background: será da cor #ECF4FF .
O próximo passo é transformarmos as bordas do botão em
arredondadas com o já conhecido border-radius:. De volta ao
Figma, copiaremos o valor da propriedade de 100px e colaremos
no nosso .tema button.
Outra coisa que faremos é passar a nossa borda, pois ela ainda
está um pouco simples demais, e podemos deixá-la melhor
definida. Podemos escolher sua espessura, seu tamanho e a cor que
queremos.
//código anterior omitido
.titulo h1 {
font-weight: 700;
font-size: 36px;
}
.titulo h3 {
font-weight: 400;
font-size: 24px;
}

132 10.6 BORDAS DO BOTÃO

.tema button {
align-self: flex-end;
font-size: 24px;
font-weight: 400;
padding: 8px 16px;
background: #ECF4FF;
border-radius: 100px;
}
.projetos {
display: flex;
flex-direction: column;
background: linear-gradient(230.65deg, #499cfe 27.49%, #9cc8fc
83.19%);
margin-top: 32px;
padding: 32px;
box-shadow: 2px 2px 4px rgba(16, 16, 16, 0.42);
border-radius: 20px;
}
//código posterior omitido
Porém, ainda não conseguimos colocar o botão no exato canto
superior direito que precisamos, pois por enquanto está apenas
alinhado à direita e centralizado horizontalmente com os demais
elementos do cabeçalho.
Então vamos separar em mais uma divisão, e em uma teremos
o nome e o título com o subtítulo, e em outra teremos o botão com
suas configurações.
De volta ao nosso arquivo HTML, englobaremos a foto com o
texto do cabeçalho dentro de uma tag
abaixo do
, cuja classe chamaremos de "perfil" com as informações do perfil.
Já o

10.6 BORDAS DO BOTÃO 133

será chamado de "cabeçalho", pois englobará os elementos de perfil e o botão de alterar o tema.
<body>
<div class="container">
<header class="cabecalho">
<div class="perfil">
<img class="perfil-foto" src="https://github.com/rafaball
erini.png" />
<div class="titulo">
<h1>Rafaella Ballerini</h1>
<h3>Instrutora e desenvolvedora front-end #imersaodev</
h3>
</div>
</div>
<div class="tema">
<button onclick="mudaTema()">Alterar Tema</button>
</div>
</header>
//código omitido
</div>
</body>
Perfeito. Vamos ver como o nosso CSS está. O perfil agora vai
ser a nossa imagem junto com as nossas informações. Vamos
precisar mudar a disposição dos elementos, podemos apagar o
align-items: center; e acima desse perfil vamos estilizar o
nosso cabeçalho.
Lembrando que nosso cabeçalho tem a tag perfil e a tag tema,
que é o botão e o conjunto de foto com os títulos. Nesse
.cabecalho do CSS colocaremos display: flex , para
posicionar os elementos, e justify-content: space-between ,
para justificar os elementos. Queremos que tenha espaço entre os
elementos, com o space-between colocaremos um espaço entre
o perfil, com a foto e o título, e o nosso tema.
.cabecalho {
display: flex;

134 10.6 BORDAS DO BOTÃO

justify-content: space-between;
}
Já mudou. Comparado com o projeto do Figma está correto.
Agora queremos fazer o botão funcionar. Como fazemos a parte
do JavaScript para ele funcionar?

Por enquanto, ao clicar no botão só aparece no console que
"mudaTema is not defined". A primeira coisa a fazer é criar essa
função function mudaTema(). Vamos fazer alguma coisa dentro
dessa função que vai manipular o CSS. Como fazemos isso? Vamos
criar uma função no Javascript chamada mudaTema .
function mudaTema() {
}
Assim como temos aquele document.getElementById() ,
document.getElementByName() , entre outras coisas que usamos
no JavaScript para manipular o HTML e o CSS, temos o
document.body() . Esse body é a tag do HTML, que engloba
todos os elementos que são visíveis na nossa página.
E é justamente aí que queremos atacar. Queremos pegar o
nosso body e atribuir uma classe para ele. Ao atribuir essa classe,
teremos no nosso CSS um CSS para essa classe. Vamos criar uma
"classe dark", por exemplo. Vamos escrever no nosso CSS a
estilização para essa classe, mas é o JavaScript que vai decidir
quando essa classe entra e quando ela sai. Nesse caso, será no
onClick.
No onClick do nosso botão de tema queremos alterar a classe
10.7 MUDANDO A COR

10.7 MUDANDO A COR 135

do nosso body. Então colocaremos
document.body.classlist.toggle(), toggle é o comando que faz isso,
traduzido para o português significa "alternância". Vamos alternar
a classlist, a classe do nosso elemento body, e colocar dark como
parâmetro para o nosso elemento.
function mudaTema() {
document.body.classList.toggle("dark");
}
Porém, ainda não vai mudar nada em relação ao nosso tema.
Porque ainda não fizemos a estilização da classe dark. Ao clicar no
botão, ele vai mudar para a classe dark, mas ainda não temos a
estilização desse estilo no CSS.

Vamos escrever esse código no CSS abaixo do código que já
temos. Vamos inserir o .dark . Ao estilizar esse .dark , o que
estamos estilizando de fato? A nossa tag body quando ela tiver a
classe dark. O que normalmente estilizamos na tag body é o
background, a fonte - a fonte vai ficar a mesma, não precisa trocar
- mas o background vamos trocar. Vamos verificar no Figma qual
é a cor do background do tema escuro.
Vou clicar na cor do dark mode e copiar o código CSS da cor e
do linear-gradient do background para colar no nosso CSS.
.dark {
background: linear-gradient(236.85deg, #375b86 27.26%, #6b87a9
96.03%);
}
Vamos salvar e rodar para ver se o botão está funcionando?
10.8 CSS DO DARK MODE

136 10.8 CSS DO DARK MODE

O fundo já está sendo alterado. Vamos, agora, estilizar o resto
das coisas. Abrindo o Figma para ver o que mais precisamos alterar
no nosso CSS. Precisamos trocar o nosso container, que antes era o
espaço branco, e trocar a cor da fonte e a cor do botão. Já pode
copiar o código CSS da cor do background do container e vamos
voltar para o CodePen.
Agora temos que lembrar que cada elemento será estilizado de
uma forma específica. Podemos colocar o .container da classe dark,
então .dark .container. Vamos colocar o código da cor que você
copiou do background. Além disso, também trocaremos a cor da
fonte, vamos pegar lá no Figma qual é a cor da fonte no modo
dark.
.dark {
background: linear-gradient(236.85deg, #375b86 27.26%, #6b87a9
96.03%);
}
.dark .container {
background: #333439;
color: #f6f6f6;
}
Agora ficou legal. A fonte do texto de "Projetos" também ficou
branca no modo dark, mas ficou estranho. O pessoal que fez o
layout no Figma também percebeu que era melhor deixar essa
fonte dos projetos e os nomes dos projetos em uma fonte escura.
Vamos ver no HTML qual era a tag dessa parte de projetos.
Podemos pegar essa classe="projetos", porque queremos trocar a
cor de todos os elementos. Então vamos escrever no CSS, .dark
.projetos e colocar color escura igual a que está no Figma.
.dark .container {
background: #333439;

10.8 CSS DO DARK MODE 137

color: #f6f6f6;
}
.dark .projetos {
color: #1c1c1c;
}

Vamos salvar e rodar. Agora não está mais mudando a cor da
fonte dos projetos. Outra coisa que devemos fazer é alterar o botão,
porque no dark mode ele também fica escuro.
Podemos copiar o código da cor do botão no Figma.
Vamos criar o .dark .tema button , e dentro dele a cor do
background. Além disso, temos que mudar a cor da fonte do
botão. Além disso, podemos mudar também a borda do botão com
o border de 2px, que é o tamanho da borda; solid, para ser uma
borda sólida e a cor pode ser um pouco mais clara.
.dark .tema button {
background: #1c1c1c;
color: #ffffff;
border: 2px solid #f7f7f7;
}
Vamos salvar e rodar. Clica em "Alterar Tema".

Ficou bem legal. Vamos colocar esse projeto no ar para que
qualquer pessoa, com o link que vamos passar, possa visualizar
esse layout.
10.9 DARK MODE NO BOTÃO

COLOCANDO O PORTFÓLIO NO AR

138 10.9 DARK MODE NO BOTÃO

Quando temos um projeto web, que é o caso do projeto que
estamos desenvolvendo. Aqui está dentro do CodePen, que é uma
ferramenta web e você só vai ver no CodePen. Às vezes queremos
colocar isso no nosso site ou tem outros sistemas que permitem
que você faça isso.
Então, quando queremos hospedar, existem vários serviços de
cloud (na nuvem), tem ferramenta da Amazon, da Oracle, do
Azure, do Google, tem esses grandes. Mas tem serviços menores de
host de website. Tem algumas ferramentas para devs, como o
GitHub, que até dá um espaço gratuito para fazermos isso. Não foi
à toa que mostramos o GitHub na aula passada e estamos te
provocando para usar o tal do GitHub porque, querendo ou não,
você vai acabar usando GitHub na sua vida.
Agora o ideal é pegar esse site que fizemos e colocar no ar. Já
está no ar no CodePen, mas vamos fazer de um jeito um pouco
mais tradicional, mais profissional, vamos chamar assim.
E o que precisamos para conseguir vincular esse projeto que
fizemos no CodePen lá no LinkedIn e ter um link para mostrar
para várias outras pessoas?

A primeira coisa a fazer é acessar o GitHub. Eu já estou logado.
Mas se você não estiver, no canto superior direito vai ter um botão
Sign up, clica nele e faz um cadastro para logar no GitHub.
10.10 CRIANDO UMA CONTA NO GITHUB

10.11 CRIANDO UM REPOSITÓRIO

10.10 CRIANDO UMA CONTA NO GITHUB 139

Para conseguirmos pegar o código no CodePen e passar para o
GitHub, vamos criar uma pasta, também chamada de repositório,
para manter todos os códigos do CodePen. Para criar essa pasta,
vou clicar no ícone de mais, no canto superior direito, e clicar em
"New Repository". Vamos ter que escolher um nome para esse
repositório. Qual vai ser o nome?
Pode ser "certificard", é um bom nome para o nosso
certificado.
Lembrando que não podemos ter dois repositórios com o
mesmo nome, o GitHub faz essa verificação. Agora, não vou me
preocupar com os outros campos, a descrição do projeto, se ele é
público ou privado, readme, gitgnore.
Em seguida, aparecerá uma página com algumas linhas de
código. É possível enviar os arquivos do CodePen para o GitHub
só com linhas de código no terminal. Não é o que vamos fazer. Nós
vamos fazer upload de arquivos existentes, clicando em "uploading
an existing file". Vai aparecer um quadro para passarmos nossos
códigos para o GitHub.

Vamos precisar fazer download do nosso código no CodePen.
No canto inferior direito do CodePen existe um botão "Export" ,
ao clicar nele temos as opções de salvar como Gist do GitHub, não
é o que queremos, e tem o "Export.zip" que é a opção que
escolheremos. Quando eu clicar em "Export.zip" , ele vai
preparar o ZIP e avisar que já podemos fazer o download dos
10.12 DOWNLOAD DO PROJETO DO
CODEPEN

140 10.12 DOWNLOAD DO PROJETO DO CODEPEN

arquivos.
Ao abrir esse arquivo que baixamos, "certificardaula-10.zip".
Ele vai extrair. Se você estiver usando Windows, pode usar o
WinRar ou algo do tipo para extrair os arquivos do ZIP. Dentro
dele tem uma série de arquivos, tem o "license.txt";
"README.markdown"; uma pasta "src" com index, script e style; e
a pasta "dist", que é a pasta que vamos usar.
Vamos entrar na pasta "dist". Quando abrimos o arquivo
index.html do dist, na linha 6, temos o seguinte código:
<link rel="stylesheet" href="./style.css">
Ou seja, ele já tem um link que "conversa" com o arquivo css.
Se abrimos o source direto, ele não tem. Vamos abrir para
verificarmos, e também ao link, como o VSCode. Esse link traz
exatamente o código que estávamos vendo anteriormente, não é o
que queremos. Nós queremos o código do dist já com CSS e
JavaScript funcionando.
Então, vamos selecionar, não do src, mas do dist, os três
arquivos e arrastar para o VSCode. Selecionaremos os três links do
dist e arrastaremos para dentro do VSCode. Assim, ele pegará os
três arquivos e mandará para o GitHub. Mais abaixo, há uma
palavra que nos depararemos sempre como Devs que é Commit .

O Commit é a linha do tempo. No "Commit changes" eu
"adicionei os arquivos do certificard". Isso nos permite perceber as
alterações que estamos realizando no GitHub, temos o commit em
uma foto - que nós colocamos - dos arquivos que fizemos e
10.13 COMMIT
