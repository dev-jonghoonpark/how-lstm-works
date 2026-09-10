# How LSTM Works

**LSTM은 어떻게 기억하는가** — 순환 신경망이 긴 문맥을 잃어버리는 이유부터, 셀 상태와 세 개의 게이트가 그 문제를 어떻게 우회하는지까지 브라우저에서 직접 실험하며 배우는 인터랙티브 교육 자료입니다.

🔗 **[데모 바로가기](https://dev-jonghoonpark.github.io/how-lstm-works/)**

## 다루는 내용

1. **상태를 들고 다니는 신경망 — RNN** · 루프 표기와 펼친 사슬, 파라미터 공유
2. **먼 과거는 왜 잊히는가** · 야코비안이 k번 곱해지며 생기는 기울기 소멸/폭발, 표현력이 아니라 최적화의 문제라는 점
3. **LSTM의 핵심** · 원소별 곱과 덧셈만 거치는 셀 상태 레일, 시그모이드 게이트의 정체
4. **한 스텝을 네 단계로** · 망각 f → 입력 i·후보 C̃ → 갱신 C = f⊙C + i⊙C̃ → 출력 h = o⊙tanh(C), C와 h를 나눈 이유, 파라미터 수
5. **손으로 가중치를 심어 보기** · 사람이 직접 정한 게이트만으로 괄호 깊이를 세는 LSTM, tanh 압축 상태와의 비교
6. **변형들** · 핍홀 연결, 망각·입력 결합, GRU, Depth Gated RNN, Clockwork RNN, 대규모 비교 실험(Greff 2015 / Jozefowicz 2015)의 결론
7. **실제 문장은 어디에 담기는가** · 가중치(붙박이)와 상태(메모장)의 구분, 브라우저에서 직접 학습한 12차원 char-LSTM의 셀 상태를 영어 문장에 대해 열어 보기
8. **그 뒤에 무슨 일이 있었나** · 어텐션, Grid LSTM, 생성 모델, 그리고 Transformer 이후에도 살아남은 아이디어

## 인터랙티브 데모 8종

| 데모 | 무엇을 확인하나 |
| --- | --- |
| 루프를 펼쳐 보기 | 루프 표기 = 펼친 사슬, 상태가 전달되는 순서 애니메이션 |
| 신호는 몇 걸음이나 살아남는가 | λ^k(RNN) vs f^k(LSTM) 로그 스케일 비교, 1/1000 도달 거리 |
| 게이트는 밸브다 | 시그모이드 값에 따라 벡터 성분이 통과하는 비율 |
| 셀 한 스텝 따라가기 | 망각·입력·갱신·출력 단계별 경로 하이라이트 다이어그램 |
| 게이트 조작기 | f·i·C̃·o 조합이 만드는 유지/덮어쓰기/지우기/누적 동작, 20스텝 궤적 |
| 한 글자씩 실행하기 | 손으로 심은 가중치로 괄호 깊이를 세는 LSTM, 문자열 직접 입력 |
| 구조와 파라미터 비교 | LSTM : GRU : RNN = 4 : 3 : 1 |
| 영어 문장이 격자에 새겨지는 것을 보기 | 브라우저에서 즉석 학습한 char-LSTM · 셀 12개 × 글자 T개 격자 · 한 칸의 갱신 방정식 · 글자 하나의 기억 수명 |

여기에 이해도 확인 퀴즈 7문항이 포함되어 있습니다.

## 사용 방법

별도 설치 없이 [데모 페이지](https://dev-jonghoonpark.github.io/how-lstm-works/)를 열면 됩니다. 로컬에서 보려면 `index.html` 파일 하나만 열면 됩니다 — 외부 의존성이 전혀 없습니다.

## 출처와 참고

이 자료는 Christopher Olah의 [Understanding LSTM Networks](https://colah.github.io/posts/2015-08-Understanding-LSTMs/)(2015)를 바탕으로 한 한국어 번역·보충 설명 자료입니다. 원문이 다루는 개념과 설명 순서를 그대로 따라가되, 본문·그림·데모를 한국어 학습용으로 새로 작성했습니다. 이 사실은 페이지 상단에도 명시되어 있습니다. 원문도 함께 읽어 보시길 권합니다.

주요 참고 문헌은 페이지 하단에 정리되어 있습니다 — Hochreiter(1991), Bengio 등(1994), Hochreiter & Schmidhuber(1997), Gers & Schmidhuber(2000), Cho 등(2014), Koutník 등(2014), Karpathy 등(2015), Yao 등(2015), Greff 등(2015), Jozefowicz 등(2015), Xu 등(2015), Kalchbrenner 등(2015) 외.

## 관련 자료

[how-ai-works](https://github.com/dev-jonghoonpark/how-ai-works) 시리즈의 일부입니다.

- [How RNN Works](https://dev-jonghoonpark.github.io/how-rnn-works/) — RNN 부흥기(2014–2016) 전반
- [How seq2seq Works](https://dev-jonghoonpark.github.io/how-seq2seq-works/) — LSTM으로 만든 인코더·디코더
- [How Attention Works](https://dev-jonghoonpark.github.io/how-attention-works/) — 순환을 대체한 다음 걸음
