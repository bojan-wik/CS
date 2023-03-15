#java

Na przykładzie pliku `employees.json`
```json
{
	"firstName": "John",
	"lastName": "Kennedy",
	"address": [
		{
			"street": "abc",
			"city": "Hyderabad",
			"state": "TL"
		},
		{
			"street": "xyz",
			"city": "Chennai",
			"state": "TN"
		}
	]
}
```

## Read JSON from a file
(korzystając z biblioteki JSON.simple)

```java
public void readDataFromJsonFile() {  
    JSONParser jsonParser = new JSONParser();  
  
    try (FileReader fileReader = new FileReader("employees.json")) {  
  
        Object javaObject = jsonParser.parse(fileReader);  
        JSONObject employeesJsonObject = (JSONObject)javaObject;  
  
        String firstName = employeesJsonObject.get("firstName").toString(); // John  
        String lastName = employeesJsonObject.get("lastName").toString(); // Kennedy  
  
        JSONArray addressArray = (JSONArray)employeesJsonObject.get("address");  
        JSONObject firstAddressJsonObject = (JSONObject)addressArray.get(0);  
        JSONObject secondAddressJsonObject = (JSONObject)addressArray.get(1);  
  
        String firstAddressStreet = firstAddressJsonObject.get("street")
	        .toString(); // abc  
        String secondAddressCity = secondAddressJsonObject.get("city")
	        .toString(); // Chennai  
    } 
    catch (IOException | ParseException e) {  
        e.printStackTrace();  
    }  
}
```

## Convert Map to JSONObject
(korzystając dodatkowo z biblioteki Jackson)

```java
Map<String, String> requestBody = Map.of(  
        "firstName": "John",  
        "lastName": "Kennedy");

public void convertMapToJsonObject() {
	JSONParser jsonParser = new JSONParser();

	try {
		String requestBodyAsString = new ObjectMapper().writeValueAsString(requestBody);
		JSONObject array = (JSONObject) jsonParser.parse(requestBodyAsString);
	}
	catch (JsonProcessingException | ParseException exception) {  
	    exception.printStackTrace();  
	}
}
```
> https://www.javatpoint.com/how-to-convert-string-to-json-object-in-java

## Źródła:
- https://www.youtube.com/watch?v=U-5VHRvOFpA
- https://howtodoinjava.com/java/library/json-simple-read-write-json-examples/#4-read-json-from-a-file