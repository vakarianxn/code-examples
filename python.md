**Task**:  
Create a for loop that iterates over a list of string values with at least 10 items related to your work and skips
some specific values (at least two, but not all).

**Solution**:  
```cards_released_today = ['1089_003', '27_089', '27_013', '13_044', '1089_002', '20_064', '1089_004', '1089_005',
                        '27_016', '27_011']

for x in cards_released_today:
    if '27_' in x:
        continue
    else:
        print(x)"```

