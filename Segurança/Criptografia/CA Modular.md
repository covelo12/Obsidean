# Definições
#### Co-primos
Dois números são co-primos se o ùnico número inteiro que é divisor dos 2 é o 1
# Iniciação
$4^{-1} mod 7$ equivale a pedir um multiplicado de 4 que em módulo de 7 equiva-la a 1.
Isto pode ser usado para chaves.
As cifras têm de ser fáceis de calcular e difícil de inverter
# Maior/Menor divisor comum
Para descobrir o  Mdc sendo $A_k$ o número de vezes que o número primo de ordem  $_k$ divide o número $A$, para calcular 
$Mdc(A,B)=$ <span style="color: #BBFABBA6;">$(Primo_{k1}*Min(A_{k1},B_{k1}))$</span>  $*$ <font style="color:#FFF3A3A6;">$(Primo_{k2}*Min(A_{k2},B_{k2}))$</font>...
$Mmc(A,B)=$ <span style="color: #BBFABBA6;">$(Primo_{k1}*Max(A_{k1},B_{k1}))$</span>  $*$ <font style="color:#FFF3A3A6;">$(Primo_{k2}*Max(A_{k2},B_{k2}))$</font>...

## Teorema de Euclid
Fazemos $Mdc(A,B)= (A modB, B)$
$Mdc(273,715)=Mdc(715-$ <font style="color:#FFF3A3A6;">$2*273$</font> $) =Mdc(273,169)$... $Mdc(13,0)=13$
`Logo Mdc(273,715) = 13`
### O teorema estendido de Euclid
Teorema que nos deixa calcular o inverso modular de dois números, esta forma tem complexidade O(logn)

# Mapas lineares
Para a criptografia o que importa é a baralhação e  multiplicar por um número e achar um módulo ($Ax\; mod\;m$)não  é suficientemente bom. Assim publicava-se o $m$ e o $A$, sendo $x$ a mensagem,  no entanto fazendo o inverso modular do $A$ facilmente se encontra a mensagem.
$A$ e $m$ têm de ter um máximo divisor comum=1 pois senão não dá para desencriptar a informação.

# Pequeno teorema de Fermat
Para fins criptográficos necessitamos de uma função que baralhe melhor a informação. E ao usar exponenciação ao invés de multiplicação.
<span style="color:#0070c0">Unidades</span>: Coisas que têm inverso segundo um módulo
Em vez de funcionar para todos possíveis, apenas funciona para todos os números [[#Co-primos]] daquele módulo. Quando
o módulo é primo todos os números inteiros até ao módulo  são [[#Co-primos]] e logo  são unidades.
Sendo $e$ o número de números primos de $m$, podemos ver que $a^e=a \ mod(m)$
Se $f(x)= ax \ mod(m)$ então $a^e=1$. Logo  há maneira de de conseguir x sem saber $a$ pois $a^{xk}=b^y \ logo \ 3x=1 \ \ mod(e-1)$
![[Pasted image 20231018141605.png]]
# Teorema do resto chinês
Diz  que tendo $x\equiv a (mod\  m)$ e $x\equiv b \ (mod \ n)$  $\implies$ $x\equiv a+cm \ (mod \ mn)$ eg:
$$ x \equiv 1 \ (mod \ 2) \ \& \  x \equiv 2 \ (mod \ 3) \implies x \equiv 5 \ (mod \ (2*3)) $$ onde 5 = é o primeiro número com as duas condições iniciais
## Juntando o Teorema do resto chines com o de Fermat
Fazendo umas contas quais queres com os 2 teoremas chegamos ao resultado: $x^{r(p-1)+1} \equiv 1 \ (mod \ p)$ onde r pode ser um número qualquer e $p$ e $x$ são [[#Co-primos]].
Esta parte eu não percebi,  mas chegamos ao resultado, onde $M$ é a mensagem, $C$ é o criptograma e publicamos o produto de $pq$ e o $e$.
$$M^e \ (mod \ pq)=C $$
Para quem tem a chave privada (p e q) pode descobrir $M$ com 
$$C^d \ (mod \ pq)=M$$
mas d é desconhecido, no entanto pode ser descoberto através de:
$$ ed= 1 mod(mmc(p-1,q-1))$$