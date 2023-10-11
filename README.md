
# BotaniBuddy BackEnd

BotaniBuddy is a collaborative project created by a group of students from Northcoders. This phone application empowers users to effortlessly identify plants by simply taking a picture and receive an accurate identification in return. In addition to plant identification, the application allows users to create a digital garden, where they can keep track of the plants they've identified and receive personalized daily tasks.

The FrontEnd can be found [here](https://github.com/AndreiThira/BotaniBuddy-FE).

## Table of Contents
1. [Technologies Used](#TechUsed)
2. [Deployment](#Deployment)
3. [Usage Guide](#Installation)
4. [API Documentation](#APIDocs)
5. [Acknowledgments](#Ack)

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
While it's possible to run BotaniBuddy locally, we recommend using the hosted API for a hassle-free experience. Setting up a local environment with MongoDB and Mongoose can be challenging, and we want to ensure a smooth experience for our users. If you'd like to explore the hosted API, please follow these steps:

1. **Visit the Hosted API:** Access the Plant Identification and Garden Assistant at [API Link](https://tame-blue-horse-tutu.cyclic.cloud/register).

2. **Sign Up:** Create an account to get started with your digital garden and plant identification.

3. **Upload Plant Photos:** Take pictures of plants and let our image recognition technology identify them for you.

4. **Manage Your Garden:** Add identified plants to your digital garden and receive a customised list of daily gardening tasks.

***

### API Documentation <a name="APIDocs"></a>

#### `POST /api/register`
- **Description:** Allows user to register an account using a unique username and a password.
- **Example Input:**
  ```json
  {"username": "Bob", "password": "password"}
  ```

- **Example Response:**
```json
{
  "user": {
    "user_id": "6526a0399326a52638d9a132",
    "username": "Bob",
    "password": "$2b$10$fhpv06oN.WJE.Mvbrd3nhOONkyuLbXuJzsKUopa.tATJEBT2/rUXq"
  }
}
```

#### `POST /api/login`
- **Description:** Allows user to login to an account using their registered username and password.
- **Example Input:**
```json
  {
	"user": {
		"msg": "Login succesful",
		"user_id": "6526a0399326a52638d9a132",
		"username": "Bob",
		"token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyX2lkIjoiNjUyNmEwMzk5MzI2YTUyNjM4ZDlhMTMyIiwidXNlcm5hbWUiOiJCb2IiLCJpYXQiOjE2OTcwMzA3NTUsImV4cCI6MTY5NzExNzE1NX0.DeupW-twqmbchKB_uQGFJdxXZPD-xys9PlzXTHYWVHw"
	}
}
```

#### `POST /api/users/user_id/add_by_search`
- **Description:** Allows user to add a plant to their garden by name.
- **Example Input:**
```json
{"name": "daisy"}
```

- **Example Response:**
```json
{
	"plant": {
		"tasks": {
			"toBeWateredAgain": "14-10-2023"
		},
		"_id": "6526a2fdf6a5ae8c00682b6f",
		"users": [
			"6526a0399326a52638d9a132"
		],
		"plantType": 924,
		"__v": 0
	}
}
```

#### `POST /api/users/user_id/identify_plants_image`
- **Description** Allows a user to upload a plant image for identification, returning the identified plant name and confidence rating.
- **Example Reponse:**
```json
{
  "score": 0.30212,
  "plantName": "Araucaria columnaris"
}
```

#### `GET /api/users/user_id/plants`
- **Description:** Returns all the user's owned plants.
- **Example Response:**
``` json
{
	"myPlants": [
		"6526a2fdf6a5ae8c00682b6f",
		"6526a3aaf6a5ae8c00682b75"
	]
}
```

#### `GET /api/users/user_id/plants/plant_id`
- **Description:** Returns information about a specific plant owned by the user.
- **Example Response:**
```json
{
	"myPlant": {
		"wateringPeriod": {
			"value": "3-4",
			"unit": "days"
		},
		"_id": "651425c9c8ea5f61d76f184a",
		"perenualId": 924,
		"commonName": "African daisy",
		"scientificName": "Arctotis hybrida",
		"maxHeight": "0 feet",
		"wateringFrequency": "Average",
		"sunlight": [
			"Full sun"
		],
		"pruningMonth": [
			"May",
			"June",
			"July",
			"June",
			"July",
			"August",
			"March",
			"April",
			"May"
		],
		"maintenance": "Moderate",
		"poisonousToHumans": false,
		"poisonousToPets": false,
		"rareLevel": 0,
		"indoor": false,
		"description": "The African daisy (Arctotis hybrida) is an amazing specimen of flower, with stunning white and orange petals that spread wide and proud. Perfect for both the garden bed and vase, the African daisy will bring a touch of sunshine to any spot. Along with its showy flowers, this species produces a sweet, strong scent that will linger in the air. Easy to grow and maintain, African daisies are an ideal choice for any garden. A true symbol of beauty and life, the African daisy is an amazing way to brighten any space.",
		"__v": 0
	}
}
```

#### `GET /api/users/user_id/tasks`
- **Description:** Returns a list of the user's tasks that need to be completed today. Returns empty array if nothing needs completing today.
- **Example Response:**
  ```{
	"tasks": []
}

#### `PATCH /api/users/user_id/tasks/plant_id`
- **Description:** Returns the updated plant with the next watering date.
- **Example Response:**
```json 
{
	"nextWaterDate": {
		"tasks": {
			"toBeWateredAgain": "14-10-2023"
		},
		"_id": "6526a2fdf6a5ae8c00682b6f",
		"users": [
			"6526a0399326a52638d9a132"
		],
		"plantType": 924,
		"__v": 0
	}
}
```
***
### Acknowledgments <a name="Ack"></a>
- [PlantNet](https://plantnet.org/en/) for the image identification API
- [Perenual](https://perenual.com/docs/api) for the plant care information API.


