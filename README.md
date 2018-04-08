# modbus-restapi

Small Flask application that exposes Modbus TCP devices with REST API. Using to perform some testing routines.

### Available functions

1. Read Modbus registers: `POST` on (`/modbus-explorer/api/tcp/read'`):
````
{
    ip: [string],
    port: [integer],
    slave_id: [integer],
    type_prefix: [integer],
    start_address: [integer],
    count: [integer]
}
````

2. Write Modbus registers: `POST` on (`/modbus-explorer/api/tcp/post'`):
````
{
    ip: [string],
    port: [integer],
    slave_id: [integer],
    type_prefix: [integer],
    start_address: [integer],
    data: [array of integers]
}
````


### Usage examples

Read first 10 coils:
```
curl -i -H "Content-Type: application/json" -X POST -d '{"ip":"localhost", "port":"5020", "slave_id": 1, "type_prefix": 1, "start_address": 1, "count": 10}' http://localhost:5000/modbus-explorer/api/tcp/read
```

Write some coils:
```
curl -i -H "Content-Type: application/json" -X POST -d '{"ip":"localhost", "port":"5020", "slave_id": 0, "type_prefix": 1, "start_address": 10, "data": [1, 0, 0, 1]}' http://localhost:5000/modbus-explorer/api/tcp/write
```

