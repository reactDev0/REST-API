# Rest Api

A RESTful API for Article

See the API's [documentation](DOCS.md).

## Commands

After you generate your project, these commands are available in `package.json`.

```bash
npm run lint # lint using ESLint
npm run dev # run the API in development mode
npm run prod # run the API in production mode
npm run docs # generate API docs
```

## Playing locally

First, you will need to install and run [MongoDB](https://www.mongodb.com/) in another terminal instance.

```bash
$ mongod
```

Then, run the server in development mode.

```bash
$ npm run dev
Express server listening on http://localhost:4000/, in development mode
```

If you choose to generate the authentication API, you can start to play with it.
> Note that creating and authenticating users needs a master key (which is defined in the `.env` file)

Create a user (sign up):
```bash
curl -X POST http://localhost:4000/users -i -d "email=test@example.com&password=123456&access_token=MASTER_KEY_HERE"
```

It will return something like:
```bash
HTTP/1.1 201 Created
...
{
  "id": "57d8160eabfa186c7887a8d3",
  "name": "test",
  "picture":"https://gravatar.com/avatar/55502f40dc8b7c769880b10874abc9d0?d=identicon",
  "email": "test@example.com",
  "createdAt": "2018-07-23 09:35:04.193"
}
```

Authenticate the user (sign in):
```bash
curl -X POST http://0.0.0.0:4000/auth -i -u test@example.com:123456 -d "access_token=MASTER_KEY_HERE"
```

It will return something like:
```bash
HTTP/1.1 201 Created
...
{
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9",
  "user": {
    "id": "57d8160eabfa186c7887a8d3",
    "name": "test",
    "picture": "https://gravatar.com/avatar/55502f40dc8b7c769880b10874abc9d0?d=identicon",
    "email": "test@example.com",
    "createdAt":"2018-07-23T14:35:04.193Z"
  }
}
```

Now you can use the `eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9` token (it's usually greater than this) to call user protected APIs. For example, you can create a new `article` API using `yo rest:api` and make the `POST /articles` endpoint only accessible to authenticated users. Then, to create a new article you must pass the `access_token` parameter.
```bash
curl -X POST http://0.0.0.0:4000/articles -i -d "title=Awesome Article&autor=smith&content=Yeah Baby&access_token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9"
```

It will return something like:
```bash
HTTP/1.1 201 Created
...
{
  "id": "57d819bfabfa186c7887a8d6",
  "title": "Awesome Article",
  "autor": "smith",
  "content": "Yeah Baby",
  "createdAt": "2018-07-23T14:37:43.768Z",
  "updatedAt":"2018-07-23T14:37:43.768Z"
}
```
