# Hyperledger-study-46

하이퍼레져 앱 만들기 실습 46일차 - veu.js로 TO DO LIST 앱 만들기

A. Vuejs module 불러오기

1. index.html 만들기

        <!doctype html>
        <html lang="ko">
            <head>
            </head>
            <body>
            </body>
        </html>

2. Vuejs 가져오기

        # <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>

3. index.html 웹 페이지에서 실행

        # 웹 페이지 주소창에 해당 파일 주소 입력

        # ex) /Users/username/filename/index.html

        # 실행 후 '검사 - Console' 창에 아래의 메세지가 나오면 성공
        'You are running Vue in development mode.
        Make sure to turn on production mode when deploying for production.
        See more tips at https://vuejs.org/guide/deployment.html'


B. Vuejs를 활용하여 간단한 Login 구현

        <!doctype html>
        <html lang="ko">
            <head>

            </head>

            <body>
                <div id='app'>
                    <input type="text" id="user_id" v-model="userId">
                    <input type="password" id="user_password" v-model="userPassword">
                    <button type="button">로그인</button>
                    <br />
                    아이디 : {{ userId }}
                    <br />
                    비밀번호 : {{ userPassword }}
                </div>
                <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
                <script>
                    new Vue({
                        el: '#app',
                        data() {
                            return {
                                userId: '',
                                userPassword: ''
                            }
                        }
                    })
                </script>
            </body>
        </html>
