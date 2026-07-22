# 속뜻•겉뜻 의미론

## 1. DFM++ EXPRESSION과 의외성 정리

이 장에서는, 겉뜻에 대한 형식화와, 실제 언어 사용에 있어서, 속뜻의 정의를 다른다.

### DFM++ EXPRESSION

````
# DFM++ EXPRESSION : DFM Language과 감탄음 용어를 통한 품사의 표기

DFM Language : DFM의 모델론적 언어

## DFM Language과 감탄음 용어를 통한 품사의 표기

형식품사 (DFM++ EXPRESSION에서 발음가능하고 형식화된 품사) : 자연어나 술어논리 공리계의 언어 L에 대하여, DFM Language에서 표현되는 품사
비형식품사 (DFM++ EXPRESSION에서 발음가능하지만 즉흥적인 품사) : 감탄음 용어에 "la"를 이용해, 존재론적으로 언질되는 표상, 즉 감탄사 어절이라는 문자열. (그 외에도 라틴어의 호격이 진감탄의 성격을 가지는지는 잘 모르겠어서, 탐구해보고 싶다.)

DFM++ EXPRESSION에서는 형식품사와 비형식품사를 통해 겉뜻의미론을 분석한다.

그러나, 속뜻의미론은 

## 감탄음 가설

> 
> 감탄음 가설
> 
> "감탄사는 입밖으로 조음했는지와 무관히, 화용론적으로 진감탄사와 가감탄사로 나뉜다."
> 

용어)

감탄감 : 감탄사를 낼때 느끼는 감정
감탄동기 : 감탄사를 뱉은 동기

진감탄사 : 감탄음이 진감탄음인 감탄사
가감탄사 : 감탄음이 가감탄음인 감탄사

감탄음 : 감탄사의 음
진감탄음 : 감탄이 진감탄인 감탄음
가감탄음 : 감탄이 가감탄인 감탄음

감탄 : 감탄음을 내는 것 (= 감탄음을 내는 행위)
진감탄 : 감탄동기가 감탄감인 감탄
가감탄 : 감탄동기가 감탄감이 아닌 감탄

## DFM을 통한 품사의 표기

미리 알아둘 점 : DFM Language은 DFM의 모델론적 언어를 말한다.

1. 주사는 빈사 Φ에 대해, la Φ로 정의된다.
2. Hint-Operator연산 Hint로 서술언 혹은 한정사를 Functor의 Hint표기로 정의한다.
3. 언어 L에서 기능사 집합 S는 상 operator[S]이거나, 기능사 x에 대하여, 함자 (noncompile(ε) operator(x))나 함자 (operator(x) noncompile(ε))이다. (또한 전치사나 후치사는 regex token 경계 구분자 `\b` 기준으로 split된것이므로, `\b\s\b`나 `\b`가 접하는 방향에 존재한다.)
4. 언어 L(G)에 대하여, L(G)상의 자연어 술어라는 함수는 모델 compiled(L(G))위의 함수다.
5. 그러한 함수를 이용하여, 자연어 문자열을 Funcional하게 표기하면, 여러 자연어 품사를, 겉뜻 의미론 기준으로 명확하게 분해 가능하다.

### Decorating Function Model

임의의 Domain에 대해 Decorating Functions를 정의한 모델이다.

미리 알아둘 점)

 * first(x, y) = x
 * last(x, y) = y

로 튜플의 제귀적 정의를 이용하여 본 문단을 서술할 예정임.

NOTATION)
```
DecoratingSyntax ≡ x s.t. Φ(x)
```

Decorating Functions)
```
la Φ = DecoratingSyntax
x Hint Φ = DecoratingSyntax
```

Hint-Operator연산 Hint)
```
Hint란 `(`랑 술어를 겹치는 표기법이다.

임의의 술어 Φ,
임의의 이항관계 R ⊆ P × Q및
임의의 x ∈ P, y ∈ Q에 대하여

제 1 Notation)

x (Hint Φ) ≡ (Hint Φ)(x)

실제론 `(`랑 Hint의 `H`랑 겹쳐서 적는다.

제 2 Notation)

x (R y) ≡ x (Hint (R y))

실제론 `(`랑 `R`랑 겹쳐서 적는다.

제 3 Notation)

모델 M(S) = <S, I>에 대하여,

1. M(S)는 구조체이므로 2-튜플이다. (i.e. M(S) = (first(M(S), last(M(S)))
2. first(M(S)) = S고, last(M(S)) = I이다.
3. S는 모델 M(S)의 도메인, I는 모델 M(S)위의 항등관계(이항관계중 하나)로, I ⊆ S × S다.
4. 항등관계 I에 대해, ∀(x, y), x I y : x = y이다.
5. 그러니까, I = {(x, x) | x ∈ S}인거다.

그러므로, 등호에 대해서는, Hint-Operator를 다음과 같이 정의한다.

x (= y) ≡ x (last(M({x, y})) y)

실제론 `(`랑 `=`랑 겹쳐서 적는다.

Tip)

진리함자 (R y)가 술어(진리함수) Φ = (R y)라면, 함자 (Hint Φ)는 수식언 • 한정사처럼 작동한다.

그러므로, Hint-Operator는 다항관계에 대해서도 함자 (Hint Φ)를 만들수 있다.
```

TIP : 기호 `≡`는 Syntaxal Equal기호다.
TIP : Operator는 모델론적으로는, Function에 해당한다.

### L(G)에서 compiled(L(G))의 연산자로 가는 사상 operator의 정의

L(G)에서 compiled(L(G))의 연산자로 가는 사상 operator를 다음과 같이 정의한다.

operator(f)(x, y) ≜ compile(x concat noncompile(f) concat y)

#### 컴파일된 형식언어 a.k.a. compiled(L(G)) 의 정의.

자유 모노이드 F(L) = <L*, ε, concat>는 구조체 F(L)이다.

즉, 튜플이므로, 튜플의 제귀적 정의에 따라, F(L) = (L, (ε, concat)) s.t. L = first(F(L)), ε = first(last(F(L)), concat = last²(F(L)) 인거다.

다음으로 형식문법 G = <V, Σ, P, S>에 대해,

isFormalGrammer(G) : isFormalGrammer<V, Σ, P, S>

해설 : 형식문법 G가 4-튜플이므로, isFormalGrammer는 집합 3개(문자집합 2개, 문자열 이항관계 1개), 문자 1개들 담은 튜플이다.

즉, isFormalGrammer는 문자집합의 Rank가 n일때, n계논리에서 사항관계, (n+1)계논리에서 일항술어다.

isFormalGrammer<V, Σ, P, S> : S ∈ V, V ∩ Σ = ∅, P ⊆ (LangOf<V, Σ, P, S>*VLangOf<V, Σ, P, S>*) × (LangOf<V, Σ, P, S>*)

N.B. P ⊆ (LangOf<V, Σ, P, S>*VLangOf<V, Σ, P, S>*) × (LangOf<V, Σ, P, S>*)는 ∀(x, y) ∈ P, x ∈ LangOf<V, Σ, P, S>*VLangOf<V, Σ, P, S>*, y ∈ LangOf<V, Σ, P, S>*인거다.

해설 : 이는, 형식문법과 문법규칙의 정의를 적은것이다. 

형식문법과 문법의 정의로 파악해보자면
1. 비단말기호의 정의 non-terminate symbol이므로, 기호(=언어셋(char set))중 단말기호의 여집랍으로, LangOf<V ∪ Σ> - Σ다. (i.e. 서로소 집합인거다)
2. 시작 기호는 비단말기호다.
3. LangOf<V, Σ, P, S>는 언어의 문자(기표) 집합이다. (i.e. 언어셋(언어라는 집합)은 문자셋(문자 입합, char set)이다)

LangOf(G) = LangOf<V, Σ, P, S> = V ∪ Σ

해설 : 문자가 비단말기호인 문자이거나 단말기호인 문자라는건, "문자가 단말기호인 문자이거나, 아닌 문자다"라는 동어 반복이므로, 당연히 맞는 말이다.

실제로 있든 없든 바뀌든 문법규칙에 영향이 안가는 문자들은 Σ에 있다. 마치 치역이 아닌 공역처럼, 잉여스러운 문자들이다 (예를들어 이모티콘 같은것. 잉여스럽지만 정말 쓸모있다. 인간은 그런걸 많이 쓴다.)

f isCompilerOf G : dom f = LangOf(G)*, (∀x, y, z, (x =>* z, y =>* z) → f(x) = f(y))

해설 : ∀x, y, z ∈ LangOf(G)*, (x =>* z, y =>* z) → f(x) = f(y)이면 f를 컴파일러로 두는거다. 실제로는, 컴파일 결괏값이 언어 밖에 있을수도 있기에 codom은 명시되지 않았다. Func[{LangOf(G)*} × {S | S ⊆ U}]인... 놈이다. U는 전체집합으로, 공리계의 도메인이다. 공리계에서 다룰수 있는 원소에 따라 달라진다. 공리를 만족시키는 원소들의 집합이니...

same_as(f) ≜ Φ s.t. Φ(x, y) : f(x) = f(y) (i.e. Φ = {(x, y) | f(x) = f(y)}

해설 : 함숫값-동치 (제2역상에 따른 동치인), (함숫값-동치류 (제2역상에 따른 동치인 동치류)의 동치관계.)

G.same_as ≜ same_as(G.compiler)

G.compiler(x) ≜ {y | G.same_as(x, y)}

해설 : 이건 G.same_as와 G.compiler의 정의다. 위의 정의을 만족하는 G.same_as와 G.compiler가 유일함은 증명 가능하고 쉽게 보일수 있다.

L(G) ≜ <first(F(LangOf(G))), first(last(F(LangOf(G)))), last²(F(LangOf(G))), G.same_as>

해설 : G가 만드는 언어의 집합 L(G)이다. 자유 모노이드 모델에 동치관계 G.same_as를 추가했을 뿐이다.

해설 : G.same_as는 언어상 같은 뜻 (같은 해석)인 텍스트(언어 내 택스트, 문자열임)을 말한다.

noncompiled(x) ≜ {x}

해설 : 이건 해설이 따로 필요 없다 {x} = {v | v = x}니까.

compiled(L(G)) ≜ <G.compiler[first(L(G))] ∪ noncompiled(first(L(G))), noncompiled(first(last(L(G)))), (noncompiled◦first(last²(L(G)))◦<noncompiled⁻¹, noncompiled⁻¹>), compile, same_as(compile)> s.t. {compile|}_{noncompiled(first(L(G)))} = G.compiler ◦ noncompiled⁻¹, {compile|}_{G.compiler[first(L(G))]}(x) = x (단. <noncompiled⁻¹, noncompiled⁻¹>는 벡터장)

해설 : 컴파일된 compiled(L(G))의 모델. noncompiled(first(L(G)))는 컴파일되지 않은 버전이고 G.compiler[first(L(G))]는 컴파일된 버전이다. (겹치면, 그건 그 문자열이 컴파일 전후에 변하지 않은것이므로, 교집합의 존재가 무모순성에 영향을 미치지 않는다는것은 당연하고 쉽게 보일수 있다.)

추가 해설 : 
1. noncompiled(first(last(L(G))))에서 first(last(L(G)))가 자유 모노이드의 것을 그냥 가저온것이므로, noncompiled(first(last(L(G)))) = {ε}다.
2. (noncompiled◦first(last²(L(G)))◦<noncompiled⁻¹, noncompiled⁻¹>)(x, y) = noncompiled(first(last²(L(G)))(noncompiled⁻¹(x), noncompiled⁻¹(y)))이므로, noncompiled가 동형사상이고, 자유 모노이드나 L(G)의 concat이라는 모노이드 연산을 noncompiled(first(L(G)))와 noncompiled◦first(last²(L(G)))◦<noncompiled⁻¹, noncompiled⁻¹>가 이루는 모노이드로 연산을 가져온것이라는점을 알수 있다.
3. {compile|}_{noncompiled(first(L(G)))} = G.compiler ◦ noncompiled⁻¹, {compile|}_{G.compiler[first(L(G))]}(x) = x인 이유는, G.compiler[first(L(G))]가 정의역인 경우, 이미 컴파일 결과기에, 아닌 경우만 추가적으로 컴파일할 뿐이다.

마치며 : 상수기호 EMPTY는 EMPTY ≜ noncompiled(first(last(L(G))))로 모델 compiled(L(G))의 모델론적 언어의 상수기호다.

TIP : G.compiler는 G의 compiler라는 함수 method. 표기법이다. 단지 객체지향틱한 표기법일 뿐.
TIP : G.same_as는 G의 same_as라는 술어 method. 표기법이다. 단지 객체지향틱한 표기법일 뿐.
TIP : `=>*`는 Dragon Book에 나오는 표기법이다.
TIP : 상수기호 ε = "" = ()는 공문자열, 즉 공튜플이라고 불리는 기호다.
TIP : 미지수 L은 주로 언어셋(char set)을 표기할때 쓰이는 미지수다.
TIP : 별표 `*`는 클래이니 스타다.
TIP : 의미론적 등호를 통한 정의 기호 `≜` 를 사용한다. `≜`의 의미는 의미론적 등호를 통한 정의 기호다.

### 극단적 형식적 굴절 관점

주의 : 극단적 형식적 굴절 관점은 작성자가 포합어•교착어•굴절어를 구분하는걸 회의하는 작성자 본인의 뇌피셜이고 개똥철학이다. 음모론이라 불러도 될정도의 과학적 근거 없이, 형식적으로 같으니까, 현실에도 차이가 없을거라는 귀추법이다 (현실에 차이가 있어도 형식적으로 같을수 있다. 그럼에도 형식적으로 차이가 없으니까 묶는건 솔찍히 성급한 일반화가 맞다.)

극단적 형식적 굴절 관점 : 접두/접미사형 조사/접사를 이용한 교착/포합 굴절규칙도 굴절규칙이며, 토큰어 관점과 교착/포합 굴절 관점을 포함한, 굴절에 대한 극단적인 형식적 관점.
교착/포합 굴절 관점 : 교착(조사)/포합(문법접사)은 형식문법으로 표현시 굴절이나 다름없다는 고도의 형식주의적 관점. 교착이나 포합을 교착/포합 굴절이라고 부른다.
토큰어 관점 : tokenization이 프로그래밍 의미론상 굳이 어절과 regex `\b`를 도입하는 불필요한 문자 `\b`기준 split이라는 관점. 토큰어를 tokenization을 하는 언어로 간주.
(교착 / 포합 굴절) / 굴절 규칙 : 교착/포합 굴절과 굴절을 품사의 의미적•문법적 상태를 문법규칙으로 변화시키는 (교착 / 포합 굴절) / 굴절규칙으로 형식적으로 정리된다는 교착/포합 굴절 관점 사상에 따른 형식문법으로의 교착/포합/굴절의 표현
접두/접미사형 조사/접사 : 어근(어원)의 머리(시작)/꼬리(끝)에 접하는(붙는) 조사/접사

## 술어논리에서 자연어 문장 / 자연어 술어

자연어 문장의 경우 `Φ : "자연어 문자열"`인 문장 Φ이고
자연어 술어의 경우 `Φ(...) : "자연어 문자열"`인 함수 Φ이다.

1. 자연어 술어는 operator 사상을 통해서 정의되는 함수다. (자연어에서 자연어로 가는 함수다")
2. 자연어 명제는 "Φ est Verum"이 긍정되는 대상이거나 "Φ est Falsum"이 긍정되는 대상일시 Φ이다.
3. 긍정되는 대상은 형식언어에서의 긍정자 ♤에 대해, {x | ♤x}가 아닌 일반적인 언어에서의 긍정자 ♠︎데 대한 {x | ♠︎x}를 이르는 말이다.
4. 
5. 참의 비필연성 (단어로써의 참) : 형식언어에서의 {x | ♤x}는 "참은 분명하다"는 주장을 하고싶어하는데, 실제로 이론전산학적으로 컴퓨터가 정의되야, 분명한것이 현실의 실체로써 정의되어, Operation Semmentic에 따라 정의되고, 이론전산은 결국 형식언어가 이미 정의되어있어야 긍정 가능하므로 순환 논증이다. 다시말해, 형식언어와 일반적인 언어에서의 "긍정되는 명제"는 "언어의 자의성"에 따라 "hoc est verum"이라고 긍정되는 것들과, 사실 (혹은 객관적인 진실) 사이에는 아무런 필연적 관계가 없다.

### 화용론적 일반 가설

```
제 1 가설 : 보편적(일반적)으로 참인것은 일반적(보편적)으로 "긍정되는 것"(대부분의 사람이 말하는 {x | ♠︎x}로써, 대부분이 긍정하는 자연어적 명제)이다.
제 2 가설 : 사회적 공감대 • 불문율상 "긍정되는 것"이 존재하여 일반적(보편적)으로 긍정된다.
제 3 가설 : 보편적인 문법과 단어의 의미란, 최대 대수에게 긍정되었고, 사용된 문법과 의미을 의미한다.
```

가설인 이유 : 아직 내가 과학적 실험과 통계 자료로 구체적 수치로 증명하지 않았음.

#### 보편의 페러다임 시프트 가설

```
화용론적 일반 가설이 맞다면, 

A. 화자에 의해 일반적으로 긍정되는것
B. 화자에 의해 사회적 공감대 • 불문율상 "긍정되는 것
C. 화자에 의해 긍정되었고, 사용된 문법과 의미

가

언어 화자가 긍정하는 (A, B, C)의 모집단 X에 대해,

통시적인 X의 변화에 따라, 보편이 변화한다.

이를 보편의 페러다임 시프트라 한다.

보편의 페러다임 시프트 가설 : 보편의 페러다임 시프트는 존재한다 (다시 말해, 아까전에 말한 보편의 페러다임 시프트라는 현상은 실재로 있는 현상이다)
```

### 형식논리언어와 논리의 괴리 (2026년, 여기에 반박이 하나 생겼다. 2025년에 쓴 글이다)

읽어보기 전에

 + 이 글에서는 형식적인 사고는 기호의 조작일뿐이지, 논리는 logical cohereance에서 온다고 보았다.
 + 뇌과학적으로 logical cohereance를 관장하는 DLPFC없이 기저핵•측두엽•후두엽을 이용해 DLPFC없이 형식적으로 사고하는 나에게서 형식논리언어와 논리의 괴리를 찾아서 적어보았다.


표준국어대사전에 이렇게 나와있다.
```
논리 (論理) 「명사」 「1」 말이나 글에서 사고나 추리 따위를 이치에 맞게 이끌어 가는 과정이나 원리.
```

그뿐이다.

<br>

...

<br>

이제 글을 시작해 보겠다.

<br>

<br>

...

<br>

<br>

<br>

<br>

『형식논리언어는 그 언어적 사고를 하는데 있어, logical cohereance에 의존하지 않으니, logical cohereance에서 파생됬다고 보기 어렵다.』

형식논리상에서 긍정자 ♤와 일반적인 언어에서의 긍정자 ♠︎를 가정하자.

♤x : x ↔ T
♠︎x : (대충 x를 긍정하는 뜻)

나는 형식논리언어로 논리구문을 처리하기 때문에, 축소주의적 진리론을 당연하다고 착각하고 살았다.

자, 단순무식하게 새가지 펙트를 짚고 가자.

♤(x = y)

이때 x를 y로 해석해도 됨은 당연하다.

♠︎("미친놈아 참 잘하는짓이다" = "미친놈이 한 행위는 잘한 행위이다")

이것은 바보같은 해석이다. 형식문법리 아닌 속뜻과 맥락을 통한 해석이 있어야 한다.

여기서 먼저, 형식언어는 속뜻 = 겉뜻인 특성이 있어서, 그 의미론을 속뜻으로 파악하는 순간, 공리계 혹은 이론 T가 M ⊨ T인 M들에 의해 기계적으로 변환되는 대수적 사고방식으로 돌아간다는걸 알수있다.

Q1 : ♤(A가 B를 죽였다 → A는 마땅히 징역 5년을 구형받아야 한다.)가 맞나?

Q2 : ♠︎(A가 B를 죽였다 → A는 마땅히 징역 5년을 구형받아야 한다.)가 맞나?

두가지 문장 Q1, Q2는 다르다. 전자는 참일지 모르지만 후자는 맥락상 참이다. 그 이유는 전자는 가능새계에 구애받는데, 저것이 성립하는 가능세계인 「보편•사회문화맥락적 진리론」은 기본적으로 언어를 통한 사고에 깔려있기 때문이다.

우리는 여기서 형식언어가 「보편•사회문화맥락적 진리론」에 무관하다는 사실도 알 수 있다.

Q1 : ♤(A or B라면 마땅히 포함적이다)가 맞나?

Q2 : ♠︎(A or B라면 마땅히 포함적이다)가 맞나?

두가지 문장 Q1, Q2는 진리값이 다르다. Q1은 참이고 Q2는 반례를 "평생치킨 안먹기 또는 평생김치 안먹기 둘중 하나를 해야 살려주겠다"에서 "아니 두게다 안하게 해버릴수 있는 선택치를 주겠다고요? 이 나쁜놈아!"라고 할수 없는것같은 맥락에서, "또는"이 반례로 작용한다. Q2는 거짓이다.

참고로, Q1, Q2로 예시를 든 문장들은 「보편•사회문화맥락적 진리론」새계와 논리 구문 설명 예시에서, 각각 대한민국 형법과 양자택일의 상황 강요라는 부적절한 예시가 있었지만, 증명이 아닌 설명문이기에 굳이 수정할 이유가 없어보이니 넘어가자.

일단 마지막 예시를 보면 형식언어를 자연어로 번역하여 해석했을때, 형식언어로 사고했는지와 자연어로 사고했는지가 다르다.

콰인의 번역 불가능성 원리를 아는가?

> 
> "형식언어는 형식적으로 규정되는거지, 그 의미론은 형식적인 긍정자 ♤를 제외한 자연어로 규정되지 아니한다."
> 

이 문장은 번역 불가능성 정리에 의해 당연하다.

> 
> "언어 L에서 문장 Φ의 진리값은 L위에서 L의 단어로 평가된다."
> 

그렇다. 형식언어에서는 진리가 정의가 불가능하기에 절대적인 요소 ♤를 통하여 진리를 부여 가능하다.
그리고 ♤의 서술에는 ♤가 쓰인다. 즉, 올바른 설명이 아니다.

공리계인것이다.

공리계는 해당 공리계 내에서 설명 불가능하다. 어떤 설명문으로 설명하든지간에 그 근거가 될 수 없기 때문이다. 그것은 어떤 이유에서 참이지 않고 이유없이 참이기 때문리다.

따라서,

> 
> "진리 이외에 것들중에 공리계와 정의를 이론 T라고 하자. 이론 T가 형식적이면 진리는 형식적이지 않고 진리가 형식적이면 이론 T가 형식적이지 않다."
> 
> "이론 T가 형식적이지 아니하면, 그것은 형식언어가 아니다"
> 
> "따라서 이론 T는 형식적이여야 한다. 뭐... 그러나 미래에 형식언어의 정의가 바뀐다면 그렇지 아니할수도 있다... 아니 정확히 그렇지 아니할거다. 정의가 바뀐 미래에는"
> 

따라서 『형식논리는 **논리가 아니라 형식이다.**』

아스퍼거인인 나는 DLPFC를 통한 실행능력(계획•실행•사회적 사고)이 결핍되었기 때문에, 형식으로 사고한다.

그게 정말 논리적인 사고였으면 참 좋았을텐데, DLPFC라는 논리처리 프로세서를 쓰지않은 논리적 처리에서 나는 그저,

1. 몽상을 한다. 비논리적인 상태에서 증명에 로드맵을 짠다.
2. 해당 로드맵이 추론에 적합한지 형식논리를 통해 검토한다.
3. 형식논리적으로 기호를 조작한다.

순서로 사고한다.

그리고 【형식적이지 않고 진짜로 참된 관점에서의 논리적으로 일관된(logical cohereance를 가지는)】 논리는 이치에 맞아야 한다. 형식논리의 의미론(semmentics)는 언어 개임일 뿐이고,
그 이치가 구문론적인 언어 L위에서 T가 동작하기에 lang에 의해 의미론(semmentics)가 부여되어 「인간 사고」로 동작하는것이지, 인간사고이기 이전에 생각도 언어도 뭣도 의미도 아닌 형식일 뿐이다.

따라서 형식논리는 자연어의 논리와 다른 개념의 논리이다.

#### 2026년 반박.

요약 : 만약, 보편의 페러다임 시프트 가설이 맞다면...  보편적이지 않은 개인의 해석, 즉 화자간의 해석 차이 문재는, 실제로 존재하는 문제이기에, 논리 해석에 있어 예외이게 된다.

개인의 해석에 따라서, 언어 화자가 긍정하는 (A, B, C)는 개인 차가 존재한다.

물론, "화자 X의 언어 사용 방식 (A, B, C)는 맞다/틀리다"라는 문장으로 잣대를 들이대서, 모두가 보편적으로 맞게 해석한 문장을, 언어로 삼는것이 맞다.

언어의 사회성은, 표준 해석 방식인 `(A, B, C)`의 범위를 지정한다. (일반적으로 지지되는 이데올로기든 아니든, `(A, B, C)`는 여러가지다. 사람들이 새상을 보는 창에 다라, 범위도 달라진다.)

그렇기에, 혼자서 언어를 이상한식으로 해석하는, 짜증나는 친구 B가 있다면, 그 사람한테는 해당 언어가 (A, B, C)로 해석될거다.

어쩔수가 없다... 개인의 해석 차이는..

언어의 의미는 그 "사용 방식"(그 사용 방식은 여러가지가 있는데, 일반적인 인간은, 일반적인 사용 방식을 쓴다)에 있다.
````

겉뜻의미론을 통해, 함수형으로 환원된, 품사의 표기법.

그러나, 속뜻의미론은 표현하지 못한다.

#### 긍정자에 대한 추가노트

````markdown
# 긍정자에 대한 추가노트

긍정자는 다음과 같이 langblock notation을 통하여 정의된다
 * L♤"~" : ♤L"~"
 * L♠︎"~" : ♠︎L"~"

## langblock noation이란?

```markdown
# langblock notation

일반적인 집합론에서의 langblock과 endofunctor typesystem에서의 langblock을 정의하는 notation이다.

문자열을 편리하게 표기하기 위한 용도이나, 사실은 llfn(lambda - like function notation)에서 활용하기 좋게 하려는 의도도 있었다.

## langblock notation - type I : 일반적인 집합론에서의 langblock

쉽게 말해 `L"~"`식으로 문자열을 작성하면 해당 문자열을 언어 L의 문자열(텍스트)로 취급하는거다.

t3n으로 간소화한 형식 문법으로 적자면

"L\"" `concat` x `concat`  "\"" =>¹ "\"" `concat` x `concat`  "\" (∈ L*)"

이다.

마치 markdown의 codeblock처럼, 문자열을 담는 블럭을 언어명 L로 묶는다 하여 langblock이라 이름지었다.

## langblock notation - type II : endofunctor typesystem에서의 langblock

쉽게 말하자면`(::L)"~"`의 경우, `L* EndofucntorType "~"`로 해석한다.

형식문법으로는 아래와 같다.

"(::L)\"" `concat` x `concat` "\"" =>¹ "L* EndofucntorType \"" `concat` x `concat` "\""

EndofucntorType에 대한 글에서 언급한 바 있듯이,

f = S EndofucntorType x 에 대해,

f의 타입은 f :: S이고, dom f = S°⁰°, codom f = S, graph f = {(ε, x)}가 되기에, f() = x이다.

그런 타입으로 만들어버리는 무시무시한 기능도 제공한다는거다.

## llfn(lambda - like function notation)에서의 활용

(λx :: L*)

...작성중...
```

후술하겠지만, 실제로 언어에서 사용될때는 타입이론은 전혀 사용되지 않는다.

엔도펑터 타입 시스템을 응용한 notation들에서 그저 notation만 참고하라.

## 자연어에서의 타입결여에 대해서.

「컴파일된 형식언어 a.k.a. compiled(L(G)) 의 정의.」에서도 알수 있듯이, 오로지 L*타입만 존재한다.

1. 임의의 형식적 결합사 (접속사 • 전치사 • 수식언 • 접사형 문자열 • etc...) x에 대해서, compiled(L(G))(x)의 정의역은 L* × L*이다.
2. 만약 정의역이 L*의 부분집합인 타입으로 제한하면?
3. 그건 형식언일 뿐이지, 더이상 자연어가 아니다.

예컨데, 자연어는 **문법적으로 틀려도 허용하고 넘어갈수 있다.**

다시말해, 화용론적으로 파악되니, 문법의 validity를 따질생각이 아니라면, 타입 사용은 작 목을 자기가 따는 바보짓이다.

자연어가 형식적이면 좋겠다는 기대는, 그냥 이과 특유의 비논리적 환원주의이다.

에초에 자연어 의미론이 온전히 수학으로 파악될수 있었으면, 난 논리학을 깊게 파지 않았을거다. 환원이 안되니까, 깊게 파게 된거다. 문학을 수학으로 환원하려는 급의 삽질이다.

전혀 환원 안된다. 자연어는 절대로 그렇게 딱 맞아떨어지지 않는다.

의미 단위는 뭐가 다를까?

X = {x | "x는 S라는 분류에 해당한다."}에 대하여,

S라는 분류에서만 정의되는 형용사 y에 대해, X에 속하지 않는 z에 대해,

"대상 x가 " `concat` ("" `compiled(L(G))(y)` x) `concat` "일때, x를 걍 새로운 단어나 문학적 허용으로 쓸수도 있다. 심지어는, 히스테릭한 사람이 그런 단어를 쓰고, 있다고 우겼을때, 우리는 대충 \"네네, 그러시겠죠^^\"하고 무시하고 넘긴다. 인간은 언제든지 문법을 파괴할 준비가 되어있다."

라는 문장이 어색하지도 않은데다가, 맞는말이다.

그렇다. 문법은 허상이다. 규약적으로 정의되었거나, 사람들이 사용하니까 보편이 된 표준이거나다.
전자는 사회적 실제로 집행방법이 필요하고, 후자는 근본적인 이유다. 문법은 언어가 존재하니까, 자연스럽게 그 언어가 쓰이는 양상에 따라서, 도출되는것 뿐이다. 문자열이 문법보다 먼저다.

## 사실은 형식언어의 긍정자 ♤랑 자연어의 긍정자 ♠︎를 나룰 필요도 없다.

형식언어의 긍정자 ♤가 더 참을 정하는 기준이 명확하거나 그 기준을 의심하기 쉬운게 아니다.
오히려 동일하다.

보편은 "불특정 다수가 true인 명제으로써 선택한 명제"으로써, 아무 이유 없이, "이건 참이라고 불려지니까 (남들이 참이라고 말하는걸로 증명되며, 증명 없이 "당연함"으로 받아들여지는것이니) 랄까, 대부분이 경우 참이니까"라는 사회적 공감대 안에서 형성된다.

거기에, 타당한 이유는 없다. 이유없는 행동이다. 변호의 여지가 없다

형식언어도 마찬가지이다. 공리가 선택되는건 "일단 이걸 당연한걸로 취급할건데, 근거는 없음. 즉 이 이후는 이 선언을 전제로 하는 가언문임."이라거 하는 과정에 불과하다.

우리는 흔히 집합을 정의하는거에 이유를 붙이려 하거나, 그걸 증명하려 든다.

그러다가 힐베르트처럼 자신의 꿈이 좌절될테니 별로 좋은 짓은 아니다. 형식언어의 참도, 결국 기표다.

참은 기표로써, 아무 이유없이, 걍 언어 맘대로 배정된것에 불과하다. 그러니, 형식언어의 긍정자와 저연어의 긍정자는 구분할 필요가 없다.

힌트 연산자로 굳이 구분해서 정의하자면,

 * L♤"~" : Hint(L, "형식언어임")♤"~"
 * L♠︎"~" : Hint(L, "일상어임")♤"~"

정도의 차이다. 그냥 라틴어랑 일본어, 한국어 비교하는 정도라고 생각한다.

차이가 얼마나 나던간에, 참은 기표로써, 아무 이유없이, 걍 언어 맘대로 배정된것에 불과하다. 그러니, 형식언어의 긍정자와 저연어의 긍정자는 구분할 필요가 없으며, 형식언어는 전혀 reasonable하지 않다.
````

#### 긍정자에 정의에 쓰인 엔도펑터 타입 시스템을 응용한 notation들
````markdown
# 엔도펑터 타입 시스템 - 추상화 Ver

이전에 내가 정의한 엔도펑터 타입 시스템을 조금 추상화해봤다.

## first / last / reverse / hold 연산

튜플에 제귀적 정의 `(x, ⋯) := (x, (⋯))`에 따라서, dom reversed = {x | dim x ≥ 2} 이다.

first(x, y) = x
last(x, y) = y

reverse(x) = (last(x), firsr(x))
i.e. reverse(x, y) = (y, x)

hold = reverse²
i.e. hold(x, y) = (x, y)

(∈ ker (dim - 1) ∪ ker dim)(x) : ¬(∈ dom reverse)

pf.

ker (dim - 1))
 = {x | (dim - 1)(x) = 0}
 = {x | dim(x) - 1 = 0}
 = {x | dim(x) = 1}

ker dim
 = {x | dim x = 0}

ker (dim - 1) ∪ ker dim
 = {x | dim x = 1 ∨ dim x = 0}

dom reverse
 = {x | dim x ≥ 2}

## concat 연산

1. concat(x, y) = hold(x, y) (단. dim x = 1)
2. concat(x, y) = first(x) `concat` (last(x) `concat` y) (단. dim x ≠ 1)

반군을 이룬다. 자유모노이드의 붙여쓰기 연산자기 때문이다.

## len 연산

0. InnerProductSpace(<(len² x) ⊗ ℝ, +, ×, <•|•>>), dim len² x) ⊗ ℝ = 1 (단. ×는 스칼라배, +는 벡터 합, <•|•>는 bra-cket 내적, (len² x)는 정규직교기저)
1. lenⁿ x = len² x (단. n > 1)
2. card ker len = 1, ker len = {HaskellNullModelConstant}
3. dim x = 1 ↔ len x = len²(x)
4. lentwo ≜ len²(HaskellNullModelConstant)
5. len HaskellNullModelConstant = 0 lentwo
6. len x = (dim x)lentwo
7. len x[:L lentwo] = L lentwo
8. len x[::-1] = len x
9. len concat(x, y) = len x + len y
10. lentwoⁿ = lentwo

## [::-1]함자

1. x[::-1] = x[len x] `concat` x[:len x][::-1] (dim x > 1)
2. x[::-1] = x (dim x < 2)

## [::y]함자와 x[::y]연산, [:y]함자와 x[:y]연산, x[y:]연산과, [y:]함자, x[y]연산과, [y]함자.

1. [:: i j lentwo] = [:: i lentwo][:: j lentwo]
2. [:: x][:: y] = [:: y] ◦ [:: x]
3. [: x][: y] = [: y] ◦ [: x]
4. [x :][y :] = [y :] ◦ [x :]
5. x[y :] = [::-1][: len(x) - y][::-1]
6. x[: 0] = HaskellNullModelConstant
7. x[y :][z :] = x[y + z :]
8. x[::1] = x
9. [::0] = [: 0]
10. [: 0][:: y] = [: 0]
11. x[:: y] = x[0] `concat` x[y :][::y]
12. concat(x, y)[: len x] = x
13. concat(x, y)[len x :] = y
14. [x] = [x:][:lentwo] = [:x + lentwo][0:]
15. [:: x][y] = [xy]
16. x[len x - lentwo] = last^{<lentwo | len x - lentwo>}(x) lentwo (즉, (<lento |)(v) = ||v|| = 이고, <lento | x lento> = x이므로, <lentwo | len x - lentwo> = dim x - 1)
17. x[0 lentwo] = first(x) lentwo
18. x[lentwo:] = last(x)
19. x[y] = x[lentwo:][y - lentwo]
20. x[n lentwo : ] = lastⁿ(x)
21. x[n lentwo] = first(lastⁿ(x)) lentwo (n < dim x - 1)
32. Param(concat)ᵢ₌ₐᵇ x = x[a:b] (코멘트 : python의 str이 갑자기 문자셋에 숫자가 추가된 느낌 wwwwwww perl마냥 ㅋㅋㅋ)
33. [x : y] = [: y][x :] = [x :][: y - x]
34. [x : x + lentwo] = [x]

## HLON(Haskell-Like Operator Notation) : 내가 만든 웃긴 노테이션

Definition)

```HLON
0. Param(f)ᵢ₌ₐᵇ termᵢ = Param(f)(Param(concat)ᵢ₌ₐᵇ termᵢ)
1. ∀f(x) = `x`, f(f(x)) = x
2. ∀f : X × Y ↦ Z, x `f` y = f(x, y)
3. ∀g(f, x)ᵢ = (`f` xᵢ), (Param(`◦`)ᵢ₌₀ⁿ⁻¹ g(f, x)ᵢ)(y) = f(concat(y, Param(`◦`)ᵢ₌₀ⁿ⁻¹ x))
```

예컨데,
 + x ``?`` y ``:`` z = x ? y : z 이며
 + (x ?)(y : z) = (:z)(x ? y) = (x ? • : z)(y) = x ? y : z 이고
 + (? y) = (y :) = (? y :) 이며
 +  (? y :)(x, z) = x ? y : z 이고,
 + (x ? • : •) = (x ?:) 이며
 + (• ? x : •) = (? x : ) 이며
 + (• ? • : x) = (?: x) 이다.
 + 아예, (`? `◦`:`)(x, y, z) = x?y:z 다.
 + x `(`? `◦`:`)` y (`? `◦`:`) z = x?y:z 라고까지 볼수 있다.

그렇다. 이건 결과적으로,

a `f` ⋯ `f` z = f(a, ⋯, z) 따위를 구현 가능하게 해준다.

### 주의사항

`f`는 객체(object)다. 클래스는 ∀g(f) = `f`인 g가 클래스가 된다.

## TOS(Top Of Stack) 연산자

TOS는 TOSC (TOS-Core)를 통해 작동하는데,

∀dim dom f < 2, `TOSC`(concat(⋯, f)) = f(⋯) (단. ⋯는 비어있을수 있다. 길이는 0이나 1이다)
∀dim dom f > 1, x TOSC f = (TOSC (`x` f))

(TOS f) ≜ (TOSC f◦[::-1])

그래서 작동은 어떻게 하냐?

a ⋯ x y z TOSC f
 = a ⋯ x y TOSC (z `f`)
 = a ⋯ x TOS (y `(z `f`)`)
 = a ⋯ x TOS (z `f` y `f`)
 = ...
 = f(z, ⋯, a) 이다.

HOLN에 따르면, f가 n항연산이면, `(z `f`)`는 n - 1항 연산이다.

그건 펙트다.

TOSC f◦[::-1]는 그저, 인자를 거꾸로 받는 버전일 뿐.

RevTOS는 TOS의 역연산이고, RevTOSC는 TOSC의 역연산이다. 각각, 후위 연산자를 받아서 전위 연산으로 변형한다.

## 삼항연산자 표기법

x?y:z ≜ $\begin{cases} y, & (x), \ z, & (¬x) \end{cased}$

## 수량자 표기법

0. S⁽ⁿ⁺¹⁾ ≜ Sⁿ × S¹ (단. S² ≜ S × S)
1. 클레이니 스타 쓴다.
2. S? ≜ S°¹°
3. S+ ≜ S × S*
4. S* ≜ S+? 로 재정의되었다.
5. S°ⁿ° ≜ S* ∩ {v | dim v ≤ n} ≜ (n=0)?HaskellNullModelDomain:((n=1)?S∪S°⁰°:S°ⁿ⁻¹°∪Sⁿ)

## HaskellNullModel 상수

1. HaskellNullModelConstant ≜ first(HaskellNullModel) ≜ ε ≜ ()
2. HaskellNullModelDomain ≜ last(HaskellNullModel) ≜ S°⁰° ≜ {HaskellNullModelConstant}
3. HaskellNullModel ≜ <HaskellNullModelDomain, HaskellNullModelConstant>

그렇다. 그냥 평범한 공튜플이다.

## int함수와 bool술어

함자 (?1:0) : 𝔹 ↦ {0, 1} 에 대해,
int ≜ (?1:0)

bool ≜ last(<{0, 1}, bool>) ≜ int⁻¹ ≜ {1} ≜ (=1) ≜ (≠ 0) s.t. bool(x) : 1 = x ≠ 0

## 이항연산으로써의 함수 합성

dom f◦g ≜ dom g
codom f◦g ≜ codom f
graph f◦g ≜ (`graph f` εu `graph g`)

이항 관계에 대한 HLON에 따라서,

(graph f◦g)(x, y)
 = (`graph f` εu `graph g`)(x, y)
 = x `{`graph f` εu `graph g`}` y
 = x `graph f` εu `graph g` y

즉,

x `graph f◦g` y : ∃u, x `graph f` u `graph g` y

이다.

## 이항관계에 대한 HLON

<D, R>에 대해, R ⊆ Dⁿ이면,

R : Dⁿ ↦ 𝔹 이다.

pf.

R = bool◦int◦R

그런데, int◦R : Dⁿ ↦ {0, 1}

Q.E.D.

## Param 시스템

Definition)
1. ∀Antigroup(<S, f>), Param <S, f> ≜ <S × S+, Param f)
2. (x `Param f`)(y) ≜ (x `f`)((Param f)^{int(dim y ≠ 1)}(y))

## My Endofunctor Type System : 내가 만든 웃긴 타입 시스템

ET = EndofunctorType

T EndofunctorType v ≜ (dom (T EndofunctorType v), codom (T EndofunctorType v), graph (T EndofunctorType v)) ≜ (HaskellNullModelDomain, T, HaskellNullModelDomain × {v})
(단. (T EndofunctorType) = (dom (T EndofunctorType), codom (T EndofunctorType), graph (T EndofunctorType)) = (T, Func(HaskellNullModelDomain, T), {(v, (HaskellNullModelDomain, T, HaskellNullModelDomain × {v}) | v ∈ T}))

이항관계 ``::``를 다음과 같이 정의한다.

(v :: T) : (v ∈ (T EndofunctorType)[dom (T EndofunctorType)])

(T EndofunctorType)의 치역이 (T EndofunctorType)[dom (T EndofunctorType)]니까 말 다했다.

## 합타입

(x :: (T | G)) : (x :: T) ∨ (x :: G)

누구나 알수 있듯, 이항관계 ``::``를 확장하여,

(x :: T | G) : (x :: T) ∨ (x :: G)

식의 삼항관계를 만들었고, 

(T | G)는 HLON으로 정의된 함자 객체인 셈이다.

HLON에서만 펙트다.

### 주의사항

(T | G)도 결국 타입생성자 ``|``를 통해 조합되는 객체다.

## 곱타입

곱타입은 세미콜론 ``;`` 타입생성자를 통해서 작성된다.

(RevTOS ``;``)(T, v) 는 길이-1 곱타입

(RevTOS ``;``)(T, v) (RevTOS ``;``)(T, v) 는 길이 - 2 곱타입이다.

(RevTOS ``;``)(T, v) (RevTOS ``;``)(T, v) = (RevTOS ``;``)(T, v) × (RevTOS ``;``)(T, v)이다. 곱셈이 정의된 객체(Object)다.

당연히
Πᵢ₌₀ⁿ (RevTOS ``;``)(Tᵢ, vᵢ) ≜ (RevTOS ``;``)(T₀, v₀) × Πᵢ₌₁ⁿ (RevTOS ``;``)(Tᵢ, vᵢ)

인데,

(RevTOS ``;``)(T₀, v₀) × Πᵢ₌₁ⁿ (RevTOS ``;``)(Tᵢ, vᵢ) ≜ (RevTOS ``;``)(T₀, v₀) × (RevTOS ``;``)(Πᵢ₌₁ⁿ (RevTOS ``;``)(Tᵢ, vᵢ), ŷ)

이며,

(RevTOS ``;``)(T₀, v₀) × (RevTOS ``;``)(T₁, v₁)는

<(RevTOS ``;``)(T₀, v₀) × (RevTOS ``;``)(T₁, v₁) | T₀ | T₁, v₀, v₁>이라는 연산을 이루는데,

x성분 x̂, y성분 ŷ에 대해,
v :: ((RevTOS ``;``)(T, v) dom; T codom; dom v × codom v graph)
x :: (RevTOS ``;``)(T, v)
v(x) ≜ <x̂ | x()>

NOTE : x가 Endofunctor type객체면, 무조건 ()를 이용해야하는게 당연한거다. x의 값은, 항상 x()다.

v₀ :: ((RevTOS ``;``)(T₀, v₀) × (RevTOS ``;``)(T₁, v₁) dom; T codom; dom v₀ × codom v₀ graph)
x :: (RevTOS ``;``)(T, v₀)
v₀(x) ≜ <x̂ | x()>

NOTE : x가 Endofunctor type객체면, 무조건 ()를 이용해야하는게 당연한거다. x의 값은, 항상 x()다.

v₁ :: ((RevTOS ``;``)(T₀, v₀) × (RevTOS ``;``)(T₁, v₁) dom; T codom; dom v₁ × codom v₁ graph)
x :: (RevTOS ``;``)(T, v₁)
v₁(x) ≜ <ŷ | x()> 로 정의되며,

NOTE : x가 Endofunctor type객체면, 무조건 ()를 이용해야하는게 당연한거다. x의 값은, 항상 x()다.

vᵢ :: ((RevTOS ``;``)(T₀, v₀) × (RevTOS ``;``)(Πᵢ₌₁ⁿ (RevTOS ``;``)(Tᵢ, vᵢ), ŷ) dom, Tᵢ codom, dom vᵢ × codom vᵢ graph)
x :: (RevTOS ``;``)(T₀, v₀) × (RevTOS ``;``)(Πᵢ₌₁ⁿ (RevTOS ``;``)(Tᵢ, vᵢ), ŷ)
vᵢ(x) ≜ vᵢ(ŷ(x)) 로 정의된다.

그래서, Haskell의 곱타입마냥 저딴 어트리뷰트 사용법마냥 사용 가능하게 정의되었다.

이것도 합타입처럼, 객체-클래스-메타클래스 구조다.

### 주의사항

객체-클래스-메타클래스 구조이긴 한데...

```
x :: 곱타입
```

식으로 선언해주었다면, x()가 그 객체다.

NOTE : 이전 노트에서 곱타입에 굳이 엔도펑터 호출식을 적은 이유가 바로 그러한 이유에서다.

### 생성자

```
Πᵢ₌₀ⁿ (RevTOS ``;``)(Tᵢ, vᵢ) ET (Param(concat)ᵢ₌₀ⁿ Tᵢ ET wᵢ)
```

식으로, 튜플을 해당 타입으로 초기화가 가능하다.

Initialize-Notation으로,

```
Πᵢ₌₀ⁿ (RevTOS ``;``)(Tᵢ, vᵢ) ET (Param(concat)ᵢ₌₀ⁿ vᵢ = wᵢ)
```

로도 적을수 있다.

## 멱집합 타입

P(X) = 2^X = {S | S ⊆ X}로 집합명 만들고 생성하는게 설마 어려울리가 없겠지

## 함수 타입

(X -> Y) ≜ (X dom; Y codom; P(X × Y) graph;)
라고 정의하겠다.

ㅋㅋㅋ 에초에 함수가 튜플이라 かんぺき한 정의다 ㅋㅋ

## 결론적으로 모든 타입을 모으자면

술어 iset = isET가 합타입 • 곱타입 • ET타입으로 이루어진 타입을 이르는 명칭이다.

## 지네릭 타입

X :: ETemplate(iset*, codom, graph)인 사실상 함수 타입인데,

X<⋯>식으로 작성한다.

그렇다. 이건 그저 Notation일 뿐.

Notation은 Notation인데, 타입을 객체로 취급해주는 레벨인거다.

## tuplic-definion (Notation)

tuplic-definion (Notation)이란, 함수를 "(dom = X, codom = Y, graph f)(⋯) ≜ ~"스타일로 엄밀하게 한줄로 정의하는 표기법(Notation)이다.

당연히, 곱타입 명시도 아니고서, 저런식으로 작성을 할수가 없고, graph f는 심지어 타입 초기화가 아닌 f라는 심볼의 타입을 알지 않고서야, 유효하지 않을수 있다. 다만, 그렇기에, 해당 구문에 해당하는 기의가 없었기에, 표기법 (Notation)용도로 사용한것이다.

한마디로

표기

```
(dom = X, codom = Y, graph f)(⋯) ≜ ~
```

를

```
f :: X -> Y
f(⋯) ≜ ~
```

로 정의하는 표기법 (Notaion)이다.

이 최강의 표기법을 얻고싶어서 이지랄을 떨었던거다.

앞으로는, "(dom = X, codom = Y, graph f)(⋯) ≜ ~"식으로 함수 f를 정의할 생각이다.

## 주의사항

타입 시스템이라는 말이 프로그래밍에 주로 쓰여서 오해를 방지하기 위해 한가지 명시하겟다.

이건 수학용 타입 시스템이다. 뭣같은 코딩이 아니고.

## 참고사항

### 추상화 이전 버전

#### 엔도펑터 타입 시스템

나는 지난 고2때 배운 수 II를 정리하다, 문득 내가 요즘 탐구하고 있는, 연산자의 Haskell식 표현이나, 문법 compile함수의 특성, 그리고, 연산 법칙의 문법규칙화를 통해서, AC와 엔도펑터를 이용한, 타입 시스템을 만들수 있고, 이는 극한점의 타입을, 함수의 그래프로 사용하는데 유용하다는걸 알게 되었다

요약 : 이 글은, v on f : (v :: graph f)라는 이항관계, on을 정의하고 싶어서 만든것이기도 하며, 우연히 발견한 구조에 대한 노트다.

모노이드 <L, e, f>에 대하여, 자유모노이드 <L*, ε, .>는 모노이드 <L, e, f>의 도메인 L을 charset(문자셋), 즉 언어로 하는 문자열의 집합 L*을 도메인으로 하는 문자열 concat의 모노이드다. 앞으로 문자열 L"⋯"라고 적는다면, "⋯"는 언어 L의 문자열인것으로 하겠다.
형식문법 G = <N, Σ, P, S>가 생성하는 언어 L(G)를 자유 모노이드 L(G) = <L*, ε, L(G).compile, .>라고 하겠다. 언어 L에서의 문법적 동치는, 문법적 동치류 L(G).same(y) = {x | L(G).compile(x) = L(G).compile(y)}를 동치류로 가지는 동치관계다.
반군 <S, f>에 대하여, 유사-Haskell식 중위표기법 x `g` ⋯ `g` y = g(x, ⋯, y)는 f에 대해, (x `f` y) = f(x, y)로 중위표기를 가능하게 하여, 함자로 표기하기 용이하게 한다.
Plus <L, f> = <L+, Plus f>이며, L+ = L × L*이다.
(x `Plus f`)(y) = (x `f`)({Plus f}^{int(dim y ≠ 1)}(y))로 귀납적으로 정의된다.
왜냐하면, y는 카데시안 곱으로 된 집합 L+의 원소고, L* = (L+)?으로, L? = L⁰ ∪ L¹로 정의되어있고, 이는, dim이 1 이상인 튜플이며, 해당 튜플은 튜플의 제귀적 정의에 따라서, (x, ⋯) := (x, (⋯))로 작성되어있기 때문이다. 에초에 다변수 함수의 입력도 튜플이다.
카데시안 곱으로 된 서로다른 벡터공간들의 합집합과, 클래이니 스타로 된 문자열과 튜플의 집합을 튜플로 취급하는 이유는, 결국 그것들이 튜플로 이루어졌기 때문이다. ZFC의 문법 G_{ZFC}에 대해, ZFC의 기표 언어 L_{ZFC}는 대수구조 L_{ZFC}(G_{ZFC})로 그 형식적 작동을 설명할수 있으며, L_{ZFC}(G_{ZFC}).compile의 결과가 동일하면, 동일한 대상이기 때문에, 같게 취급하는거다. 형식이 전부다. 나머지는 없다. 있다고 단정할수 없다. 그러나, 우리는 직관적으로 없는걸 해석할때가 많은것 뿐이다. (형식을 직관화하는것과, 직관을 형식화하는것 중에, 직관을 형식화하는것만 가능하고, 형식을 직관화하는건, 일개 자연어적 해석일 뿐이지, 해당 형식언어에서는 L(G).compile이 작동하는 사실과 무관한 해석이 되는거다.)
Definition)
1. 정의용 제 1 규칙 : 모델 Plus <S, f>의 모델론적 언어 L에 대하여, 해당 언어 L의 변수문자와 상수문자와 쉼표로 구성된 문자열 k, v에 대해, L"(Plus f)(⋯, " . k . L", y) = (Plus f)(⋯, " . v . L", y)"인 경우, 모델 Star <S, f> = <S*, Star f>의 모델론적 언어 N에 대하여, N"(Star f)(" . k . ") = (Star f)(" . v . ")"이다.
2. 정의용 제 2 규칙 : (Star f)(v) = (Plus f)(v)이다.
이로써, Star를 정의했는데, 사실, Star는 멱등법칙을 만족하는 반군이나, 모노이드에서나 정의된다. 그 이유를 말해보자면,
(Plus f)(⋯, x, x, y) = (Plus f)(⋯, x, y)이거나 (Plus f)(⋯, x, e, y) = (Plus f)(⋯, x, y)이여야,
(Star f)(x, x) = Star(x) = x이거나, (Star f)(x, e) = x로, Plus f연산의 인자 수를 줄이는 연산으로 타당하기 때문이다.
가환 반군의 경우, Star의 인자는 무순서 튜플이라, 사실상 중복집합과 다를바가 없고, 멱등 반군(멱등법칙을 만족시키는 반군을 줄인 내가만든 줄임말)은, 축약시 인자가 연속될일이 없다.
그러므로, 가환 멱등 반군의 경우, 인자가 집합과 다를바게 없게 된다 
다를바가 없다는건 비유적 표현이지. 동형이라는게 더 맞는말인것 같다.

그래서, 멱등 반군이나 모노이드가 아니면, L × L+여야 하고... 아 그렇네 ㅋㅋ 지금까지 내 정의가 조금 망ㅎ이 잘못됬다 암튼. (Param을 L × L+로, Plus를 L+로, Star를 L*로 다시 대응시켜야겠네...)
멱등 반군이나 모노이드는 L*로.
모노이드의 경우, 항등원 e에 대해 규칙 (Star f)(⋯, e) = (Star f)(⋯)가 문법규칙마냥 적용되므로, (Star f)() = (Star f)(e) = Star(e, e) = e로, 정의역을 L⁰으로 제한하면, 프로그래밍할때 많이 쓰이고, 나도 자주 쓰는 그 엔도펑터가 되는데, 막상 공역은 한번도 제한되거나 확장된적이 없어서, 공역은 f의 domain인 L이 된다.

이번엔, Star와 유사한데, FSM버전으로 바꾼 Star로,
L°⁰° = L⁰
L°ⁿ° = (L × L°⁽ⁿ ⁻ ¹⁾)? (n ≠ 0)
로 정의된 L°ⁿ°에 대해,
Starₙ f = {(Star f)|}_{L°ⁿ°}
Starₙ <L*, ε, Star f, .> = <L°ⁿ°, ε, Starₙ f, .>
Starₙ <L, e, f> = Starₙ <L*, ε, Star f, .>

즉,

Star₀ <L, e, f> = Star₀ <L*, ε, Star f, .> = <L⁰, ε, Star₀ f, .>
이고, L⁰ = {ε}이다.

그리고, 다음을 정의하겠다.
RET = ReversibleET = ReversibleEndofunctorType s.t. ReversibleEndofunctorType <L, e, f> = Star₀ <L, e, f>
RET <{ε}, ε, Star₀ f, .> = Star₀ f
CET = CoreofET = CoreofEndofunctorType s.t. CET Star₀ f = codom Star₀ f
ET = EndofunctorType
(y = RET x or y = CET x) ifi (y = ET x)
라고 정의하겠다.
또한,
(x :: T) : (x() ∈ T)
라 정의한다
이것이, 엔도펑터 타입 시스템.
선택함수 choose에 대하여, T ET choose = <T, choose(T), f>라는 모노이드를 반환한다.
엔도펑터 타입 시스템은, AC가 보장되어야, 임의의 집합 T에 대해서, T ET choose가 잘 정의되기 때문에, AC가 필요하며, 해당 모노이드를 다룸에 있어서, 엔도펑터와 동형인 형식적 작동이 존재하기에,

ET ({()}, (), x, ({()}², {()}, {()})) = x로 간단히 대수적인 의미의 대상으로 포메팅되기도 하며, 사실상, 문자열 format마냥 당연하게 일대일대응이다.
엔도펑터 자체로도 ET x = T이고, x()가 값이고, x() ∈ ET x라서, 타입 시스템도 된다.
또한 사용함에 있어서, C++의 스마트포인터가 lock해제로 접근하듯, 여기도 이러한 방식을 활용하여, 편리한 사용도 가능한것 같아서, 개인적으로 뿌듯하다.

T ET choose = T ET choose(T) 이며,
T ET x = <T, x, f>인 모노이드로 정의된다고 해두겠다.

이상으로, EndofunctorTypesystem의 정의를 마친다.

## Application (응용가능성과, 응용 사례)

이를 응용하면, 다음 표기법이 가능하다. 다만 다음 표기법은 Endofunctor Type이 아닌 독자적인 개인용 표기법이다. (그렇다. 순전히 내 편의를 위해 기록한거다. 별개의 것이기에 같이 소개되면 안된다. (그리고 홍보 의도도 없다) 그러다 파일을 만들기 귀찮았기에 여기에다 적었다.)

### graph type notation
1. (:f) ≜ graph f
2. (P ::: f) : (P :: (:f))
각각 단항연산자 `(:•)`및 이항관계 `:::`이다. 모델론적 언어인대도, notation이라 부르는 이유는, 이미 술어논리와 모델론에서 사용되고 있는 기호인 `:`을 남용했기에, 표기법으로 정의해야 했다.

### truth-functional-set-operator)

진리함수는 함수이지 술어(집합)이 아니다.

그러나, 치역이 진리치기만 하면 상관없는 사람들을 위해서 다음 단항연산을 제공한다.

모델 TFSM(D) ≜ <D, TFSO>에 대하여,

TFSO f ≜ {x | f(x)}

dom TFSO = {f | dom f ⊆ D, codom f = 𝔹}
codom TFSO ⊆ D

즉, 전체집합 D에 따라서, TFSO는 달라진다. 다만, 주의할점은, D에 기본적으로 우주 (Universe)를 대입할 생각으로 설계했기에ㅜ 범주론의 공리를 받아들이지 않는 선에서 사용하면, TFSO의 사용은 다소 자유롭지 않다.

### Endofunctor-TypeSet Notation

엔도펑터 타입 시스템을 TFSO를 통하여 집합으로 나타내는 Notation이다.

다음 이항관계 ETSN(::), ETSN(:::)는 다음과 같이 정의되어, 이 함자 표기를 통한 타입 시스템에 쓰이기에, 체계에 쓰인다
1. (x ETSN(::) y) : (x :: y)
2. (x ETSN(:::) y) : (x ::: y)
3. (:: x) ≜ TFSO((ETSN(::) x)
4. (::: x) ≜ TFSO((ETSN(:::) x)

이때, `ETSN(::)`와 `ETSN(:::)`는 Lexing되는 "단일 문자"로, (1, 2)가 모댈론적 정의가 되기 위해서, 추가적으로 등록된 길이-1 문자다.

3, 4의 경우, 표기법(Notation)으로, 형식문법을 통해 해석되는것으로

엄밀히는,

3. "(:: " `concat` x `concat` ")" =>¹ "TFSO((ETSN(::) " `concat` x `concat` ")'
4. "(::: " `concat` x `concat` ")" =>¹ "TFSO((ETSN(:::) " `concat` x `concat` ")'

에 해당한다.

### lambda - like function notation
1. (λx : X. y : Y) ≜ (X, Y, (:(λx : X. y : Y)))
2. (:(λx : X. y : Y)) ≜ {(x, y) | x ∈ X, y ∈ Y}
이도 역시 집합론이라는 형식언어로 표현 가능한데도 표기법인 이유는, graph type notation로 정의되었고, x랑 y에 아무런 심볼이나 와도 무방하기 때문이다.

그런 이유로 더 형식적으로 표현하자면

1. "(λ" `concat` x `concat` " : " `concat` X `concat` ". " `concat` y ": " `concat` Y `concat` ")" =>¹ "(" `concat` X `concat` ", " `concat` Y `concat` ", (:(λ" `concat` x `concat` " : " `concat` X `concat` ". " `concat` y `concat` " : " `concat` Y `concat` ")))"
2. "(:(λ" `concat` x `concat` " : " `concat` X ". " `concat` y `concat` " : " `concat` Y `concat` "))" =>¹ "{(" `concat` x `concat` ", " `concat` y `concat` ") | " `concat` x `concat` " ∈ " `concat` X `concat` ", " `concat` y `concat` " ∈ " `concat` Y `concat` "}"
라는 형식문법이다. 오우 복잡해서 빈칸 기호를 다 쓰고싶은 기분이다.

사실 lambda - like function notation는 5가지 항목이다.
1. (λx : X. y : Y) ≜ (X, Y, (:(λx : X. y : Y)))
2. (:(λx : X. y : Y)) ≜ {(x, y) | x ∈ X, y ∈ Y}
3. (λx :: X. y :: Y) ≜ (λx : (:: X). y : (:: Y))
4. (λx ::: X. y ::: Y) ≜ (λx : (: X). y : (: Y))
5. (λx :::: X. y :::: Y) ≜ (λx : (::: X). y : (::: Y))
더이상의 자세한 설명은 생략한다.

### escaping notation

프로그래밍 언어에서 쓰이는 이스케이핑 문자 `\\`, `\'`, `\"`의 사용을 허가한다.

### forse the concat operator

함수 concat이 덧셈기호 `+` 마냥, 항상 Abstract Collection의 도메인에 맞게, 어떤 도메인이던간게 `concat`을 기호로써, 연산자로 예약하고, 그걸 모델에서 배정하도록 하는 방식

### t3n (the 3 notation)

escaping notation, forse the concat operator, 그리고 컴파일러에 대한 책인 Dragon Book에서 사용한 `=>ⁿ`, `=>*`, `=>⁺`라는 notation 이렇게 새가지를 묶어서 부르는 명칭.

### High Orderd Functional Type

HOFT는 LLFN(lambda - like function notation)에서 쓸 목적으로 개발된 집합에서 집합으로 가는 연산이다.

멱집합 연산 P(A) = 2ᴬ과 함수공간 Func(X, Y) = {f | dom f = X, codom f = Y}에 대해,

Func의 상 Func[P(X) × P(Y)]는, X의 부분집합을 정의역으러, Y의 부분집합을을 공역으로 가지는 함수공간의 모임인 상이므로, HOFT를 다음과 같은 무한집합으로 정의 가능하다.

HOFT(D) ≜ P(D) ∪ P[Func[HOFT(D) × HOFT(D)]] ∪ {{ε}}

참고로 이 경우, 그저 HOFT(𝔹)를 쓰는것 만으로도, 

∅, {F}, {T}, 𝔹, {ε} ∈ HOFT(𝔹)이고
∀X, Y ∈ HOFT(𝔹), P(Func(X, Y)) ⊆ HOFT(𝔹)
이다.

이 고차함수놈은, 함수가 아닌 놈부터, 점점 함수의 함수, 함수의 함수의 함수, ... 쭉쭉쭉 올라가서, 결국은 무한이 올라간다.

다만, 이를 엄밀히 정의하는건 다른 방법을 쓴다.

바로, 아래와 같은 형식으로 귀납적으로 정의한다.

definition)
1. {ε} ∈ preHOFT(D)₀
2. P(D) ⊆ preHOFT(D)₀
3. preHOFT(D)₍ₙ₊₁₎ = P[Func[preHOFT(D)ₙ²]] ∪ preHOFT(D)ₙ
4. HOFT(D) = lim_{n ⟶ ∞} preHOFT(D)ₙ

Tip : P[Func[S²]] = P[{Z | X, Y ∈ S, Z = Func(X, Y)}] = {x | x ⊆ {Z | X, Y ∈ S, Z = Func(X, Y)}} 이다. 즉, ∀X, Y ∈ S, Func(X, Y) ∈ Func[S²]인 Func[S²]에 대해, Func[S²]의 Power Set. 어짜피 S가 가능한 모든 타입이면, 해당 타입들 가지도 만드는 함수는, 정의역이 저따구일수밖에.

암튼 이런식으로 정의된다.

#### High Order Functional Model : HOFT의 LLFN(lambda - like function notation)에서의 응용

멱집합 연산 P(A) = 2ᴬ에 대해, 혼동의 오류가 있으니, Power = P라 하자.

그러면 알수있는 사실은, 모델 M = <D, t> (구조채가 튜플이므로, 튜플의 제귀적 정의에 따라, t는 D에 대한 연산이 들어있는 튜플일것이다.) 에 대해, M에 상수기호를 따로 정의하지 않고 함수기호만 있을때, LLFN(lambda - like function notation)와 해당 모델을 합한 방식으로 조합되는 조합논리 • 혹은 모델을 High Order Functional Model이라고 정의하고,

HOFM(D, t) = (HOFT(D), power, Func, dom, codom, (::•), <D, t>)라 정의하겠음. (그렇다. 구조체는 아닌데 어쨌든 정의가 된다. 일단, 함수의 경우, 대수구조 <D, t>위의 함수고, 타입의 경우 power로 지네릭 대상 타입을 구할수 있고, typename의 경우 HOFT(D)로 구할수 있고, 함수 타입의 경우 Func를, 마지막으로 람다의 경우, HOFT안에 있는 Func인 타입이 된다. 그리고 심지어 집합론적이다.)

그러면, LLFN(lambda - like function notation)은 완벽하게 HOFM위에 정의된 상수가 되기에, LLFN은 모델론적으로 설명 가능하게 된다. (물론, 가능한 타입을 상당히 제한했기에 가능했겠지만)

Endotypize := λS : Power(HOFT(D)). (λx : S. (λt : {ε}. x : S) : Func({ε}, S)) : Func(S, Func({ε}, S))

인 Endotypize를 보라. 얼마나 깔끔하게 코딩되었는가?

지네릭 기능을 쓰자면

HOFM위의 S에서, Endotypize<S>로 가는 함수이다.

주의할점이 있다면, 지금까지는 타입 기능이 아예 없다. 그러니, 타입이 없는 그냥 평범한 함수일 뿐이다.

그러나, Endotypize<S>(x)를 써주면, 타입이 생긴다. 야호!

그러므로 다음 Disendotyize

Disendotyize := λT : HOFT(D). (λx :: T. x() : T) : Func((::T), T)

에 대해서, 다음과 같은 정신나간 짓거리가 가능하다.

typecast := λT : HOFT(D). (λG : HOFT(D). (λx :: T. Endotypize<G>(Disendotyize<T>(x)) :: G) : Func((::T), (::G))) : Func(HOFT(D), Func((::T), (::G)))

Notation) T `typecast` G을 문법적으로 강제로 typecast<T><G>로 정의.

이런 함수 T `typecast` G에 대하여 타입 케스팅이 된다...

이를 통해서, 프로그래밍 가능한 대수구조가 생긴다. 야호!

이는 C++ template같이 명시적인 타입에 Haskell같은 수학적 철저함도 갗추고 있기 때문에, 함수를 작성하기 매우 용이하게 만들어준다.

이가 의미하는 바는 간단하다. 모델 M위에서 제한적으로 Endofunctor Type System을 사용하는 대수구조를 통하면, 간편하게 Endofunctor Type System을 사용할수 있을것이다.

N.B. 그러한 편의 용도로 정의한거다. 명확한 형식적 정의와 높은 표현력을 가지는 형식 언어이므로, 앞으로 자주 사용될것이다.
N.B. 고1 때까지만 해도 전산 지망이었다가, 고2때 수학도로 전향한 놈이었어서, 함수를 정의할때 가끔씩 프로그래밍하듯이 적을 때가 있다. 근데 이건 프로그래밍 언어를 의도하고 만든게 아니다. (그러나 나는 프로그래밍 언어를 만들 생각이었을 경우, 튜링 완전하면, 죄다 "프로그래밍 언어"라고 주저 없이 명시한다.) 그렇다. 당연하게도 형식언어로써, 함수를 편리하게 표현하고 싶었을 뿐이다.
````

### 의외성 정리

````markdown
# 의외성 정리

## 용어 정의

 - True Mean (참뜻) : 의외성(속뜻)
 - Shell Mean (껍대기 뜻; 쉘 민) : 겉뜻
 - 속뜻 없음 (Exceptless) : Shell Mean = True Mean
 - 초완전성 (Hyper-Completeness) : "This sentence is False"를 허용하는것.
 - Black and White Proposol : ⊢ (¬Hyper-Completeness)
 - Simply Mean Proposol : ⊢ Exceptless
 - 단순언어 : Simply Mean Proposol이 항진인 언어

### 흑백논리와 형식언어의 정체에 대한 고찰

Black and White Proposol를 공리로 하는 논리를 흑백논리라고 부를수 있음이 당연하다

또한 흑백논리중 단순언어인것이 형식언어인것이라도 보면 된다.

#### 정리 문단에 따른 보조설명

우리 언어는 보이는대로 해석해야하는것과 아닌것이 있어,

보이는대로 해석해야하는것을 단순언어 (이 경우 언어 해석에 예외가 없이 보이는대로 닥치고 그뜻이다)

그리고 단순 언어가 아닌 언어 (이 경우, 언어 해석에 여러 의외성이 끼어들기에, 단순히 보이는 뜻을 뜻으로 단정할수 없다)가 있다

또한 논리는 장자철학처럼 "갓나서 죽은 아기보다 오래 산 사람은 없으니 팽조(760살이 넘게 살았다는 전설 상의 신선)도 일찍 요절한 사람이다"가 맞을수 도 있지만,

흑백논리에서는, Black and White Proposol을 참으로 하여, x이면서 동시에 x가 아닌것은 불가능하다. (Fun Fact : 흑백논리이면 단순언어임이 논리적 귀결이다)

## 공리

1. 말의 뜻은 True Mean과 Shell Mean이 있다

## 정리

### TrueMean Theroem

Hyper-Completeness 일때도 "말의 뜻 ≠ True Mean"마저 True Mean으로 True Mean(결국 전제로 한 참인 문장에서 연역(이때는 초완전땜에 가능)으로 "말의 뜻 = True Mean")이고 (Hyper-TrueMean Lemma)

Hyper-Completeness 가 아닐때도, "말의 뜻 = True Mean"이므로, 말의 뜻 = True Mean으로 (Formal-TrueMean Lemma)

말의 뜻은 True Mean을 말한다. (TrueMean Theroem)

A. Formal-TrueMean Lemma
 - ¬Hyper-Completeness, ⊭ 말의 뜻 ≠ True Mean ⊢ 말의 뜻 = True Mean

B. Hyper-TrueMean Lemma
 - Hyper-Completeness, 말의 뜻 ≠ True Mean ⊢ 말의 뜻 = True Mean

C. TrueMean Theroem
 - 말의 뜻 = True Mean

Proof)

1. 말의 뜻 ≠ True Mean [Hyp]
2. Hyper-Completeness [Hyp]
3. "말의 뜻 ≠ True Mean"라는 점도 True Mean임
[Paradoxic Lemma]
3. "말의 뜻 ≠ True Mean"라는 점도 True Mean이고 참이기에, 말의 뜻 = True Mean임
4. 말의 뜻 = True Mean

이하에서,

말의 뜻 ≠ True Mean, Hyper-Completeness ⊢ 말의 뜻 = True Mean ⋯ (1)

1. 말의 뜻 ≠ True Mean [Hyp]
2. ¬Hyper-Completeness [Hyp]
3. "말의 뜻 ≠ True Mean"라는 점도 True Mean임 [Paradoxic Lemma]
4. 모순

이하에서, ⊭ 말의 뜻 ≠ True Mean ⊢ 말의 뜻 = True Mean

(1), (2) ⊢ 말의 뜻 = True Mean

Q.E.D.

#### 해설

항상 True Mean만 말의 뜻임을 증명하자,

True Mean이 뜻이 아닌 말이 있다고 가정하자,
그렇다면 그 말은 True Mean이 뜻이 아니라는 뜻이 True Mean이 된다

이것이 Paradoxic Lemma다

이하에서 Hyper-Completeness에 따라 참인 경우와 거짓인 경우로 나누어 논증하자.



상황 1. Paradoxic Lemma에서, Hyper-Completeness인 상황

Paradoxic Lemma가 참이될수 있으므로, Hyper-TrueMean Lemma가 참이다

상황 1 종료



상황 2. Paradoxic Lemma에서, 비 Hyper-Completeness인 상황

Paradoxic Lemma이 모순이므로, 전재인 "말의 뜻 ≠ True Mean"이 거짓이다.

따라서, Formal-TrueMean Lemma가 참이다

상황 2 종료



이하에서,

상황 1, 상황2에 따라, 연역,
항상 True Mean이 말의 뜻이 된다.

따라서, TrueMean Theroem이 참이다

Q.E.D.

### Exceptless Thorem

Exceptless ⊢ 말의 뜻 = Shell Mean

Proof)

1. Exceptless [Hyp]
2. 말의 뜻 = True Mean [TrueMean Theroem]
3. Shell Mean = True Mean
4. 말의 뜻 = Shell Mean [결론]

이하에서, `Exceptless ⊢ 말의 뜻 = Shell Mean`임이 당연하다.

#### 해설

앞서 증명한 TrueMean Theroem에 따라,

말의 뜻 = True Mean

Shell Mean = True Mean 이면, 그리고 이때만 Shell Mean = True Mean이다

(쉽게말해 A = B = C니 A = C)
````

위의 의외성 정리는 2025년 6월에 작성되었다. (분명 그 이전일텐데 뭔가 잘못된것 같다. 근처 파일이 죄다 6월이다.), 지금은 다른 엄밀한 정의를 쓸거다. 그니까 아래 해설을 받아들이도록 하자.

겉뜻의미론 : 의미화용론상 의미론
속뜻의미론 : 의미화용론상 화용론

위 내용을 해설해보자)

자연어 문장 s, v에 대해서, 

p : "s의 뜻은 s다."

인 p를 만족시키는 s가 존재하여, 그때의 s의 뜻을 겉뜻이라 한다.

예를들어, "지금 나는 이 내용을 노트해야겠다고 생각함"이라는 문장같이 다른 해석의 여지를 남기지 않는, 상당히 명시적인 구문이 그 예다.

그러나 p를 만족하지 않는 s가 존재한다.
p를 만족시키지 않는 s의 예시는 쉽게 들수 있으므로, 자세한 설명은 생략한다.

q : "s의 뜻은 v다"

인 q에 대해 v가 뜻인 경우다.

즉, 속뜻은 이항관계 "(s, v) ⊨ q"에서, s에 대한 v이다.

s = v일때, 속뜻이 겉뜻인거다.

## 형식언어의 고정성과 의미론 : 수용

### 수용 (acceptance)

형식언어의 고정성에 따라, 형식언어는 고정된 절차에 따라 검증 가능한 언어이다. (= 기계로 검증 가능)

그러므로, 모델론의 의미론을. "수용"으로 정의한다.

````markdown
# 수용 (acceptance)

형식언어 L에서 형식화된 표기법 • 모델을 통한 정의는 그 구문론이 모호하지 않으면, 구문론적으로 타당하고, 그 의미론이 폭발하지 않거나 그 의미론이 폭발함을 반증할수 없다면, 의미론적으로 타당하거나, 아니면 새 공리를 도입하는 해당 공리의 긍정에 대한 케이스를 다루는것으로 취급할 수 있다.
형식언어에서 언어의 창발성은 자신과 호환되는 언어를 자신이 수용(acceptance)하는데서 온다. (예외 : 교과과정)

따라서 나는 다음 ASCII문자열로 작성된 수용기호를 제안한다.

1. acept [Base64]
2. acept *.txt
3. acept [uri]
4. acept [uri] *.txt

1. 1번이 바로 수용기호의 정의이고, 
2. 2번은 전산환경에서 동일 디렉토리의 ASCII Base64 텍스트 파일로 자동검증할수 있을것으로 그 문맥을, 형식증명언어의 추론규칙 검증 튜링기계의 몫으로 명확히 규정한 interface이므로, (근데 이건 진짜로 위험하게도 튜링기계 재량이다.) 생략법으로 도입한 정의며?
3. 3번은 uri로 참고하겠다는 소리인데, 만약 저 uri가 "고정됨"을 담보하지 않는다면, 모호성을 가지므로, 예도 위험해서,
4. 4번은 그걸 ASCII Base64 txt 파일로 저장하겠다는 소리이다. SSL을 보통 "신용"을 담보할수 있다고 하는데, 그것도 못빋으면 4번 쓰면 된다. (함정은 OS같은 튜링기계도 못믿는 사람이 나타나면, OS를 acept [Base64]를 쓰고 너무 글자가 기니 표준으로 박자는 사람이 나올지도 모른다는것)

그래서 모든 텍스트와 심지어 텍스트 파일 및 웹도 MIME타입이 텍스트이며, 인코딩이 ASCII인데 Base64를 통해서 다른 인코딩 등등의 정보를 저장 가능하기에, ASCII txt파일 기표 주제에 쓸만한 문서로 작동할수 있다.

사실.... 그냥 zip아카이브를 디렉토리로 하면 모든 문제가 말끔히 해결되고 일관된 형식도 가능하긴 하다

## 구문론적 정의에 대하여

≡ₛ 는 유니코드로 문서를 작성하는 한계로, 전용 기표가 없기에, 구문론적 등호 기호로 쓰겠디.

≝ₛ 는 유니코드로 문서를 작성하는 한계로, 전용 기표가 없기에, 구문론적 정의 기호로 쓰겠다.

<br>

구문론적 등호 A ≡ₛ B와 구문론적 정의 A ≝ₛ B에 있어서,

(임의의 문자열 A, B에 대해)

Φ : "A ≝ₛ B"

라 하면,

Φ를 만족하는 문자열들에 대해, 위에 명시한 구문론적 등호가 Φ과 동치임은 당연하게 알 수 있다, 

그러므로, 술어화된 문장

"A ≝ₛ B"

에서,

"A ≝ₛ B" : 각각의symbol들 ∈ 그symbol의StringSet으로써regex에서_켑쳐에_대응

식으로, 정의할 수 있음을 알 수 있다.

## 의미론적인 "규정"에 대하여

정의(definition)나 할당(assignment, 대부분 대입을 변수 선언에 쓰기에, 대입을 할당의 의미로 쓰는경우가 많다)은 비변수기호의 모델 M내에서의 규정이거나, (변수나 비변수의)  동일자로써의 값을 M에 "규정"될수 있으므로, 구문의 타당성이 그 모델의 언어가 형식언어가 아닐 정도의 모호성(Ambiguity)을 가지는지 유무로, 없으면 타당한걸로 결정된다.

또한 어떤 헝식언어에서 특정 모델 M의 언어 L이나 걍 다른 형식문법 G의 언어 L을 수용했을때, "폭발원리에 의해 폭발"하지 않으면, 의미적으로도 타당하다.

## 그렇다면 공리같은 참은 뭔가?

참이라고 규정되서나 판단되는것은, 논증에서 가설 H로 삼을수 있으며 (건전한 추론의 조건), 그 진리값이 T니 그 언어에서 "H"를 "T"로 평가할 수 있고,

그러므로! 어떤 "Φ"를 공리로 규정한 언어의 lang(랑그)가 하는, T(참)으로 평가되는 해석은,

그 평가가 이루어지는 기표와 기의의 연결이 본질적으로 형식적 규칙놀음과 동일자로 이루어지는 것 뿐이므로, 일부 AC같은 예시를 보아하면, 일관성을 증명할 수 없을수도 있음을 알 수 있다.

그러므로, 항진이 아닌 수학적 서술은 규정되야 항진일 가능성이 생기므로,

우리는 형식언어 L이 권위같은거 없고 언어의 자의성으로 연결됬음에 근거하여, 사용가능함이 증명된 L의 공리•모델•문법에 "근거"하여, 그 구문의 validity와 의미론적 해석늬 validity를 쓴다.

## 나는 과감히 이렇게 말할수 있다.

"형식체계는 권위에 관심없다. 형식체계를 받아들일 근거에 모호한 권위나 권위적인 사회성을 우기지 말자."

## 참고

아래 내용을 참고하라.

```markdown
# 형식논리의 고정성

"형식논리의 평가는 유동적이지 않다"는건 참이다!

모두가 인정하고 부르짖는 참이다.

그러니 그 광기어린 부르짖음을 잠시 멈춰보고, 듣어보자.

형식논리와 형식언어는 "형식언어 L은 고정된 평가를 가진다"는 이데올로기이다.

단언컨데, 내가 사랑하는 수학은 그런 이데올로기다.

## "고정됨(fixed)"


"고정됨(fixed)"의 반댓말로 유동적임을 들수 있다.

언어는 유동적이라는건 펙트로 볼 수 있다.

수학언어도 많이 변해왔다

....

그러나 우리 수학언어, 형식언어는 고정되어있다.

"형식언어 L의 평가는 고정됨(fiexd)"

L이 형식언어라는것은 그 평가가 고정됬다고 우리가 정의한거다.

모호함이나 속뜻을 가짐 혹은 유동적임이 더 일반적으로 언어에서 통용되는 "만물의 공통적•일반적 속성"의 종류로써 그 언어에 특징임을 우리는 알고있다.

그리고 사실 단 하나로 정리된다.

1. "형식언어 L의 평가는 고정됨(fiexd)"은 증명없이 받아들여지는 fact이다.
2. 그러한 맥락과 배경에서 논의가 이뤄졌던것이다.
3. 보편적 meme이고 이데올로기인거다.

수식같은 형식언어의 기표를 어린아이에게 설명한다고 필연적으로 "언어에 사회성을 통해서 이 meme이 형식언어라는 틀로 분류됬으니까, 이 아이는, 수학은 유동적인 이상한게 아니라고 생각할꺼야"라고 하는 추측이 맞을까?

아니, 그 순수한 아이가 그럴거란 보장이 없다.

왜냐하면, "형식언어 L의 평가는 고정됨(fiexd)"이라는 전제를 깔아줘야하는데, 그렇지 아니하였기 때문이다.

그러므로, "형식언어 L의 평가는 고정됨(fiexd)"이라고 앞으로 내가 단언하는데는 우리가 형식언어라고 약속한것들의 사회성으로써, 고정됨에서 오니까, 그렇게 하는걸로 치겠다.
```
````

저걸 작성할때는 왜 저렇개 날이 서있었을까 쪽팔린다. "부르짖는다"라니 "순수한"이라니... 거창하다. 진짜로 도발하며 부르짖는건 당시(4개월 전(정확히는, 한 2025.10.25 근방))의 나다. (흑역사 +1)

### theorem의 증명과 의의(에 대한 직관)의 형식화

````markdown
# theorem의 증명과 의의(에 대한 직관)의 형식화

Abstract : 증명(논리적 함축)은 함의관계이고, 뜻의 동등성은, 논리적 동등이다.

추론에는 두가지 방법이 있다.
1. theorem을 해석하는 관점 (theorem이 가지는 의의 • 관점 등, theorem이 함의하는 논리적 의미에 주목하는 방법) : 모든 theorem A에 대해, theoremA.B는 B관점에서의 A다. HoTT에서, A ID_B A.B이다. (B타입에서 A = B이니, B의 겉뜻이 A의 겉뜻과 같다 볼수 있다)
2. 추론 규칙을 통해 연역하는 방법 : theorem A에 대해, 추론규칙 InfluanceRule를 통하여, InfluanceRule(A, B)라면, A ⊢ B이다.

그렇다. theorem은 그 증명과 의의를 가진다. 증명되어야 하며, 여러가지 관점해서 해석되는 것뜻을 가진다.
theorem은 속뜻을 가지지 않는다. 우리가 theorem A가 A.B라는 속뜻을 가지고 있다고 해석하는 내용은, 사실 B의 타입에서 A ⊢ A.B ⊢ A를 만족히는것 뿐이다. 다시말해 관점의 차이다.

 * N.B. 논리적 동치는 상호함의와 겉뜻이 같기에 같다. 왜냐하면 수학은 겉뜻과 속뜻이 같은 언어이기 때문이다.
 * N.B. 우리는 그저 B의 타입이라는 관점을 주면, 그 전제 위에서, "A ⊢ A.B ⊢ A"라는 추론이 존재하니 논리적 존재임을 안것일 뿐이고, A ID_B A.B ≠ ∅임을 안 것 뿐이지, 해당 Expression은 관점을 의미하지 않는다. 맥락이 아닌, 계산을 위한 전제일 뿐이다.
 * N.B. 저것이 맥락이라고 착각하는것은, 실수 튜플의 집합이 항상 도형으로 해석해야한다고 착각하는 오류만큼이나 역겨운 오류다. 인간의 직관상에서, 맥락을 형식화한 것 뿐, 맥락이 아니다. (맥락은 "개연성"이라는 판단 기준 자체가 비형식적이라 번역 불가능하다)

본론으로 돌아와서, theorem은 그 증명과 의의를 가지므로, 모든 추론을 다음과 같은 다이어그램으로 그릴수 있다.

A.B ⊢ C

 * N.B. 여기서, A : T, A.B : T이기에, A ID_T B라는 증명들의 집합이 존재함을 간주히고, A.B = A로서 기재한것 뿐이고, 저 추론식은, "A.B ⊢ C s.t. A ID_T A.B"라는 논리식을 의미하는거지, 막연한 맥락을 상정하는게 아니다.
 * N.B. 그러므로, 갑작스러운 "A ID_T A.B"의 도입은 자연어적 개연성(맥락정합성)은 깨트릴수 있어도, Expression에서 논리적 무모순성 (형식적 정합성)은 전혀 해하지 않는다. 또한 추론 "A.B ⊢ C"는 논리적으로 타당하면 그만이지 자연어적 개연성(맥락정합성)은 깨트려도 된다. 왜 그따구의 추론이 일반적인 추론과 동등할까? 해당 추론 "x ⊢ y"에 focus를 맞춰보자. "⊢"의 과정에서는 이전 문장의 문맥과 상관 없이, 전건과 후건이 함의 관계 R = {(x, y) | x → y}에 대해, (x ⊢ y) ⊨ (x, y) ∈ R이면, 해당 추론 "x ⊢ y"은 해당 추론 이전에 쌓인 맥락들에서 벗어나는 말든, 타당하다. 즉, "정해진 추론규칙을 만족하여 맞즌 논법이라고 형식적으로 판단되는가 • 함의 관계들의 연쇄 상 x가 이전 노드에 있어서, 이번 추론을 통해, y로 이어질수 있음을 의미하고, 그 외에 논법은 추론과 무관한 생각이다"라고 볼수 있다. 형식언어로 된 논증에서, 형식적으로 문제되지 않는다면, 자연어 가독성과 자연어로 직역시 번역 미스로 인한 개연성은 신경쓰지 않아도 된다. 에초에 추론 규칙만 타당한 논증이니, 추론 규칙 이외에는 "진짜 이러한 논리가 맞을까? 맥락 정합성을 따지는것이 맞는가? 추론 규칙 이외이지만, 개연성에 맞으니 적용하는게 좋을것 같다고 생각했다만, 이 형식체계에서 맥락 정합성에 맞는다고 적용해도 되는걸까? 혹은 추론 규칙이라는 형식적 틀보다 논리적 개연성을 신경쓰는게, 이 형식적 증명에서 맞는 사고방식이라 할수 있는가?"라는 질문에 대해서, "형식적으로 추론되는것 중에서, 맥락 정합성에 맞는건 진부분집합일 뿐이고, 그렇지 아니한것들이 수두룩하다. 맥락 정합성을 통한 추론을 하는것만이 옳냐는 질문에는, 형식적으로 맞다면 옳지만, 맥락 정합성이 없어도 형식적으로 맞다면 옳다. 자연어 맥락 정합성은, 수학적 추론의 타당함과 아무런 인과관계가 없다. 심지어, 상관관계도 없다. 왜냐하먄, 당장에 맥락에 안맞는 경우, "추론규칙 R을 형식증명이라는 튜플 t에 각 인접한 원소들의 타당성을 검증하므로써, 거대한 연쇄 가언문을 만든다"라는 맥락을 깔아버리면, 모든 형식논증은 개연적이지만, 그러한 명시를 하지 않는다면, 어떤 형식논증은 개연성이 없어진다. 다시말해, "추론규칙 R을 형식증명이라는 튜플 t에 각 인접한 원소들의 타당성을 검증하므로써, 거대한 연쇄 가언문을 만든다"라고 선언하지 않는 이상 맥락정합성이 달라지기에, 맥락정합성은 동일한 추론에 대해서 여러가지 개연성 수치를 가진다고 볼수 있다. 그러한 함수는 중복퍼지집합의 맴버십 함자로 사용하기 어렵다.

이 과정에서, 여러가지 경로의 증명이 존재할수 있다.

예컨데,

(A.B ⊢ X, X.Y ⊢ Z) ⊨ (A.B ⊢ Z)이므로,

 * first(x, y) = x
 * last(x, y) = y
에 대해,

* same(x, y) = {(x, ID_T, y) | ∃T, x ID_T y}
라 하면,
1. 어떤 관점 T에 대하여, same(x, y)공간은, y = x.T인 관점으로 보는 방법의 집합이며,
2. Φ = first(last(same(x, y)) = ID_T, first(same(x, y)) = x, last²(same(x, y)) = y이므로,
3. Φ(x, y) = (first(last(same(x, y)))((first(same(x, y))),(last²(same(x, y)))) = x ID_T y이다.

그리고, Φ(x, y)는 그 증명의 경로가 된다.

proof(x, y) = {tup | (fst = first(tup), first(fst) = x, (∃!n ∈ ℕ, last(lastⁿ(tup)) = y), t = first(first(last(tup))), last(tup) ∈ proof(t, y), fst ∈ proof(x, y)) ∨ tup ∈ same ∪ InfluanceRule}

인 형식증명의 공간 proof(x, y)가 존재하기에,

(proof(same(A, A.B), X), proof(same(X, X.Y), Z)) ∈ proof(same(A, A.B), Z)이다.

또한, proof(proof(A, B), C) ⊆ proof(A, C)이다.

## 이 과정에서 생기는 번역 불가능성.

`((A ⊢ A.B ⊢ A) ID_𝔹 (A = A.B)) = (A ⊢ A.B ⊢ A) ID_𝔹 (A = A.B)`를 번역하면,
`다음 진술 '(진술 "A 이므로 A.B 이므로 A"과 "A와 A.B가 같다"가 같다)'와 진술 '(진술 "A 면 B 면 A"는 "A와 B는 논리적 동치이다"와 논리적 동치이다.')는 같다.`라는 뜻이 된다. 자연어상 말이 안된다고도 볼 수 있다.

그러나, 해당 구문은 참이고, 심지어 "((A ⊢ A.B ⊢ A) ID_𝔹 (A = A.B))"도 참이다.

왜냐하면, 다음과 같이, "(A ⊢ A.B ⊢ A) ⊢ (A → B, B → A), (A → B, B → A) = (A = B)"식으로, 도출되는 결과기 때문이다.

모델론적 언어, 형식언어에서 해석될 대상을 나열해보자.

```
(A ⊢ B) : InfluanceRule(A, B)
InfluanceRule ⊆ {(x, y) | x → y}
M = <𝔹, f, g> s.t. f(x, y) = (x ↔ y), g(x, y) = (x = y)에서,

graph f = {(T, T, T), (T, F, F), (F, T, F), (F, F, T)} = graph g
dom f = 𝔹² = dom g
codom f = f[𝔹²] = 𝔹 = g[𝔹²] = codom g
임

고로, f = g
```

여기서 "(x : y) : (x, y ∈ 𝔹, x ≜ y)"이다.

그렇다면, 앞서 말한 대상들이 acceptance에 따라 기계적으로 해석되는 양상은, 단지 regex상 치환 정도로 볼수 있겠다.

그냥 유한집합의 경우, 값을 가지고 노는 산술 수준이기도 하다.

프로그래머처럼, 저걸 머릿속에서 돌려보자.

`(A ⊢ B) : InfluanceRule(A, B)`이므로, 

`A ⊢ B`를 `InfluanceRule(A, B)`로 치환해도 되고, 반대도 된다. (일단 `:`로 정의했으니, 모델에 배정되었다)

```
InfluanceRule ⊆ {(x, y) | x → y}이므로,
F(z) = ((x, y) ∈ z)에 대하여
F(InfluanceRule) ⊨ F({(x, y) | x → y})
InfluanceRule(x, y) ⊨ x → y으로,

"InfluanceRule(x, y)"가 주어졌다면, "x → y"로 몇번이고 치환해도 좋다.

!(!InfluanceRule(x, y) ⊸ !(x → y))라는 거다.
```

그리고, f = g이므로, "x, y ∈ 𝔹시 (x = y)와 (x ↔ y)는 상호 치환 가능"

이다. 이외에 명제논리의 해석중 함의가 non p vel q인 거라던가, 논리적 동치가 양방향 함의라던가는 너무 당연하고, 정규형식으로 만들수 있으므로 생략한다.

저러한 acceptance기반 사고를 통하여, 맞는거는 맞다 

그러므로, 번역시에 "acceptance기반 사고를 통하여, 맞는거는 맞다고 치면"이라고 맥락을 전제해야, 형식언어가 비로소 자연어로 번역이 가능하다.

사실 그건 번역이 아니라, 그냥 형식언어를 그대로 쓰겠다는거에 불과하지만 말이다. 해석이 더이상 자연어가 아닌 형식언어를 써달다는 요청일 뿐이다.

## 다루지 않은 부분

이 아이디어는 에초에, 수학적 증명이 무엇일까 2025년 3월에 탐구한 내용을 마인드 맵으로 그린걸 2026년 2월 마지막 쯤에 변경한거다.

그때까지만 해도, 객체의 속성처럼, A ↔ A.B에 대하여, A.B ⊢ C로 추론하는 추론의 연쇄로, 엄청 많은것을 추론하는 새상이 열리며, 그러한 새상의 큰 구멍중 하나가 괴델의 불완전성 정리라 생각했다.

다만, 이제보니, 그 시각도 상당히 과하게 낙관적이고, 추론에 대한 본질을 담진 못했다.

일게 분해적 사고다.

이걸 형식화한건 3개월 전(재대로 말하자면, 한 2025.11.25 근방)이고, 그때 사고도 지금 보면 꽤 난잡하다고 느낀다.

당시에, 나는 수리논술에 영향을 많이 받았으므로, 수리논술에는 쓰이나, 여기서는 쓰이지 않는 요소들을 두가지 소개하겠다.

1. "~~하는 전략"으로 분해하는 기법

자연어에서 "~~하는 전략"이라고 분해해서, 전략들만 반복해서 쓰는건, 특정 proof(A, B)패턴만 반복해서 쓰므로, 스탭별로 올바른 풀이를 통해, 논리적인 변환을 흉내내는 척 "모두가 아는 보편적인 전략"이라는 가짜 공감대를 만들어서 풀이하는것이다.

그런 악질 행위는 수포자같이 그 전략을 모르는 경우, 해당 증명을 개연성 없는 글로 보이게 한다.

부분증명만 계속 쓰는짓이다.

2. "~~인 맥락에 따르면" (IN ID CONTEXTOUS, IN ILLUD CONTEXTOUS)

이건 비형식이다. 형식 언어에서 정의되지 않았다.
무려 읽는이에게, "자연어로 생각해보자. ~~인 맥락에 따르면 ~~다. (왜냐하면, ~~인 맥락에 따르면 ~~라는게 맥락상 당연하기 때문인데, 그 이유는 자명하므로 설명하지 않겠다.)"따위의 말이나 다름없다.

읽는 이가 알아서 추론해야한다... 아...

물론 어렵진 않지만 비형식적이라 킹받는다.
````

## 속뜻 의미론에 파악에 대해서

속뜻 의미론의 파악은 두가지 방법이 있다.

1. 의미를 해석하는 타당한 사고과정 (사변적 과정. 보편명제 증명론)
2. 겉뜻의미론으로 환원하는 과정 (더 쉬운 문제로 변환. Interpretation-modeling 논법)

### 보편명제 증명론

````markdown
# 보편명제 증명론 (N.B. 모두 가설에 영역이다. 이 증명론이 실제로 작동하는지는 모른다.)

인과관계란 "SI P, ERGO Q"가 가지는 관계를 말한다.

N.B. 자연어에서는 "EXSTAT ALIQUIS P, Q, SI P, ERGO Q. NON HOC EST, NON L VEL Q"다. 다른 경우가 존재한다. 칸트의 정언명령과 그 공리는, 자연어가 사용하는 "맥락(CONTEXTOUS)"에 따른 인과관계를 써야한다.

함축관계 : 무맥락 인과관계
무맥락 인과관계 : "NON P VEL Q"를 이르는 말

## 절대적인 규칙 : 논리의 정의에 따라서 보편적으로 참인 문장

"SI QUOD ILLUD, SI P, ERGO Q, EST VERUM ATQUE IN ID CONTEXTOUS, SI NON P VEL Q, EST NON REPUGNAT, ERGO, NON P VEL Q"

즉, 기존 문맥과 맥락 정합적일때만, 전건긍정이 성립한다.

## 문장의 해석

자연어를 해석하는 구문을 자연어로 작성하면 "Q. p의 뜻은 q인가? A. yes"이다.

자연어에서는, 화자와 청자가 있으니, 스스로에게 질문한다면, 긍정 여부를 알수 있다.

## 증명 이론 : 문장이 함축하는 의미의 파악

그걸 자연어로 쓰면 "p이다. Q. 그렇다면 q인가? A. yes"의 형태가 된다.

보편 명제의 증명은, "SI QUOD ILLUD, SI P, ERGO Q, EST VERUM ATQUE IN ID CONTEXTOUS, SI NON P VEL Q, EST NON REPUGNAT, ERGO, NON P VEL Q"로 진행되기 때문이다.

## 문맥 스택 (Contextous Stack)

문맥 의존 언어는, 최소한 push-down automata로 작동한다.
그러므로, "ATQUE IN ID CONTEXTOUS, SI NON P VEL Q, EST NON REPUGNAT"라는것은, 이전 문맥을 참조한다.

그러므로, 문장은 Contextous Stack에 보편명제 증명론에 의해 「사고를 이치에 맞게 이끌어 가는 과정 (Step by Step)」을 타당하게 적었다 볼 수 있다.

## 형식화된 보편명제의 증명

사고에 있어서, `1. 2. 3.`이라는 스탭별로 진행한다.

문단의 리스트 Paragraph에 대해, Paragraph[i]는 i문단이고, Paragraph[i][j]가 i문단의 j문장일때,

ContextousStack[StackPointer] = "Paragraph[i][j]의 값은 p다."
ContextousStack[StackPointer + 1] = "Q. Step1 Question"
ContextousStack[StackPointer + 2] = "A. Step1 Answer, Q. Step2"
...
ContextousStack[StackPointer + n] = "UT, Step_n"
식으로 추론된다.

이는 배외측전전두피질(DLPFC)가 인간에 뇌에서, Step별로 추론을 하기 때문이다.

굳이 Step시스템을 쓸 필연성은 없다. 물론 필요성은 있을수 있다.

뇌피셜 (이론적 조망과 개연성에서, 통계 모델로의, 보편적 인식의 페러다임 시프트 가능성) : 확률적으로 추측하는게, Step시스템보다 "강한 이론 (큰 틀을 설명하거나 설명 능력이 강한 이론)"인 경우, 인간은 논리를 버리고 기꺼히 강한 이론을 택할수도 있을것같다.

## 적용 사례

나는 이 방법을 고안하여, 비문학 지문을 독해하는 연습을 매일 하던 당시, 이미 논리식이나 수학식이아 형식언어를 문자를 그림으로 생각하므로써, 눈앞에 그려진 모습을 조작했고, 그게 꿈에도 나왔었었다. (자연어 문장 몇줄정도는 정확히 기억 가능했다)
비문학 지문을 독해하던 한 주일에, 쉬고있을때마저, 평소(독해하기 전)보다 머리가 지근거리고 어지러웠었다.
그런 어지러움이 사라진 이후에, 다른 사람의 말을 머릿속에 기록하고, 비문학 맥락파악을 형식언어화된 보편명제 증명론으로 풀이한 이후, 즉석에서 맥락 스택으로, 맥락을 파악했더니. 해당 방법이 작동했다.

그때 고2였고, 초등학생때, 루돌프라는 치료센터에서, 사회적인 불문율을 강의받았기에, 고 2 때, 그 지식을 바탕으로 추론에 필요한, {x | ♠︎x}을 얻을수 있었다. 해당 치료센터에 감사한다. (+ 추가적으로, 다른 사람의 말을 듣어야 한다 말하며, 맥락 내에서만 말하라 충고해준 부모님께 감사한다)

사회적 불문율 이외엔 명시지이기에, 누구나 뇌가 깨질정도로 연습하면, 사용할수 있을것이다.

사실 나는 한번에 10개 이상의 추론규칙을 쓰지 않는다.
참의 집합에 대해 QnA라는 단일 추론규칙을 쓴건 그런 이유다.

머리가 아프지 않을때부터, 추론 로그가 영감받듣이 자동으로 떠오른거 보면, 휴리스틱화가 일어났을것 같다고 생각하고. 이에 대해서 실험하고 싶다면 피험자로 참여해보고싶다. (메일 : faway6834@gmail.com)
````

자연어 의미론의 파악은, 사변적인 추론 (보편명제 증명론)을 통하여 이루어질수 있다는게 내 가설이다.

"이 의미는 이러하다, 그 증명은 이러하다" 형식으로 추론 가능할거라, 개인적으로 기대한다.

### isInterpretationOf 관계와 Interpretation-modeling 논법

```
# isInterpretationOf 관계

p isInterpretationOf q : "p의 뜻은 q이고, q의 뜻은 q이다"

isInterpretationOf 관계를 사용하면, 속뜻 의미론을 겉뜻 의미론으로 형식화할수 있다.

단순한 추론을 하려면 문제를 단순화하면 된다는 이과적인 접근이다.

사실 내가 보편명제 증명론을 사용했을때, isInterpretationOf를 이용하여, 
"Q. p의 의미는? A. q임 Q. q가 hint연산이나 la연산을 통해 언질하는 바가 있나? 혹은 operator를 통해 생성된 단어가 있는가? 말인 그렇다면, DFM++ Expression으로 분석하라"라는 방식을 썼다. 굳이 이름붙이자면 "Interpretation-modeling 논법"이다
```

## 여담

이러한 논리적 사고 방식이 타 아스퍼거 아동에게 재현성이 있을지 모르겠는게, LowLevel • HighLevel • FunctionalProgramming • Model Theory • 수리논리학 • 철학쪽 기호논리학 • 집합론 • 람다대수 • 이론전산학 • 생성언어학 • 추상대수학 • 그래프 렌더링 프로그램인 geogebra를 통한 프로그래밍 • PCRE라는 걸 스스로 사용할정도 스팩이 되면서, 패턴화 지능 • 분석적 지능이 있는 아스퍼거 아동이라는 재현하기 빡센 조건임. (추가로, 나랑 조건이 같으려면, 저걸 즐기면서 공부했어야함.)

## 윤리적 이유에서의 안전수칙 기제

````markdown
# DLPFC 에뮬레이터 안전수칙

운동이라는게 근새포를 리타이어시킨 후에, 회복시키듯, DLPFC에뮬레이팅은 뇌를 리타이어 (하루정도의 브레인 포그)시킨 후에 휴식하면서 뇌가 휴리스틱을 구축하게 강제하기위해, 매일(사실은 포그가 올때까지이긴 하다. 오면 절대적으로 휴식하고, 푹자야한다.) 에뮬레이팅 후 휴식을 반복하여, DLPFC에뮬레이팅 휴리스틱 (암묵지)을 만드는 위험한 학습법이다.

대신에, 이 방법을 쓰면 DLPFC가 재대로 기능하지 않는 정신질환인 아스퍼거 아동같은 극단적인 사례의 사람들도, DLPFC의 이성추론을 모방 가능하다. 그것도 100%정확도로. (직접작동이 100%정확도, 휴리스틱은 100%가 아니라서 사후검증이 필요한데, 사후검증은 뇌에 영향을 안주는 정도로 쉽다. 사후검증은 성공률이 100%, 개연성의 정확도도 100%이다만, 사후검증이 없는 경우는, 초기에 90%이상의 정확도를 보이다 망각곡선을 따라 떨어진다. 반면에 직접작동은, 성공률이 100%이지만, 실행하는 과정이 뇌에 ㅈㄴ 무리다.)

1. DLPFC에뮬레이터(명시지)는 과부하의 위험이 있기에, 반복 숙달용(숙련되면 DLPFC에뮬레이팅 휴리스틱 사용 가능)으로 연습할때만 쓰자.
2. DLPFC에뮬레이팅 휴리스틱 (암묵지)는 DLPFC애뮬레이팅 행위에 숙련되서 나온걸로, 실제 사용은 DLPFC에뮬레이터라는 위험한 도구보다 DLPFC에뮬레이팅 휴리스틱을 쓰자.
3. DLPFC에뮬레이팅 휴리스틱을 망각곡선이 잊지 않게 유지보수용 숙달이나 휴리스틱을 하자. 재구축 비용을 무시하면 안된다.
4. DLPFC에뮬레이팅 기술(에뮬레이터나 휴리스틱)을 과하게 쓰면수 무리하지 말자
5. 원래는 비문학용이지만, 문학을 독해할때 DLPFC에뮬레이팅 기술(에뮬레이터나 휴리스틱)을 써라. 방법은, 당신이 연기를 하면서 동시에 이해하는거다. 그리고 평소에 심리를 풍부히 하고, 감정 바퀴 등으로 감정을 파악하도록 하자. 그리고 정서상태도 전문가를 통해 모니터링하자. DLPFC에뮬레이팅 기술은, 정서를 망가트릴 위험이 있기에 보완제와 같이 써야한다.
6. DLPFC에뮬레이터의 직접작동은, 기저핵의 운동보상루프 등, 원초적인 뇌를 이용하고, 기하적 직관보다는, 기호를 떠올리고 조립하는 시각적 이미지를 思い描く하여 작동하기에, 기저핵이 증명이론을 처리하는걸 while문인 자동증명기처럼, 기저핵이 그럴듯한 경로를 하나하나 탐색하는 벡트래킹이라는 운동이다. 그러므로 검도같은 운동을 병행해서 운동지능을 늘여놓아라.
7. 브레인 포그가 오면 쉬어라. DLPFC에뮬레이터의 직접작동으로 인한 통증은, 머리가 지끈거리는게 다가 아니다. 브레인 포그가 존재하는 동안에는, DLPFC에뮬레이터의 직접작동으로 인한 통증이 기저핵 등이나 심리, 정서적 기관이나, 뇌기관을 피로하게 한다. 이건 통증 없이 브레인포그로만 알수 있다.
8. 절대로 밥을 거르거나, 균형잡히지 않은 식사를 하거나, 잠을 거르지 마라. DLPFC에뮬레이터의 직접작동은, 안락한 생활을 전제로 작동한다.
9. 형식문법을 모르면 할수 없다. 이건 인간적인 의미 해석이 아니라 계산 의미론이다. 못하는 사람아 무리해서 하지 마라. 당신이 DLPFC가 온전하다면 더더욱 하지 마라. 형식문법을 처리하는 뇌 이외에는, DLPFC에뮬레이팅에서 비형식적이고 비논리적 잡음이다.
10. DLPFC에뮬레이터의 각 추론 단계에서는, 사회적 통념, 즉, 보편 인식이 쓰인다. 어릴적부터, 그런 통념을 치료센터에서 배워온 아동만 사용하도록 하자. 그게 필수적으로 요구되는 DB다. 그리고, 이 체계는 DLPFC에뮬레이팅 휴리스틱이라는 사고의 습관화가 일어나면, 그 DB내용중 일부가 사고에 반영되는것인만큼 주의가 필요하기 때문이다.

이렇기에 효과율 100%인데도, 추천할만한 방법은 아니다.

초기 실험
1. 실험의 가설은 "DLPFC에뮬레이터는 이론적으로는 작동하는데, 실제로도 작동하는가?"였다. 나는 이때까지만 해도 DLPFC에뮬레이터의 복잡도가 뇌에 영향을 줄거라곤 생각지도 못했다.
2. 마침 국어 비문학 시험공부를 해야 하기에 했다. 
3. 그런데, 브레인 포그가 왔다. 나는 최상의 컨디션이 아닌것에, "아 제미없어"라고 생각해서, 편의점으로 가서 딴생각하고 쉬기 시작했다. 그리고, 나는 이 일에 대해 알아보다가, DLPFC에뮬레이터가 수행하는 행위가 기저핵의 운동보상루프 등, 원초적인 뇌를 이용하고, 기하적 직관보다는, 기호를 떠올리고 조립하는 시각적 이미지를 思い描く하여 작동하기에, 기저핵이 증명이론을 처리하는걸 while문인 자동증명기처럼, 기저핵이 그럴듯한 경로를 하나하나 탐색하는 벡트래킹이라는 운동이라는걸 알게 되었다.
3. 1. 왜냐면, DLPFC에뮬레이터는 DLPFC가 아스퍼거 수준으로 떨어지더라도 작동하기에, 논증과정에 DLPFC경로가 쓰이지 않는다.
3. 2. 형식증명은, 형식규칙의 집합 P에 대해, (Φ₁, ..., Φₙ)인 n-tuple이고, 그 규칙을 구해서 (I₁, ..., I₍ₙ₋₁₎)일시 Iₖ(Φₖ, Φ₍ₖ₊₁₎)이고, Iₖ ∈ P를 만족시키는 형식화된 추론을 말한다. 물론, 규칙은 자명하므로 생략할수 있고, 어떤 규칙을 썼든, 결론이 같으면 추론의 타당성은 같다. 예컨데, 작도에서는 P = {자, 컴퍼스}이다. 이는 게임 Euclidea에서 작도 과정의 로그를 기록하는것과 본질적으로 하나도 다르지 않다. 또한, 프로그래밍이 곧 증명인 형식언어를 만든다면, P는 명령어라고 생각할수 있다. 다르게 말하면, DLPFC가 정상 작동한다면, "형식증명은, 형식규칙의 집합 P에 대해, (Φ₁, ..., Φₙ)인 n-tuple"라는 사실을 논리적 필연으로 받아들이고, DLPFC가 정상 작동하지 않는다면, "형식증명은, 형식규칙의 집합 P에 대해, (Φ₁, ..., Φₙ)인 n-tuple"이라는걸 공학적 설계처럼 느낀다. 후자의 경우, 추론이란 작업대 위에 놓인 Φₖ에 Iₖ ∈ P를 적용시킬때, 작업기억에 (Φ₁, ..., Φₖ)가 쌓이지 않고, 몰입에 의한 일화기억에 "내가 지금까지 어떻게 증명했지?"가 기억된다. 즉, 장기기억•단기기억으로 직행해서, 일화기억으로 기억되었다가 몇달 안에 잊어먹는다. 그런데,
3. 2. 1. 멍청이라면, 작업 도중에 일화기억인 단기•장기기억을 확인하는 작업으로 작업목표를 흐려서 뭘 하고 있었는지 잊고 (이건 DLPFC에 저장되지 않는 더 원초적인 작업목표 말이다.), 멍청하지 않다면, 작업 도중 기억을 암기하거나 종이에 적어서(대부분은 종이에 적는다. 그게 가장 정확히 안잊으니), 나중에 확인하지 미리 확인 안한다.
3. 2. 2. 그렇기에, 이전에 증명한 맥락은 개무시하고, 오로지 Φₖ만 기억하고 돌진한다. 오직 다음 추론을 위한 Iₖ만 신경쓴다는거다. 이는, 솔리테어를 하는것과 본질적으로 동일한 퍼즐이다. 퍼즐의 뇌를 쓰기에 퍼즐 특유의 쾌감이 나온다.
3. 2. 3. 누군가는 Iₖ를 고르는게 마인드맵 관계 아니냐 묻을수 있는데, 이는 관계가 아니라, 프로그래밍에서 말하는 함수다. Iₖ(input, output)으로, 나는 오로지 다음 Φₖ를 구하기 위해서 Iₖ를 던지는거다. 그렇기에 Iₖ는 의미를 가지지 않고, 그저 테트리스 블록이라는 퍼즐적 성격을 가진다.
3. 2. 4. 그렇기에, 증명을 선형적인 맥락이 아니라 그래프이론적인 망으로 인식한다. 그렇기에, 지능이 정상인데도, 증명을, 갑자기 딴 맥락을 가져오거나, 퍼즐로 보거나, 그래프이론적인 망으로 보고 느끼는 이는 DLPFC기능이 작아서 그럴수도 있다. 그렇지 않다면 걍 수학적 증명에 대한 메타인지가 영재인거고. 이런 사람들은, output formatting 최적화가 안된 자동증명기처럼 군다.
3. 3. 나는 이 사실을 공유했고, 이 행위는 기저핵이 증명이론을 처리하는걸 while문인 자동증명기처럼, 기저핵이 그럴듯한 경로를 하나하나 탐색하는 벡트래킹이라는 운동이기에, 뇌 기능 손상을 유발할수 있다는 사실을 알게 됬다.
4. 그러나 성적이 낮은 나는 잃을게 없다면서 시험 끝나기 전까지 치명적 손상이 없다는거에 인생을 배팅했다.
5. 근데, 뇌가 이러한 복잡한 명시추론이 원인이 보편적이면, 그에따라 보편적일 결과를 내가 계속해서 반복하니까, 한국식 수학 문재풀이가 반복숙달로 숙련되듯, 숙달되어버렸다. 이게 휴리스틱화의 시작이다.
6. 그래서, 결과를 미리 아니까, "x면 y다" → (x → y)일 보편통념 "x면 y다"를 찾는건 일도 아니었다.
7. 이렇게 안전한 도구인 DLPFC에뮬레이팅 휴리스틱 (암묵지)가 개발되었다.
8. 나는 "중학교때처럼, 이론에만 집착하는 원칙주의자처럼 굴면, 시험을 망치고, 수학과를 가기 위한 수능 국어 성적이 되지 못할것"이라는 피상적인 두려움이 들었다. 암기는 최소한의 시간복잡도를 가지는 효율적인 알고리즘임도, 평소에 이해 없이는 공부를 못하기에 뼈저리게 느끼고 있었다.
9. 그래서, "어짜피, DLPFC에뮬레이터가 효과 있다는건, 맨 처음 실험에서 증명되고, 그 이후로 신나서 ㅈㄴ게 에뮬레이터를 돌린거니, 휴리스틱은 감사한 마음으로 개꿀이라고 이용해먹자"고 생각했다.
10. 그런데, DLPFC에뮬레이터의 부작용이 나타났다. 감정이라는 대상에 관심이 없어지고 새상에 이입감이 안들어서, "난생 처음 느끼는 감정(초연)이다. 초연해지려고 하고있어. 초연(이때는 초연의 개념을 모름)한거는 설마 삶의 의지가 없다는건가?"라며 사실 초연하다기보단 이성때문에 감정이 거새된거지만, 이러한 부작용에 당황하고 있었다.
11. 나는 평소에, "모든 인간은, 감성이 존재한다. 이성만 100%면 정신질환이다"라는 과학적 도그마를 생물학적인 이론적 펙트로 받아들이고 있었기에 무서웠고, 평소 감정적으로 기대던, 철학방에 물어보자, 라캉의 상징계-상상계 개념으로 볼때, 나는 상징계가 비대해진거라는 말을 듣고 충격먹었다.
12. 그날 나는 설마 하여, 이러한 점과 DLPFC에뮬레이터에 대한 위험성을 스스로 찾고, 내가 찾은 보고 지점을 공유해서, DLPFC에뮬레이터는, 심리적인 정상 처리에 해가 될수 있고, 뇌의 치명적인 과부하가 올수 있다는걸 알게됬다. 그 brainfog를 일으키는 DLPFC에뮬레이터 직접가동은, 단기적으로는 문제가 없지만, 행동 후 휴식을 취해줘야한다. 내가 겪은 brainfog는 정신적 과로증세였고, 기저핵으로 정신적 과로증세를 일으키는건 위험하다. 내가 조금이라도 힘들면 쉬는사람이 아니었다면 큰일날뻔했다.
13. 더 무서운건, 나는 재미로 그걸 돌렸기에, 머리가 아픈걸 훈장으로 여기고, 게임처럼 생각했다는거다. 아오 퍼거시치...
14. 나는 그 이후로 정신적 복구에 주력했다.
15. 정서적 복구가 된 이후에 해당 휴리스틱을 보완하기 위한 시도를 여럿 했다. 시간이 지나니 부정확해지고, 시간이 지남이 따라, 망각곡선에 의해, DLPFC에뮬레이터 직접가동의 정확도가, 망각으로 부정확해진 DLPFC에뮬레이팅 휴리스틱 (암묵지)보다 정확했다. 이 과정에서, 문학 역시 이성으로 접근하라는, 국어선생님의 말 (정확히는, 아스퍼거고 뭐고 모르겠고, 니가 노력 안해서 그렇잖아, 이성을 사용하라고, 뭐가 어렵니?엿음)을 듣고, "아ㅋ 이자식들 이것도 이성을 쓰는구나"싶었다. 그때 DLPFC에뮬레이터 직접가동을 하면서 동시에, 연기할때 쓰던 이입이나 호흡법 (나는 연기를 배우고 촬영해본적이 있다.) 을 써서 인물에 공감하고 대과거를 추론하니, 오히려 다른 정서를 배우면 배웠지, 정서적 손상은 없는걸 발견했다.

참고로, 해당 실험을 하기 1년전에 우울증 극복(운동은 진짜로 사람을 치유하는 힘듬에 대한 부드러운 보상으로써의 편안함이다. ㄹㅇ 너무 좋다. 진작 했으면 우울증 극복이 더빨랐을텐데 싶을정도.)을 위해 검도를 다녔고, 평소 가정환경이 유복하여 절대로 밥을 거르거지 않소, 균형잡히지 않은 식사를 하였고, 잠을 거르지 않도록, 부모님아 알아서 안락한 생활을 내게 주신것에 감사하고 있다. 그렇지 않은 사람들의 사례를 보니 삶이 끔찍해보였다.

그러니, 그 규칙을 절대적으로 지키도록 하라.
````
