# SQL-advanced
CREATE TABLE users
(
    id       bigserial PRIMARY KEY,
    name     VARCHAR(30),
    email    VARCHAR(30),
    password VARCHAR(30)
);
CREATE TABLE orders
(
    id           bigserial PRIMARY KEY,
    product_name VARCHAR(30),
    price        INTEGER,
    user_id      BIGINT,
    CONSTRAINT ref1 FOREIGN KEY (user_id)
        REFERENCES users (id)
);

INSERT INTO users (name, email, password)
VALUES ('John', 'john@example.com', 'mypassword'),
       ('Karl', 'karl@example.com', 'secpassword'),
       ('Sarah', 'sarah@example.com', 'thirdpassword'),
       ('Ben', 'ben@example.com', 'fourthpassword'),
       ('Nill', 'nill@example.com', 'fifthpassword'),
       ('Roby', 'roby@example.com', 'sixthpassword');

UPDATE users
SET name='Jane'
WHERE id = 1;

DELETE
FROM users
WHERE email = 'john@example.com';

INSERT INTO orders (product_name, price, user_id)
VALUES ('ball', 30, 1),
       ('water', 80, 1),
       ('eraser', 100, 2),
       ('apples', 65, 2),
       ('wine', 90, 3),
       ('smartphone', 7000, 3),
       ('icecream', 70, 4),
       ('book', 300, 4),
       ('pen', 20, 5),
       ('sccissors', 70, 5),
       ('plate', 230, 6),
       ('canoe', 700, 6);


SELECT * FROM users
FULL JOIN orders o on users.id = o.user_id
WHERE name='Jane'

SELECT * FROM users
FULL JOIN orders o on users.id = o.user_id
WHERE price>100;
