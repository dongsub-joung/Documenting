# **러스트랭으로 풀스택 개발하기 - Leptos 프레임워크 편**


## 개요
- Client-side rendering with Trunk
- Full-stackserver-side rendering with cargo-leptos

> 목표: 간단한 ToDoList만들기

---

## 설치

```
// Hello World! Getting Set up for Leptos CSR Development
$ cargo install trunk

// 새 프로젝트 
$ cargo init leptos-tutorial

// cd into your new leptos-tutorial project && leptos 의존성 추가
$ cargo add leptos --features=csr

// WebAssembly 변환 컴파일 옵션
$ rustup target add wasm32-unknown-unknown

```

---







---
# Ref
- [Leptos home](https://leptos.dev/)
- [Getting Started](https://book.leptos.dev/getting_started/index.html)
- https://github.com/oxide-byte/todo-leptos/tree/main
