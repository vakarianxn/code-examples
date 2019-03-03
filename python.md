**Task 1**:  
Create a for loop that iterates over a list of string values with at least 10 items related to your work and skips
some specific values (at least two, but not all).

**Solution**:  
``` 
cards_released_today = ['1089_003', '27_089', '27_013', '13_044', '1089_002', '20_064', '1089_004', 
			'1089_005', '27_016', '27_011']

for x in cards_released_today:
    if '27_' in x:
        continue
    else:
        print(x)" ```


**Task 2**:  
Use "while" statement to print the numbers starting from 1 till 256. If current number equals 128 exit the while
statement (i. e. values 128 - 256 should not be printed).

**Solution**:  
``` 
x = 1

while x < 256:
    if x == 128:
        break

    print(x)
    x += 1 ```


**Task 3**:  
Create a function that gets user input and adds "not " at the beginning then prints the result in
the next line. In case user input has "not " at the beginning, no need to add anything, print as is.
When "exit" is printed, exit the program.

**Solution**:  
``` 
while True:
    user_input = input('Please say something: ')
    if 'not ' in user_input:
        print(user_input)
    elif 'exit' in user_input:
        break
    else:
        print('not ' + user_input)```


**Task 4**: 
Create a function that gets two integer values and prints "true" in case both numbers end with the same number and
"false" otherwise. For example, 7 and 17 should result in "true", 6 and 17 - false.

**Solution**:  
```
def get_numbers(num, num2):
    num = int(input('Enter the first number: '))
    num2 = int(input('Enter the second number: '))

    print((num2 % 10) == (num % 10))

get_numbers()```


**Task 5**: 
Create functions that calculate area of a circle and perimeter of a rectangle. Import those functions and renaming
both in file "task5". Then print each function by calling them with some parameters in "task5".

**Solution**:  
```
import func_circarea as calc_circle_area
import func_rectperimeter as calc_rectangle_perimeter

print(calc_circle_area.circle_area(5))
print(calc_rectangle_perimeter.rectper(5, 9))```



**Task 6**: 
Write multiplication table to a file task6.txt in the following format
https://us.123rf.com/450wm/extracoin/extracoin1708/extracoin170800030/84812574-multiplication-table-on-white-background.jpg?ver=6
In case program is executed multiple times append new multiplication table to the file content, do not override it.

**Solution**:  
```
with open('multitable.txt', 'a') as text:
    for i in range(1, 11):
        for j in range(1, 6):
            output = (f"{j} x {i} = {i * j}\t")
            text.write(output)
        text.write('\n')
    text.write('\n')
    for i in range(1, 11):
        for j in range(6, 11):
            output = (f"{j} x {i} = {i * j}\t")
            text.write(output)
        text.write('\n')
    text.write('\n\n')
    text.close()```



**Task 7**: 
Read some long text file (for example some book in txt format) and print total count of lines, words and letters in
that book.

**Solution**:  
```
line_count = 0

with open('harry_potter_and_the_prisoner_of_azkaban.txt', 'r') as text:
    for line in text:
        if '\n' in line:
            line_count += 1
        else:
            continue

print(line_count)```


**Task 8**:
Read some long text file (for example some book in txt format) and write its content to file task9.txt.
Skip each line that contains any of the words "he", "she", "it", "they". 


**Solution**:  
```
a = ["he", "she", "it", "they"]

with open('task9.txt', 'a') as dst_text:
    with open('harry_potter_and_the_prisoner_of_azkaban.txt', 'r') as src_text:
        for line in src_text:
            if(set(a).intersection(set(line.split()))):
                print(line)```


**Task 9**:
First check if directory task10 exists and if not create it. After that in directory task10 create file
50_installations.txt and add 50 random installations in a format we used during previous practical task.
Also create file 50_users.txt and add 50 random users there in a format we used during practical task.

**Solution**:  
```
import uuid
import os

if not os.path.exists('task10'):
    os.makedirs('task10')

with open(r"C:\Users\Flo\PycharmProjects\Homework_3\src\task10\50_installations.txt", 'a') as fifty_inst:
    for i in range(50):
        fifty_inst.write(f"{i + 1}.\n")
        fifty_inst.write(f"POST /call/v1/installations\n")

        installation_id = str(uuid.uuid4())
        fifty_inst.write(f"""{{
        "id": {installation_id},
        "additional_fields": {{}},
        "device_type": "random_device",
        "device_class": "random_name",
        "device_model": "random_name",
        "os_ver": "14.04",
        "locale_id": "US-NE",
        "time_zone": "PST",
        "carrier": "default_carrier",
        "lang": "en",
        "source_client": 1,
        "source_client_version": "4.7.0",
        "ifa": "2F871E6F-D681-4AD5-8138-C2BE34007357"
    }}\n""")

        fifty_inst.write(f"POST /call/v1/users\n")

        user_id = str(uuid.uuid4())
        fifty_inst.write(f"""{{
        "installation_id": {installation_id},
            "user": {{
                "id": {user_id},
                "username": null,
                "name": null,
                "email": null,
                "photo_file_id": null,
                "additional_fields": {{}},
                "source_client": 1,
                "source_client_version": "4.7.0"
            }}
    }}\n""")
fifty_inst.close()```