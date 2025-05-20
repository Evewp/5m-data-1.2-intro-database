# Assignment

## Brief

Create an ERD for each of the following case study question.

## Instructions

Paste the answer as DBML in the answer code section below each question.

### Question 1

Construct an ERD for a social media company whose database includes information about users, their followers, and the posts that they make. Users can follow multiple users and create multiple posts.

Each entity has the following attributes:

- User: id, username, email, created_at
- Post: id, title, body, user_id, status, created_at
- Follows: following_user_id, followed_user_id, created_at

Answer:

DBML:
```
Table users {
  id int [pk, increment]
  username varchar
  email varchar
  created_at datetime
}

Table posts {
  id int [pk, increment]
  title varchar
  body text [note: 'Content of the post']
  user_id int
  status boolean
  created_at datetime
}

Table follows {
  following_user_id int
  followed_user_id int
  created_at datetime
}

Ref: posts.user_id > users.id // one user to many posts

Ref: follows.following_user_id > users.id // one user to many following users

Ref: follows.followed_user_id > users.id // one user to many followed users
```

### Question 2

Construct an ERD for a company that sells books online. The company has a website where customers can browse available books and add them to their shopping carts. Each cart can contain multiple books.

There are 4 entities, think of what attributes each entity should have.

- Customer
- Book
- Cart
- CartItem

Answer:

DBML:
```
Table customers {
  id int [pk, increment]
  name varchar
  address varchar
  phone varchar
  email varchar
  created_at datetime
}

Table books {
  id int [pk, increment]
  title varchar
  author varchar
  price decimal
  isbn varchar
  created_at datetime
}

Table carts {
  id int [pk, increment]
  customer_id int
  book_id int
  created_at datetime
}

Table cart_items {
  id int [pk, increment]
  cart_id int
  book_id int
  quantity int
  created_at datetime
}

Ref: carts.customer_id > customers.id // one customer to many carts

Ref: cart_items.cart_id > carts.id // one cart to many cart items

Ref: cart_items.book_id > books.id // one book to many cart items
```

## Submission

- Submit the URL of the GitHub Repository that contains your work to NTU black board.
- Should you reference the work of your classmate(s) or online resources, give them credit by adding either the name of your classmate or URL.
