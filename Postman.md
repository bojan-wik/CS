#api 

Response-body przypomina obiekt JavaScript, ale to tak naprawdę String. Żeby przekonwertować response-body do obiektu JS musimy użyć:
```
pm.response.json();
```