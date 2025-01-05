# 13.교차로 자동차 카운팅 인공지능 해커톤
Repository for my Hackathon Experionce of the vehicles detection and counting in the road.

* **Date : 2022-03-23**
* **Last Modified At : 2022-06-29**


# 2021 교차로 자동차 카운팅 인공지능 해커톤 후기

<br>
<p align="center" style="color:gray">
    <img src="https://user-images.githubusercontent.com/76824867/147730147-bd88e4bb-fec1-484a-94ee-620f926e8833.jpg">
</p>
<center><b></b></center>
<br>

<!-- TOC -->

- [교차로 자동차 카운팅 인공지능 해커톤 후기](#%EA%B5%90%EC%B0%A8%EB%A1%9C-%EC%9E%90%EB%8F%99%EC%B0%A8-%EC%B9%B4%EC%9A%B4%ED%8C%85-%EC%9D%B8%EA%B3%B5%EC%A7%80%EB%8A%A5-%ED%95%B4%EC%BB%A4%ED%86%A4-%ED%9B%84%EA%B8%B0)
    - [대회 소개](#%EB%8C%80%ED%9A%8C-%EC%86%8C%EA%B0%9C)
    - [팀 빌딩은 어떻게 하게 되었나?](#%ED%8C%80-%EB%B9%8C%EB%94%A9%EC%9D%80-%EC%96%B4%EB%96%BB%EA%B2%8C-%ED%95%98%EA%B2%8C-%EB%90%98%EC%97%88%EB%82%98)
    - [해커톤 제출자료 설명](#%ED%95%B4%EC%BB%A4%ED%86%A4-%EC%A0%9C%EC%B6%9C%EC%9E%90%EB%A3%8C-%EC%84%A4%EB%AA%85)
        - [주제선정](#%EC%A3%BC%EC%A0%9C%EC%84%A0%EC%A0%95)
            - [a. 주제선정 동기](#a-%EC%A3%BC%EC%A0%9C%EC%84%A0%EC%A0%95-%EB%8F%99%EA%B8%B0)
            - [b. 프로젝트 목표](#b-%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8-%EB%AA%A9%ED%91%9C)
        - [YOLO 모델 선정과정과 활용](#yolo-%EB%AA%A8%EB%8D%B8-%EC%84%A0%EC%A0%95%EA%B3%BC%EC%A0%95%EA%B3%BC-%ED%99%9C%EC%9A%A9)
            - [a. 모델 선정 과정](#a-%EB%AA%A8%EB%8D%B8-%EC%84%A0%EC%A0%95-%EA%B3%BC%EC%A0%95)
            - [b. One-Stage Detection 방법 선택](#b-one-stage-detection-%EB%B0%A9%EB%B2%95-%EC%84%A0%ED%83%9D)
            - [c. Yolo 모델 선택](#c-yolo-%EB%AA%A8%EB%8D%B8-%EC%84%A0%ED%83%9D)
            - [d. 모델 성능을 높이기 위한 다양한 활용 방안](#d-%EB%AA%A8%EB%8D%B8-%EC%84%B1%EB%8A%A5%EC%9D%84-%EB%86%92%EC%9D%B4%EA%B8%B0-%EC%9C%84%ED%95%9C-%EB%8B%A4%EC%96%91%ED%95%9C-%ED%99%9C%EC%9A%A9-%EB%B0%A9%EC%95%88)
        - [YOLOv5를 이용한 객체탐지 및 카운팅 구현](#yolov5%EB%A5%BC-%EC%9D%B4%EC%9A%A9%ED%95%9C-%EA%B0%9D%EC%B2%B4%ED%83%90%EC%A7%80-%EB%B0%8F-%EC%B9%B4%EC%9A%B4%ED%8C%85-%EA%B5%AC%ED%98%84)
            - [a. YOLOv5 모델을 사용한 차량 객체 탐지 - 라온피플 데이터 활용](#a-yolov5-%EB%AA%A8%EB%8D%B8%EC%9D%84-%EC%82%AC%EC%9A%A9%ED%95%9C-%EC%B0%A8%EB%9F%89-%EA%B0%9D%EC%B2%B4-%ED%83%90%EC%A7%80---%EB%9D%BC%EC%98%A8%ED%94%BC%ED%94%8C-%EB%8D%B0%EC%9D%B4%ED%84%B0-%ED%99%9C%EC%9A%A9)
            - [b. COCO Dataset 활용](#b-coco-dataset-%ED%99%9C%EC%9A%A9)
        - [활용방안 교통혼잡도, 사회적 안전망](#%ED%99%9C%EC%9A%A9%EB%B0%A9%EC%95%88-%EA%B5%90%ED%86%B5%ED%98%BC%EC%9E%A1%EB%8F%84-%EC%82%AC%ED%9A%8C%EC%A0%81-%EC%95%88%EC%A0%84%EB%A7%9D)
            - [a. 활용방안1 : 교통 혼잡도 및 사고 상황 알림 서비스](#a-%ED%99%9C%EC%9A%A9%EB%B0%A9%EC%95%881--%EA%B5%90%ED%86%B5-%ED%98%BC%EC%9E%A1%EB%8F%84-%EB%B0%8F-%EC%82%AC%EA%B3%A0-%EC%83%81%ED%99%A9-%EC%95%8C%EB%A6%BC-%EC%84%9C%EB%B9%84%EC%8A%A4)
            - [b. 활용방안2 : 도로 공간의 트래픽 벡터 분석을 이용한 교통 혼잡도 및 회전교차로의 설치의 기반을 마련](#b-%ED%99%9C%EC%9A%A9%EB%B0%A9%EC%95%882--%EB%8F%84%EB%A1%9C-%EA%B3%B5%EA%B0%84%EC%9D%98-%ED%8A%B8%EB%9E%98%ED%94%BD-%EB%B2%A1%ED%84%B0-%EB%B6%84%EC%84%9D%EC%9D%84-%EC%9D%B4%EC%9A%A9%ED%95%9C-%EA%B5%90%ED%86%B5-%ED%98%BC%EC%9E%A1%EB%8F%84-%EB%B0%8F-%ED%9A%8C%EC%A0%84%EA%B5%90%EC%B0%A8%EB%A1%9C%EC%9D%98-%EC%84%A4%EC%B9%98%EC%9D%98-%EA%B8%B0%EB%B0%98%EC%9D%84-%EB%A7%88%EB%A0%A8)
            - [c. 활용방안3 : 정책적 측면에서의 제안](#c-%ED%99%9C%EC%9A%A9%EB%B0%A9%EC%95%883--%EC%A0%95%EC%B1%85%EC%A0%81-%EC%B8%A1%EB%A9%B4%EC%97%90%EC%84%9C%EC%9D%98-%EC%A0%9C%EC%95%88)
        - [기대 효과](#%EA%B8%B0%EB%8C%80-%ED%9A%A8%EA%B3%BC)
        - [개선 방안](#%EA%B0%9C%EC%84%A0-%EB%B0%A9%EC%95%88)
    - [해커톤 심사 결과](#%ED%95%B4%EC%BB%A4%ED%86%A4-%EC%8B%AC%EC%82%AC-%EA%B2%B0%EA%B3%BC)
    - [Reference](#reference)

<!-- /TOC -->

이번 포스팅에서는 2021년 12월에 경험했던 <2021 교차로 자동차 카운팅 인공지능 해커톤>에 참가하여, 대상을 수상하기까지의 인공지능 해커톤 프로젝트에 관한 후기를 쓰고자 한다.

사실 예전부터 인공지능이나 프로그래밍 대회에는 관심이 많았지만, 프로그래밍이나 머신러닝 공부를 하면 할수록 세상에는 똑똑한 사람이 많고 내 자신의 실력이 부족하다고 느껴졌다. 그리고 대부분의 대회가 팀 단위로 진행되었는데, 내가 사는 지역에서는 나와 비슷한 수준의 참가자를 찾기 어려웠다. 

결국 해커톤에 관심은 있으나 실제로 참여한 적은 없었는데, 2021년 12월에 우연한 기회로 해커톤 대회에 5인 팀으로 참가하게 되었다. 그리고 굉장히 좋은 결과를 얻었다!! 그 기록을 다시 정리해보고자 한다.



## 대회 소개

간단히 대회를 소개하자면, 라온피플(주) 컨소시엄에서 2021년 인공지능 학습용 데이터 구축(2차) 사업의 일환으로, 형상 추정 데이터를 수집 및 가공하여 AI 학습데이터를 구축하고 있었는데, 대회를 통해 데이터를 검증하고 활용도를 높이려는 목적에서 개최된 해커톤 같았다.

* **대회명 : 2021 교차로 자동차 카운팅 인공지능 해커톤**
* **주제 : 교차로 자동차 카운팅 인공지능 학습데이터를 활용하여 AI 학습모델 개발 및 데이터 활용 아이디어 기획**
* **목적 : 디지털 뉴딜 '데이터 댐'의 핵심사업인 인공지능 학습용 데이터 구축을 통한 산업계 AI 서비스 혁신 인식 확산 / AI 학습 데이터를 활용한 문화 조성과 더불어 혁신적인 알고리즘 아이디어 발굴**
* **주최/주관 : 과학기술정보통신부, 한국지능정보사회진흥원 / 라온피플 (주)**

해커톤 대회의 주제는, 해커톤 이름에서도 알 수 있듯이 교차로에서의 차량 인식에 관한 것이었다.

도로 위의 차량 인식과 관련하여 이미 여러가지 객체탐지 모델이 활용되고 있다는 것은 알고 있었다. 이 대회는 그 중에서도 특별히 "교차로"에 한정하고, 단순히 차량을 탐지하는 것을 넘어서 차량의 세부적인 종류를 8가지 종류로 인식하고 카운팅하는 것을 요구하고 있었다. 즉, 매 순간 주어지는 CCTV 동영상 프레임에 대해 일종의 Multi Label Classification 문제를 풀 것이라고 예상했다.

어려운 문제일 것으로 생각했지만 해커톤 초반에는 크게 걱정하지 않았다. 왜냐하면 보통 이런 대회에는 주최측에서 이미 수집된 데이터셋을 주고, 데이터셋을 받은 참가자 그룹은 해당 데이터셋의 성능을 극대화할 수 있는 모델구축 및 성능최적화로 경쟁하는 것이 일반적이라고 알고 있었기 때문이다.

우리 팀이 대회에 참가할 때는 크게 2가지 분야 중 하나를 선택할 수 있었다.

* **AI 학습모델 개발** : 교차로 자동차 카운팅 인공지능 학습데이터 활용 AI 학습모델 개발
* **데이터 활용 IDEA 기획** : 교차로 자동차 카운팅 인공지능 학습데이터 활용 서비스/아이디어 기획

인공지능의 기술적 측면에 관심이 많았던 우리 팀은 당연히(?) "AI 학습모델 개발" 분야를 선택하여 해커톤 대회에 나가게 되었다.



## 팀 빌딩은 어떻게 하게 되었나?

학교를 다니며 머신러닝/프로그래밍 관련 대회에 참가하려고 할 때, 가장 난감했던 점은 팀 빌딩이었다. 이는 아마도 서울 이외의 지역에서 공부하는 학생들이라면 비슷한 경험을 겪을 것이라 생각된다. 분명 내가 사는 지역에도 프로그래밍이나 인공지능을 좋아하는 학생들이 있을텐데, 이상하게 나와 잘 맞는 팀원을 구하기가 굉장히 힘들었다. 학교나 지역 커뮤니티에서 찾아봐도, 지극히 초보적인 수준의 학생들만이 일부 있을 뿐이었고, (정말 이유를 알 수 없지만) 나와 비슷한 정도의 실력을 갖는 학생들이 보이지 않았다.

그러다가 우연히 예전에 수강했던 빅데이터/인공지능 기술인재 1기 교육과정의 교육생들이 모인 단톡방에서 해당 대회에 참가할 팀을 모집한다는 소식을 듣게 되었다. '적어도 같이 인공지능 교육과정을 6개월 동안 듣고 수료해낸 사람들이라면, 일정 수준의 실력과 의지가 보장되지 않을까?' 생각하여 나도 함께 참여하게 되었다. ㅎㅎ 지금 생각해도 굉장히 운이 좋았다!



## 해커톤 제출자료 설명

해커톤 제출 자료를 설명하기에 앞서, 프로젝트 기간 동안 우리팀이 느꼈던 난감함을 먼저 설명하고 싶다.

대회가 본격적으로 시작되기 전 단계에서, 우리는 문제상황을 해결할 수 있는 (대회측에서 미리 준비한) 데이터셋을 제공받고, 그 데이터셋의 효용성을 극대화할 수 있는 모델의 구축 및 성능을 경쟁할 것이라고 생각했다.

그런데 해커톤 주최측에서는 '우리가 구체적으로 무엇을 해야 하고, 정확히 무엇으로 평가받는가?' 하는 질문에 대해 굉장히 애매한 답변을 해왔었다.

즉, 해커톤 대회의 문제상황을 직접적으로 해결할 수 있는 데이터셋은 지극히 적은 샘플(수십장의 이미지 정도)밖에 제공되지 않았고, 그런 상황에서 주어진 문제를 해결해야 했던 것이다! 또한, 대회 평가요소 중에는 "효율적인 모델학습을 위한 새로운 방법 제시"가 있었는데.. 이것이 또 우리를 당혹스럽게 했다.

왜냐하면.. 정말로 객체인식 모델에 대한 새롭고 효율적인 학습방법을 알고 있다면, 어느 바보가 (별로 높은 상금이 걸린 것도 아닌) 해커톤 대회에 그것을 제출하겠는가?? 차라리 인공지능 학회에 논문으로 제출하는 것이 훨씬 이득이 아닐까?? 우리 팀원은 모두 이런 생각을 했고, 결국 대회측에서 정확히 어떤 것을 요구하는지 도저히 갈피를 잡지 못했다.

해커톤 프로젝트 기간은 약 14일이었는데, 그 중 3~4일은 대회 주최측의 애매하고 이해하기 어려운 답변으로 인해, 우리팀은 프로젝트 초반에 어떻게 진행해나가야 할지 알 수 없었다.

이대로 가다가는 망할 것 같다는 불길한 느낌이 강하게 들었기 때문에, 나는 결국 "우리팀이 할 수 있는 범위 안에서 이것저것 다 해보자"고 제안했다. 당시의 나는 이대로 가다가는 아무것도 안 될 것이기 때문에, (어차피 수상 가능성은 낮으니 처음부터 기대도 안하고) 객체탐지라는 분야를 공부하고 해커톤을 경험해본다는 정도의 의의를 두고, 이렇게 과감한 제안을 했던 것이다.

어차피 주최측으로부터 데이터셋은 제공되지 않으니 우리가 활용할만한 외부 데이터셋을 찾아보고, YOLO 모델도 입으로만 떠들지 말고 실제로 코드로 구현해보고, 관련분야 논문도 읽어보고, 이러한 모델로 활용가능한 컨텐츠에는 뭐가 있을지 주장과 그 근거도 찾아보기로 하였다!!

지금 생각해보면 약간 자폭성 발언이지만, 이게 의외로 먹혔다. (왜?? ㅇㅁㅇ...)



### 1. 주제선정

#### a. 주제선정 동기

<br>
<p align="center" style="color:gray">
    <img src="https://user-images.githubusercontent.com/76824867/159697252-0c1f98a7-de49-4fbb-8e5e-0ba3cac5c639.png">
</p>
<center><b>Figure 1. 주제 선정</b></center>
<br>

애초에 해커톤 대회에 "AI 학습모델 개발" 주제로 참가했기 때문에 주제선정 동기는 별로 새로울 것이 없었다.

객체인식의 교통분야 응용과 관련된 논문이나 신문기사를 많이 읽어보니, 교차로에서 AI를 활용한 플랫폼 사업이 꾸준히 증가하고 있다는 것을 알 수 있었다. 그리고 교차로 주변의 보행자에 대한 안전망 구축도 자주 언급되는 키워드여서, "차량 객체인식 모델의 구현 + 도로교통에 대한 교통취약자들의 사회안전망 구축" 정도의 컨셉으로 가기로 했다.



#### b. 프로젝트 목표

프로젝트의 목표는, 일단 최우선사항으로 자동차 인식 및 카운팅을 잘하는 객체인식 모델을 구현하는 것이었다.

그러나 해커톤 프로젝트 기한이 실질적으로는 약 10일 정도밖에 없었기 때문에, 나와 다른 대학원생 팀원이 주로 Yolo 모델에 대한 프로그래밍 작업을 담당하고, 다른 학부생 팀원들은 논문을 읽거나 관련분야 기사를 수집하여 인공지능 모델의 활용방안에 관한 아이디어 뱅크 역할을 하는 것으로 방향이 잡혔다.

정리하자면 다음과 같았다.

1. 교차로 내에서 차량을 감지하는 방법에 대해 탐구하고자 했다.
2. Object Detection을 통해 교차로에서 객체탐지 모델을 구현해보고자 했다.
3. 객체탐지를 구현하였다면, 교차로에서 어떤 서비스를 추가적으로 제공할 수 있는지 팀원들과 브레인스토밍을 하려고 했다.
4. 논의한 서비스를 제공할 수 있는 기능의 시스템(프로그램)을 구현해보고, 구현이 어렵다면 타당한 근거와 함께 방법을 제시하려고 했다.

결국 크게 2가지 프로젝트 목표가 존재했다.

* **교차로 모니터링 시스템을 고도화할 수 있는 프로그램의 구축**
* **영상 데이터의 활용 방안을 제안**



### 2. YOLO 모델 선정과정과 활용

#### a. 모델 선정 과정

아마 머신러닝/딥러닝을 조금 공부한 사람들이라면 컴퓨터비전(Computer Vision) 분야, 특히 그 중에서 객체인식과 관련해서 YOLO를 한번 정도는 들어보았을 것이다.

<br>
<p align="center" style="color:gray">
    <img src="https://user-images.githubusercontent.com/76824867/159697270-40fa57e2-17b8-4104-9aac-1e95bc7e5583.png">
</p>
<center><b></b></center>
<br>

이러한 Object Detection 분야의 모델은 크게 2가지로 나뉜다.

* 1-Stage Detector
* 2-Stage Detector

<br>
<p align="center" style="color:gray">
    <img src="https://user-images.githubusercontent.com/76824867/159697272-3038f2ae-66df-4647-8fda-e981c2857c54.png">
</p>
<center><b>Object Detection Milestones</b></center>
<br>

여기서 1-Stage Detector 방식의 모델은 Classification(분류)와 Localization(바운딩 박스를 통해 물체의 위치정보 표시)을 동시에 수행하는 것으로 알려져 있다.

한편, 2-Stage Detector 방식의 모델은 Classification과 Localization을 순차적으로 수행한다.

즉, 다음과 같았다.

* 1-Stage Detector : 속도 빠름, 정확도 낮음
* 2-Stage Detector : 속도 느림, 정확도 높음

따라서, 실시간 CCTV 영상처리에 어떤 모델을 사용하는 것이 더 적합한지를 생각해봐야 했다.

> Q. 실시간 CCTV 영상에서는 어떤 모델을 사용하는 것이 더 적합할까??

당연히 Real Time으로 작동하는 모델이 필요했기 때문에, 정확도를 다소 희생해서라도 빠른 속도의 1-Stage 모델을 사용해야 했다. 이에 대해 좀 더 자세히 알아보자.



#### b. One-Stage Detection 방법 선택

<br>
<p align="center" style="color:gray">
    <img src="https://user-images.githubusercontent.com/76824867/159697277-cd5583ea-c378-47f4-8751-3d395ee443bb.png">
</p>
<center><b></b></center>
<br>

위 그림은 VOC 2007 Dataset을 다양한 모델로 학습한 결과를 보여준다.

여기서 One-Stage Detection 모델들이 Two-Stage Detection 모델들보다 상대적으로 더 높은 FPS 값과 mAP 값을 갖는 것을 알 수 있다.

특히, One-Stage Object Detection 방법인 YOLOv2 모델은 기존의 Two-Stage Object Detection의 치명적인 단점이었던 낮은 FPS 값이 상당히 높은 값을 갖는 것을 확인할 수 있었다.

CCTV가 수집하는 실시간 차량의 동영상은 부드럽게 끊기지 않고 보는 것이 중요했기 때문에, 우리의 모델은 높은 FPS 값을 갖고 있어야 했다. 따라서 (당연하지만) One-Stage Detection 방법이 더 적합하다고 판단했다.

<br>
<p align="center" style="color:gray">
    <img src="https://user-images.githubusercontent.com/76824867/159697280-90f127f5-e335-456a-88f8-e11a40abb20b.png">
</p>
<center><b></b></center>
<br> 

위 그림은 COCO Dataset을 다양한 모델로 학습한 결과이다.

1-Stage 방법은 2-Stage 방법보다 비교적 빠른 추론시간(Inference Time)을 갖지만, 낮은 AP 값을 갖는 것을 확인할 수 있다. CCTV 영상에서 실시간 혼잡도를 예측하기 위해서는 아주 정확한 Counting은 안 되더라도 대략적인 Counting을 할 수 있으면 되고, CCTV 영상은 보통 실시간으로 촬영되고 있는 경우가 많기 때문에, 최종적으로 Inference Time이 더 빠른 One-Stage Detection 모델들이 더 적합하다고 판단했다. 

<br>
<p align="center" style="color:gray">
    <img src="https://user-images.githubusercontent.com/76824867/160303152-687dfe52-d519-490b-8823-3c7f430750d5.png">
</p>
<center><b></b></center>
<br>



#### c. Yolo 모델 선택

1-Stage 방법의 대표적인 모델로는 YOLO, RetinaNet, SSD 등이 있다. 

RetinaNet은 mAP 성능은 매우 좋지만, 추론시간이 매우 긴 것으로 알려져 있다. SSD와 YOLO의 mAP 값은 비슷하지만, 속도 측면에서는 YOLO가 3배 정도 더 빠른 것을 확인할 수 있었다.

따라서 One-Stage Detection 모델 중, YOLO 모델을 사용하여 객체탐지 및 카운팅 모델을 구축하기로 하였다.

<br>
<p align="center" style="color:gray">
    <img src="https://user-images.githubusercontent.com/76824867/159697289-a0a73496-02fa-475b-b768-11a99b13216a.png">
</p>
<center><b></b></center>
<br>



#### d. 모델 성능을 높이기 위한 다양한 활용 방안

<br>
<p align="center" style="color:gray">
    <img src="https://user-images.githubusercontent.com/76824867/159697290-f727fdf2-82f3-47c5-8efd-355f5ace0898.png">
</p>
<center><b></b></center>
<br>

위 그림에서 확인할 수 있듯이 CCTV는 보통 위치가 고정되어 있다. 그러므로 촬영되는 화면은 항상 같은 영역을 보여준다. Background Subtraction Algorithm을 적용한다면, 좀 더 빠른 성능의 객체검출을 통해서 Real Time에 알맞은 부드러운 영상으로 볼 수 있을 것으로 예상했다.

<br>
<p align="center" style="color:gray">
    <img src="https://user-images.githubusercontent.com/76824867/159697307-b6480910-07e2-4d29-990d-235536201fe6.png">
</p>
<center><b></b></center>
<br>

OpenCV를 이용하여 배경을 제거한 후, 특정한 영역을 설정하고 해당 영역을 통과하는 경우나 ROI 라인을 통과하는 경우 카운팅을 실시한다.

다른 바운딩 박스들의 데이터를 통해 불법 주정차들을 탐지할 수 있는 Anomaly Detection을 수행할 수 있을 것으로 예상했다. 예를 들면, 위 그림에서 빨강색 영역의 바운딩 박스의 ```is_parked``` 변수가 True로 변하게 된다면 도로에 문제가 발생하는 특수한 Event를 파악할 수 있을 것이다.

Tracking Detection을 사용하여 차량을 추적하고 바운딩 박스를 유지해나가는 방식으로, 차량이 정차 시 겹치게 되는 부분에 대해서도 해결할 수 있을 것으로 예상했다. 또한, 차량의 경로파악도 가능했다. 결과적으로 해당 경로에서 실시간으로 차량의 수를 카운팅할 수 있을 것이다.



### YOLOv5를 이용한 객체탐지 및 카운팅 구현

#### a. YOLOv5 모델을 사용한 차량 객체 탐지 - 라온피플 데이터 활용

도로교통 외부데이터(AI Hub Korea, 30743번, 주관사 라온피플)를 사용하여 Yolo에 대한 Custom 학습을 진행하였다. 학습하기 이전의 모델은 여러 차량(Car)이 나열된 모습을 열차(Train)으로 인식하는 오류가 있었다. 외부데이터로 학습한 모델은 그러한 면이 제거되어 성능이 향상됨을 확인할 수 있었다.

<br>
<p align="center" style="color:gray">
    <img src="https://user-images.githubusercontent.com/76824867/159697339-e093c609-b8b8-4d37-b453-5c807a60ac98.png">
</p>
<center><b></b></center>
<br>

<br>
<p align="center" style="color:gray">
    <img src="https://user-images.githubusercontent.com/76824867/159697341-e9de135e-651e-4862-a0f9-33eb3179b59a.png">
</p>
<center><b></b></center>
<br>

구체적인 검증을 위해 임의의 도로영상을 수집하여 프레임으로 분해하고, 각 프레임마다 Yolo 모델을 연속적으로 적용하여 성능을 테스트하였다. 그러나 Truck, Bike, Person 등의 대상에 대한 인식성능이 저조한 문제가 있었다.

이는 추후, COCO 데이터셋을 기반으로 재학습하여 최종적으로 Real Time Object Detection 성능향상을 이룰 수 있었다. (Github : https://github.com/jeong-ah313/Car_Hackathon)



#### b. COCO Dataset 활용

COCO Dataset을 활용하여 재학습된 모델은 다음 그림과 같이 오토바이, 트럭, 버스에 대해서도 잘 인식하게 되었다. 또한 추가적인 기능으로, 화면 왼쪽 하단을 통해 현재 화면 속에 있는 차량을 Counting할 수 있도록 구현하였다.

<br>
<p align="center" style="color:gray">
    <img src="https://user-images.githubusercontent.com/76824867/159697358-8bd35481-fd1f-40e2-a7d4-d345e874a5ea.png">
</p>
<center><b></b></center>
<br>

이렇게 객체인식 알고리즘을 적용한 모니터링은 검출되는 객체에 대한 정보를 바탕으로 **관리의 효율성**을 높일 수 있는 장점이 있다. 해커톤 프로젝트가 진행되는 기간 동안, 공공데이터를 바탕으로 자동차의 단순 인식을 넘어서 차종에 따른 분류까지 구현이 가능했다. (Github : https://github.com/jeong-ah313/Car_Hackathon)

<br>
<p align="center" style="color:gray">
    <img src="https://user-images.githubusercontent.com/76824867/159697396-f9ff86e9-83c2-4133-9813-32dd698e4067.gif">
</p>
<center><b></b></center>
<br>



### 4. 활용방안 (교통혼잡도, 사회적 안전망)

#### a. 활용방안(1) : 교통 혼잡도 및 사고 상황 알림 서비스

<br>
<p align="center" style="color:gray">
    <img src="https://user-images.githubusercontent.com/76824867/159697409-72f021d1-4cb4-429a-b2f1-6ca00b82aef7.png">
</p>
<center><b></b></center>
<br>

첫번째 활용방안으로 도로위의 교통 혼잡도를 계산하여 사고발생 가능성을 미리 알려주는 서비스를 생각하였다.

교통 혼잡도를 계산하는 방식은 다음과 같았다.

* 우선 CCTV 영상에서 도로면적 부분을 계산한다.
* "전체면적 - 바운딩 박스가 있는 부분 + 바운딩 박스가 겹치는 부분(그림에서 회색)"을 계산한다.
* X1 = ((바운딩 박스가 있는 부분 - 바운딩 박스가 겹치는 부분(회색)) / 전체면적) x 100%을 계산한다.
* X1이 일정 값을 넘으면 교통 혼잡도가 발생하는 지역으로 분류한다.
* 화면의 하단 오른쪽에 교통 혼잡도의 퍼센트(%)를 출력한다.

<br>
<p align="center" style="color:gray">
    <img src="https://user-images.githubusercontent.com/76824867/159697416-59fc2b93-3708-4cf3-ada5-927fa943f35a.png">
</p>
<center><b></b></center>
<br>

또한, 차량사고 이미지 데이터를 학습하여 도로에서 갑작스러운 사고상황이 발생했을 때, 그것을 검출할 수 있다면 사고상황 시 즉각적인 피드백 시스템이 적용될 수 있으리라 기대하였다.

다음 그림과 같이 영상 속에서 교통사고를 감지하면, 영상 우측 상단의 원이 붉은 색으로 바뀌며 위기상황을 안내한다.

<br>
<p align="center" style="color:gray">
    <img src="https://user-images.githubusercontent.com/76824867/159697457-631fe40f-9c26-4b3d-ac7e-6810320e669c.png">
</p>
<center><b></b></center>
<br>

<br>
<p align="center" style="color:gray">
    <img src="https://user-images.githubusercontent.com/76824867/159697490-c9e2e038-4d6d-4f4a-93d0-b89c90388da6.png">
</p>
<center><b></b></center>
<br>

사고는 크게 3종류로 분류하며, 사고의 종류에 따라 원의 색상도 노랑, 주황, 빨강으로 다르게 변화시키기로 하였다. 

사고의 종류는 다음과 같았다.

* 인명사고 : 도로위의 사람이 검출된 경우
* 차량사고 : 차량간의 사고가 검출된 경우
* 연쇄사고 : 다량의 사고가 검출된 경우

즉, 위 그림과 같은 알고리즘을 통해 영상에 신호를 발생시킨다. 그러나 이 아이디어는 신호발생은 구현하였으나, 사고발생을 학습할 수 있는 적절한 데이터의 부재로 모델학습은 시키지 못해서 현재 사용은 불가했다.



#### b. 활용방안(2) : 도로 공간의 트래픽 벡터 분석을 이용한 교통 혼잡도 및 회전교차로의 설치의 기반을 마련

이 부분은 내가 제시한 아이디어로 구성되었다. 도로에서 차량이 이동하는 이미지를 보았을 때 내가 먼저 떠올린 것은 시간에 따라 변화하는, 즉 물리적으로 말하자면 Time Evolution이 허용되는 벡터공간이었다. 그래서 보통 이공계 1~2 학년때 배우게 되는 기초적인 수준의 벡터해석학 내용을 Numerical, Discrete한 방식으로 응용할 수 있지 않을까 생각했다.

<br>
<p align="center" style="color:gray">
    <img src="https://user-images.githubusercontent.com/76824867/159697495-cef23c9f-e91d-4701-b95e-cb75da277921.png">
</p>
<center><b></b></center>
<br>

즉, 위 그림과 같이 CCTV 도로영상이 주어진다고 할 때, 우선 **영상은 이미지의 Time Sequence**로 생각할 수 있는데, 동영상을 매 순간의 프레임으로 분리하고, 각 프레임에서 객체인식을 수행하고자 하였다. 좀 더 구체적으로 말하자면, 각 이미지에 존재하는 차량 객체의 프레임 별 이동궤적을 계산하고, **목표공간(국소적 도로영역)의 차량 Traffic을 지배하는 임의의 벡터함수 $F(t)$가 존재할 것이라 가정했다.** 여기서 벡터함수는 도로의 국소적 영역에서의 차량의 흐름을 표현하는 함수이다.

그리고 이 단계에서 **벡터해석학(Vector Analysis)**를 적용하여 Traffic 벡터에 대한 보다 정교한 해석을 시도할 수 있으리라 생각했다. 예를 들면, 다음 그림과 같이 어떠한 시스템을 구축할 것이라 생각해보자.

<br>
<p align="center" style="color:gray">
    <img src="https://user-images.githubusercontent.com/76824867/159697571-6dd04682-0010-4b15-b9b6-9b7d2578686d.png">
</p>
<center><b></b></center>
<br>

전체 도로지도를 갖고 있는 기업이나 단체의 관점에서, 각 CCTV는 도로위의 각 지점에 존재하면서 특정한 각도(방향)으로 할당된 영역을 관측할 것이다.

따라서 모든 CCTV에 대하여 **호환가능한 방향변환식**을 **좌표변환**을 통해 계산가능할 것이므로, 이를 각 CCTV 영상의 교통량 흐름을 표현하는 벡터에 모두 적용하고 통합하면 좋겠다고 생각했다.

대한민국의 대부분의 도로에는 CCTV가 있으므로, CCTV가 없는 일부 지역을 제외하더라도 **전체 도로맵의 교통량을 분석할 수 있는 유용한 Traffic 분석의 기반시스템을 구축**할 수 있을 것이다. 

그리고 그러한 기반시스템이 존재하는 상황에서 간단한 벡터 연산으로도 곳곳의 차량의 흐름을 잘 표현할 수 있다고 생각했다. 벡터해석학을 배운지 오래되어 다 기억나지는 않았지만, 대표적인 3가지 연산만으로도 효과적인 해석을 할 수 있으리라 생각해서 다음과 같이 주장하였다.

<br>
<p align="center" style="color:gray">
    <img src="https://user-images.githubusercontent.com/76824867/159697600-51ffcb44-7d10-4333-a8b4-4c598cf61fae.png">
</p>
<center><b></b></center>
<br>

위 그림은 물리학과에서 벡터함수를 다루며 절대 모를 수가 없는 3가지 대표적인 연산인 Gradient, Divergence, Curl의 직관적인 개념을 보여준다.

우리의 교통 Traffic 통합 시스템이 다루게 될 데이터 유형은 시간적 변화를 갖는 도로영역의 벡터함수일 것이므로, **수학적/물리적 관점에서 특정공간(도로)의 Traffic을 지배하는 어떤 벡터함수 F를 가정하고, Gradient, Divergence, Curl 등의 해석학을 적용**하여 차량의 흐름을 보다 정교하게 계산할 수 있다. 이는 도로위의 국소적인 영역에 대해 **교통혼잡도 분석 또는 Traffic 예측 등의 계산을 가능**하게 할 것이다. 또한, **교통관련 시설설치/관련정책에 정량적인 근거**로 활용될 가능성이 있었다.

간단히 3가지 연산을 컴퓨터 알고리즘의 관점에서 풀어서 설명하면 다음과 같다.

* **Divergence** :
    CCTV 영상 이미지를 일정 크기의 격자단위로 분할하고, 단위면적 당 들어오고 나가는 Traffic 벡터의 양을 계산하는 방법이다. 연산결과로 스칼라(실수) 값을 얻는데, (예를 들면) 이를 색상으로 시각화하여 국소적인 영역에서의 교통 흐름을 분석할 수 있다고 생각했다.
* **Curl(Rotation)** :
    격자단위로 분할된 단위영역에서 Traffic 벡터의 회전하는 정도를 계산하는 방법. 어떤 공간에서 Curl 값이 높게 나올 경우 -> 해당 영역의 Traffic 벡터의 회전이 높다고 추론할 수 있다. 
    따라서 Curl 값이 높은 영역 -> 회전교차로를 만들 경우 원활한 교통흐름을 유도할 수 있다.
* **Gradient** :
    공간상에서 Traffic 벡터의 변화율이 가장 크게 변화하는 방향을 가리키는 벡터를 계산하는 방법이다.
    예를 들면, 출퇴근 시간에 도로위에서의 교통량 변화를 예측하는 계산의 근거로 활용가능할 것으로 생각했다.



#### c. 활용방안(3) : 정책적 측면에서의 제안

그럼, 이러한 모델이 구현되었을 때 어떤 활용이 가능할까?

우리 팀은 도로위에서의 차량 움직임이 복잡해짐에 따라 안전사고 발생이 증가한다는 점에 주목하여, 사회적 안전망과 관련된 여러 아이디어를 생각했다.

<br>
<p align="center" style="color:gray">
    <img src="https://user-images.githubusercontent.com/76824867/159697608-34894c23-1a33-44c8-a546-90412560cd77.png">
</p>
<center><b></b></center>
<br>

예를 들면, 위 그림과 같이 일반 교차로의 어린이 사고다발 구간에 대해 어린이 보호구역 뿐만 아니라 일반교차로에도 스마트알리미를 설치할 것을 제안했다. 이는 단순히 보호구역 지정만으로는 안전사고 방지에 저조한 효과를 보이는 것으로 알려져 있었기 때문이다.

또한, 일반도로에서 퍼스널 모빌리티를 다수 감지하는 도로에 퍼스널 모빌리티용 도로를 따로 설치할 것을 제안하기도 하였다. (사실 이 부분은 내가 제안한 내용이 아니고, 다른 팀원이 여러 기사의 내용을 기반으로 주장한 것이어서 확신할 수는 없지만, 나름대로 괜찮은 아이디어 같았다.)



### 5. 기대 효과

최종적으로 우리가 제안하는 모델의 기대효과는 다음과 같았다.

* **사고 분류 및 신호 알고리즘**
    단순히 교통환경 제어 및 계측을 넘어서 사회 안전망 시스템으로 활용될 수 있다.
* **혼잡도 측정 정확도 향상**
    차량 움직임의 벡터화를 통해 이동수단의 속도를 예측할 수 있으며, 흐름선으로 교통 상황을 확인할 수 있다.
* **교통사고 피해 최소화**
    사고현장 이미지 데이터셋을 통해 사고상황에 따른 알림 기능을 안전망 시스템에 활용하여 생명 또는 화재피해 최소화를 가능하게 한다.



### 6. 개선 방안

그러나 모델의 구현에 있어서는, 적절한 데이터셋의 부재로 인해 사고상황에 따른 알림 시스템을 구현할 수는 없었다. 사실 해커톤 주최측에서 데이터를 제공하지 않는 시점에서 자포자기해서 데이터를 제외하고 시도할 수 있는 것은 다 했다.

데이터가 제공되지는 않았지만, 우리가 나름대로 수집한 외부데이터로 자체적인 모델을 구현하여 사고상황 데이터가 수집되면 학습 시 바로 적용될 수 있는 코드를 구현하였다. 

* Github : https://github.com/jeong-ah313/Car_Hackathon



## 해커톤 심사 결과

최종적으로 다음과 같이 대상을 수상하게 되었다!!

<br>
<p align="center" style="color:gray">
    <img src="https://user-images.githubusercontent.com/76824867/147730147-bd88e4bb-fec1-484a-94ee-620f926e8833.jpg">
</p>
<center><b>와! 대상!</b></center>
<br>

<br>
<p align="center" style="color:gray">
    <img src="https://user-images.githubusercontent.com/76824867/160304126-c7b2e757-5d5e-4729-882d-a37cb73afb99.png">
</p>
<center><b>상장</b></center>
<br>

이 상을 받았을 때는 굉장히 기분좋았다. ㅎㅎㅎ

팀장님과 나와 다른 팀원 3명은 특히 막판에 크리스마스 이브를 희생하며 전력으로 제출물을 정리하였고, 크리스마스 새벽 1시가 넘어서야 모두 한숨을 돌릴 수 있었기에 감회가 새로웠다. 

사실 처음에는 단순히 '나도 한번 해커톤이라는 대회를 경험이라도 해보자', '객체인식 프로젝트 경험을 쌓아보자' 정도로 시작했는데, 해커톤이 시작되며 의외로 다른 팀원들이 열심히 해주었기에 나도 마지막까지 전력을 다하게 되었고 좋은 결과로 이어진 것 같다. 특히 팀장님께서 굉장히 주도적으로 노력해주셨기 때문에 나와 다른 팀원도 믿고 따라가기 좋았다. 몇 년 만에 팀 프로젝트에서의 진정한 리더쉽을 느꼈다 ㅠ.ㅠ



## Reference

* https://www.joongang.co.kr/article/23238183#home
* https://www.newspim.com/news/view/20211217000692
* https://digitalcommons.unl.edu/cgi/viewcontent.cgi?article=9123&context=libphilprac
* Zhengxia Zou, Zhenwei Shi, Member, IEEE, Yuhong Guo, and Jieping Ye, Senior Member, IEEE  「 Object Detection in 20 Years: A Survey 」, 2019년, p.2
* Joseph Redmon, Ali Farhadi, 「 YOLO9000: Better, Faster, Stronger 」, 2016년, p.4
* Liu Liu, Rujing Wang, Chengjun Xie, Rui Li,Fangyuan Wang, Man Zhou, Yue Teng, 「 ORIGINAL ARTICLELearning region-guided scale-aware feature selection for objectdetection 」, 2021년
* https://stackoverflow.com/questions/43430056/what-is-the-purpose-of-the-roi-layer-in-a-fast-r-cnn
* Joseph Redmon Ali Farhadi , 「 YOLOv3: An Incremental Improvement 」, 2018년, p1
* https://www.koreascience.or.kr/article/JAKO201909358629535.pdf
* https://medium.com/machine-learning-world/tutorial-making-road-traffic-counting-app-based-on-computer-vision-and-opencv-166937911660
* Joseph Redmon Ali Farhadi , 「 YOLOv3: An Incremental Improvement 」, 2018년, p1

---
