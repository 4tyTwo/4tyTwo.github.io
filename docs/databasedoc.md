---
layout: page
title: "Database Documentation"
permalink: /databasedoc/
---
# Tables

### <a name="clients"></a>clients

| Name | Type | Default | Nullable | References |
| -- | -- | -- | -- | ---------- |
| id <span style="background: #ddd; padding: 2px; font-size: 0.75rem; color: black">PK</span> | <a href="https://www.postgresql.org/docs/9.5/datatype-numeric.html">integer</a> |  | False | 
first_name | <a href="https://www.postgresql.org/docs/9.5/datatype-character.html">text</a> |  | False | 
last_name | <a href="https://www.postgresql.org/docs/9.5/datatype-character.html">text</a> | 'Andersson'::text | False | 
joined_at | <a href="https://www.postgresql.org/docs/9.5/datatype-datetime.html">timestamp without time zone</a> |  | True | 
contact_info | [contact_info](#contact_info) | ROW('EMAIL'::contact_method, 'default@email.com'::text) | False | 
adress | <a href="https://www.postgresql.org/docs/9.5/datatype-character.html">text</a> |  | True |  |

### <a name="pets"></a>pets

| Name | Type | Default | Nullable | References |
| -- | -- | -- | -- | ---------- |
| id <span style="background: #ddd; padding: 2px; font-size: 0.75rem; color: black">PK</span> | <a href="https://www.postgresql.org/docs/9.5/datatype-numeric.html">integer</a> |  | False | 
owner | <a href="https://www.postgresql.org/docs/9.5/datatype-numeric.html">integer</a> |  | True | [clients.id](#clients)
type | [pet_type](#pet_type) |  | False | 
breed | <a href="https://www.postgresql.org/docs/9.5/datatype-character.html">text</a> |  | False | 
name | <a href="https://www.postgresql.org/docs/9.5/datatype-character.html">text</a> |  | True | 
born_at | <a href="https://www.postgresql.org/docs/9.5/datatype-datetime.html">date</a> |  | False | 
bought_at | <a href="https://www.postgresql.org/docs/9.5/datatype-datetime.html">date</a> |  | True |  |

### <a name="contracts"></a>contracts

| Name | Type | Default | Nullable | References |
| -- | -- | -- | -- | ---------- |
| id <span style="background: #ddd; padding: 2px; font-size: 0.75rem; color: black">PK</span> | <a href="https://www.postgresql.org/docs/9.5/datatype-numeric.html">integer</a> |  | False | 
owner | <a href="https://www.postgresql.org/docs/9.5/datatype-numeric.html">integer</a> |  | True | [clients.id](#clients)
subject | <a href="https://www.postgresql.org/docs/9.5/datatype-numeric.html">integer</a> |  | True | [pets.id](#pets)
signed_at | <a href="https://www.postgresql.org/docs/9.5/datatype-datetime.html">timestamp without time zone</a> |  | False | 
cost | [currency_amount](#currency_amount) |  | False | 
valid_until | <a href="https://www.postgresql.org/docs/9.5/datatype-datetime.html">timestamp without time zone</a> |  | True |  |

# Types

### <a name="contact_method" > </a>contact_method


 - EMAIL
 - PHONE
 - MAIL

### <a name="currency" > </a>currency


 - USD
 - EUR
 - SEK

### <a name="pet_type" > </a>pet_type


 - CAT
 - DOG
 - PARROT
 - HAMSTER
 - FISH

### <a name="contact_info" > </a>contact_info

| column name | type | position | required? |
| ----------- | ---- | -------- | --------- |
| method | [contact_method](#contact_method) | 1 | false
adress | <a href="https://www.postgresql.org/docs/9.5/datatype-character.html">text</a> | 2 | false |

### <a name="currency_amount" > </a>currency_amount

| column name | type | position | required? |
| ----------- | ---- | -------- | --------- |
| currency | [currency](#currency) | 1 | false
amount | <a href="https://www.postgresql.org/docs/9.5/datatype-numeric.html">integer</a> | 2 | false |
