# Relatório - Coelinhos da Páscoa

> [!CAUTION]
> - Lembre-se que você <ins>**não pode utilizar ferramentas de IA para
>   escrever este relatório**</ins>

## Dados do aluno

- **Cartão UFRGS**: 00581131
- **Nome**: Rafael Petry da Silva

## Passos que eu segui para resolver o problema especificado (em formato de *"prompt"*)

> [!IMPORTANT]
> - Coloque aqui todas as informações necessárias para que alguém
>   (pessoa ou ferramenta de IA) possa reproduzir os seus passos para
>   solucionar o problema
> - Escreva em formato imperativo, como se fosse um *prompt* com as
>   instruções a serem seguidas na solução do problema
> - Seja objetivo e conciso: quanto *menos palavras* você utilizar,
>   melhor
> - Seja técnico e use terminologia adequada: assuma que quem irá ler
>   os seus passos possui conhecimento de Ciência da Computação e
>   Computação Gráfica
> - Caso você queira incluir informações "longas" (como algum *prompt*
>   grande usado com alguma ferramenta de IA), crie arquivos à parte e
>   adicione links no texto (por exemplo, crie o arquivo `PROMPTS.md`
>   e adicione um link markdown `[os prompts detalhados estão
>   aqui](PROMPTS.md)`)
> - Novamente, lembre-se que você *não pode utilizar ferramentas
>   de IA para escrever este relatório*

1. Defina uma constante de velocidade angular `angularSpeed` com valor 0.6f e
uma constante de raio do círculo `rotationRadius` centrado no chão com valor 1.75f.

2. Calcule a variável de tempo do coelho `bunnyTime` para o parâmetro das funções trigonométricas
a serem usadas, inicialmente com o valor de `glfwGetTime()`.

3. Calcule o ângulo do coelho `bunnyAngle` com o valor de `bunnyTime * angularSpeed`.

4. Calcule as posições X e Z do coelho, `bunnyX` e `bunnyZ`, como uma órbita ao redor
do círculo centrado no chão, respectivamente com as funções trigonométricas `-cos(bunnyAngle) * rotationRadius` e
`sin(bunnyAngle) * rotationRadius`. Calcule também a posição Y do coelho para fazer os seus "saltos"
4 vezes por volta com a função trigonométrica `-cos(bunnyAngle*4.0f) * 0.5f`. Altere a translação do coelho,
`translateBunny`, para usar os valores X, Y e Z calculados.

5. Altere a escala do coelho, `scaleBunny`, para um fator de 0.22f em todas dimensões.

6. Crie uma matriz de rotação no eixo Y para o coelho, `rotationBunnyY`, com o ângulo dele para fazê-lo "apontar"
em direção do movimento, com um offset de 90º para corrigir a rotação inicial do modelo: `bunnyAngle + M_PI/2.0f`.

7. Defina uma matriz `bunnyOrbit` com o valor de `translateBunny * rotationBunnyY` e o modelo do coelho como
`bunnyOrbit * scaleBunny`. Faça o desenho do modelo.

8. Defina uma constante do tamanho do raio de órbita do ovo, `eggOrbitRadius`, e da velocidade angular de um ovo,
`eggAngularSpeed` como 2.0f. Faça um loop for de tamanho dois para o desenho dos ovos que irão "orbitar" o coelho.

9. Dentro do loop, defina o ângulo de órbita inicial dos ovos, `eggStartingAngle`, como `eggIndex * M_PI`, para
eles estarem "espelhados" em relação ao centro de órbita. Defina o ângulo atual, `eggAngle`, com o valor
`-glfwGetTime()*eggAngularSpeed + eggStartingAngle`.

10. Calcule as posições Y e Z dos ovos, `eggY` e `eggZ`, como uma órbita ao redor do círculo em que os ovos moverão, respectivamente
com as funções trigonométricas `cos(eggAngle) * eggOrbitRadius` e `sin(eggAngle) * eggOrbitRadius`. Defina X como 0.0f e
uma matriz `translateEgg` de translação dos ovos com os valores X, Y e Z. Altere a escala dos ovos, `scaleEgg`, para
redimensionar os valores (X,Y,Z) = (0.07f,0.11f,0.07f).

11. Defina o modelo como `bunnyOrbit * translateEgg * scaleEgg`, para aplicar as matrizes definidas, usando `bunnyOrbit` para
centrar o círculo de órbita dos ovos na posição do coelho.

12. Agora, altere o código para expandir a solução de um coelho para `bunnyCount = 16` coelhos: Coloque as linhas
adicionadas previamente dentro de um loop for que percorre `bunnyCount`. Também defina uma constante, `bunnyFollowDelay`,
como `bunnyFollowDelay = (2.0f * M_PI / bunnyCount) / angularSpeed`, para sincronização do movimento dos coelhos de forma 
que pareça que um está "seguindo" o outro. Altere `bunnyTime` para ser `glfwGetTime() - bunnyIndex*bunnyFollowDelay`.

13. Altere para que, para cada coelho com índice múltiplo de quatro, seja aplicada uma matriz, `rotationBunnyZ`, de rotação no eixo Z (para
fazê-lo "dar um mortal"). A matriz deve ter o parâmetro `bunnyAngle*4.0f`, para dar 4 mortais por volta, ou ser a identidade
casa o índice não seja múltiplo de quatro. Multiplique a matriz no `model` do coelho, à esquerda de `scaleBunny`.

## Principais dificuldades encontradas durante o desenvolvimento (formato livre)

A principal dificuldade foi entender como fazer o *delay* para que parecesse
que os coelhos estão "seguindo" uns aos outros, apesar da solução ter sido simples.
Além disso, entender a forma que as funções trigonométricas se relacionavam com cada
tipo de movimento/rotação na cena impôs um desafio inicial. 

## Você acha que conseguiu resolver o problema de forma adequada?

Acredito que sim, a cena gerada é bastante parecida com a que deveria ser reproduzida.
Talvez somente alguns detalhes de offset e escala não sejam exatamente iguais, mas vejo
mais como detalhes, visto que alteraria pouca coisa da solução proposta.

## Se você quiser compartilhar mais alguma coisa, coloque aqui:

Nada a relatar.

## Se você possui alguma sugestão para o professor sobre esta atividade, coloque aqui:

Nada a relatar.
