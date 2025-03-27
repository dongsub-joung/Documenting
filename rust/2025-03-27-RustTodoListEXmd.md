# **러스트랭으로 풀스택 개발하기 - Leptos 프레임워크 편**


## 개요
- Client-side rendering with Trunk
- Full-stackserver-side rendering with cargo-leptos

> 목표: 간단한 ToDoList만들기

---

## 설치

```bash
// Hello World! Getting Set up for Leptos CSR Development
$ cargo install trunk

// 새 프로젝트 
$ cargo init leptos-tutorial

// cd into your new leptos-tutorial project && leptos 의존성 추가
$ cargo add leptos --features=csr

// WebAssembly 변환 컴파일 옵션
$ rustup target add wasm32-unknown-unknown

// init
$ trunk serve --open

```


---

## HTML Dom을 Rust로 조작

```rust
 view! {
          <div class="bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4 flex flex-row">

                <div class="basis-11/12">
                    <p class="text-lg text-gray-900">
                        {todo_item.get().title}
                    </p>

                    <textarea class="text-left text-gray-500 w-full" rows=3>
                        {todo_item.get().description}
                    </textarea>
                </div>

                <div class="basis-1/12 flex items-center justify-center">
                   <div class="flex flex-row-reverse space-x-4 space-x-reverse">
                        <button on:click=on_edit
                            class="text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-full text-sm p-2.5 text-center inline-flex items-center mr-2">
                             <i class="fa-solid fa-edit"></i>
                        </button>
                        <button on:click=on_delete
                            class="text-white bg-red-700 hover:bg-red-800 focus:ring-4 focus:outline-none focus:ring-red-300 font-medium rounded-full text-sm p-2.5 text-center inline-flex items-center mr-2">
                             <i class="fa-solid fa-minus"></i>
                        </button>
                   </div>
                </div>
          </div>

```


## JS를 웹어셈블리로 컴파일해서 동작

```rust
  let on_add_event = move |_| {

        let title = input_title.get().expect("<input> to exist").value();
        let description = input_description.get().expect("<textarea> to exist").value();
        let id = if todo_item.get().is_some() {todo_item.get().unwrap().id} else {
            let mut rng = rand::rng();
            format!("{}", rng.random::<char>())
        };

        let new_item = Todo{
            id,
            title,
            description,
        };

        on_add(new_item);

```

# FIx features

- UUID -> random string
- created_time -> delete

https://github.com/oxide-byte/todo-leptos/tree/main
-> 
https://github.com/dongsub-joung/rust-fullstack/tree/main/leptos

---
## 결과 화면
![todo list result err](https://private-user-images.githubusercontent.com/59364300/427417686-bb111fe4-f4d6-444d-94e2-c784676b5590.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NDMwNjQ5NjEsIm5iZiI6MTc0MzA2NDY2MSwicGF0aCI6Ii81OTM2NDMwMC80Mjc0MTc2ODYtYmIxMTFmZTQtZjRkNi00NDRkLTk0ZTItYzc4NDY3NmI1NTkwLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNTAzMjclMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjUwMzI3VDA4Mzc0MVomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTQ0ZjQ2OWEyMGU2MGQ1NjYwMTJlODRlMjZiZGZkZDgxYjUzMTgyYzNlNWZmNmFjZmJlODQ2NGQ5ODMwNDMwMTYmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0In0.gYch3pVL7NLpDBRpUAv_vlMA4uXzk9qKtXzki1CrvHo)


---

# Ref
- [Leptos home](https://leptos.dev/)
- [Leptos Getting Started](https://book.leptos.dev/getting_started/index.html)
- 


> Welcome to the world of UI development with Rust and WebAssembly (WASM), powered by Leptos and Trunk!
