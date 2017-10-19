# 결과 및 논의 {#result}

R을 통해서 NCA 를 구할 수 있도록 R 패키지를 구축하였습니다. 값비싼 상용소프트웨어를 사용하지 않고도 동일한 비구획분석이 가능한 것은 비용과 작업 효율 측면에서 큰 잇점을 가져올 것입니다.

현재 R에 기본적으로 내장되어 있는 PO 테오필린(theophylline)과 IV bolus 인도메타신(indomethacin)에 대해서 예가 잘 나와있습니다.
약물에 대한 자료를 고른 후 각 약물의 복용량, 감소 구간에서의 log 치환 여부, 복용방법, 정맥주사일 경우 투입 시간(정맥주사 이외의 값들 경우에는 infusion time은 내부 함수에 따라 값이 적용되지 않는다.)을 각각 설정할 경우 값을 도출할 수 있습니다.
 
Edison 내에서 실제 Theophylline의 용량에 따라 구현된 각각의 graph를 spaghetti plot형태로 Edison의 결과 가시화 tab을 이용하여 확인할 수 있으며, 그래프의 형태를 변형할 수 있게 설정하였다. 
Y축(농도)의 경우 linear plot과 semi-logarithmic plot을 모두 함께 확인할 수 있도록 하여 다양한 구간에서의 그래프의 추세를 선택적으로 확인할 수 있도록 하였다.
 
언급하였던 공식 이외에도 Pharmacokinetic and Pharmacodynamic Data Analysis 5th edition 에 언급된 공식을 적용하여 다음과 같이 값을 도출하였다.(figure 8) 

또한 결과 값이 모두 도출된 이후 실제 NCA program으로 가장 흔히 사용되고 있는 WinNonlin® (Version 7.0  Pharsight, CA, USA) software 와의 결과 비교에서도 모든 조건을 현재 Edison simulator에서 준 값과 동일하게 설정하여 프로그램을 실행할 경우, 모든 지표에서 같은 값이 계산됨을 확인하였다. (figure 8, figure 9)
 
현재 가장 간단한 분석 방식인 비구획 분석을 통해서 약동학 분석에 필수적인 지표들을 산출해 내었지만, 마찬가지로 수학적 원리를 반영하여 R script를 구성한다면 보다 고차원적적 약동학 분석 방법인 구획 분석(Compartmental analysis)과 비선형적 약동학(nonlinear mixed effect modeling) 분석 또한 실시할 수 있다. 

실제로 Edison 사이언스 엡에 추가한 ‘NONMEM(Nonlinear mixed effect modeling), method’라는 엡을 통해 현재 입력 되어있는 Theoph(theophylline)의 시간 농도 데이터를 가지고 FO(first-order method), FOCE(first-order conditional estimation method), LAPL(Laplace's method)의 방법을 이용하여 현재 사용하는 NONMEM software와 유사한 값들을 재현해 낼 수 있다. 

Figure 4 논문 내에서의 설정 값 

Figure 5. 앞서 설정한 Theophylline에 대한 linear spaghetti plot
 
Figure 6. 앞서 설정한 Theophylline에 대한 scatter plot
 
Figure 7. 앞서 설정한 Theophylline에 대한 semi-logarithmic spaghetti plot

Figure 8. 앞서 설정한 Theophylline에 대한 NCA 분석 결과
 
Figure 9. Theophylline에 대하여 같은 data와 설정값으로 계산한 WinNonlin® (Version 7.0  Pharsight, CA, USA) software의 결과

Figure 10. NONMEM(Nonlinear mixed effect modeling), method 엡에 입력되어 있는 theophylline data의 농도 시간 곡선
 
Figure 11. theophylline data에 대한 model
 
Figure 12. nonlinear mixed effect modeling First order method를 통해 도출된 parameter

# 결론 {#conclusion}

약물을 연구하고 개발하는데 있어서 약동학은 굉장히 필수적인 분야이며, 그 동안 이러한 약동학 지표들을 구하기 위해서 그러한 결론이 도출되는 과정을 고려하지 않고 일부 프로그램의 사용에만 의존하는 모습이 주를 이뤘습니다.

하지만 이번 Edison program과 다양한 수학적, 통계적 지식을 coding에 활용하여 실제 임상적으로도 활용 가능한 결과값을 도출해 낼 수 있음을 확인하였으며 앞으로도 약동학 분야에서 다양하게 활용할 수 있을 것으로 예측됩니다.
