# 🏢호텔 리뷰 데이터를 활용한 감정 분석 및 자연어 생성

## 📒DataSet
- [전체 147,344개의 호텔 리뷰](https://github.com/siyeonSon/hotel-review-sentiment-analysis/blob/main/Hotel_reviews.csv)
- [20,000개의 호텔 리뷰](https://github.com/siyeonSon/hotel-review-sentiment-analysis/blob/main/Hotel_reviews_20k.csv)

---

## 💁‍♂️[좋은 단어와 나쁜 단어 분석](https://github.com/siyeonSon/hotel-review-sentiment-analysis/blob/main/1.%20%EC%A2%8B%EC%9D%80%20%EB%8B%A8%EC%96%B4%EC%99%80%20%EB%82%98%EC%81%9C%20%EB%8B%A8%EC%96%B4%20%EB%B6%84%EC%84%9D.ipynb)
- val_loss는 감소, val_accuracy는 증가 추세이다
- 정확도는 62%이다

![image](https://github.com/siyeonSon/hotel-review-sentiment-analysis/assets/87802191/2f3faf1b-22dc-4f37-93b6-a0fc22cd71e8)


1. 좋은 단어 상위 30개

![image](https://github.com/siyeonSon/hotel-review-sentiment-analysis/assets/87802191/14e3f709-b220-49bc-b318-bce58d986362)

2. 나쁜 단어 상위 30개

![image](https://github.com/siyeonSon/hotel-review-sentiment-analysis/assets/87802191/0c19e934-7cff-4100-9ce3-c78f473069e3)

3. 좋은 단어 단어 구름

![image](https://github.com/siyeonSon/hotel-review-sentiment-analysis/assets/87802191/e12a0965-8c5b-4038-8f56-3e67c0135c25)

4. 니쁜 단어 단어 구름

![image](https://github.com/siyeonSon/hotel-review-sentiment-analysis/assets/87802191/4a74bb31-9940-4664-8476-b4184f1ea87f)

5. 감정 점수 계산

![image](https://github.com/siyeonSon/hotel-review-sentiment-analysis/assets/87802191/8a5e27a6-01c8-4a13-8d33-e0229b0b1185)

---

## 💁‍♀️[별점 비율이 동일한 데이터 셋으로 재분석](https://github.com/siyeonSon/hotel-review-sentiment-analysis/blob/main/2.%20%EB%B3%84%EC%A0%90%20%EB%B9%84%EC%9C%A8%EC%9D%B4%20%EB%8F%99%EC%9D%BC%ED%95%9C%20%EB%8D%B0%EC%9D%B4%ED%84%B0%20%EC%85%8B%EC%9C%BC%EB%A1%9C%20%EC%9E%AC%EB%B6%84%EC%84%9D.ipynb)
- 가설: 별점 비율이 동일한 데이터로 학습한 모델의 성능이 더 좋을 것이다
- loss는 감소하지만 accuracy는 0.35에서 머문다 -> 기존보다 성능이 감소했다
- 모델에 입력되는 특징들이 뚜렷하지 않아 중요한 정보를 잘 전달하지 못한 것이라 판단한다

![image](https://github.com/siyeonSon/hotel-review-sentiment-analysis/assets/87802191/4ff7e26e-2db7-4ce4-b6dd-379d5bd747bb)

---

## 🔠[자연어 생성](https://github.com/siyeonSon/hotel-review-sentiment-analysis/blob/main/3.%20%EC%9E%90%EC%97%B0%EC%96%B4%20%EC%83%9D%EC%84%B1.ipynb)
```python
print(sentence_generation(model, tokenizer, 'hotel', 15))
print(sentence_generation(model, tokenizer, 'this hotel', 20))
print(sentence_generation(model, tokenizer, 'visit', 15))
print(sentence_generation(model, tokenizer, 'it', 15))
print(sentence_generation(model, tokenizer, 'the', 15))
```

```
# result
hotel my mutton pm me may hamper a few times and half hours that the oven
this hotel that a be pm from may hamper dont restaurant and found dont embarrassing to send behave customer when and were
visit that a few minutes of were food i am my manager offered in 20 minutes
it the mutton quality bit high market dimension solution ltd reads my ltd offered in a
the mutton i sold may hamper a few minutes of were food i am my manager
```
- 시작 단어를 hotel, this hotel, visit, it, the 와 같이 주었는데 어느 정도 나쁜 리뷰들을 잘 조합해내는 것을 볼 수 있다
- epoch를 30으로 batch size는 32로 학습시키는데 무려 20분이 소요되었다
- 만약 epoch를 더 늘리고, batch size를 줄여서 학습 시키면 더 연관성 있는 리뷰를 생성할 것이라고 예상할 수 있다
