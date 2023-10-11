
# BotaniBuddy BackEnd

BotaniBuddy is a collaborative project created by a group of students from Northcoders. This phone application empowers users to effortlessly identify plants by simply taking a picture and receive an accurate identification in return. In addition to plant identification, the application allows users to create a digital garden, where they can keep track of the plants they've identified and receive personalized daily tasks.

The FrontEnd can be found [here](https://github.com/AndreiThira/BotaniBuddy-FE).

## Table of Contents
1. [Technologies Used](#TechUsed)
2. [Deployment](#Deployment)
3. [Usage Guide](#Installation)
4. [API Documentation](#APIDocs)

***

### Technologies Used <a name="TechUsed"></a>
- **Node.js:** A JavaScript runtime for building server-side applications.
- **Express:** A web application framework for Node.js, used to create the backend server.
- **MongoDB:** A NoSQL database used for storing plant and user data.
- **Mongoose:** An elegant MongoDB object modeling tool for Node.js.
- **Axios:** A promise-based HTTP client for making requests to external services.
- **Bcrypt:** A library for securely hashing and salting passwords.
- **CORS:** A middleware for enabling Cross-Origin Resource Sharing.
- **Dayjs:** A minimalistic JavaScript library for parsing and formatting dates.
- **Dotenv:** A zero-dependency module for loading environment variables.
- **Express Mongo Sanitize:** Middleware for sanitizing user-supplied data against NoSQL query injection.
- **JSON Web Token (JWT):** A compact, URL-safe means of representing claims to be transferred between two parties.
- **Multer:** A middleware for handling multipart/form-data, used for handling plant images.
- **Jest:** A widely-used JavaScript testing framework for ensuring the reliability and correctness of the codebase.
- **Jest-Extended:** A library of custom matchers for Jest that provide useful additional matchers for your tests.
- **Supertest:** A library for testing HTTP requests/responses, used for testing the API.
- **fs:** The Node.js File System module for handling file-related operations.

***

### Deployment <a name="Deployment"></a>
**Cyclic for API Hosting**    
We have deployed the RESTful API using [Cyclic](https://www.cyclic.sh/), a powerful platform for hosting web applications. This ensures that our API is highly available and scales effortlessly to meet user demand. You can access our API [here](https://tame-blue-horse-tutu.cyclic.cloud/).

**Database Instance with MongoDB Atlas**  
For our database needs, we rely on [MongoDB Atlas](https://www.elephantsql.com/), a managed NoSQL database service. This hosted database instance ensures data durability, reliability, scalability as well as easy acessibility.

***

### Usage Guide <a name="Installation"></a>
While it's possible to run the Plant Identification and Garden Assistant locally, we recommend using the hosted API for a hassle-free experience. Setting up a local environment with MongoDB and Mongoose can be challenging, and we want to ensure a smooth experience for our users. If you'd like to explore the hosted API, please follow these steps:

1. **Visit the Hosted API:** Access the Plant Identification and Garden Assistant at [API Link]((https://tame-blue-horse-tutu.cyclic.cloud/register).

2. **Sign Up:** Create an account to get started with your digital garden and plant identification.

3. **Upload Plant Photos:** Take pictures of plants and let our image recognition technology identify them for you.

4. **Manage Your Garden:** Add identified plants to your digital garden and receive daily gardening tasks.

***

### API Documentation <a name="APIDocs"></a>
- **Description:** Serves an array of all topics.
- **Example Response:**

#### `POST /api/register`
- **Description:** Allows user to register an account using a unique username and a password.
- **Example Input:**
  ```json
  {"username": "Bob", "password": "password"}
  ```
- **Example Response:**
  
#### `POST /api/login`

#### `POST /api/users/user_id/add_by_search`

#### `POST /api/users/user_id/identify_plants_image`

#### `GET /api/users/user_id/plants`

#### `GET /api/users/user_id/plants/plant_id`

#### `GET /api/users/user_id/tasks`

#### `PATCH /api/users/user_id/tasks/plant_id`


```json
{
  "topics": [
    {
      "slug": "coding",
      "description": "Code is love, code is life"
    },
    {
      "slug": "football",
      "description": "FOOTIE!"
    },
    {
      "slug": "cooking",
      "description": "Hey good looking, what you got cooking?"
    }
  ]
}
```

#### `GET /api/articles`

- **Description:** Serves an array of all articles.
- **Example Response:**
```json
{
  "articles": [
    {
      "title": "Seafood substitutions are increasing",
      "topic": "cooking",
      "author": "weegembump",
      "body": "Text from the article..",
      "created_at": "2018-05-30T15:59:13.341Z",
      "votes": 0,
      "comment_count": 6
    }
  ]
}
```

#### `GET /api/articles/:article_id`

- **Description:** Serves the article with the corresponding `article_id`.
- **Example Response:**

```json
{
  "article": [
    {
      "article_id": 3,
      "title": "Eight pug gifs that remind me of mitch",
      "topic": "mitch",
      "author": "icellusedkars",
      "body": "some gifs",
      "created_at": "2020-11-03T09:12:00.000Z",
      "votes": 0,
      "article_img_url": "https://images.pexels.com/photos/158651/news-newsletter-newspaper-information-158651.jpeg?w=700&h=700"
    }
  ]
}
```

#### `GET /api/articles/:article_id/comments`

- **Description:** Serves all comments for the corresponding `article_id`, sorted by most recent.
- **Example Response:**

```json
{
  "comments": [
    {
      "body": "This morning, I showered for nine minutes.",
      "votes": 16,
      "author": "butter_bridge",
      "article_id": 1,
      "created_at": "2020-12-03T09:12:00.000Z",
      "comment_id": 12
    }
  ]
}
```

#### `POST /api/articles/:article_id/comments`

- **Description:** Allows the client to post a comment to a specific article, then serves the new comment.
- **Example Input:**

```json
{
  "body": "This morning, I showered for nine minutes.",
  "user": "butter_bridge"
}
```
- **Example Output:**

```json
{
  "comment": [
    {
      "body": "This morning, I showered for nine minutes.",
      "votes": 16,
      "author": "butter_bridge",
      "article_id": 1,
      "created_at": "2020-12-03T09:12:00.000Z",
      "comment_id": 12
    }
  ]
}
```

#### `PATCH /api/articles/:article_id`

- **Description:** Allows the client to update votes by a certain value.
- **Example Input:**

```json
{
  "inc_votes": 12
}
```
- **Example Output:**
```json
{
  "article": [
    {
      "article_id": 3,
      "title": "Eight pug gifs that remind me of mitch",
      "topic": "mitch",
      "author": "icellusedkars",
      "body": "some gifs",
      "created_at": "2020-11-03T09:12:00.000Z",
      "votes": 12,
      "article_img_url": "https://images.pexels.com/photos/158651/news-newsletter-newspaper-information-158651.jpeg?w=700&h=700"
    }
  ]
}
```
