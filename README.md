# Linnuspy
#### Introdução

Linnuspy é um programa simples escrito em python que realiza de forma automatizada a configuração eletrônica de um átomo com base em seu número atômico.

##

#### O Diagrama de Pauling

O diagrama de Linnus Pauling é usado para determinar a configuração eletrônica de um átomo, molécula ou íon. O princípio postula um processo hipotético em que um átomo é "construído" pela adição progressiva de elétrons. Os elétrons preenchem os orbitais atômicos disponíveis dos níveis de energia mais baixos antes de ocuparem níveis mais altos. Como eles são adicionados, eles assumem as condições mais estáveis (orbital atômico) com relação ao núcleo e aos elétrons que já estão lá. Por exemplo, a camada 1s é preenchida antes que a subcamada 2s esteja ocupada. Desta forma, os elétrons de um átomo ou íon formam a configuração eletrônica mais estável possível. Um exemplo é a configuração 1s2 2s2 2p6 3s2 3p3 para o átomo de fósforo, o que significa que a subcamada 1s tem 2 elétrons e assim por diante[[1]](https://pt.wikipedia.org/wiki/Princ%C3%ADpio_de_Aufbau).

##

#### Abordagem

Inicialmente foi definido as variáveis que serão utilizadas ao decorrer do código, padrão, porém vale explicar duas delas:
```python
diagrama = ('1s', '2s', '2p', '3s', '3p', '4s', '3d', '4p', '5s', '4d', '5p', '6s', '4f', '5d', '6p', '7s', '5f', '6d')
eletrons = (2, 2, 6, 2, 6, 2, 10, 6, 2, 10, 6, 2, 14, 10, 6, 2, 14, 10)
```
A primeira variável aí, que foi chamada de diagrama, é uma lista contendo strings que significam, ao todo, a ordem de possibilidade da configuração e dos subníveis; a segunda, chamada eletrons, recebe o número máximo de elétrons por subnível.

Considerando que o valor do número atômico já foi dado pelo usuário, o programa executará uma função que faz uma limitação da possivel configuração eletrônica daquele elemento
```python
for x in eletrons:
    while sum(eletronsz) < z:
        eletronsz.append(x)
        break
```
Atribuindo a uma variável de lista ja existente, os elementos da lista eletrons a partir do valor do número atômico. Logo em seguida é subtraido do ultimo item da lista eletronsz, o número excedente para a configuração eletrônica ser verdadeira
```python
idx = len(eletronsz) - 1
if sum(eletronsz) > z:
    while sum(eletronsz) > z:
        eletronsz[idx] -= 1

diagramaz = diagrama[0:idx+1]
```
E então atravéz do fatiamento da variável diagrama, selecionamos os subníveis que serão preenchidos, através de um ciclo for entre duas listas
```python
for x,y in zip(diagramaz, eletronsz):
    config.append(x + str(y))
```
Por fim, a lista config é imprimida para o usuário, contendo a configuração eletrônica do átomo desejado.
