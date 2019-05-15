# Python switch/case statement

Not really but close enough?

```python
switch_months = {
	1: 'January',
   	2: 'February',
   	3: 'March',
   	4: 'April',
   	5: 'May',
   	6: 'June',
   	7: 'July',
   	8: 'August',
   	9: 'September',
   	10: 'October',
   	11: 'November',
   	12: 'December'
}

print(switch_months.get(2, 'Invalid month'))
>> February

print(switch_months.get(13, 'Invalid month'))
>> 'Invalid month'
```

Another example.

```python
switch_status = {
    'good': 'Success',
    'bad': 'Failed',
    'retry: 'Try Again'
}

print(switch_status.get('good', 'Unknown status'))
>> 'Success'

print(switch_months.get('none', 'Unknown status'))
>> 'Unknown status'
```

Putting it into a method:

```python
def result(status):
	switch_status = {
	    'good': 'Success',
	    'bad': 'Failed',
	    'retry: 'Try Again'
	}

	return switch_status.get(status, 'Unknown status')
	
print(result('good'))
>> 'Success'

print(result('none'))
>> 'Unknown status'
```

Calling methods from the switched key:

```python
def say_hello(*args):
    print('hello')

def say_something(*args):
    print(f'Saying something: {args}')

def default(*args):
	print('Not sure what to do')
	
switch_commands = {
    'hello': say_hello,
    'something': say_something
}

>>> switch_commands.get('hello', default)()
hello

>>> switch_commands.get('something', default)('stuff and things')
Something with words: stuff and things

>>> switch_commands.get('what', default)('please print me')
Not sure what to do
```