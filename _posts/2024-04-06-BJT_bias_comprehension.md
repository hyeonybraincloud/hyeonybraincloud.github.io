---
layout: single
title:  "3-2 BJT의 DC 해석(바이어스 해석)"
categories: "전자회로"
use_math: true
---

# 2.4 전압궤환 바이어스 회로 해석

고정된 $V_{CC}$ 전원을 사용하지 않고, 컬렉터 출력전압 $V_C$을 $R_B$ 저항을 통해 궤환시켜 입력 축에 순바이어스를 걸어 $I_B$ 전류를 흐르게 하여 **전압궤환 바이어스 회로(컬렉터 궤환 바이어스, 자기 바이어스)**라고 한다. 이 회로는 고정 바이어스의 경우보다 궤환 작용으로 안정도가 향상된 특징을 보인다.

**● 전압궤환 바이어스 회로 DC 해석**

![[Figure_10]__Voltage_Feedback_Bias_Circuit]({{site.url}}/images/2024-04-06-BJT_bias_comprehension/[Figure_10]__Voltage_Feedback_Bias_Circuit.jpg)

위 그림은 전압궤환 바이어스 회로의 예시이다.

다음 그림은 입력측 등가회로를 나타낸 것이다.

![[Figure_11]_Equivalent_circuit_input]({{site.url}}/images/2024-04-06-BJT_bias_comprehension/[Figure_11]_Equivalent_circuit_input.jpg)

$V_{CC}=R_C(I_B+I_C)+R_BI_B+V_{BE}=R_CI_B+R_C\beta I_B+R_BI_B+V_{BE}=R_C(1+\beta)I_B+R_BI_B+V_{BE}$

$I_B=\frac{V_{CC}-V_{BE}}{R_B+(1+\beta)R_C}$

$I_C=\beta I_B+(1+\beta)I_{CO}\approx \beta I_B$

($I_{CO}$가 매우 작아 無)

$I_E=I_B+I_C=(1+ \beta )I_B$

다음 그림은 출력측 등가회로를 나타낸 것이다.

![[Figure_12]_Equivalent_circuit_output]({{site.url}}/images/2024-04-06-BJT_bias_comprehension/[Figure_12]_Equivalent_circuit_output-1712412961340-4.jpg)

$V_{CC}=R_C(I_B+I_C)+V_{CE}=R_C(1+\beta)I_B+V_{CE}$

$V_{CE}=V_{CC}-R_C(1+\beta)I_B$

$V_{CE}=R_BI_B+V_{BE}$

$V_{CB}=V_{CE}-V_{BE}=R_BI_B>0$

**● 교류신호 이득 감소를 방지하기 위한 방법**

본 페이지의 최상단 그림으로 나타낸 전압궤환 바이어스 회로는 직류 및 교류 신호 모두 부궤환이 걸리므로, 교류 신호 측면에서는 신호 증폭이 안정되고 주파수 특성이 향상되지만, 부궤환으로 신호 출력 이득은 감소한다.

그러므로 다음 그림과 같이 콘덴서 $C$을 사용하면 , 직류 성분은 부궤환이 걸리게 하고, 교류 성분은 부궤환이 걸리지 않게 하는 회로가 된다.

![[Figure_13]_voltage_feedback_bias_circuit_for_avoiding_signal_gain_reduction]({{site.url}}/images/2024-04-06-BJT_bias_comprehension/[Figure_13]_voltage_feedback_bias_circuit_for_avoiding_signal_gain_reduction.jpg)

