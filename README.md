# Bruno Tutorials

My first tutorials using [Bruno](https://www.usebruno.com/) — an open-source, fast, and Git-friendly API client.

## What is Bruno?

Bruno is a desktop API client that stores your collections directly as plain text files on your filesystem. Unlike Postman or Insomnia, Bruno's `.bru` file format is designed to be committed to version control alongside your code.

## Tutorial Overview

This repository contains a beginner-friendly Bruno collection that demonstrates how to interact with the [JSONPlaceholder](https://jsonplaceholder.typicode.com/) free fake REST API.

The collection covers the fundamental HTTP methods:

| Request | Method | Description |
|---|---|---|
| Get All Posts | GET | Retrieve a list of all posts |
| Get Post by ID | GET | Retrieve a single post by its ID |
| Create Post | POST | Create a new post |
| Update Post | PUT | Replace an existing post |
| Delete Post | DELETE | Delete a post by ID |

## Collection Structure

```
JSONPlaceholder/
├── bruno.json                  # Collection manifest
├── environments/
│   └── Default.bru             # Environment variables (base URL, etc.)
├── Get All Posts.bru
├── Get Post by ID.bru
├── Create Post.bru
├── Update Post.bru
└── Delete Post.bru
```

## Getting Started

1. **Install Bruno** — Download from [usebruno.com](https://www.usebruno.com/downloads)
2. **Open the collection** — In Bruno, click *Open Collection* and select the `JSONPlaceholder` folder
3. **Select the environment** — Choose the `Default` environment from the environment dropdown
4. **Run a request** — Click any request and press *Send*

## Prerequisites

No API key is required. JSONPlaceholder is a free public API intended for testing and prototyping.

# Bruno API Testing
[<img src="https://fetch.usebruno.com/button.svg" alt="Fetch in Bruno" style="width: 130px; height: 30px;" width="128" height="32">](https://fetch.usebruno.com?url=https%3A%2F%2Fgithub.com%2FHoussemmhadhbi78%2FTutorials_Bruno.git "target=_blank rel=noopener noreferrer")