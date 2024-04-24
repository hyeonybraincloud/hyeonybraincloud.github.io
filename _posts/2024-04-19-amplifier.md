---
layout: single
title:  "5-1 Amplifier"
categories: "전자회로"
use_math: true
---

# 1.1 The Ideal Operational Amplifier

**1.1.1 Function and Characteristics of the Ideal Op Amp** 

![[Figure_64]_equivalent_circuit_of_the_ideal_op_amp]({{site.url}}/images/2024-04-19-amplifier/[Figure_64]_equivalent_circuit_of_the_ideal_op_amp.jpg)

**※ Input & Output Impedances**

① Input impedance of an ideal op amp is supposed to be infinite.

$\rightarrow i_1 = i_2 = 0$

② Output impedance of an ideal op amp is supposed to be zero.

output impedance가 낮을수록 output을 load로 충분히 보낼 수 있다.

**※ Basic properties of ideal op amp**

① output의 위상은 $v_2$와는 동일하나, $v_1$와는 반대이다.

② common-mode rejection

③ Differential gain A(open-loop gain) is infinite.

④ Bandwidth is also infinite.

-> 어떠한 frequency의 신호이든, 동일한 gain으로 증폭 可

**1.1.2 Differential and Common-mode Signals**

Op Amp의 input을 다음과 같이 나타낼 수도 있다.

![[Figure_65]_common_mode_input_signal]({{site.url}}/images/2024-04-19-amplifier/[Figure_65]_common_mode_input_signal.jpg)

① Differential input signal

$v_{Id}=v_2 - v_1$

② Common-mode input signal

$v_{Icm} = \frac{1}{2} (v_1 + v_2)$

위 두 식에 의해

$v_1 = v_{Icm} - \frac{I_{Id}}{2}$

$v_2 = v_{Icm} + \frac{I_{Id}}{2}$

# 1.2 The Inverting Configuration

**1.2.1 The Closed-Loop Gain**

Op Amp은 앞서 언급된 것처럼 단독으로 쓰이지 않고, 다음 그림처럼 feedback circuit 형태로 구현된다.

![[Figure_66]_the_inverting_closed_loop_configuration]({{site.url}}/images/2024-04-19-amplifier/[Figure_66]_the_inverting_closed_loop_configuration.jpg)

Closed-Loop Gain은 다음과 같이 정의된다.

$G \equiv \frac{v_O}{v_I}$

input과 output의 관계를 gain $A$에 관하여 표현하면 다음과 같다.

$v_O = A(v_2 - v_1)$

이때 gain $A$가 이상적으로 무한대에 가까워지만, 다음과 같은 결론을 내릴 수 있다.

$v_2 - v_1 = \frac{v_O}{A} = 0$

$\therefore v_1 = v_2$(virtual short circuit)

$R_1, R_2$을 포함하여 입출력 간 관계를 나타내려면 다음 그림과 같은 과정을 거치면 된다.

![[Figure_67]_the_closed_loop_gain]({{site.url}}/images/2024-04-19-amplifier/[Figure_67]_the_closed_loop_gain.jpg)

위 과정으로, closed-loop gain은 op amp gain에 independent함을 알 수 있다. 또한, 저항만으로 그 gain을 control할 수 있다.

**1.2.2 Application: The Weighted Summer**

다음 그림은 weighted summer이다.

![[Figure_68]_the_weighted_summer_1]({{site.url}}/images/2024-04-19-amplifier/[Figure_68]_the_weighted_summer_1.jpg)

다음 그림은 (+)와 (-) 부호의 계수를 가지는 weighted summer이다.

![[Figure_69]_the_weighted_summer_2]({{site.url}}/images/2024-04-19-amplifier/[Figure_69]_the_weighted_summer_2.jpg)

# 1.3 The Noninverting Configuration

**1.3.1 The Closed-Loop Gain**

![[Figure_70]_the_inverting_configuration]({{site.url}}/images/2024-04-19-amplifier/[Figure_70]_the_inverting_configuration.jpg)

**1.3.2 The Voltage Follower**

voltage follower(a.k.a buffer amplifier)는 voltage gain이 1이다. 이는 impedance transformer 또는 power amplifier로 사용된다.

![[Figure_71]_the_voltage_follower]({{site.url}}/images/2024-04-19-amplifier/[Figure_71]_the_voltage_follower.jpg)

$v_O = v_I$, $R_{in} = \infty$, $R_{out} = 0$

# 1.4 Integrator and Differentiators

**1.4.1 The Inverting Configuration with General Impedances**

기존의 inverting op amp의 저항 $R_1, R_2$을 frequency에 관하여 대체 표현하면 $Z_1(s), Z_2(s)$이다.

따라서 다음이 성립한다.

$\frac{V_o(s)}{V_i(s)} = - \frac{Z_2(s)}{Z_1(s)}$

**1.4.2 The Inverting Integrator**

![[Figure_72]_the_integrator]({{site.url}}/images/2024-04-19-amplifier/[Figure_72]_the_integrator.jpg)

적분값에 (-)가 붙어 **inverting integrator**(a.k.a **Miller integrator**)라고 불린다.

**※ Bode plot for the inverting integrator**

![[Figure_73]_bode_plot]({{site.url}}/images/2024-04-19-amplifier/[Figure_73]_bode_plot.jpg)

위 그림에서 볼 수 있듯이, magnitude bode plot은 기울기가 6 dB/octave(-20 dB/decade)인 직선의 형태이다.

**※ DC problem of the integrator circuit**

integrator는 corner frequency가 0인 STC low-pass network로 동작한다. 위 bode plot에서 볼 수 있듯이, $w=0$일 때, gain은 무한대이다. 즉, dc에서 op-amp는 open-loop로 동작한다. 또한, dc에서 capacitor는 open-circuit으로 동작한다. 따라서 input signal에 dc component가 적게라도 있으면 output은 무한대가 될 수 있다.

**※ The Miller integrator with a large resistance $R_F$**

앞서 언급된 DC problem은 capacitor에 저항 $R_F$을 병렬연결하여 완화할 수 있다. $R_F$까지 고려한 integrator의 transfer function은 다음과 같다.

$\frac{V_o(s)}{V_i(s)} = - \frac{R_F/R}{1+sCR_F}$

![[Figure_74]_the_integrator_with_alleviated_dc_problem_by_R]({{site.url}}/images/2024-04-19-amplifier/[Figure_74]_the_integrator_with_alleviated_dc_problem_by_R.jpg)

large resistance $R_F$ 때문에 다음과 같이 기존 특성에 변화가 생긴다.

① dc gain이 $- \frac{R_F}{R}$이 된다.

② $R_F$가 dc feedback path를 제공하여 integration 보다 덜 ideal하게 된다.

③ $w=0$이었던 corner frequency가 $w= \frac{1}{CR_F}$로 바뀐다.

# 2.1 Differential Amplifiers

**※ Single-Ended and Differential Operation**

Single-Ended signal란?

GND처럼 고정된 전위에 대해 측정되는 신호이다.

Differential signal란?

고정된 전위를 중심으로 신호가 동일하고 반대인 두 노드 사이에서 측정되는 신호이다.

differential signal에서 "center" potential을 "common-mode"(CM) level라 한다.(bias)

예를 들어, Single-Ended signal 출력의 peak amplitude가 $V_0$라 할 때, single-ended peak-to-peak swing은 $2V_0$, differential peak-to-peak swing은 $4V_0$이다.



**※ Advantages of Differential Operation**

signal-ended signaling보다 "environmental" noise에 대해 높은 immunity을 가지고 있다.

예를 들어, clock line $L_2$에서의 transition은 line 간 capacitive coupling때문에 sensitive한 single line $L_1$의 signal을 손상시킨다. 만약 그 sensitive한 signal이 동일 위상과 반대 위상, 총 두 개로 나누어졌을 때, signal line $L_1$과 $L_2$의 중간에 위치한 clock line $L_2$의 transition은 그 두 개의 위상의 signals을 동일하게 손상시키지만, 그 위상 간 difference는 변함이 없다. 이를 **common-mode(CM) rejection**이라 한다.

한편 **CM rejection**은 noise가 있는 supply voltage에도 발생한다.

![[Figure_75]_CM_rejection2]({{site.url}}/images/2024-04-19-amplifier/[Figure_75]_CM_rejection2.jpg)

왼쪽 그림에서 CS stage을 볼 수 있는데, 여기서 $V_{DD}$가 $\triangle V$만큼 변한다면, $V_{out}$도 같은 정도로 변할 수 있다. 오른쪽 그림은 대칭적인 형태의 회로를 보여주는데, $V_{DD}$의 noise가 $V_X$와 $V_Y$에 영향을 주지만, $V_X - V_Y = V_{out}$에는 영향을 미치지 않는다.

위와 같은 원리로, differential operation은 sensitive signal("victims")만큼 noise가 많은 line("aggressors")에서도 유용하다.

![[Figure_76]_CM_rejection3]({{site.url}}/images/2024-04-19-amplifier/[Figure_76]_CM_rejection3.jpg)

위와 같은 완벽한 대칭성으로, $\overline{CK}$와 $CK$에서 sensitive signal line으로 연결된 component는 서로 상쇄된다.

![[Figure_77]_CM_rejection4]({{site.url}}/images/2024-04-19-amplifier/[Figure_77]_CM_rejection4.jpg)

첫 그림에서는 $V_{out}^+$와 $V_{out}^-$가 opposite jump을 거치므로, $V_{out}^+ - V_{out}^-$가 손상된다. 반면, 두 번째 그림처럼 회로를 수정하면 그 손상을 면할 수 있다.

따라서 differential signaling은 얻을 수 있는 voltage swing의 최댓값을 증가시킬 수 있다. 즉, differential circuit에서 $X$ node에서 얻을 수 있는 output swing의 최댓값이 $V_{DD} - (V_{GS} - V_{TH})$라 할 때, $V_X - V_Y$에 대해서, $2(V_{DD} - (V_{GS} - V_{TH}))$을 얻을 수 있다.

지금까지 살펴본 장점 외에도, differential circuit은 더 간단한 biasing과 더 높은 선형성이라는 장점이 있다. 이러한 장점은 면적의 증가라는 단점을 압도할 정도이다.

**※ Basic Differential Pair**

![[Figure_78]_Differential_Pair]({{site.url}}/images/2024-04-19-amplifier/[Figure_78]_Differential_Pair.png)

위 그림에서 $V_{in1}$과 $V_{in2}$은 CM level $V_{in,CM}$가 포함된다. 이에 따라 그 output도 $V_{out,CM}$을 중심으로 swing한다. 이러한 회로는 상기했듯이 noise rejection과 higher output swing을 제공한다.

$V_{in,CM}$이 변하면, $M_1$과 $M_2$에서의 bias current 또한 변하며, 그에 따라 transconductance와 output CM level도 변한다. 만약 input CM level이 극도로 낮으면, $V_{in1}$와 $V_{in2}$의 최솟값은 $M_1$과 $M_2$을 turn off할 것이며, 이는 output에서의 clipping(파형 왜곡)으로 이어질 것이다. 이에 따라 bias current는 input CM level의 영향을 최소한으로 받아야 한다.

![[Figure_79]_Differential_Pair2]({{site.url}}/images/2024-04-19-amplifier/[Figure_79]_Differential_Pair2.png)

앞서 언급된 문제의 해결책으로, input CM level에 independent한, current source $I_{SS} = I_{D1} + I_{D2}$을 포함시키는 방법이 있다.

![[Figure_80]_Incorporating_current_source]({{site.url}}/images/2024-04-19-amplifier/[Figure_80]_Incorporating_current_source.png)

만약 $V_{in1} = V_{in2}$라면 $M_1$과 $M_2$ 모두 bias current가 $\frac{I_{SS}}{2}$이며, output CM level은 항상 $V_{DD} - \frac{R_D I_{SS}}{2}$이다.

![[Figure_81]_Incorporating_current_source_2]({{site.url}}/images/2024-04-19-amplifier/[Figure_81]_Incorporating_current_source_2.png)

위 그래프에 의해 small-signal gain((b) 그래프에서의 기울기)은 $V_{in1} = V_{in2}$(equilibrium)일 때, 최대임을 알 수 있다. 또한, $vert V_{in1} - V_{in2} \vert$가 증가할수록 gain은 0에 수렴한다. 즉, input voltage swing이 증가할수록, circuit은 점점 nonlinear해진다는 것이다.

아래 그림처럼 $V_{in1} = V_{in2} = V{in,CM}$라 하고, $V_{in,CM}$의 범위를 $0$에서 $V_{DD}$까지로 설정하겠다.

![[Figure_82]_Common_mode_behavior]({{site.url}}/images/2024-04-19-amplifier/[Figure_82]_Common_mode_behavior.png)

![[Figure_83]_Common_mode_behavior2]({{site.url}}/images/2024-04-19-amplifier/[Figure_83]_Common_mode_behavior2.png)

**※ Basic Differential Pair: Common-mode Behavior**

대칭성 때문에, $V_{out1} = V_{out2}$이다.

한편, $V_{in,CM}=0$일 때, $M_1$과 $M_2$은 off이고, $I_{D3}=0$, $M_3$은 deep triode region에서 동작한다. 또한, $V_P=0$이며, $V_{out1} = V_{out2} = V_{DD}$이다.

$I_{D1} = I_{D2} = 0$이므로, 회로는 signal amplification이 불가능하다.

반면, $V_{in,CM} \geq V_{TH}$이면, $M_1$과 $M_2$은 켜진다. 비로소 $I_{D1}$과 $I_{D2}$, $V_P$가 증가한다.

$V_{in,CM}$이 충분히 높아졌을 때, $V_{DS3} > V_{GS3} - V_{TH3}$이고 #M_3# node가 saturation region에서 동작하면, $I_{D1} + I_{D2}$는 일정해진다.

amplification을 위해서는, $V_{in,CM} \geq V_{GS1} + (V_{GS3} - V_{TH3})$ 여야 한다.

![[Figure_84]_Common_mode_behavior3]({{site.url}}/images/2024-04-19-amplifier/[Figure_84]_Common_mode_behavior3.png)

$V_{in, CM}$이 계속 증가하면서, $V_{out1}$과 $V_{out2}$은 상대적으로 일정한 값으로 유지되는데,_

_만약 $V_{in,CM} > V_{out1,2} + V_{TH} = V_{DD} - \frac{R_D I_{SS}}{2} + V_{TH}$이면

결과적으로 $M_1$과 $M_2$은 triode region에 들어선다.

$V_{in,CM}$의 범위는 다음과 같다.

$V_{GS1} + (V_{GS3} - V_{TH3}) \geq V_{in,CM} \geq V_{DD} - \frac{R_D I_SS}{2} + V_{TH}$

$M_1$과 $M_2$ 모두 triode region에 들어선 이후로, differential gain($\vert A_v \vert$)은 다음 그림처럼 감소한다.

![[Figure_85]_Common_mode_behavior4]({{site.url}}/images/2024-04-19-amplifier/[Figure_85]_Common_mode_behavior4.png)



**※ Basic Differential Pair: Output Swings**

$V_{in,CM} - V_{TH} \geq V_{out} \geq V_{DD}$

$V_{in,CM}$이 증가할수록 가능한 output swing은 작아진다.

다시 말해, 큰 output swing을 얻기 위해서는 $V_{in,CM}$이 작아야 한다. 물론, $V_{GS1} + (V_{GS3} - V_{TH3}) \geq V_{in,CM}$

output voltage의 실질적인 최솟값은 $V_{in,CM} + V_0 - V_{TH}$임을 알자.

![[Figure_86]_Common_mode_behavior5]({{site.url}}/images/2024-04-19-amplifier/[Figure_86]_Common_mode_behavior5.png)



# 3.1 Cascode Amplifiers





출처 및 참고)

백광현 교수, 『전자회로』 강의자료, 중앙대학교 전자전기공학부, 2024

심용 교수, 『메모리및SoC설계』 강의자료, 중앙대학교 전자전기공학부, 2024