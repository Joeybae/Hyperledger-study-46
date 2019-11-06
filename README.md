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

C. Vuejs For문 사용

1. 사용할 데이터 생성

        <script>
                    new Vue({
                        el: '#app',
                        data() {
                            return {
                                items: [
                                    {
                                        id: 1,
                                        image: 'home.png',
                                        title: 'HOME'
                                    },
                                    {
                                        id: 2,
                                        image: 'query.jpg',
                                        title: 'Query'
                                    },
                                    {
                                        id: 3,
                                        image: 'create.jpg',
                                        title: 'Create'
                                    },
                                    {
                                        id: 4,
                                        image: 'change.jpg',
                                        title: 'Change'
                                    },
                                ]
                            }
                        }
                    })
        </script>

2. Vuejs에서 For문 호출

        <div id='app'>
                    <ul style="list-style: none;">
                        <template v-for="item in items">
                                <li>
                                    <img :src="item.id">
                                </li>
                                <li>
                                    {{item.title}}
                                </li>
                        </template>
                    </ul>
        </div>

3. Vuejs 이미지 슬라이더

        <!doctype html>
        <html lang="ko">
            <head>

            </head>

            <body>
                <div id='app'>
                    <image-slider>
                        <p>
                            <a @click="prev">Previous</a> || <a @click="next">Next</a>
                        </p>
                        <div
                            v-for="number in [currentNumber]"
                            transition="fade"
                        > 
                        <img
                            :src="images[Math.abs(currentNumber) % images.length]"
                            v-on:mouseover="stopRotation"
                            v-on:mouseout="startRotation"
                        />
                        </div>
                    </image-slider>
                </div>
                <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
                <script>
                    new Vue({
                        el: 'image-slider',
                        data: {
                        images: ['home.png', 'create.jpg', 'query.jpg', 'change.jpg'],
                        currentNumber: 0,
                        timer: null
                        },

                        ready: function () {
                            this.startRotation();
                        },

                        methods: {
                            startRotation: function() {
                                this.timer = setInterval(this.next, 3000);
                            },

                            stopRotation: function() {
                                clearTimeout(this.timer);
                                this.timer = null;
                            },

                            next: function() {
                                this.currentNumber += 1
                            },
                            prev: function() {
                                this.currentNumber -= 1
                            }
                        }
                    });
                </script>
            </body>
        </html>
