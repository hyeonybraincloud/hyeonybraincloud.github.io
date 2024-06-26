---
layout: single
title:  "4-2 Applying MOSFET in amplifier design"
categories: "전자회로"
use_math: true
---

# 1.1 Voltage Amplifier

**1.1.1 Obtaining a voltage amplifier**

MOSFET은 다음 그림처럼 Voltage-controlled Current Source의 역할을 한다.

  ![[Figure_24]_MOSFET_acts_as_voltage_controlled_current_source]({{site.url}}/images/2024-04-16-Applying_MOSFET_in_amplifier/[Figure_24]_MOSFET_acts_as_voltage_controlled_current_source.jpg)

input은 $v_{GS}$이고, output은 $i_D$인데, 이들의 관계식은 아래와 같다.

$i_D=\frac{1}{2} k_n’ \left( \frac{W}{L} \right)(v_{GS}-V_{TH,n})^2=\frac{1}{2}k_n’ \left( \frac{W}{L} \right)v_{OV}^2$

위 식과 다음 그래프에 의해, $v_{GS}$-$i_D$ 관계가 비선형적임을 알 수 있다.

![[Figure_25]_input_output_nonlinear]({{site.url}}/images/2024-04-16-Applying_MOSFET_in_amplifier/[Figure_25]_input_output_nonlinear.jpg)

물론, $\vartriangle v_{GS}$가 매우 작으면, 위 그림처럼 선형적인 부분이 있다. 그 부분에서의 기울기, 즉, transconductance(보통 sat.에서 정의)은 다음과 같다.

$g_m \equiv \left. \frac{\partial i_D}{\partial v_{GS}}\right\vert_{v_{GS}=V_{GS}}=k_n’ \left( \frac{W}{L} \right)(V_{GS}-V_{TH,n})=k_nV_{OV}$

Linear amplification을 위해서는 위 그래프에서 보았듯이, DC-bias voltage $V_{GS}$와 매우 작은 크기의 $v_{gs}$가 필요하다.

그런데, 그 output으로 voltage가 아닌, current가 도출되었다.

transconductance amplifier에서 voltage amplifier로의 변화를 위해, 다음 그림처럼 $i_D$로 하여금 저항을 통과시킬 필요가 있다.

참고로 다음 그림은 **Common-Source[CS] mode amplifier**의 기본 구조이다.

![[Figure_26]_CS_mode_amplifier]({{site.url}}/images/2024-04-16-Applying_MOSFET_in_amplifier/[Figure_26]_CS_mode_amplifier.jpg)

$v_o=v_{DS}=V_{DD}-R_Di_D$

**transconductance의 세 가지 표현 방식**

① $g_m=(\mu_n C_{ox})\frac{W}{L}(V_{GS}-V_{TH})=k_n(V_{GS}-V_{TH})=k_nV_{OV}$

$\frac{W}{L}$이 일정하면

![[Figure_28]_transconductance_1]({{site.url}}/images/2024-04-16-Applying_MOSFET_in_amplifier/[Figure_28]_transconductance_1.jpg)

② $g_m=\sqrt{2k_n’}\sqrt{\frac{W}{L}}\sqrt{I_D}$

$\frac{W}{L}$이 일정하면

![[Figure_29]_transconductance_2]({{site.url}}/images/2024-04-16-Applying_MOSFET_in_amplifier/[Figure_29]_transconductance_2.jpg)

③ $g_m=\frac{2I_D}{V_{GS}-V_{TH}}=\frac{2I_D}{V_{OV}}$

$I_D$가 일정하면

![[Figure_30]_transconductance_3]({{site.url}}/images/2024-04-16-Applying_MOSFET_in_amplifier/[Figure_30]_transconductance_3.jpg)

위 세 가지 표현은 transconductance의 동작을 탐구할 때 유용하다. 여기서 $I_D$와 $V_{OV}$는 bias value인데, bias value가 정의된 device에 어떤 신호가 인가되면, $I_D$ 및 $V_{OV}$이 달라져 $g_m$도 달라지지만, 소신호 분석에서는 그 신호의 진폭이 충분히 작아서 그러한 변화는 무시할 수 있다.

**transconductance을 $V_{DS}$에 관하여 표현하기**

$V_{DS} \ge V_b-V_{TH}$인 한, $M_1$은 saturation region에 있으므로, $I_D$와 $g_m$은 상대적으로 일정하다.

그런데 $V_{DS}<V_b-V_{TH}$이면, $M_1$은 triode region으로 진입하는데, 이때의 transconductance은 다음과 같이 정의된다.

$g_m=\frac{\partial}{\partial V_{GS}}{\frac{1}{2}\mu_nC_{ox}\frac{W}{L}[2(V_{GS}-V_{TH})V_{DS}-V_{DS}^2]}=\mu_nC_{ox}\frac{W}{L}V_{DS}$

![[Figure_31]_when_triode_region_transconductance]({{site.url}}/images/2024-04-16-Applying_MOSFET_in_amplifier/[Figure_31]_when_triode_region_transconductance.jpg)

**1.1.2 The Voltage Transfer Characteristics(VTC)**

![[Figure_27]_VTC]({{site.url}}/images/2024-04-16-Applying_MOSFET_in_amplifier/[Figure_27]_VTC.jpg)

Saturation Region에서는 아래 식과 같이 VTC가 비선형적인 양상을 보인다.

$i_D=\frac{1}{2}k_n’ \frac{W}{L}(v_{GS}-V_{TH})^2$

$v_O=v_{DS}=V_{DD}-R_Di_D=V_{DD}- \frac{1}{2}k_n (v_{GS}-V_{TH})^2 R_D$

$i_D$에서 signal current을 알아보자.

$v_{GS}=v_{gs}+V_{GS}$이고,

$k_n = k_n’ \frac{W}{L}$이므로

$i_D=\frac{1}{2} k_n (V_{GS}+v_{gs}-V_{TH})^2=\frac{1}{2}k_n(V_{GS}-V_{TH})^2+k_n(V_{GS}-V_{TH})v_{gs} + \frac{1}{2}k_n v_{gs}^2$

위 식을 linear하게 근사하려면

$\frac{1}{2}k_nv_{gs}^2 \ll k_n(V_{GS}-V_{TH})v_{gs}$라 할 때

$i_D \approx \frac{1}{2}k_n(V_{GS}-V_{TH})^2+k_n(V_{GS}-V_{TH})v_{gs} = I_D + i_d$

$\therefore i_d=k_n(V_{GS}-V_{TH})v_{gs}$

한편, Triode Region에서는 $i_D$가 아래 식과 같다.

$i_D=k_n’ \left( \frac{W}{L} \right) \left[ (v_{GS}-V_{TH}v_{DS}- \frac{1}{2}v_{DS}^2) \right]$

**참고 사항**

여기서 Q점에서의 접선의 기울기가 VTC가 된다고 할 수 있겠다. 물론, 거시적으로는 곡선이므로, 현실적인 오차는 존재할 수밖에 없다.

**1.1.3 Linear Amplifier**

Saturation Region에서 $v_O$에 관한 식은 다음과 같다.

$v_O=v_{DS}=V_{DD}-R_Di_D=V_{DD}- \frac{1}{2}k_n (v_{GS}-V_{TH})^2 R_D$

위 식으로부터 얻은 Voltage Gain에 관한 식은 다음과 같다.

$A_v \equiv \left. \frac{dv_O}{dv_I}\right\vert_{v_I=V_Q}= \left. \frac{dv_{DS}}{dv_{GS}} \right\vert_{v_{GS}=V_{GS}}$

$\therefore A_v=-k_n(V_{GS}-V_{TH})R_D=-k_nV_{OV}R_D$

where $k_n=k_n’\frac{W}{L}$

Bias Point(Q점)에서 $I_D=\frac{1}{2}k_nV_{OV}^2$

$A_v=-\frac{I_DR_D}{V_{OV}/2}=-\frac{V_{DD}-V_{DS}}{V_{OV}/2}$

**※ 질문: $A_v$는 $V_{OV}$에 비례하는가? 반비례하는가?**

위에서 다음 두 식이 도출되었다.

① $A_v=-k_nV_{OV}R_D$

② $A_v=-\frac{I_DR_D}{V_{OV}/2}$

위 두 식을 보고 비례와 반비례가 동시에 성립한다고 단정짓기에는 다소 무리가 있다. 이는 상황에 따라 알맞게 해석해야 한다.

**① Saturation region**

$V_{OV}$가 커질수록 일반적으로 더 높은 $I_D$가 발생하고, 이는 더 큰 $g_m$으로 이어진다. $A_v$는 $g_m$에 비례하므로, $V_{OV}$의 증가는 곧 $A_v$의 증가로 귀결된다고 정리할 수 있다.

**② triode region 근처 또는 channel-length modulation을 고려할 때**

이 경우에서는 $A_v$가 $V_{OV}$에 반비례할 수 있는데, 이는 더 큰 $V_{OV}$가 트랜지스터를 deeper saturation region에 놓여지게 하여 출력 저항 $r_{ds}$을 감소시킬 수 있기 때문이다. 즉, 높아진 $V_{OV}$으로 감소한 $r_{ds}$은 $A_v$을 높아지게 한다.

결론적으로 상황에 따라 비례와 반비례가 각각 성립한다고 할 수 있다.

**1.1.4 Small-signal equivalent-circuit model**

다음 그림처럼 CS mode의 소신호 등가회로를 나타낼 수 있다.

![[Figure_32]_small-signal_equivalent-circuit]({{site.url}}/images/2024-04-16-Applying_MOSFET_in_amplifier/[Figure_32]_small-signal_equivalent-circuit.jpg)

Saturation에서의 drain-source resistance는 $r_o=\frac{\left\vert V_A \right\vert}{I_D}$

Bias는 $I_D=\frac{1}{2}k_n V_{OV}^2$

Small-signal gain은 $A_v \equiv \frac{v_d}{v_{gs}}=-g_m(R_D\vert\vert r_o)=-g_mR_D$(when $r_o=\infty$)

한편, body effect까지 고려하면 small-signal equivalent-circuit은 다음 그림과 같다.

![[Figure_33]_small-signal_equivalent-circuit_with_body-effect]({{site.url}}/images/2024-04-16-Applying_MOSFET_in_amplifier/[Figure_33]_small-signal_equivalent-circuit_with_body-effect.jpg)

body effect 때문에 bulk(body) potential은 $V_{TH}$에 영향을 미쳐서 $V_{OV}$에까지 영향을 끼친다.

한편, 다른 모든 단자에 일정한 전압이 걸려있다면, $g_{mb}V_{BS}$에 의해 $I_D$은 bulk(body) voltage에 관한 식이므로 bulk는 추가적인 gate 역할을 한다.(참고로 $V_{BS}$나 $V_{GS}$는 그 역할상 다를 바가 없다.)

$g_{mb}=\frac{\partial I_D}{\partial V_{BS}}=\mu_n C_{ox} \frac{W}{L}(V_{GS}-V_{TH})\left( -\frac{\partial V_{TH}}{\partial V_{BS}} \right)$

$\frac{\partial V_{TH}}{\partial V_{BS}}=-\frac{\partial V_{TH}}{\partial V_{SB}}=-\frac{\gamma}{2} \frac{1}{\sqrt{2\phi_F + V_{SB}}}$

$g_{mb}=g_m \frac{\gamma}{2\sqrt{2 \phi_F + V_{SB}}}=\eta g_m$

($\eta = \frac{g_{mb}}{g_m}$)

body effect까지 고려한 small-signal equivalent-circuit model은 보통 low-frequency small-signal 분석에 적합하다.

한편, 현실적으로 각 단자는 그 재료의 저항성으로 일정한 저항값을 가진다. 그런데 다음 그림처럼 folding으로 $R_G$을 4배나 감소시키는 등 적절한 layout은 그러한 저항을 최소화할 수 있다. $R_G$은 줄이면 줄일수록 좋다.

![[Figure_34]_reducing_gate_resistance]({{site.url}}/images/2024-04-16-Applying_MOSFET_in_amplifier/[Figure_34]_reducing_gate_resistance.jpg)

**※ T equivalent-circuit model**

![[Figure_36]_T_equivalent_circuit]({{site.url}}/images/2024-04-16-Applying_MOSFET_in_amplifier/[Figure_36]_T_equivalent_circuit.jpg)

**1.1.5 NMOS vs. PMOS**

기존까지 다뤘던 것은 NMOS이고, 다음 그림은 small-signal model을 PMOS에 관해 나타낸 것이다.

![[Figure_35]_apply_with_PMOS]({{site.url}}/images/2024-04-16-Applying_MOSFET_in_amplifier/[Figure_35]_apply_with_PMOS.jpg)

보통 CMOS 측면에서 NMOS가 PMOS보다 우수하다. PMOS는 hole의 낮은 mobility($\mu_p C_{ox}  \approx 0.5 \mu_n C_{ox}$; 공정마다 다름) 때문에 상대적으로 낮은 current drive와 conductance을 보인다. 반면, NMOS는 높은 output resistance로 좀 더 이상적인 current source와 높은 gain을 제공한다. 따라서 실제로 PMOS보다는 NMOS가 선호된다.

출처 및 참고)

김호성 교수, 『기초전자회로』 강의자료, 중앙대학교 전자전기공학부, 2021

백광현 교수, 『전자회로』 강의자료, 중앙대학교 전자전기공학부, 2024