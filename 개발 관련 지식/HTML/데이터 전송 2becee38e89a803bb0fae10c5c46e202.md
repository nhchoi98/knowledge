# 데이터 전송

## Multipart란?

HTTP 요청 본문(body)을 **여러 파트로 나눠서 전송**하는 방식이에요. 주로 `multipart/form-data` 형태로 파일 업로드에 사용됩니다.

## 왜 필요한가?

일반 폼 데이터는 이렇게 전송돼요:

```jsx
name=홍길동&age=25
```

하지만 파일은 바이너리 데이터라서 이 방식으로는 못 보내요. 그래서 각 데이터를 **구분선(boundary)**으로 나눠서 보내는 게 multipart입니다.

```jsx
POST /upload HTTP/1.1
Content-Type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxk

------WebKitFormBoundary7MA4YWxk
Content-Disposition: form-data; name="username"

홍길동
------WebKitFormBoundary7MA4YWxk
Content-Disposition: form-data; name="file"; filename="photo.jpg"
Content-Type: image/jpeg

(여기에 바이너리 데이터...)
------WebKitFormBoundary7MA4YWxk--
```

## 핵심 포인트

- **boundary**: 각 파트를 구분하는 고유한 문자열
- 각 파트마다 자신만의 Content-Type을 가질 수 있음
- 텍스트와 바이너리를 한 요청에 섞어서 보낼 수 있음

## FormData와의 관계

```jsx
const formData = new FormData();
formData.append('username', '홍길동');
formData.append('file', fileInput.files[0]);

fetch('/upload', { method: 'POST', body: formData });
```