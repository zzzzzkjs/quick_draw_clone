# Quick Draw clone
Google QuickDraw clone project  ๐ https://quickdraw.withgoogle.com/data
<br/>
<br/>
# netlify ๋ฐฐํฌ ๋งํฌ
[![Netlify Status](https://api.netlify.com/api/v1/badges/12040fc8-88a5-4276-a984-f49cad615b24/deploy-status)](https://app.netlify.com/sites/zzzzzkjs/deploys)
<br/>
๐ https://zzzzzkjs.netlify.app/#/
<br/>
<br/>
vue 3 ๋ฒ์  vetur ์์ ์ธ์ ๋ชปํด์ ์ค๋ฅ๋  ๋ ์ฐธ๊ณ <br/>
https://stackoverflow.com/questions/64867504/vue-3-the-template-root-requires-exactly-one-element-eslint-plugin-vue

## TODO
~~Canvas ๋ชจ๋ฐ์ผ ํฐ์น ์ด๋ฒคํธ ์ถ๊ฐ ํด์ผ๋จ~~


# flask_file_upload
~~flask ํ์ผ์๋ก๋ ์๋ฒ(vue.js ์ฐ๋์์ )~~

frontend, backend ๋์ ๊ตฌ๋๊ฐ๋ฅํ ํ๊ฒฝ ๋ง๋๋๊ฒ ์์ฃผ ๋ฒ๊ฑฐ๋ก์์ ๊ทธ๋ฅ ๋ถ๋ฆฌํ๊ธฐ๋กํจ
backend ๊ตฌ์กฐ๋ ์๋ flask-restx์ ๋ณด์ผ๋ฌํ๋ ์ดํธ ์์ค ์ฐธ๊ณ 

#### FLASK RESTX BOILER-PLATE WITH JWT

# ํ์ด์ฌ 3.3๋ฒ์ ๋ถํฐ venv๋ชจ๋ ๋ด์ฅ๋์ ๋ณ๋ ํจํค์ง ์ค์น ์์ด venv์ฌ์ฉ ๊ฐ๋ฅ
python -m venv .venv

### Terminal commands
Note: make sure you have `pip` and `virtualenv` installed.

    Initial installation: make install

    To run test: make tests

    To run application: make run

    To run all commands at once : make all

Make sure to run the initial migration commands to update the database.
    
    > python manage.py db init

    > python manage.py db migrate --message 'initial database migration'

    > python manage.py db upgrade


### Viewing the app ###

    Open the following url on your browser to view swagger documentation
    http://127.0.0.1:5000/


### Using Postman ####

    Authorization header is in the following format:

    Key: Authorization
    Value: "token_generated_during_login"

    For testing authorization, url for getting all user requires an admin token while url for getting a single
    user by public_id requires just a regular authentication.

### Full description and guide ###
https://medium.freecodecamp.org/structuring-a-flask-restplus-web-service-for-production-builds-c2ec676de563


### Contributing
If you want to contribute to this flask restplus boilerplate, clone the repository and just start making pull requests.

```
https://github.com/cosmic-byte/flask-restplus-boilerplate.git
```
