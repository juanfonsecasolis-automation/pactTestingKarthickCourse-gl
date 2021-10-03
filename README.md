# pactTestingKarthickCourse-gl
Linux version adapted from Karthick's code provided on https://gorillalogic.udemy.com/course/api-testing-with-restsharp-and-specflow-in-csharp/ by Juan Fonseca-Solis 2021.

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

As declared in the ConsumerPactTest.cs, the testing checks that the API returns an employee as follows:
```
_mockProviderService
                .Given("Employee Details for Id '1'")
                .UponReceiving("A GET request to retrieve the employee details")
                .With(new ProviderServiceRequest
                {

                    Method = HttpVerb.Get,
                    Path = "/employee/1",
                    Headers = new Dictionary<string, object>
                    {
                        { "Accept", "application/json" }
                    }


                })
                .WillRespondWith(new ProviderServiceResponse
                {
                    Status = 200,
                    Headers = new Dictionary<string, object>
                    {
                        { "Content-Type", "application/json; charset=utf-8" }
                    },
                    Body = new //NOTE: Note the case sensitivity here, the body will be serialised as per the casing defined
                    {
                        id = 1,
                        employeeName = "Karthik",
                        email = "karthik@techgeek.co.in",
                        city = "Auckland"
                    }
                });
```