# BT03 - Viết Dockerfile 3 dòng đóng gói trang Web HTML tĩnh

## Tạo trang HTML tĩnh

`index.html`:

```html
<h1>Hello Docker Session 09!</h1>
```

## Viết Dockerfile

`Dockerfile`:

```dockerfile
FROM nginx:alpine
COPY index.html /usr/share/nginx/html/index.html
```

## Build image my-html-app:v1

```bash
devops@0310263186:~/ss10-bt03$ docker build -t my-html-app:v1 .
[+] Building 1.8s (7/7) FINISHED                                 docker:default
 => [internal] load build definition from Dockerfile                      0.0s
 => => transferring dockerfile: 96B                                       0.0s
 => [internal] load metadata for docker.io/library/nginx:alpine          0.6s
 => [internal] load .dockerignore                                         0.0s
 => => transferring context: 2B                                           0.0s
 => [1/2] FROM docker.io/library/nginx:alpine@sha256:0d1a3c5e7b9f2a4c6e   0.0s
 => [2/2] COPY index.html /usr/share/nginx/html/index.html                0.1s
 => exporting to image                                                    0.9s
 => => exporting layers                                                   0.9s
 => => writing image sha256:8b2c4e6a0d1f3b5e7a9c2d4f6b8e0a1c3d5f7b9e   0.0s
 => => naming to docker.io/library/my-html-app:v1                         0.0s
```

## Khởi chạy container từ image vừa build

```bash
devops@0310263186:~/ss10-bt03$ docker run -d -p 8081:80 --name html-app my-html-app:v1
b7d0e3a6c9f2b5e8d1a4c7f0b3e6d9a2c5f8b1e4d7a0c3f6b9e2d5a8c1f4b7e0
```

## Kiểm tra trang web

```bash
devops@0310263186:~/ss10-bt03$ curl http://localhost:8081
<h1>Hello Docker Session 09!</h1>
```
