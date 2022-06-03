Node.js 심화 주차 개인 과제




🏁 **Goal:  "**누구나 사이트 및 게시판을 자유롭게 생성할 수 있고 익명으로 게시글과 댓글을 작성할 수 있는 웹 사이트를 구현한다.**"**

- 학습 과제를 끝내고 나면 할 수 있어요!
    - 추상화에 대해 직접적으로 경험합니다.
    - 테스트 코드가 만족하도록 구현하므로 TDD의 장단점을 느낄 수 있습니다.

❗ 지금 까지 진행했던 기능 개발 위주의 과제가 아닌 백엔드 개발자의 기초를 다지는 과제가 될 것입니다!

⚙️ Process: 아래에 설명된 준비 단계를 거쳐 `index.spec.js`의 테스트가 통과 할 수 있도록 `index.js`에 기능을 구현해주세요.

모든 테스트 코드가 통과할 수 있도록 코드를 작성했다면 index.js 파일을 Commit하고 Push한 뒤, 자신의 GitHub 레파지토리 링크를 제출해주세요!

1️⃣ Preparation: 준비 단계

[https://github.com/selenehyun/abstract-site](https://github.com/selenehyun/abstract-site)

- 위 repository를 여러분의 GitHub 계정으로 fork해주세요.
- fork한 repo를 clone하여 파일을 받아주세요.
- 터미널을 활용하여 clone한 repo경로에 들어가주세요.
- `npm install` 로 패키지를 설치해주시면 과제를 시작할 준비는 끝납니다!

2️⃣ Test Code: 테스트 코드 활용하기


- 위 준비 절차를 잘 따라하셨다면 이미 jest는 설치된 상태입니다!
- jest가 뭔지, 어떻게 테스트 코드가 실행되는건지 기억이 잘 안나신다면 심화 5주차 수업을 다시 확인해보세요! (`npm run test` 로 테스트 코드를 테스트할 수 있습니다)
- 아래 사진처럼 나올 수 있을 때 까지 코드를 작성하며 테스트를 돌려보세요!
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/70eab46a-e66b-44a2-9c38-1008c082cf37/Untitled.png)
    
- 테스트 코드에서 각 클래스의 어떤 메서드를 호출하고 있는지, 어떤 값을 인자로 전달하고 있는지 확인하며 index.js에 구현하면 됩니다.
    - index.js > Site class 구현 예시
        
        ```jsx
        class Site {
        		constructor() {
        				this.boards = [];
        		}
        
            addBoard(board) {
                this.boards.push(board);
            }
        }
        ```
        
    - 위 예시처럼 구현한 뒤 다시 `npm run test` 명령어를 실행하면 이전에는 통과하지 않던 테스트 코드가 통과하는 것을 볼 수 있게 됩니다.

🚩 **Requirement:  과제에 요구되는 사항이에요**

 과제 요구 사항을 모두 완수해야 합니다!

✅ 과제 요구 사항: `index.spec.js`의 모든 테스트 통과


![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/70eab46a-e66b-44a2-9c38-1008c082cf37/Untitled.png)

📖 테스트 코드 해석이 어렵다면, 아래 정리된 줄글로 작성된 요구 사항을 참고해주세요.


## Site 요구사항

- `Site`는 n개 이상 생성 할 수 있다.
- `Site`에는 `Board` 를 추가하고 추가된 `Board`를 조회할 수 있다.
- 하나의 `Site`에 동일한 이름의 `Board`를 추가할 수 없다.
- `Board`는 n개 이상 추가 할 수 있다.

## Board 요구사항

- `Board`는 `name` 데이터를 포함해야 하며 `null` 또는 빈 문자열(`''`)은 허용하지 않는다.
- `Site` 에 추가된 `Board`만 사용 가능한 것으로 간주하며 사용 불가능한 `Board`에는 `Article`을 추가할 수 없다.
- `Board`에 `Article`을 추가할 때 `Article`에 ID를 자동 생성해서 부여해야 한다.
    - 규칙은 `${board.name}-${랜덤 값}` 를 따른다.
- `Board`에 `Article`을 추가할 때 `Article`에 작성 일자가 들어가야 한다.
    - 저장되는 형식은 `[ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)`을 따른다. ([참고](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Date/toISOString))
- `Article` 은 n개 이상 추가 할 수 있다.
- 작성된 `Article` 목록을 조회 할 수 있어야 한다.

## Article 요구사항

- `Article`은 `subject`, `content`, `author` 3개의 데이터를 포함해야 하며 `null` 또는 빈 문자열(`''`)은 허용하지 않는다.
- `Board`에 추가된 `Article`만 사용 가능한 것으로 간주하며 사용 불가능한 `Article`에는 `Comment`를 추가할 수 없다.
- `Article`에 `Comment`를 추가할 때 `Comment`에 작성 일자가 들어가야 한다.
    - 저장되는 형식은 `[ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)`을 따른다. ([참고](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Date/toISOString))
- `Comment`는 n개 이상 추가 할 수 있다.
- 작성된 `Comment` 목록을 조회 할 수 있어야 한다.

## Comment 요구사항

- `Comment`는 `content`, `author` 2개의 데이터를 포함해야 하며 `null` 또는 빈 문자열(`''`)은 허용하지 않는다.

💪 References: 한 번 읽어보시면 과제 수행에 도움이 되실 거에요!


- GitHub 원격 저장소 가져오기 ([Link](https://lktprogrammer.tistory.com/6))
- JavaScript 클래스 관련 ([Link](https://poiemaweb.com/es6-class))
- 테스트 관련 ([Link](https://velog.io/@ysong0504/Node.js-Jest%EB%A5%BC-%EC%9D%B4%EC%9A%A9%ED%95%9C-API-%ED%85%8C%EC%8A%A4%ED%8A%B8-%EC%BD%94%EB%93%9C-%EC%9E%91%EC%84%B1%ED%95%98%EA%B8%B0))


⚠️ **Warning : 꼭 지켜야 할 것과 하지 않아도 되는 것!**

- 이것은 꼭 지켜주세요(Do's)
    - 과제 요구 사항은 모두 지켜주세요. 특정 기능을 임의로 배제하면 안 됩니다!
    - 테스트 코드 자체를 과제 요구 사항으로 받아들이시면 됩니다. 즉, 테스트 코드는 수정되어선 안됩니다!
- 이것은 하지 않으셔도 돼요(Don'ts)
    - 과제 추가 기획 때문에 고민하지 마세요. 위에 작성된 과제 요구 사항만 지키면 됩니다!