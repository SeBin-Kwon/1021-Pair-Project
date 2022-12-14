# ๐๏ธ Django Project (Pair programming) 

> ์ผ์ : 2022-10-21
>
> ํ ๊ตฌ์ฑ : 3์ธ 1ํ (1-14 ๊ถ์ธ๋น, ๋ธ์๋น, ์ด์๊ฒฝ)



![221021](https://user-images.githubusercontent.com/106902415/197198156-219de00f-2ca0-4dc2-a279-53b349bd3864.gif)



## ๐ซง Contributors

<a href="https://github.com/code-sum/221021-PJT/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=code-sum/221021-PJT" />
</a>



## โ๏ธ Stacks

<img src="https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=Python&logoColor=ffffff"/> <img src="https://img.shields.io/badge/Django-092E20?style=flat-square&logo=Django&logoColor=ffffff"/> <img src="https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=HTML5&logoColor=ffffff"/> <img src="https://img.shields.io/badge/CSS3-1572B6?style=flat-square&logo=CSS3&logoColor=ffffff"/> <img src="https://img.shields.io/badge/Bootstrap-7952B3?style=flat-square&logo=Bootstrap&logoColor=ffffff"/> <img src="https://img.shields.io/badge/Visual Studio Code-007ACC?style=flat-square&logo=Visual Studio Code&logoColor=ffffff"/> <img src="https://img.shields.io/badge/Git-F05032?style=flat-square&logo=Git&logoColor=ffffff"/> <img src="https://img.shields.io/badge/GitHub-181717?style=flat-square&logo=GitHub&logoColor=ffffff"/>



## ๐ Requirements 

> ํ์ด ํ๋ก๊ทธ๋๋ฐ์ ํตํ ํ์์  ์ปค๋ฎค๋ํฐ ์๋น์ค๋ฅผ ๊ฐ๋ฐํฉ๋๋ค. ์๋ ์กฐ๊ฑด์ ๋ง์กฑํด์ผํฉ๋๋ค.

- **CRUD** ๊ตฌํ
- **Staticfiles** ํ์ฉ ์ ์  ํ์ผ(images, CSS, JS) ๋ค๋ฃจ๊ธฐ
- **Django Auth** ํ์ฉ ํ์ ๊ด๋ฆฌ ๊ตฌํ
- **Media** ํ์ฉ ๋์  ํ์ผ ๋ค๋ฃจ๊ธฐ
- ๋ชจ๋ธ๊ฐ **1 : N** ๊ด๊ณ ๋งคํ ์ฝ๋ ์์ฑ ๋ฐ ํ์ฉ
  - ์ ์  - ๋ฆฌ๋ทฐ
  - ์ ์  - ๋๊ธ
  - ๋ฆฌ๋ทฐ - ๋๊ธ



## ๐ฅ Issues

- ๋ฌธ์  ์ํฉ

  - `accounts` ๊ธฐ๋ฅ๊ณผ `reviews` ๊ธฐ๋ฅ์ ๊ตฌํํ๊ณ  ๋ ๊ฐ์ ์ฑ์ ์ฐ๋ํ๋ ๊ณผ์ ์์ DB ์ด์ ๋ฐ์

    - `Comment` ๋ชจ๋ธ์ `review_id` ๊ฐ `NOT NULL` ์ ์ฝ์กฐ๊ฑด์ ์๋ฐฐ๋จ
    - `Comment` ๋ชจ๋ธ์ `user` ๊ฐ ์ธ๋ํค ํ๋๊ฐ ์๋ `CharField()` ๋ก ์์ฑ๋จ 

    ```python
    class Comment(models.Model):
        reivew = models.ForeignKey(Review, on_delete=models.CASCADE)
        user = models.CharField(max_length=20)
        content = models.CharField(max_length=80)
    ```

- ๋ฌธ์  ํด๊ฒฐ

  ```python
  class Comment(models.Model):
      review = models.ForeignKey(Review, on_delete=models.CASCADE)
      user = models.ForeignKey(settings.AUTH_USER_MODEL, on_delete=models.CASCADE)
      content = models.CharField(max_length=80)
  ```

  

## โ๏ธ Reviews

- **๊ถ์ธ๋น** : ๋ค๊ฐ์ด ์๋ฌ๋ฅผ ์ก์๋ด๋ฉฐ ๊ฒ์๊ธ๊ณผ ๋๊ธ ๊ธฐ๋ฅ์ ๊ตฌํํด์ ์ฌ๋ฐ์์ง๋ง ๊ผญ ์๊ฒฝ์ฐ๊ณ  ์คํ๋ฅผ ์กฐ์ฌํด์ผ๊ฒ ๋ค๊ณ  ์๊ฐํ์ต๋๋ค. ๊ทธ๋ฆฌ๊ณ  CSS ๊ณต๋ถ๋ฅผ ์ข ๋ ํด์ผํ  ๊ฒ ๊ฐ์ต๋๋ค.
- **๋ธ์๋น** : ๊ตฌํ ์ค๊ฐ์ค๊ฐ ์๋ฌ๋ฅผ ํ์๋ค๊ณผ ํจ๊ป ๊ณ ์ณ๋๊ฐ๋ฉฐ ๋์ด ์ํ ์ง๋ง ๋ ํด๊ฒฐ์ ํ๋ ์ข์์ต๋๋ค.  ๋ Django ๊ตฌํ์ ๊ธ๋ฐฉ ํ์ง๋ง CSS์์ ์์ฃผ ๋งํ์ ๊ณต๋ถ๋ฅผ ์ข ๋ ํด์ผ๊ฒ ๋ค๊ณ  ์๊ฐํ์ต๋๋ค ์ข์ ํ์ ๋ถ๋ค๊ณผ ํจ๊ปํด์ ์์ฃผ ์ฆ๊ฑฐ์ ์ต๋๋น
- **์ด์๊ฒฝ** : ๊ฒ์๊ธ ๋ชฉ๋ก์ ๋ง์ฐ์ค๋ฅผ ์ฌ๋ฆฌ๋ฉด ํธ๋ฒ ํจ๊ณผ๊ฐ ์ ์ฉ๋๋๋ก ํ์๋ค๊ณผ ์ด์ฌํ ๋ธ๋ ฅํ์ต๋๋ค! Django ๋ฅผ ํ์ฉํด์ ํ์ ๊ธฐ๋ฅ์ ๊ตฌํํ  ๋๋ณด๋ค ํจ์ฌ ์ค๋ ์๊ฐ์ด ๊ฑธ๋ ธ์ง๋ง, CSS ๋ฅผ ๋ณต์ตํ  ์ ์์ด์ ์ข์ ๊ฒฝํ์ด์์ต๋๋ค.