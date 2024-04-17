---
layout: single
title:  "1-3 PN 다이오드의 특성곡선과 등가모델"
categories: "전자회로"
use_math: true
---

# 3.1 PN 다이오드의 특성곡선

**● PN 다이오드의 특성곡선**

![[Figure_1]_PN_diode_characteristic_curve]({{site.url}}/images/2024-03-31-PN_diode_characteristic_equivalent_model/[Figure_1]_PN_diode_characteristic_curve-1712025739270-3.png)

**① 순바이어스 전류($V_D > V_\gamma$)**

$I_D = I_O[e^\frac{eV_D}{KT}-1] \cong I_Oe^\frac{eV_D}{KT} = I_Oe^\frac{V_D}{V_T} (V_D \gg V_T=\frac{KT}{e} \cong 26)$



**② 역바이어스 전류($V_D < 0$)**

$I_D=I_O[e^\frac{eV_D}{KT}-1]\cong-I_O$



**③ 순바이어스 차단 영역($0 \leq V_D < V_\gamma$)**

$I_D\cong0$

장벽(potential barrier)을 낮출 수 없는 열평형 상태로 간주할 수 있다.



**● 온도에 따른 다이오드의 특성곡선**

온도가 상승하면 $V-I$ 특성곡선은 좌측으로 이동한다. 일정한 전류를 유지하려면 온도가 1°C 상승할 때마다 순바이어스 전압을 2.5[mV] 씩 낮추어야 한다.

![[Figure_2]_PN_diode_characteristic_curve_according_to_temperature]({{site.url}}/images/2024-03-31-PN_diode_characteristic_equivalent_model/[Figure_2]_PN_diode_characteristic_curve_according_to_temperature.jpg)



# 3.2 PN 다이오드의 근사 등가모델

**3.2.1 직류(대신호) 근사 등가모델**

![[Figure_3]_The_Equivalent_1]({{site.url}}/images/2024-03-31-PN_diode_characteristic_equivalent_model/[Figure_3]_The_Equivalent_1.jpg)

① **비선형 모델**: 실제 다이오드

② **이상적 근사 등가모델**

$V_D>0$ → 양극에서 음극로 전류를 흐르게 함(switch-on)

$V_D<0$ → 전류를 흐르지 아니하게 함(switch-off)

③ **정전압 근사 등가모델**

$V_D \geq V_\gamma$ → 무한대의 전류를 흐르게 함(switch-on)

$V_D < V_\gamma$ → 전류를 차단함(switch-off)

④ **구간 선형 근사 등가모델**

$V_D \geq V_\gamma$ → 기울기의 역수는 순방향 등가저항 $r_d$이다.

$r_d\equiv \frac{\triangle V_D}{\triangle I_D}=\frac{dV_D}{dI_D}$



**3.2.2 교류(소신호) 근사 등가모델**

|       성분        | 전압 및 전류 |
| :---------------: | :----------: |
|     직류 성분     |  $V_D, I_D$  |
|     교류 성분     |  $v_d, i_d$  |
| (직류+교류) 성분  |  $v_D, i_D$  |
| 교류 실효(평균값) |  $V_d, I_d$  |

아래 그림은 교류(소신호)를 인가한 다이오드 회로의 특성곡선과 등가회로이다.

![[Figure_3]_The_Equivalent_2]({{site.url}}/images/2024-03-31-PN_diode_characteristic_equivalent_model/[Figure_3]_The_Equivalent_2.jpg)

다이오드 전류는 다음과 같다.

$i_D \cong I_Oe^\frac{(V_D+v_d)}{V_T}=I_Oe^\frac{V_D}{V_T}(e^\frac{v_d}{V_T})=I_D(e^\frac{v_d}{V_T})$



$v_d \ll V_T$인 소신호의 경우

$i_D=I_D+i_d=I_D(1+\frac{v_d}{V_T})=I_D+(\frac{I_D}{V_T})v_d$

$(e^\frac{v_d}{V_T} \cong 1+\frac{v_d}{V_T})$



교류 전압과 그 전류의 관계를 등가저항 $r_d$로 **선형등가화(linear equalization)**할 수 있는데, 그 저항을 **다이오드의 교류 저항**, **소신호 등가 교류저항**이라고 한다.

$r_d \equiv \frac{v_d}{i_d} \cong \frac{V_T}{I_D} = \frac{26}{I_D}$



ref)

강영국, 『디지털 전자회로』, 한빛아카데미, 2021
