Create a folder in the root of the project and name it "data" and create the "db.json" file inside it

Insert the JSON data
```
{
    "posts": [
        {"title": "Post 1", "body": "Lorem Ipsum...", "author": "Tom", "id": 1},
        {"title": "Post 2", "body": "Lorem Ipsum...", "author": "Andrew", "id": 2},
        {"title": "Post 3", "body": "Lorem Ipsum...", "author": "Tobey", "id": 3}
    ]
}
```

Open another terminal and run the command
```
npx json-server --watch data/db.json --port 8000
```

If you see the following message, Type "y" and hit enter
```
Need to install the following packages:
  json-server@1.0.0-beta.3
```

You will see the endpoint:
http://localhost:8000/posts

| Endpoints   |         |       |
| :---------------- | :------: | :---- |
| /posts      |   GET   | Fetch all posts |
| /posts/{id} |   GET   | Fetch a single post |
| /posts      |  POST   | Add a new post |
| /posts/{id} |  DELETE | Delete a post |