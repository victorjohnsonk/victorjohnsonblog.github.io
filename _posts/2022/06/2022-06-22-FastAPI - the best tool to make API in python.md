---
layout: post
title:  "FastAPI - the best tool to make API in python"
description: "Discover why FastAPI is the best tool for building high-performance APIs in Python. Learn about its key features, including async support, type annotations, automatic documentation, and data validation with Pydantic. Perfect for developers looking to create scalable and efficient APIs, FastAPI offers simplicity and speed, making it a top choice in the Python community."
permalink : /fastapi-the-best-tool-to-make-api-in-python
author: admin
categories: [ programming ]
image: assets/images/posts/2022/06/api-1.webp
tags: [python, api, fastapi, featured]
last_modified_at: 2024-07-31 00:00:00 +0100
---


FastAPI is an open-source, modern, fast (hence the name FastAPI), and efficient framework for building APIs in Python. It was introduced in 2019 and since then, it has gained a lot of attention from the developer community. FastAPI is built on top of Starlette, a lightweight and efficient ASGI framework, and Pydantic, a data validation and settings management library.

FastAPI is designed to provide high performance, with async support and type annotations. It is a great choice for developers who want to build scalable and reliable APIs in Python. In this article, we will dive deeper into the FastAPI framework, its features, and how to use it to build APIs. [Read more about FastAPI](https://fastapi.tiangolo.com/about/)

## Why FastAPI?

There are several reasons why FastAPI is a great choice for building APIs in Python:

- Performance: FastAPI is built to be fast, with a performance that is comparable to Node.js and Go. It leverages the power of asynchronous programming, which allows it to handle multiple requests concurrently. This makes it a great choice for building high-performance APIs.

- Type Annotations: FastAPI uses type annotations extensively, which makes it easier to write and maintain code. Type annotations provide a way to specify the data types of function arguments and return values, which helps in catching errors early in the development process.

- Automatic API Documentation: FastAPI automatically generates API documentation based on the type annotations and docstrings in the code. This makes it easy to understand the API endpoints and their functionality.

{% include random-related-article.html %}

- Validation: FastAPI uses Pydantic for data validation and settings management. Pydantic provides a way to define data models with validation rules, which makes it easy to ensure that the data sent to the API is in the correct format.

- Open-Source and Community-Driven: FastAPI is an open-source project, which means that it is free to use and anyone can contribute to its development. The framework has a large and active community of developers, which ensures that it is constantly improving and evolving.

![API Image](assets/images/posts/2022/06/api-2.webp "API Image")
###### *Representative image of API - Source: pexels.com*

### Getting Started with FastAPI:

Now that we have discussed the advantages of using FastAPI, let's dive into how to get started with the framework.

#### Installing FastAPI:
The first step is to install FastAPI. FastAPI can be installed using pip, the package installer for Python. To install FastAPI, open a terminal or command prompt and run the following command: 

    pip install fastapi

This will install the latest version of FastAPI and its dependencies.



#### Creating a New API:
Once FastAPI is installed, we can create a new API project. To create a new API project, we need to create a new Python file and import the FastAPI class.

    from fastapi import FastAPI
    app = FastAPI()
    
This will create a new FastAPI application instance. We can use this instance to define the API endpoints.

#### Defining API Endpoints:
To define an API endpoint, we need to create a function that will be called when the endpoint is accessed. The function should accept the HTTP request as an argument and return a response.
    
    from fastapi import FastAPI

    app = FastAPI()

    @app.get("/")
    async def root():
        return {"message": "Hello World"}
    
In the above code, we have defined an API endpoint at the root ("/") path. When this endpoint is accessed using an HTTP GET request, the root() function will be called and it will return a JSON response with a "message" key.

### Running the API:
To run the API, we need to start the development server. We can do this by running the following command in the terminal or command prompt:

    uvicorn main:app --reload

This will start the API

#### Handling Request Parameters:
FastAPI makes it easy to handle request parameters. We can define the parameters for an API endpoint using the FastAPI's Path, Query, Header, and Body classes. Here's an example:

    from fastapi import FastAPI, Path

    app = FastAPI()

    @app.get("/items/{item_id}")
    async def read_item(item_id: int = Path(..., title="The ID of the item to get")):
        return {"item_id": item_id}
        
In the above code, we have defined a new endpoint /items/{item_id} that accepts an item_id parameter. The Path class is used to define the item_id parameter as a path parameter. The ... syntax indicates that the parameter is required. The title argument is used to provide a human-readable name for the parameter.

#### Handling Request Bodies:
FastAPI provides a convenient way to handle request bodies using the Body class. We can use the Body class to define the request body schema and validation rules. Here's an example:

    from fastapi import FastAPI, Body
    from pydantic import BaseModel

    app = FastAPI()

    class Item(BaseModel):
        name: str
        price: float
        is_offer: bool = None

    @app.post("/items/")
    async def create_item(item: Item = Body(..., example={
        "name": "Foo",
        "price": 99.0,
        "is_offer": True
    })):
        return {"item": item}

In the above code, we have defined a new endpoint /items/ that accepts a request body of type Item. The Body class is used to define the request body schema and validation rules. The example argument is used to provide an example request body for documentation purposes.

#### Handling Responses:
FastAPI makes it easy to handle responses using the Response class. We can use the Response class to define the response headers and status code. Here's an example:

    from fastapi import FastAPI, Response

    app = FastAPI()

    @app.get("/items/{item_id}")
    async def read_item(item_id: int, response: Response):
        if item_id == 1:
            response.headers["X-Custom"] = "Custom Header Value"
        return {"item_id": item_id}

In the above code, we have defined a new endpoint /items/{item_id} that accepts an item_id parameter. The Response class is used to define the response headers. In this example, we are setting a custom header X-Custom for the response.

#### Handling Errors:
FastAPI makes it easy to handle errors using the HTTPException class. We can use the HTTPException class to define the error message and status code. Here's an example:

    from fastapi import FastAPI, HTTPException

    app = FastAPI()

    @app.get("/items/{item_id}")
    async def read_item(item_id: int):
        if item_id == 0:
            raise HTTPException(status_code=400, detail="Item not found")
        return {"item_id": item_id}

In the above code, we have defined a new endpoint /items/{item_id} that accepts an item_id parameter. If the item_id parameter is 0, we are raising an HTTPException with a 400 status code and a detail message Item not found.

{% include random-related-article.html %}


FastAPI is a powerful and easy-to-use web framework that makes building APIs in Python a breeze. Its simplicity, speed, and performance make it an excellent choice for developers looking to create high-performance web applications. The framework's ability to automatically generate documentation and validate input and output data using Pydantic models is a big plus. The framework's async capabilities make it ideal for handling multiple requests simultaneously, leading to fast response times and minimal downtime.

In this article, we covered some of the main features and benefits of using FastAPI. We explored how to define API endpoints, handle request parameters and bodies, manage responses and errors, and use Pydantic models for data validation. We also discussed how FastAPI integrates with other technologies such as OpenAPI, Docker, and SQLAlchemy.

Overall, FastAPI is a great choice for developers who want to build high-performance and scalable APIs in Python without sacrificing ease of use and readability. Its growing community, excellent documentation, and compatibility with many popular Python libraries and tools make it a top contender in the Python web development ecosystem.
