<div align='center'>
<h1>
Banco de dados para <br>
questões do ENEM <br>
(Exame Nacional do Ensino Médio)
</h1>
<h3>Uma proposta de acesso aprimorado à informação.</h3>
[] []
</div>

---

<div align='center'>

<br>

 <h2>Esclarecimentos</h2>

<div align='left'>

- *ENEM* é uma iniciativa do [Governo Federal Brasileiro](https://www.gov.br/pt-br), sob **Domínio Público**;

- NENHUM contribuidor deste repositório possui direitos específicos de controle, gestão ou propriedade sobre o conteúdo do exame;

- A NENHUM contribuidor deste repositório será definida a propriedade intelectual sobre este banco de dados;
 
- O acesso a este banco de dados é **livre** para acesso de indivíduos ou grupos de indivíduos de forma **gratuita**;
 
- Este é um projeto de **livre iniciativa**.

 </div><br>
 
<h2>Preâmbulo</h2>



Embora partindo de iniciativa governamental e aberto ao público, o conteúdo <br>
de avaliação do ENEM se torna relativamente inacessível de forma direta a desenvolvedores, <br>
principalmente iniciantes, vistos formato e modelo de distribuição das provas do exame. <br><br>

Com isso, surge a ideia do banco de dados para as questões do ENEM, <br>
hospedado na própria plataforma oferecida pelo Github, garantindo, além da <br>
acessibilidade, um ótimo nível de estabilidade. <br>

~~------------------------------------------------------------~~

</div>
<br>

## Como acessar o banco de dados?

Para ter acesso às informações, é necessário, através de uma <br>
requisição **XMLHttpRequest**, documentada <a href = 'https://developer.mozilla.org/pt-BR/docs/Web/API/XMLHttpRequest/Using_XMLHttpRequest'>aqui</a>. <br>

Cada página é referente a uma prova de determinado ano, por questões de organização. <br><br>

<h4>A estrutura é a seguinte:</h4>

- A resposta da requisição é um objeto no formato JSON; <br>
 
- As informações do objeto são referentes à prova de um ano em específico;

- As citadas questões de Linguagens, Códigos e suas Tecnologias neste banco de dados <br> começam a partir da Língua Portuguesa.
<br><br>
> Objeto global da prova: <br>

Propriedade | Tipo | Retorno | Quantidade de itens
----- | ----- | ----- | -----
ano | inteiro (int) | Ano a que foi direcionada a prova.
l0 | array | Questões de inglês. | 5 itens
l1 | array | Questões de espanhol. | 5 itens
lc | array | Questões de Linguagens, Códigos e suas Tecnologias. | 40 itens
ch | array | Questões de Ciências Humanas e suas Tecnologias. | 45 itens
cn | array | Questões de Ciências da Natureza e suas Tecnologias. | 45 itens
mt | array | Questões de Matemática e suas Tecnologias. | 45 itens

<br><br>

> Objeto individual de cada questão: <br>

Propriedade | Tipo | Retorno | Observação
----- | ----- | ----- | -----
**enunciado** | string | Enunciado da questão. | Pode possuir uma tag [IMG], caso a questão contenha uma imagem, no mesmo local onde se encontraria na prova original.

<br>

**img** | array | Objetos com informações de imagens da questão: 'src' e 'nota'. | Quantidade de imagens da questão. | Caso a questão não contenha imagens, retorna um único objeto com valores nulos.
----- | ----- | ----- | ----- | -----

***Dentro de cada objeto na array de imagens, é possível encontrar as seguintes propriedades:*** <br><br>
*`src`* = Aponta para endereço o de mídia `media/[ano]/[index_da_imagem]`. Se não existir uma imagem, retorna `null`.
<br><br>
*`nota`* = Indica o endereço de propriedade apontado após a imagem. Se não existir uma imagem, retorna uma string vazia.
<br><br>

**alternativa** | objeto | Um objeto com alternativas em formato de propriedade. | É chamada usando alternativa.[alternativa].
----- | ----- | ----- | -----

***O objeto de `alternativa` possui 5 itens, respectivamente a, b, c, d, e, que podem conter uma string ou uma tag [IMG]. <br>A critério de exatidão:*** <br><br>
*`alternativa.a`* = Alternativa A da questão.
<br>
*`alternativa.b`* = Alternativa B da questão.
<br>
*`alternativa.c`* = Alternativa C da questão.
<br>
*`alternativa.d`* = Alternativa D da questão.
<br>
*`alternativa.e`* = Alternativa E da questão.

![Representação gráfica de cada ponto do objeto.](https://github.com/Vestibular-data/enem_data/blob/main/misc/prova_objeto.png)

