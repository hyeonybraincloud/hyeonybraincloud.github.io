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



# 3.1 Cascode Amplifiers



# 4.1 A Two-Stage CMOS Op Amp



출처 및 참고)

백광현 교수, 『전자회로』 강의자료, 중앙대학교 전자전기공학부, 2024

심용 교수, 『메모리및SoC설계』 강의자료, 중앙대학교 전자전기공학부, 2024