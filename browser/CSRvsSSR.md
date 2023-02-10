## CSR (Client Side Rendering)

<img src="https://miro.medium.com/v2/resize:fit:1400/format:webp/1*jJkEQpgZ8waQ5P-W5lhxuQ.png">
1. HTML 다운<br />
2. JS 다운 <br />
3. React web app 소스코드를 로드해서 실행 (화면에 보이지 않음) <br />
4. 특정컴포넌트가 화면에 그려지며 사용자의 눈에 보임

- JS가 전부 다운로드 되어 리액트 애플리케이션이 정상 실행되기 전까지는 화면이 보이지 않음.
- JS가 전부 다운로드 되어 리액트 애플리케이션이 정상 실행된 후, 화면이 보이면서 유저가 인터렉션 가능

## SSR(Server Side Rendering)

<img src="https://miro.medium.com/v2/resize:fit:1400/format:webp/1*CRiH0hUGoS3aoZaIY4H2yg.png">

1. 이미 표현되어있는 HTML 다운 (화면에 보임)
2. JS를 다운받을 때 화면은 보이지만 기능 동작 안함
3. React App이 실행될 때 기능 동작 안 함
4. 모두 리액트가 실행된 후 동작됨

- JS가 전부 다운로드 되지 않아도, 일단 화면은 보이지만 유저가 사용할 수 없음.
- JS가 전부 다운로드 되어 리액트 애플리케이션이 정상 실행된 후, 유저가 사용 가능

→ SSR 도입이 쉽지 않음 (난이도)
