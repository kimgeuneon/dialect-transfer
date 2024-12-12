# 방언 간 번역기 (제주 방언 → 표준어 → 경상도 방언)

## 프로젝트 개요
한국의 다양한 지역 방언은 고유한 어휘와 문법적 특징을 가지고 있습니다. 본 프로젝트는 제주 방언을 먼저 표준어로 번역한 뒤, 다시 표준어를 경상도 방언으로 변환하는 단계별 방언 간 번역 시스템을 구축하였습니다. 이를 통해 언어자원 보존, 지역문화 이해 및 연구, 다양한 언어 서비스를 위한 기반을 제공할 수 있습니다.

## 프로젝트 목적
- **다단계 번역 파이프라인** 구축: 제주 방언 → 표준어 → 경상도 방언으로 이어지는 변환 과정 구현
- **언어 다양성 및 문화 보존**: 지역 언어 자원을 디지털화하고 활용 가능성을 확대
- **확장성 있는 서비스 제공**: 향후 다양한 지역 방언 및 언어로 확장 가능하도록 시스템 기반 마련

## 주요 기능
1. **제주 방언 → 표준어 번역**  
   파인튜닝된 KoBART 모델을 활용하여 제주 방언 문장을 표준어로 변환
2. **표준어 → 경상도 방언 번역**  
   별도 파인튜닝된 모델을 활용하여 표준어를 경상도 방언으로 변환
3. **파이프라인 통합**  
   두 모델을 순차적으로 적용하여 최종적으로 제주 방언을 경상도 방언으로 변환하는 종단 간(End-to-End) 프로세스 구현
4. **직관적인 API 및 예시 코드 제공**  
   Python 코드와 REST API 예시를 통해 개발자가 손쉽게 시스템을 활용할 수 있도록 지원

## 시스템 구성
### 기술 스택
- **NLP 모델**: KoBART 기반 파인튜닝 모델 2종 (제주 → 표준어, 표준어 → 경상도)
- **프레임워크**:  
  - 모델 서빙: Hugging Face Transformers  
  - 웹 서버: Flask 또는 FastAPI(선택사항)  
- **프로그래밍 언어**: Python 3.x
- **기타**:  
  - CUDA 지원 GPU 환경(선택사항)  
  - Poetry 또는 pip 기반 패키지 관리

### 시스템 플로우
1. 사용자 입력(제주 방언 문장)  
2. 제주 방언 → 표준어 변환 모델로 입력 처리  
3. 변환된 표준어를 경상도 방언 모델에 입력  
4. 최종적으로 경상도 방언 문장 반환

```mermaid
flowchart LR
A[사용자 입력 (제주 방언)] --> B[제주→표준어 모델 변환]
B --> C[표준어→경상도 모델 변환]
C --> D[경상도 방언 결과 반환]