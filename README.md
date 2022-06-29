```yaml
1     #%RAML 1.0
2     title: D-Car
3     description: Domain API providing static and dynamic car data
4     version: v1
5     mediaType: application/json
6     uses:   
7       types: exchange_modules/.../f-ccsappdatatypes.raml
8     types:
9       Car:  types.Car
10      Vin:  types.Vin
11      Vins: types.Vins  
12    documentation: 
13    - title: Data Definition Table 
14      content: !include docs/dtdCar.md
15
16    /cars:
17      description: All cars
18      get:
19        description: Get VINs of all cars
20        responses:
21          200:
22            body:
23              type: Vins
24
25      /{vin}:
26        description: A specific car identified by its VIN
27        uriParameters:
28          vin:
29          type: Vin
30        put:
31          description: Update a car
32          body:
33            type: Car
34          responses:
35            404:
36              body:
37                properties:
38                  error: string
39              example:
40                error: "No Vehicle found for the given VIN" 
```

```yaml
1     #%RAML 1.0

3     title: D-Car
4     description: Domain API providing static and dynamic car data
5     version: v1
6     mediaType: application/json
7     uses:   
8       types: exchange_modules/.../f-ccsappdatatypes.raml
9     types:
10      Car:  types.Car
11      Vin:  types.Vin
12      Vins: types.Vins  
13    documentation: 
14    - title: Data Definition Table 
15      content: !include docs/dtdCar.md

17    /cars:
18      ...
19
20      /{vin}:
21         ...
```

