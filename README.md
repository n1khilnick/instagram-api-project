# Instagran API Project

## Built With
* `Java 17`
* `Maven 4.0.0`
* `MySql Ver 8.0.32`
* `Spring Boot 3.0.5`
* `IntelliJ IDEA 2023.1 (Community Edition)`

## Data Flow


### 1. Model:
* It consists of **Admin** ,**User**, **Post** ,**AuthToken** and other entity classes along with their data members and member functions
* Used **_@Table_** and **_@Entity_** annotations inside the entity class.
* Used Lombok to reduce boilerplate code for pojo class.By using Lombok annotations like _**@Data,**_ **@_NoArgsConstructor_**, **_@AllArgsConstructor_** getters and setters for those object generate automatically.
* Used **_@OneToOne_**, **_@OneToMany_** and **_@ManyToOne_** annotation to perform one to one mapping between Employee and Address.

### 2. Controller:
* It consists of  **AdminController** ,**UserController**, **PostController** and **CommentController** classes in which used the annotations like **@RestController** to annotate the class as Controller.
* Used annotation **_@GetMapping_** , **_@PostMapping_** , **_@PutMapping_** , **_@DeleteMapping_** to map the HTTP web requests to the specific handler methods.

<br>

### API Reference:
<br>

>Admin's API References
<br>

* Set Blue Tick on User Profile:
```*.sh-session
  http://localhost:8080/admin/user/{id}/{blueTick}
```
<br>

>User's API References
<br>

* Add User:
```*.sh-session
  http://localhost:8080/user
```

*  User SigUp:
```*.sh-session
  http://localhost:8080/user/signup
```

* User SignIn:
```*.sh-session
  http://localhost:8080/user/signin
```

* User SignOut:
```*.sh-session
  http://localhost:8080/user/sign-out
```

* User Can Like:
```*.sh-session
  http://localhost:8080/user/like
```

* User can follow other user:
```*.sh-session
  http://localhost:8080/user/follow/{myId}/{otherId}
```

<br>

>Post's API References:

<br>

* Create Post via User's authentication:
```*.sh-session
  http://localhost:8080/post/email/{userEmail}/token/{token}
```

* Get all Posts:
```*.sh-session
  http://localhost:8080/post/
```

* Can see post likes:
```*.sh-session
  http://localhost:8080/post/{postId}/likeCount
```

<br>

>Comments's API References:

<br>

* Can comment on post:
```*.sh-session
  http://localhost:8080/comment
```

<br>

### 3. Service:
* It consists of  **AdminService**, **UserService**, **TokenService** and **PostService** classes in which provide some business functionalities of every handler methods.
* Used _**@Service**_ annotation to indicate that a class belongs to the service layer.
* Used **_@Transactional_** annotation to separate transaction management code from the code for business logic on the update and delete methods.

### 4. Repository:
* It consists of  **AdminDao**, **UserDao** ,**TokenDao** and **PostDao** interface classes that extends CrudRepository which is interface for generic inbuilt CRUD operations on a repository for a specific type. Usually represent the database access layer in an application.
* Used **Iterable** for User and Post to manage the data of entity classes by performing CRUD operations.
* Used _**@Repository**_ annotation is used to indicate that the class provides the mechanism for storage, retrieval, search, update and delete operation on objects.
* Used _**@Modifying**_ annotation wrote named parameters query using @Query annotation to insert, update, or delete an entity.

## Data Structure Used
Used `Iterable<T>` to store objects for entity classes.

## Project Summary
* In this project I performed CRUD operation like add,get,delete and update.<br/>
* The aim of this project to create instagram-api application uses authentication tokens to secure user data and ensure that only authenticated users can access certain features.
* Used interface CrudRepository class for generic CRUD inbuilt operations like save,saveAll,updateById, etc.
* Used our own custom finder methods and wrote operations using custom queries.
* Implemented authentication for User SignUp, SignIn and to create Post and manage their profile information
* It allows users to sign up, sign in, and manage their profile information. Users can also create and view posts.
