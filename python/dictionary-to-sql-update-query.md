# Dictionary to sql update query

This requires using [psycopg2](https://github.com/psycopg/psycopg2)

```python
import psycopg2

# Initialize your datbase connection
# Get the cursor and connection

# Dictionary that matches the database table
table = 'users'
user = {
    'id': 1,
    'firstname': 'John',
    'middlename': 'Jacob',
    'lastname': 'Smith',
    'email': 'johnsmith@gmail.com',
    'gender': 'male',
    'age': 42
}

# Get the value of and remove the id. We only want to update the user values
record_id = user.pop('id')

# >>> print(record_id)
# 1
# 
# >>> print(user)
# {'firstname': 'John', 'middlename': 'Jacob', 'lastname': 'Smith', 'email': 'johnsmith@gmail.com', 'gender': 'male', 'age': 42}

# Convert the values of the user dictionary into a list
values = list(user.values())

# >>> print(values)
# ['John', 'Jacob', 'Smith', 'johnsmith@gmail.com', 'male', 42]

# Append the id to the end of the values (see notes below)
values.append(record_id)

# >>> print(values)
# ['John', 'Jacob', 'Smith', 'johnsmith@gmail.com', 'male', 42, 1]

# Generate the set portion of the update query
setters = ', '.join(list(map(lambda column: f'{column} = %s', [*user])))

# >>> print(setters)
# firstname = %s, middlename = %s, lastname = %s, email = %s, gender = %s, age = %s

# Generate the query string
sql = f"UPDATE {table} SET {setters} WHERE id = %s;"
query = cursor.mogrify(sql, values)

# >>> print(sql)
# UPDATE users SET firstname = %s, middlename = %s, lastname = %s, email = %s, gender = %s, age = %s WHERE id = %s;
# 
# >>> print(query)
# b"UPDATE users SET firstname = 'John', middlename = 'Jacob', lastname = 'Smith', email = 'johnsmith@gmail.com', gender = 'male', age = 42 WHERE id = 1;"

# Do the database dance with mogrify
cursor.execute(query)
connection.commit()
connection.close()

# Do the database dance with just the sql and values
cursor.execute(sql, values)
connection.commit()
connection.close()
```

## Notes

The sql string is using `%s` as placeholders that are sanitized to prevent sql injection.

The `values` you pass to `mogrify` or `execute` have to match the order of the `%s` placeholders in the sql string. This is why we pop off the record id and append it to the end of the `values` list. The last `%s` in the sql string is `where id = %s`.
