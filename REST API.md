# REST API
#api 

## Co to jest?

**API** - Application Programming Interface. 
To kontrakt, który umożliwia komunikację pomiędzy jednym serwisem/aplikacją a drugim serwisem/aplikacją

## API contract

| Request    | ->  | Response |
| ---------- | --- | -------- |
| - endpoint (URL) |     | - status code         |
| - headers  |     | - headers         |
| - body           |     | - body         |

### różnica pomiędzy metodami PUT i PATCH
Obie służą do update'u ale:
- PUT wymaga, żeby body requestu był kompletne tj. to co zmieniamy + reszta
- PATCH wystarczy, że w body requestu będzie tylko to co zmieniamy

## POISED - API testing strategy
Parameters (request body)
Output (response body, status code, headers)
Interopability
Security
Errors handling
Data

## Postman

### kopiowanie requesta z devtoolsów do Postmana

1. W devtools: namierzam request który chcę skopiować -> prawy klik -> Copy as cURL
![[Pasted image 20220908140630.png]]
3. W Postman: File -> Import -> Raw text -> wklejam skopiowany request