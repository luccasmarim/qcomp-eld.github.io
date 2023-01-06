---
layout: post
title:  "Codificadores e Multiplexadores Quânticos"
date:   2023-01-03 10:00:00
author: luccas_marim
categories: teoria computacao-quântica educativo
usemathjax: true
---

Um codificador é um dispositivo que é utilizado para transformar dados de entrada X em dados de saída X' de acordo com certas regras. O decodificador, por outro lado, faz o caminho inverso levando os dados X' em X. Como o nome sugere, um conjunto de entrada é codificado de forma que apenas decodificadores podem recuperar os dados iniciais. O leitor pode perceber o quão importante é o estudo desses dispositivos não apenas em criptografia ou compiladores mas para a computação em geral, como processamento de informação. Um exemplo de codificador é o binário que transforma números em cadeias de bits.
Um multiplexador é um dispositivo que recebe como entrada dados de diversos canais e retorna, através de controladores (bits), estes dados em apenas um canal otimizando, geralmente, o tratamento dos dados posteriormente. O demultiplexador realiza a operação inversa, recebe como entrada os dados através de um canal e distribui a saida em vários canais.
Conforme esperado, em computação clássica essas operações são realizadas através de circuitos, gates e bits. Em computação quântica desejamos que ocorra o mesmo. Neste artigo introduziremos esses dispositivos clássicos e construiremos os análogos quânticos usando como referência os artigos listados na referência através do Qiskit.

### Codificadores
[adicionar teoria]
Utilizaremos como exemplo o codificador binário com inputs entre 0 e $$ N $$. Logo, teremos $$ log_2 (N+1) = K $$ linhas de saída. Se $$ N = 7 $$, por exemplo, $$ K = 3 $$ e precisaremos de 3 bits para descrever o número a ser codificado. Seguindo esse exemplo, escreveremos essa cadeia como XYZ com X,Y e Z sendo 0 ou 1.
Notemos imediatamente que XYZ = 000 quando a entrada for 0. Por outro lado, Z será 1 para as entradas 1, 3, 5 ou 7. Y será 1 quando as entradas forem 2, 3, 6 ou 7 e por fim, X será 1 quando as entradas forem 4, 5, 6 ou 7. Deste sistema com 4 equações e 4 incógnitas, notamos instantaneamente que precisaremos de pelo menos 4 gates OR.
Utilizando gates quânticos em dimensão 2, o gate OR pode ser escrito como uma composição de gates X com um gate de Toffoli:

![Gate-OR](/assets/images/encoders-multiplexers/gate_or.png)
Fonte: Autor. Utilizado o IBM Quantum Composer.

De fato, podemos ver que este gate representa o gate clássico OR através das respectivas tabelas verdade:

![00](/assets/images/encoders-multiplexers/00.png)
Fonte: Autor. Utilizado o IBM Quantum Composer.

![01](/assets/images/encoders-multiplexers/01.png)
Fonte: Autor. Utilizado o IBM Quantum Composer.

![10](/assets/images/encoders-multiplexers/10.png)
Fonte: Autor. Utilizado o IBM Quantum Composer.

![11](/assets/images/encoders-multiplexers/11.png)
Fonte: Autor. Utilizado o IBM Quantum Composer.

Onde o último qubit (ou primeiro qubit no Composer) é a resposta da operação. Uma implementação em Python usando o Qiskit está presente na referência I.


### Multiplexadores

[adicionar teoria]
Para implementar um multiplexer precisaremos das portas quânticas que reproduzem o efeito das portas clássicas OR e AND. Entretanto, a porta OR já foi estudada na seção anterior e a porta AND é equivalente, em questão de tabela verdade, a porta Toffoli desde que o target qubit seja 0. De fato, fixando o terceiro qubit de entrada como zero no Qiskit:

![000](/assets/images/encoders-multiplexers/000.png)
Fonte: Autor. Utilizado o IBM Quantum Composer.

![010](/assets/images/encoders-multiplexers/010.png)
Fonte: Autor. Utilizado o IBM Quantum Composer.

![100](/assets/images/encoders-multiplexers/100.png)
Fonte: Autor. Utilizado o IBM Quantum Composer.

![110](/assets/images/encoders-multiplexers/110.png)
Fonte: Autor. Utilizado o IBM Quantum Composer.

Para fixar o terceiro qubit como 0 podemos usar uma estrutura condicional que flipe o qubit caso este seja 1. Dessa forma nosso "AND quântico" fica:

![Gate-AND](/assets/images/encoders-multiplexers/quantum_and.png)
Fonte: Autor. Utilizado o IBM Quantum Composer.







## Referências
I. Narula, Hridey & Behera, Bikash & Panigrahi, Prasanta. (2020). Implementing Quantum Data Processing Circuits Using IBM Quantum Experience Platform. 10.13140/RG.2.2.36062.38729 [https://www.researchgate.net/publication/338411513_Implementing_Quantum_Data_Processing_Circuits_Using_IBM_Quantum_Experience_Platform]
II. [http://ijcsi.org/papers/IJCSI-9-1-3-67-74.pdf]



### Futuro
* Adicionar mais conteúdo teórico usando RefII
* 
* 

