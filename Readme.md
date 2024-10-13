# Mission 3

## Part 0-2

### ScrinCast
> https://drive.google.com/file/d/1r728e3oVs9f-AWUG0_mrV2YW9bd6obqE/view?usp=sharing
- Task 1
> https://buildship.app/remix/12556d2d-5622-4914-a31a-d2a57713c49d
- Task 2
> https://buildship.app/remix/5a029b0a-4ec0-4656-bc8c-b72cd60ed7f1

## Part3
- Получить список юзернеймов пользователей
  ```
  select * from users
  ```
- Получить кол-во отправленных сообщений каждым пользователем:
    username - number of sent messages
```
SELECT users.id,users.username, COUNT(messages.id) AS message_count
FROM  users
LEFT JOIN messages ON users.id = messages.from
GROUP BY users.id, users.username;
```
-  Получить пользователя с самым большим кол-вом полученных сообщений и само количество
    username - number of received messages
```
SELECT users.id,users.username, COUNT(messages.id) AS message_count
FROM users
LEFT JOIN messages ON users.id = messages.from
GROUP BY users.id, users.username
ORDER by message_count DESC Limit 1;
```
-  Получить среднее кол-во сообщений, отправленное каждым пользователем
 ```
SELECT AVG (message_count) AS average_messages FROM
(
SELECT users.id, COUNT (messages.id) AS message_count FROM users
LEFT JOIN messages ON users.id = messages.from    
GROUP BY users.id
) 
AS user_message_counts;
```
