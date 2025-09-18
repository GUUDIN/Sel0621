7*. Escreva o arquivo de entrada para simulação da fonte de corrente tomando cuidado em manter os transistores casados. Faça uma simulação do tipo DC variando V_{DD} entre 0 V e 5 V (considere o dreno de M_{5} em 0 V). Medir as correntes que passam pelos transistores M_{4} e M_{3} para V_{DD} = 3,0 V. (verifique se a relação entre estas correntes está dentro do esperado e, se não estiver, corrija). O que acontece com a corrente na saída quando aumentamos V_{DD}? Por quê?

8*. Ajuste o valor de R para que a corrente de saída em V_{DD} = 3,0 V seja a desejada no projeto (valor nominal). Apresente então o gráfico I_{S} x V_{DD}.

9*. Determine a faixa de valores de V_{DD} para a qual a condição $I_0(0{,}98) < I_S < I_0(1{,}02)$ seja observada, onde $I_0$ é a corrente para $V_{DD} = 3{,}0\,\text{V}$. Qual é o valor mínimo de $V_{DD}$ achado?

Chamaremos a faixa de tensão encontrada acima de faixa de operação do circuito para variações de ±2%.

10*. Caso desejemos ter pequenas variações de corrente mesmo para uma ampla variação da tensão de alimentação, quais modificações podem ser realizadas no projeto?

11*. Reprojetar o circuito com modificações para reduzir a sua sensibilidade a variações de V_{DD}. Tomar cuidado para que as dimensões não aumentem muito e que a faixa de operação não seja muito reduzida. Apresente o esquemático do circuito, com as dimensões escolhidas, e o novo gráfico I_{S} x V_{DD}.

12*. Alguns circuitos analógicos necessitam de um circuito de start-up para começarem a funcionar (por exemplo, fontes de corrente, osciladores, etc.). Verifique por simulação se a fonte de corrente necessita de um start-up (considere algumas tensões iniciais nos nós do circuito e verifique, através de simulação de transitório, se o circuito vai ou não para o ponto de operação correto). Caso haja alguma condição inicial em que o circuito não funcione, apresente figura da simulação. Qual comando deve ser utilizado para impor condições iniciais, .IC ou .NODESET?

13. Ajustar o valor de R para que a corrente em M_{5} tenha o valor nominal desejado quando V_{DD} = 3,0 V.

14*. Como deve ser desenhado o resistor (verificar no manual ENG-183_rev3.pdf como é feita a definição de um resistor)? Qual material é adequado para construí-lo?

15*. Fazer a fonte de corrente (esquemático, símbolo com a localização do layout, layout, verificações, LVS, etc.). Observe que:

a. para gerar automaticamente o layout use o viewpoint. Caso seja usado o esquemático os resistores não serão criados;

b. tomar cuidado para garantir o melhor casamento entre os transistores M_{3}, M_{4} e M_{5}; também cuidar do casamento entre os transistores M_{1} e M_{2}.

Quais são as dimensões do circuito completo (utilizar o comando Report – Windows do ICSTATION)? Apresente o layout do circuito.

16*. Extrair o circuito do layout e determinar:

a. corrente de saída para V_{DD} = 3,0 V (usar modelo típico);

b. com simulação Monte Carlo, ao menos 200 simulações, traçar o gráfico número de resultados x corrente de saída em V_{DD} = 3,0 V. Ache o valor médio;

c. Para V_{DD} = 3,0 V, qual é a máxima tensão que podemos aplicar na saída e a fonte continuar funcionando (considere que quando a corrente variou 2%, deixou de funcionar).

Obs.: O extrator gera a linha do resistor erradamente. O resistor deve ser um subcircuito. Acrescente X no início da linha gerada para o resistor. Adicionalmente deve ser acrescentado ao arquivo de simulação o modelo do resistor que se encontra em `/local/tools/dkit/ams_3.70/c35/eldo/restm.mod`.

17*. Realize a simulação DC do circuito com a temperatura variando de -20º C até 100º C, em passos de 5,0º C (V_{DD} = 3,0 V). Abaixo há um exemplo de como devem ficar os comandos:

```
.option precise
.DC temp -30 120 10
.probe DC Id(Mp1)
```

18*. Apresente a curva I_{S} x Temperatura e determine os valores extremos da corrente. Compare a dependência teórica de I_{S} com a temperatura e os resultados?

20*. Aplique um sinal AC na tensão de alimentação e faça uma simulação AC de 1,0 KHz a 100 MHz analisando 10 pontos por década (ver comando .AC). Abaixo há um exemplo de como devem ficar os comandos:

```
Vd   vd   0   3V AC 1
.AC DEC 10 1K 10MEG
.probe AC Id(Mn4) Vd(5) v(6)
```

21*. Apresente o gráfico I_{S} (em dB) x frequência (em escala logarítmica) (mostre os comandos do ELDO utilizados). Caso se deseje que o ruído na saída se mantenha inferior a 1% da corrente nominal, para um ruído de 0,1 V na fonte de alimentação, qual a máxima frequência que o ruído pode ter?

22*. Caso a fonte de alimentação apresente ruídos acima de 0,1 V em frequências acima da permitida, qual providência simples pode ser tomada para reduzi-los?

23*. Tecnologias CMOS são desenvolvidas para fornecer transistores MOS, NMOS e PMOS. Apesar disso, não raramente são também disponibilizados transistores bipolares. Verfique os transistores bipolares LAT2 e VERT10 fornecidos pela AMS, manual ENG-183. Que tipo de transistores são (NPN ou PNP) e por que são chamados de lateral, LAT2, e vertical, VERT10?

24*. Verifique o comportamento do transistor VERT10 com a temperatura. Para isso conecte o emissor dele a uma fonte de corrente (valor de corrente igual ao que você usou no projeto), a base e coletor ao terra e faça. Apresente o gráfico VBE x Temperatura. A declaração do transistor é:

```
Qname coletor base emissor VERT10
```

O modelo VERT10 encontra-se no fim do material.

Grandezas PTAT (Proportional To Absolute Temperature), como a corrente da fonte de corrente, e CTAT (Complementary To Absolute Temperature), como o VBE de um bipolar, podem ser utilizadas para gerar um sinal independente da temperatura. Para isto basta somá-las, cada uma multiplicada por um coeficiente de ajuste, de forma que as variações com a temperatura se cancelem, como mostra a Figura 3.

25*. Projete uma fonte de tensão de referência similar à da Figura 4 mas utilize a fonte de corrente que você projetou (questão 15). Na fonte de tensão faça com que a corrente do bipolar seja igual à corrente que passa pelo resistor R1 (Figura 4). O valor de R2 deve ser ajustado para que Coeficiente de Temperatura* seja inferior a 50 ppm/ºC, para temperaturas variando entre -10ºC e 100ºC. Apresente o esquemático do circuito completo, as dimensões dos transistores e os valores dos resistores. Apresente também o gráfico VREF x Temperatura.

* Coeficiente de Temperatura (partes por milhão por graus Celsius);

VMAX = Máximo valor de VREF para t ∈ [-10ºC, 100ºC]

VMIN = Mínimo valor de VREF para t ∈ [-10ºC, 100ºC]

Coeficiente de Temperatura =

Obs.: Caso a tensão de saída esteja variando muito com a temperatura, reajuste o valor de R2.

26*. Desenhe o layout da fonte de tensão completa. Utilize o transistor vertical PRIMLAB/VERT10 da biblioteca. Ajuste o comprimento de R2 no layout para que o coeficiente de temperatura do circuito extraído se mantenha abaixo de 50 ppm/ºC.

Obs.: o transistor bipolar extraído vem com o parâmetro Area. Apague este parâmetro senão ficará errado.

27*. Adicione ao layout Pads de V_{DD} e GND. Passar o DRC para verificar se tudo está correto. Quais são as dimensões do circuito com os Pads? Apresente o layout do circuito e o gráfico VREF x Temperatura para valores de V_{DD} de 2,0 V, 2,5 V e 3,0 V.

Obs.: um bloco de Pad pode ser encontrado na biblioteca IOLIB_4M, célula g-padonly.

Alguns dados adicionais: os transistores MOS, apesar de terem em primeira ordem um funcionamento simples, precisam de modelos que são cada vez mais sofisticados. Um dos modelos mais conhecidos, e não por isso o melhor, é o BSIM (Berkeley Short Channel IGFET Model, http://www-device.eecs.berkeley.edu/~bsiM_{3}/). Este modelo teve diversas edições e versões. Abaixo há exemplo dos parâmetros do modelo BSIM_{3}V3 para a tecnologia CMOS 0,35 µm da AMS.

Obs.: U0 é a mobilidade inicial e tem unidade de cm²/(Vs);

TOX é a espessura do óxido em metros;

εox = 3,5 × 10⁻¹³ F/cm.