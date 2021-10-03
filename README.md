# pactTestingKarthickCourse-gl
Linux version of Karthick's code provided on https://gorillalogic.udemy.com/course/api-testing-with-restsharp-and-specflow-in-csharp/

## Employee API 
* Run the API: `cd EmployeeAPI/;dotnet run`
* Request:`https://localhost:5001/api/employee/1`
* Response: `{"id":1,"employeeName":"Karthik","email":"karthik@techgeek.co.in","city":"Auckland"}`

## Pact testing
Execute on the root folder the command `dotnet build` to create files "service_consumer-employeelist.json" (the contract) and "employeelist_mock_service.log" (logs) in the /tmp directory. Then, execute `dotnet test`, the result should be something like this:

```
Iniciando la ejecución de pruebas, espere...
1 archivos de prueba en total coincidieron con el patrón especificado.
INFO  WEBrick 1.3.1
INFO  ruby 2.2.2 (2015-04-13) [x86_64-linux]
INFO  WEBrick::HTTPServer#start: pid=71687 port=9224

Correctas! - Con error:     0, Superado:     2, Omitido:     0, Total:     2, Duración: 472 ms -
```
