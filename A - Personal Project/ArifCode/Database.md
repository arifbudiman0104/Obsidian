# Database
## Post
|  Table Name  |      Type      |
|:------------:|:--------------:|
|      id      |      int       |
| category_id  |   foreignId    |
|    title     |     string     |
|     slug     | string, unique |
|   excerpt    |     string     |
|   content    |      text      |
| is_published | default false  |
| is_featured  | default false  |
| published_at |   timestamp    | 
|  thumbnail   |     string     |
|  timestamps  |   timestamps   |
## Post Category
| Table Name |      Type      |
|:----------:|:--------------:|
|     id     |      int       |
|   title    |     string     |
| timestamps |   timestamps   |
## Portofolio

## User
|    Table Name    |      Type      |
|:----------------:|:--------------:|
|        id        |      int       |
|       name       |     string     |
|      email       | string, unique |
| emal_verified_at |   timestamp    |
|     password     |     string     |
|     is_admin     | default false  |
|    timestamps    |   timestamps   | 
## Guestbook
