# BUTF-8 : 문자열 렌더러 옵션 및 그를 통한 확장된 문자열 렌더링 가용 인코딩

LFBE(LFB(Latin1 for BUTF) Encoding) : PU1, PU2, APC가 CLFB렌더러 전용으로 한정된 Latin1인코딩
   * non-G0영역
     * `N+□`식으로 샌다. `N+0b00□`가 G1, `N+0b01□`가 G2, `N+0b10□`가 G3, `N+0b11□`은 존재하지 않는 영역. 참고로, G1, G2, G3의 영역의 크기가 다르면, 빈 공간들은 존재하지 않는 영역 취급이다.
   * G1영역
     * 0x0F는 예약됨
     * 0x0F에 어떤 기능을 할당하든 무시됨
     * G1, G2, G3같이 non-G0영역에 묶여있음. 참고로 non-G0은 `N+□`식으로 샌다. `N+0b00□`가 G1, `N+0b01□`가 G2, `N+0b10□`가 G3, `N+0b11□`은 존재하지 않는 영역. 참고로, G1, G2, G3의 영역의 크기가 다르면, 빈 공간들은 존재하지 않는 영역 취급이다.
   + LFBECompiler : ULFB에서 CLFB로가는 Compiler.
      * 작동순서
        1. ULFB를 LFBE로 취급해 읽어드린다.
        2. LFBE문자열에 대해 PCRE등 컴파일러를 통하여 다른 LFBE문자열로 컴파일을 한다. 이걸 LFBE2LFBE컴파일이라 한다.
        3. 그러고 나온 LFBE문자열은 ULFB를 CLFB로 컴파일한 결과로, CLFB를 LFBE취급한 결과물과 같으므로, CLFB로 컴파일 결과를 뱉어내 완료한다.
       * LFBE2LFBE컴파일
         1. `PU1 SOS [문자열] ST`가 없다면, 기본값으로 파일 초반에 추가한다. (기본값 설정을 config파일에 저장하는 컴파일러가 "허용된다")
         2. `PU2 SOS [문자열] ST`가 없다면, 기본값으로 파일 초반이 추가한다.  (기본값 설정을 config파일에 저장하는 컴파일러가 "허용된다")
          3. 기본값이 없으면 정상 컴파일도 없다. 당연히 기본값이 없을때 정상컴파일을 거부해야한다. (기본값을 기본으로 제공하는게 "추천(권장보다 약함)된다.", 추천(권장보다 약함)하나 표준은 아닌다) (추천사항과 다르게, 기본값이 없을때 에러가 뱉는것도 기본값이 없을따 정상컴파일 거부로 간주되니, "허용"하고, 앞선 추천사항 그 다음으로 "추천"한다.)
   - Uncompiled LFB(Latin1 for BUTF) : 컴파일 가능성이라는 속성이 부여된 LFBE
     1. `PU1 SOS [문자열] ST`를 지정하지 않을수 있음.
     2. `PU2 SOS [문자열] ST`를 지정하지 않을수 있음.
     3. LFBE의 부분언어임
     4. 렌더링 불가
     5. 가능한 최종 컴파일 있음.
   - Compiled LFB(Latin1 for BUTF) : 렌더링 가능성이라는 속성이 부여된 LFBE의 부분언어
     1. `PU1 SOS [문자열] ST`를 지정하지 않으면 안됨.
     2. `PU2 SOS [문자열] ST`를 지정하지 않으면 안됨
     3. LFBE의 부분언어임.
     4. 렌더링 가능
     5. 이미 최종 컴파일임
 - LFBProtocal URI : 이름과 달리 URI가 아니다. URL에 가깝다.
   - scheme : `lfbp://` (참고사항으로, lfbp:/나 lfbp:나 lfbp//나 lfbp/나 lfbp///, lfbp:///도 허용됨)
   - lfbp://cache라 하면, lfbp의 cache명령(실행파일이나 shell등. linux의 env같은거다.)을 실행한다... 다만... lfbp의 것이니 bin에 있다는 보장이 없다. lfbp클라이언트가 그 위치를 특정할 뿐이다.
       - cache가 지정한 디렉토리 (마치 python이 sites-package디렉토리를 준비하듯) 에서 자원을 고른다.
       - cache --wget [URL] -O [file]을 한다면, 다운로드와 동시에 실행 가능하다. 다만, 다운로드만 원하면 cache --wget만 할것.
   - lfbp://https라 하면, lfbp의 https명령(실행파일이나 shell등. linux의 env같은거다.)을 실행한다... 다만... lfbp의 것이니 bin에 있다는 보장이 없다. lfbp클라이언트가 그 위치를 특정할 뿐이다.
       - cache와는 달리 https주소에 있큰 자원을 고르는거다.
       - 물론 cache도 https주소에서 받아올수 있다.
   - 자원(resource)의 종류
     1. LFBOrchestrator : 그냥 FW용 코드다. 즉, 프로그램이다. 이건 LFBE를 설명하는 부분의 LFBO항목을 참고하라.
       - PU1에서 호출했다면 무조건 이 타입이어야 한다.
     2. LFBOrchestrator가 지원하는 폰트 지정 파일.
       - 드물게 LFBOrchestrator형식이어도 폰트로 간주 가능한데, PU2에서 호출했다면 파일타입 검사가 없기 때문이다.
       - LFBOrchestrator형식이 아니면 죄다 이걸로 간주된다.
       - 일단 폰트로 취급되어, 그 자원이 LFBOrchestrator에게 양도되면, LFBOrchestrator가 폰트로 취급해주는거다.
        - LFBOrchestrator에서 폰트가 아닌걸로 판명나면, 컴파일을 거부라고 에러를 내는 주체는 LFBOrchestrator다.
   - lfbp 클라이언트로 주소를 실행하는것은, 어떻게 보면 lfbp클라이언트에 인자를 주는것이다. 그리고 이 클라이언트는 궁극적으로, 리소스 접근만 해준다.
 * PU1 : Orchestrator URI Modifier
   - LFBProtocal URI임
   - 한번 지정했는데 또 지정하는 경우는, 오케스트레이터 변경으로 간주한다.
    - 렌더러가 읽으면 실행 후 지워버린다.
 * PU2 : Font URI Modifier
   - LFBProtocal URI임
   - 한번 지정했는데 또 지정하는 경우는 폰트 변경으로 간주한다.
   - 렌더러가 읽으면 실행 후 지워버린다.
 * APC : Orchestrator Command
   - 렌더러가 읽으면, 명령어 취득 후, 지우고, 지워진 후에 어느 오프셋에서 명령어가 있었는지와, 명령어가 뭔지를, 오케스트레이터에 전달한다. 그리고 오케스트레이터는, 렌더러를 이용하여, 문자열 편집들을 요청하고, 렌더러는 그 문자열 열람 • 편집을 모두 허용해서 차래대로 컴파일한다.
   - Orchestrator에서 특별히 명령어로 간주하는 구간이다.
 - 렌더러
   - 만약 렌더러가, --no-rendering으로 열렸다면, 마지막에 렌더링 작업이 없다.
   - 렌더러가 무렌더링 옵션 없이 열렸다면, 마지막에 렌더링 작업이 있다.
   - 렌더링 작업이란, 오케스트레이터가, non-G0과 G0과 폰트파일들을 종합하여, 각 구역별로 폰트를 지정하고, 각 기호와 폰트를 읽어들여서, LFB Orchestratate FW(LOFW)의 "렌더링 결과 객체"로 반환한다. 그 객체를 렌더링만 하면, 형체가 나온다.
   - 그래서 렌더링이 어떻게 되는가를 알고싶다면, LFB Orchestratate FW(LOFW)항목을 살펴봐라.
 - LFB Orchestratate FW(LOFW) : 여기에 작성하려 했는데, 도저히 무리 ㅋㅋ, 이게 사실상 BUTF의 이해에 있어 핵심이니까, 이건 그냥 따로 문단을 만들겠다. LOFW문단에서 작성하도록 미루겠다

BUTF(Byted UTF)-8 : C0, C1 제어문자 중 utf-8이나 ascii가 아닌 바이트 스트림을 중간에 삽입하는 명령으로 인해 존재하는 바이트 시퀀스를 허용한 UTF-8 (기존 UTF-8은 그걸 허용 안했기 때문)
 + 정체 : Byted UTF-8은 Latin1 for BUTF라는 인코딩으로 컴파일된다. PCRE에서, utf-8이 아닌 char마저 섞인 char배열을 다루듯, 그냥 char에서 char로 가는 치환이다. 그런 목적의 인코딩이다
 - Unpreprocessed BUTF-8 : 최종 전처리 가능성 속성을 참으로 추가한 BUTF-8
   - `0b0xxxxxxx or 0b110xxxxx0b10xxxxxx인데 0b11000xx0b10xxxxxx인것 or C0, C1 제어문자 중 utf-8이나 ascii가 아닌 바이트 스트림을 중간에 삽입하는 명령으로 인해 존재하는 바이트 시퀀스`를 제외한 BUTF-8문자열이 존재 가능하다.
   - 중간에 삽입라는 바이트 시퀀스에서, 문자열 데이터가 존재한다면, 그 인코딩이 BUTF-8일때, `0b0xxxxxxx or 0b110xxxxx0b10xxxxxx인데 0b11000xx0b10xxxxxx인것 or C0, C1 제어문자 중 utf-8이나 ascii가 아닌 바이트 스트림을 중간에 삽입하는 명령으로 인해 존재하는 바이트 시퀀스`를 제외한 BUTF-8문자열이 존재 가능하다.
   - BUTF-8의 부분언어다.
   - 렌더링 불가능
   - 최종 전처리 가능성을 가진다.
 - Preprocessed BUTF-8 : 렌더링 가능성이라는 속성을 추가한 BUTF-8의 부분언어
   - `0b0xxxxxxx or 0b110xxxxx0b10xxxxxx인데 0b11000xx0b10xxxxxx인것 or C0, C1 제어문자 중 utf-8이나 ascii가 아닌 바이트 스트림을 중간에 삽입하는 명령으로 인해 존재하는 바이트 시퀀스`를 제외한 BUTF-8문자열이 존재 가능하지 않다.
   - 중간에 삽입라는 바이트 시퀀스에서, 문자열 데이터가 존재한다면, 그 인코딩이 BUTF-8일때, `0b0xxxxxxx or 0b110xxxxx0b10xxxxxx인데 0b11000xx0b10xxxxxx인것 or C0, C1 제어문자 중 utf-8이나 ascii가 아닌 바이트 스트림을 중간에 삽입하는 명령으로 인해 존재하는 바이트 시퀀스`를 제외한 BUTF-8문자열이 존재 가능하지 않다.
   - BUTF-8의 부분언어다.
   - 렌더링 불가능
   - 최종 전처리 가능성을 가진다.
 - BUTFPreprocessor : UBUTF-8에서 PBUTF-8로 가는 컴파일러(전처리기라고 부르지만...)
   * 작동순서
     1. UBUTF-8을 BUTF-8로 간주하여 읽어들인다.
     2. BUTF-8문자열에 대해 PCRE등 컴파일러를 통하여 다른 BUTF-8문자열로 컴파일을 한다. 이걸 BUTF-8toBUTF-8컴파일이라 한다.
     3. 그러고 나온 BUTF-8문자열은 UBUTF-8를 PBUTF-8로 컴파일한 결과로, PBUTF-8를 BUTF-8취급한 결과물과 같으므로, PBUTF-8로 컴파일 결과를 뱉어내 완료한다.
   * BUTF-8toBUTF-8컴파일
     1. 중간에 삽입라는 바이트 시퀀스에서, 문자열 데이터가 존재한다면, 혹은 중간 삽입이 아닌 본문이라면, 그리고 그게 BUTF-8일시, `0b0xxxxxxx or 0b110xxxxx0b10xxxxxx인데 0b11000xx0b10xxxxxx인것 or C0, C1 제어문자 중 utf-8이나 ascii가 아닌 바이트 스트림을 중간에 삽입하는 명령으로 인해 존재하는 바이트 시퀀스`에 대하요, BUTF-8문자열, 즉, Latin1에서 정의된 기본 글자를 넘어가며 동시에 유니코드 영역의 기본 글자인 글자들은, 죄다 UTF-8이므로, 그걸 Unicode로 바꿔서, 코드 포인트화 한 후, SGCE문자열을 통한 BUTF-8로 변경시킨다.
     2. 이 과정에서, 바이트 길이 2가 넘어가는 UTF-8데이터(BUTF과 달리 바이트 시퀀스 기능이 없는 표준) 및 `0b110xxxxx0b10xxxxxx`인데 0b11000xx0b10xxxxxx가 아닌것은 다, 바이트 길이 2의 SGCE심볼과, 그 유니코드 포인트로 변경된다. 한마디로, 더이상 순수 UTF-8이 아니다. BUTF-8이다.
 - BUTFCompiler : PBUTF-8을 LFBE(LFB(Latin1 for BUTF) Encoding)로 컴파일해주는 컴파일러다.
   - PBUTF-8의 `0b110000xx0b10xxxxxx`를 `0bxxxxxxxx`로 컴파일한다.
   - 그게 다다. 참 어셈블러같은놈이다.
   - 심지어, 바이트 시퀀스 중의 PBUTF-8에게도 그렇다.
   - 바이트 시퀀스중의 문자열이 PBUTF-8가 아니면, 그런 컴파일은 안한다.

## LFB Orchestratate FW(LOFW)

...필사중(오프라인 어딘가에 이미 적어놨다. 그리고 종이 말고, 뇌에 적은것도 있음)...

## 기존 표준을 준수했는가?

이것은 "표준 준수 조항 남용 (Compliance Abuse)"입니다
 - 오픈소스(MIT)이므로 사기도 아님.

그냥 내가 만든 독자 표준임.

### 참고사항

참고된 표준 : Unicode중 ISO latin1영역의 C1중, 정확히 유저가 쓰라고 만든 앱이나 사적 명령, ASCII표준 C0, Posix명령줄 권장 사항, Python PEP 표준 sites-package구조, Posix계열중 "env"같은것, UTF-8표준, 구글이 http를 "http:"로 표기하는것, 웹의 데이터를 curl하여 실행하는 표준
준수 표준 : Unicode중 ISO latin1영역의 C1중, 정확히 유저가 쓰라고 만든 앱이나 사적 명령, ASCII표준 C0, Posix명령줄 권장 사항, 웹의 데이터를 curl하여 실행하는 표준
차용된 모티프(아이디어) : Python PEP 표준 sites-package구조, Posix계열중 "env"같은것
실제로 한 짓 : UTF-8표준과 ISO latin1를 합쳐버림, 구글이 http를 "http:"로 표기하는것
결과 : UTF-8표준과 ISO latin1를 합쳐버리고, 관리 프로토콜까지 지정한, BUTF-8텍스트 내에서, 렌더러와 텍스트 폰트와 언어셋까지 일반텍스트-프로그래밍 언어가 필요할수도 있는 마크업 텍스크 렌더링등 사이를 자유자재로 변경하거나 몇번이고 평가할수 있는 텍스트 처리 후 렌더링 엔진 및 렌더링 오케스트레이션 서드파티 프레임워크 및 배포•설치 시스템

## 주의사항

믿을수 있고 멍청하지 않으신 공적인 출처께서 만든 오케스트레이터만 신뢰하는걸 추천합니다.

왜냐면 난 이걸 LaTeX • markdown • HTML렌더러랑 연관시킬 가능성마저 가지는것같다는걸 발견했거든. 오케스트레이터가 걍 하나의 프로그램(튜링 머신의 코드)이므로, 존나 미친짓을 많이 가능할것 같아서... 물론, 정신이 재대로 있다면, 렌더링 이외의 목적으론 안쓰겠지. 굳이 텍스트 뷰어의 작업을 거치는 오버해드는 싫어할테니.