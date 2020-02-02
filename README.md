# Petsit

![Petsit](https://user-images.githubusercontent.com/52801554/69431232-9b6a0380-0d37-11ea-8007-d48c551b3475.png)

---

## App Description
This is an app used for having someone take care of and for taking care of pets. There will be multiple kinds of pets you can select for use in the features. You can register as a user and volunteer to take care of pets through requests. You can also register pets to you user and make requests for people to take care of your pet. On the main page there are all the requests filtered by date. There are buttons on the main page that filter the results by pet. Under the filter buttons there is a make request button where you can make a request for pet sitting, dog walking, fish feeding, whatever. 

---

## User Stories

- **404** - As a user I want to see a nice 404 page when I go to a page that doesn’t exist so that I know it was my fault.
- **homepage** - As a user I want to be able to view all the information for the service 
- **login** - As a user I want to be able to log in on the web page so that I can get back to my account
- **logout** - As a user I want to be able to log out from the web page so that I can make sure no one will access my account
- **signup** - As a user I want to be able to sign up to use the features of the website
- **pet** - As a user I want to be able to see the pets registered to my account, change their information, and delete their information if needed 
- **request** - As a user I want to be able to make requests for my pets and delete the requests if needed
- **user** - As a user I want to be able to see and edit the information for my account 

---

## Models 

User Model 

```javascript

{
    email: {Type: String, required: true},
    password: {Type: String, required: true},
    pictureUrl: {Type: String},
    username: {Type: String, required: true},
    age: {Type: Number, min: 18, required: true},
    description: {Type: String},
    location: {Type: String},
    requests: {Type: Schema.Types.ObjectId, ref: 'Request}
    pets: {Type: Schema.Types.ObjectId, ref: 'Pet'},
}

```

Pet Model

```javascript

{
    name: {Type: String, required: true},
    age: {Type: Number},
    petPictureUrl: {Type: String},
    description: {Type: String},
    petType: {Type: String, enum: ['Dog','Cat','Bird','Fish','Rabbit','Reptile']},
    request: {Type: Schema.Types.ObjectId, ref: 'Request'},
    petOwner: {Type: Schema.Types.ObjectId, ref: 'User}
    visible: {Type: Boolean, value: true}
}

```

Request Model 

```javascript

{
    creator: {Type: Schema.Types.ObjectId, ref: 'User'},
    title: {Type: String, required: true},
    description: {Type: String, required: true},
    pet: {Type: Schema.Types.ObjectId, ref: 'Pet'},
    {
    timestamps: {
        createdAt: 'created_at',
        updatedAt: 'updated_at'
    },
}

``` 

---


## Routes 

| **Method** | **Route**                          | **Description**                                              | Request  - Body                                          |
| ---------- | ---------------------------------- | ------------------------------------------------------------ | -------------------------------------------------------- |
| `get`  | `/auth/me` | check if i'm logged |
| `post` | `/auth/login` | login |
| `post` | `/auth/signup` | signup |
| `post` | `/auth/logut` | logout |
| `get`  | `/auth/private` | private route for test |
| `GET`      | `/`                           | Renders `login` form view.                                   |                                                          |
| `GET`      | `/home`                           | Renders homepage                                   |                                                          |
| `PUT`      | `/user/:id/edit`            | User edit profile page |
| `DELETE`      | `/user/:id/delete`            | User edit profile page |
| `GET`      | `/user/:id`               | User page                  |                                                          |
| `GET`      | `/pet/:id`               | Pet page                  |                                                          |
| `POST`     | `/pet/add`              | Add a new pet                                 |
| `DELETE`   | `/pet/:id/delete` | Delete one pet |                                                          |
| `GET`      | `/request`               | Create a request                  |                                                          |
| `GET`      | `/request/:id`               | Request page                  |                                                          |
| `POST`     | `/request/add`              | Create a new request                                 |
| `DELETE`   | `/request/:id/delete` | Private route. Deletes the existing request from the current user. |                                                          |


---

## Login & Signup

this is the following `body` for the `login` and `signup` request;

```json
{
  "username": "demo",
  "password": "demo"
}
```
