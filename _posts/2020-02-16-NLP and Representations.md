
# Deeplearning, NLP, and Representations 리뷰 및 요약 


<http://colah.github.io/posts/2014-07-NLP-RNNs-Representations/> 
<br/>


*원제*
*<br/>
Deep Learning, NLP, and Representations<br/>
neural networks, deep learning, representations, NLP, recursive neural networks*


뉴럴네트워크의 특성 중 하나인 Universality는 어떤 data 를 넣어도, 잘 작동한다는 범용성을 뜻한다. 

왜이렇게 얘가 잘 작동하는걸까, NLP 예시를 통해 그 이유를 알아보는게 이 글의 목적이다. 
<br/><br/><br/><br/><br/>
## 1. Word Embeddings

Word Embedding은 단어를 (200 ~ 500 차원정도의) 고차원 벡터로 벡터화하는 것이다.


    - W(‘‘cat")=(0.2, -0.4, 0.7, ...)

    - W(‘‘mat")=(0.0, 0.6, -0.1, ...)

 

*"W is initialized to have random vectors for each word"*


단어 임베딩으로 할 수 있는 작업은, 
5-gram(sequence of 5 words)이 valid 한지를 예측하는 문제이다. 


<center><img src = "https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fk.kakaocdn.net%2Fdn%2FcHxiLE%2FbtqyQVdHhyr%2FeXg8pInumBMTWryeqKTxK0%2Fimg.png"></center>

각 W는 모듈 R의 입력으로 들어간다. 
그리고 모듈 R은 5 gram 의 valid/ unvalid 를 판단한다. 

    -  R(W(‘‘cat"), W(‘‘sat"), W(‘‘on"), W(‘‘the"), W(‘‘mat"))=1
    -  R(W(‘‘cat"), W(‘‘sat"), W(‘‘song"), W(‘‘the"), W(‘‘mat"))=0

즉 목표는, W를 학습하는 것이다. 



## 2. Neural Networks to Represent the Data

 
학습을 거친 W, 각 단어들이 임베딩된 후의 word embedding space (or map)에서는,
유사한 단어들끼리 가깝게 모이는 규칙성이 발견된다. 
 

    "a few people sing well” <-> “a couple people sing well”

 
이 때, 모듈 R 은 위 문장 중 일부가 바뀌었다고 해서 문장에 대한 validity 판단을 바꾸진 않는다. 

<br/><br/>
<b/>*"W maps 'few' and 'couple' close together -> In R's perspective it's little change"*</b>
<br/><br/>
즉, R 의 관점에선 이건 아주 사소한 변화일 뿐이고, few 와 couple 은 모두 같은 클래스 내에 위치한다.
<br/><br/>이런 식으로 특정 문장을 다른 유사한 문장 클래스와 묶어서 일반화하는 게 가능해진다. 
 <br/>
 <br/>

*This enables us to generalize from one sentence to a class of similar sentences.*
 

    -   “the wall is blue” →→ “the wall is red” 

    -   “the wall is blue” →→ “the ceiling is red”

*The impact of this is exponential with respect to the number of words.*

 <br/>
 <br/>


<b/>그렇다면 W를 어떻게 학습하는가? </b>
 <br/>
 <br/>

'Gender' , 'Singular/ Plural' 등등도 고려해주어야 한다. 

그런데 문제는, 이렇게 사람이 임의로 기준을 나눠서 valid / not valid 을 체크해주는 모델을 만들기에는 너무 고려할 것들이 많다는 것이다.


그렇기에 Neural network 는 우리가 세세한 과정을 알 필요 없이 <b/>*"learn better ways to represent the data"*</b> 한다.

---
*It’s important to appreciate that all of these properties of W are side effects.*

*We didn’t try to have similar words be close together.*

*We didn’t try to have analogies encoded with difference vectors.*

*All we tried to do was perform a simple task, like predicting whether a sentence was valid.*

*These properties more or less popped out of the optimization process.*


--- 

<br/><br/>

## 3. Shared Representation

This general tactic – learning a good representation on a task A and then using it on a task B – is one of the major tricks in the Deep Learning toolbox. ==  pretraining, transfer learning, and multi-task learning. 

 

<-> Counterpart to this trick..


There’s a counterpart to this trick. Instead of learning a way to represent one kind of data and using it to perform multiple kinds of tasks, we can learn a way to map multiple kinds of data into a single representation!


## 4. RNN


<center><img src = "https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fk.kakaocdn.net%2Fdn%2FcHxiLE%2FbtqyQVdHhyr%2FeXg8pInumBMTWryeqKTxK0%2Fimg.png"></center>


각각의 W 들이 작은 NN 이고, 이들이 다시 R을 통과하는 형태의 모델이다. 

이 모델은 널리 쓰이진 않지만, NLP에서는 훌륭한 성과를 낸다. 

 

그러나 모델의 문제점은, fixed size에서만 가능하다는 것이다. 그래서 unfixed size 에서도 가능한 다음과 같은 모델이 있다. 

 

 
<center><img src = 'https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fk.kakaocdn.net%2Fdn%2FbBIBzr%2FbtqySjF4cXX%2Fx8QlccW6Shwuxs6JYr2KK0%2Fimg.png'></center>

A는 Representing Words 에서부터 Representing Pharses, 그리고 Representing Sentences 의 단계까지 간다. 

즉, Sequence of Words를 merge 해나가는 형태이다.
 
이러한 모델을 Recursive Neural Networks 라고 한다.

 
<br/><br/>
이러한 NLP 모델에서 주된 목표 중 하나는 reversible한 sentence representation을 생성해내는 것이었다. 
 


 
<center><img src = 'https://k.kakaocdn.net/dn/LMyW6/btqyTkEvuas/AArWysEVUnWyTuaAkZwbWk/img.png'></center>

이를테면, 영어 문장를 인코딩하고 프랑스어로 디코딩하는 예시가 있다. 



 ---
 
글에서 궁극적으로 필자가 말하고자 하는 것은 다음과 같다. 

 

 

*Neural Network 가 이렇게 좋은 성능을 내는 것을 <b/>*Representation*</b>의 측면에서 봐보자는 것.*

NN 은 layered model 을 최적화하는 과정에서 데이터를 representing 하는 더 나은 방법을 찾는다. 

 

그저 Neural network 를 많이들 쓰고, 성능이 잘나오는 것을 universality 로 답하는 것은, 진짜 이유가 아니라는 것이다. 


머신러닝을 공부하다보면, 더 깊게 들어갈수록 보고있는 것들에 대한 시야가 좁아지고, 전체적인 그림을 놓치기 쉬워지는 것 같다.

 

내가 하고 있는 공부가 어떻게 돌아가는 건지에 대한 근본적인 Insight 와 큰그림을 놓지않는게 중요해보인다. 
