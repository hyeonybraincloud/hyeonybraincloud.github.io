---
layout: single
title:  "4-3 Low-Frequency Analysis"
categories: "전자회로"
use_math: true
---

# 1.1 Low-Frequency Analysis

**1.1.1 Basic MOS Amplifier Configurations** 

![[Figure_37]_three_basic_configurations]({{site.url}}/images/2024-04-16-Low_frequency_analysis/[Figure_37]_three_basic_configurations.jpg)

(a): Common Source(CS, Grounded Source)

(b): Common Gate(CG, Grounded Gate)

(c): Common Drain(CD, Grounded Drain, Source Follower)



**1.1.2 Input/Output Resistance**

![[Figure_38]_input_and_output_resistance]({{site.url}}/images/2024-04-16-Low_frequency_analysis/[Figure_38]_input_and_output_resistance.jpg)왼쪽 그림은 input resistance에 관하여 나타낸 것이며, 그 저항에 대한 식은 다음과 같다.

$R_{input}= \frac{v_i}{i_i}$

input resistance은 MOSFET의 Gate에 인가되는 signal에 대한 저항을 나타낸다. 즉, $V_G$ 및 $I_G$와 관련이 있다. 일반적으로 input resistance는 무한대라 볼 수 있지만, MOSFET이 작동할 때에는 $V_{GS}$에 따라 변할 수 있다.

한편, 오른쪽 그림은 output resistance에 관하여 나타낸 것이며, 그 저항에 대한 식은 다음과 같다.

$R_{output}= \frac{v_o}{i_o}$

output resistance은 MOSFET의 Drain-Source 경로에서의 전류에 대한 저항을 가리킨는데, 주로 $V_D$와 $I_D$가 연관성이 있다. 또한, output resistance는 출력 신호에 영향을 미친다.

Driving-point resistance는 MOSFET이 동작하는 특정 지점에서의 $V-I$의 관계를 나타낸다. 또한, MOSFET이 전압을 조절하는 동안 발생하는 내부 전압 손실을 나타내므로, input/output resistance와 관련된다.

상기 사항을 CS mode의 MOSFET에 적용하면 다음과 같다.

![[Figure_39]_input_and_output_resistance_CS]({{site.url}}/images/2024-04-16-Low_frequency_analysis/[Figure_39]_input_and_output_resistance_CS.jpg)

$R_{input}= \infty$

$R_{output}=r_o \vert\vert R_D \vert\vert R_L $

$A_v=-g_m(r_o \vert\vert R_D \vert\vert R_L) = -g_mR_{output}$



**1.1.3 Diode-connected MOSFET**

다음 그림처럼 Gate와 Drain이 단락(short)되어 있다면, "diode-connected" device라고 불리며, MOSFET이 small-signal resistor(load device)로 작동할 수 있게 한다. 이때 트랜지스터는 항상 saturation region에 놓여 있다.

![[Figure_40]_diode_connected_MOSFET]({{site.url}}/images/2024-04-16-Low_frequency_analysis/[Figure_40]_diode_connected_MOSFET.jpg)

diode-connected MOSFET의 drain 또는 gate에서 바라본 임피던스는 위 그림의 small-signal equivalent model로부터 구할 수 있다. 관련 식은 다음과 같다.

$V_1 = V_X$

$I_X = \frac{V_X}{r_O} + g_m V_X$

$\frac{V_X}{I_X} = \frac{1}{g_m + \frac{1}{r_O}} = \frac{1}{g_m} \vert\vert r_O  \approx \frac{1}{g_m}$

이러한 방식은 on되었을 때, 전류를 anode에서 cathode로만 흐르게 하는, 일종의 다이오드처럼 동작하여 'diode-connected' MOS라고 불린다.

![[Figure_41]_why_diode_connected_MOSFET]({{site.url}}/images/2024-04-16-Low_frequency_analysis/[Figure_41]_why_diode_connected_MOSFET.jpg)

$V_{GS}-V_{TH} < V_{DS}$(always in saturation)

$I_D=\frac{1}{2} \frac{W}{L} \mu_n C_{ox} (V_{GS} - V_{TH})^2 = \frac{1}{2} \frac{W}{L} \mu_n C_{ox} (V_{DS} - V_{TH})^2$

한편, body effect까지 고려했을 때, Source에서 바라본 임피던스는 다음과 같이 구할 수 있다.

![[Figure_42]_diode_connected_MOSFET_with_body_effect]({{site.url}}/images/2024-04-16-Low_frequency_analysis/[Figure_42]_diode_connected_MOSFET_with_body_effect.jpg)

$V_1=-V_X, V_{bs}=-V_X$

$(g_m + g_{mb}V_X)  + \frac{V_X}{r_O} = I_X$

$\frac{V_X}{I_X} = \frac{1}{g_m + g_{mb} + \frac{1}{r_O}} = \frac{1}{g_m + g_{mb}} \vert\vert r_O \approx \frac{1}{g_m + g_{mb}}$



**1.1.4 CS Stage with Diode-Connected Load**

![[Figure_43]_CS_stage_with_diode-connected_load]({{site.url}}/images/2024-04-16-Low_frequency_analysis/[Figure_43]_CS_stage_with_diode-connected_load.jpg)

위 그림은 diode-connected load가 CS mode의 MOS에 연결된 것을 보인다. 이때 channel-length modulation을 무시한다면

$A_v = -g_{m1} \frac{1}{g_{m2} + g_{mb2}} = -\frac{g_{m1}}{g_{m2}} \frac{1}{1+ \eta}$

여기서 $\eta = \frac{g_{mb2}}{g_{m2}}$

한편, $g_{m1}$과 $g_{m2}$을 나타낸다면, $g_m = \sqrt{2k_n'} \sqrt{\frac{W}{L}} \sqrt{I_D}$이므로

$A_v = -\sqrt{\frac{(W/L)_1}{(W/L)_2}} \frac{1}{1 + \eta}$

이는 이득이 bias current와 voltage에 관한 weak function임을 의미하는데, 상대적으로 선형적인 입출력 특성을 나타내어 장점으로 작용한다. 그러나 body effect가 발생할 수 있다.

**※ 여기서 weak function이란?**

입력 변수의 변화가 출력에 미치는 영향이 크지 않고, 일정 범위 내에서는 입출력 간 관계가 거의 일정한 경우를 의미한다. 이는 변화가 비교적 완만하거나 선형적인 경우를 포함한다.

body effect를 없애기 위해서는, 다음 그림처럼 diode-connected load을 PMOS로 구성하면 된다. 

![[Figure_44]_CS_stage_with_diode-connected_load_with_PMOS]({{site.url}}/images/2024-04-16-Low_frequency_analysis/[Figure_44]_CS_stage_with_diode-connected_load_with_PMOS.jpg)

그러나 다음 식처럼 mobility 등 부가적인 parameter을 고려해야 한다는 단점이 존재한다.

$A_v = -\sqrt{\frac{\mu_n (\frac{W}{L})_1}{\mu_p (\frac{W}{L})_2}}$

또한, 높은 gain을 얻기 위해서는 **strong input device**와 **weak load device**가 필요하다. 즉, $V_{OV}$는 커져야 하며, $V_G$는 작아져야 한다. 이는 낮은 전압에서 동작해야 함을 의미한다. 이러한 단점은 saturation region에 놓여야 하는 $M_1$을 triode region에서 동작하게 하여 output swing에 한계를 야기할 수 있다.

$\vert A_v \vert = \frac{\vert V_{GS2} - V_{TH2} \vert}{V_{GS1} - V_{TH1}}$

$I_{D1} = I_{D2}$ 이므로

$\frac{1}{2} \mu_n C_{ox} \left( \frac{W}{L} \right)_1 (V_{GS1} - V_{TH1})^2 = \frac{1}{2} \mu_p C_{ox} \left( \frac{W}{L} \right)_2 (V_{GS2} - V_{TH2})^2$

$A_v = \frac{g_{m1}}{g_{m2}}$

$= -\frac{\mu_n C_{ox} (\frac{W}{L})_1 (V_{GS1} - V_{TH1})}{\mu_p C_{ox} (\frac{W}{L})_2 \vert V_{GS2} - V_{TH2} \vert}$

$A_v \propto \vert V_{GS2} - V_{TH2} \vert$ or $\frac{1}{\vert V_{GS2} - V_{TH2} \vert}$

지금까지 열거한 단점을, 다음과 같이 해결할 수 있다.

**※ CS stage with Current-Source Load**

![[Figure_45]_CS_stage_with_current_source_load]({{site.url}}/images/2024-04-16-Low_frequency_analysis/[Figure_45]_CS_stage_with_current_source_load.jpg)

$M_2$의 width을 증가시켜 $V_{OV}$을 감소시킬 수 있으며, channel-length을 증가시켜 output swing을 제한하지 않고도 $r_{O2}$를 증가시킬 수 있다. 다시 말해, channel-length modulation의 영향을 줄이기 위해 channel-length을 높일 수 있다는 것이다. 한편, voltage gain은 다음과 같다.

$A_v = -g_{m1}(r_{O1} \vert \vert r_{O2})$

**※ CS stage with Active Load**

![[Figure_46]_CS_stage_with_active_load]({{site.url}}/images/2024-04-16-Low_frequency_analysis/[Figure_46]_CS_stage_with_active_load.jpg)

입력 신호가 load device에도 적용되어 "active"한 load가 되게 한다. 또한, $M_1$과 $M_2$는 병렬로 동작하여 전압 이득을 증가시킨다.

$V_{out} = -(g_{m1} + g_{m2})V_{in} (r_{O1} \vert\vert r_{O2})$

$A_v = -(g_{m1} + g_(m2))(r_{O1} \vert\vert r_{O2})$

CS stage with current-source load와 동일한 출력 저항을 가지지만, transconductance는 CS stage with Active load가 크다.



**※ CS stage with Triode Load**

![[Figure_47]_CS_stage_with_triode_load]({{site.url}}/images/2024-04-16-Low_frequency_analysis/[Figure_47]_CS_stage_with_triode_load.jpg)

deep-triode region에서 bias된 MOS($M_2$)는 CS stage에서 가변저항의 역할을 한다.여기서 $V_b$는 충분히 낮아서, 모든 output voltage swing에서 $M_2$로 하여금 deep-triode region에 있게 한다.

$A_v = -g_{m1}R_{on2}$일 때

$R_{on2} = \frac{1}{\mu_p C_{ox}(W/L)_2 (V_{DD} - V_b - \vert V_{TH,p}\vert)}$

위 식에 의해, $R_{on2}$은 $\mu_p C_{ox}$, $V_b$, $V_{TH,p}$로 이루어져 있어서, PVT(Process, Voltage, Temperature)에 따라 그 값이 변한다.

한편, 이 방법에서 $V_b$을 정확히 만드는 것은 굉장히 복잡해서 이러한 회로를 구성하는 것은 상당히 난이도가 있다. 그래도 triode load는 diode-connected 방식보다 voltage headroom을 덜 소모하는 장점이 있다.

**1.1.5 CS Amplifier with a Source Resistance**

![[Figure_48]_CS_with_source_resistance]({{site.url}}/images/2024-04-16-Low_frequency_analysis/[Figure_48]_CS_with_source_resistance.jpg)

$v_{gs}=v_i \frac{\frac{1}{g_m}}{\frac{1}{g_m}+R_S}=\frac{v_i}{1+g_mR_S}$

$v_o = -iR_D$

$i= \frac{v_i}{\frac{1}{g_m}+R_S} = \frac{g_m}{1+g_mR_S} v_i$

$A_v = \frac{v_o}{v_i} = -\frac{R_D}{\frac{1}{g_m} + R_S} = -\frac{g_mR_D}{1+g_mR_S}$

$R_in = \infty$, $R_O = R_D$

$A_v = -\frac{R_D}{\frac{1}{g_m} + R_S}$

여기서 전압 이득은 분모를 'Total resistance seen in the source path'로 하고, 분자를 'resistance seen at the drain'으로 한다.

위 방식에 의해, gain은 작아지나, 선형성은 좋아진다. 여기서 $R_S$는 $g_m$을 감소시켰으므로, source-degeneration resistance라고도 불린다.

다음 그림은 $r_o$가 포함된 것이다.

![[Figure_49]_CS_with_source_resistance_when_r_o_included]({{site.url}}/images/2024-04-16-Low_frequency_analysis/[Figure_49]_CS_with_source_resistance_when_r_o_included.jpg)

$v_o=v_s + (i_o + v_s(g_m + g_{mb}))r_o$

$v_o=i_o R_S + (i_o + i_o R_S(g_m + g_{mb}))r_o$

$R_{output}'=\frac{r_o}{i_o}=r_o + (1 + r_o(g_m + g_{mb}))R_S$ ...①

$R_{output}'=R_S + (1+(g_m + g_{mb})R_S)r_o \approx (1+(g_m + g_{mb})R_S)r_o$ ...②

식 ①, ②이 가리키는 것은 동일하지만, 무엇을 공통으로 묶었느냐에 대해서는 차이를 보인다.

식 ①은 $R_S$을 공통으로 묶었다. 여기서 $1+g_m r_o$ 꼴을 볼 수 있는데, 이는 CG mode에서 load가 open되어 있을 때의 gain을 의미한다.

한편, 식 ②은 $r_o$을 공통으로 묶었다. 여기서는 $1+g_m R_S$ 꼴을 볼 수 있는데, 이는 앞서 언급된 degeneration term이다. 이 식을 통해, $r_o$가 증가하면 channel-length modulation이 약화되어, 트랜지스터가 이상에 가깝게 동작하는 것을 알 수 있다.

아래의 식은 $R_S$ 유무에 따른 output resistance의 차이를 나타낸 것이다.

$R_S$가 없을 때:

$R_{output}' = r_o$

$R_S$가 있을 때:

$R_{output}' \approx (1+(g_m + g_{mb})R_S)r_o$
