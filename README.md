# Open Policy Agent 
use Open Policy Agent to implement RBAC.

## Environment
- Macbook M1 Pro
- terminal command
## Reference
CNCF sandbox project (https://www.cncf.io/projects/)
## Introduction
documentation: https://www.openpolicyagent.org/docs/latest/

## Installation
use brew to install opa
```
brew install opa
```

## Test policy
- check the rego file without error
```
opa test -v *.rego
```


## Run OPA
```
opa run --server
```

## Build data and policy to my OPA server

### data
data.json is the data file
```
curl -X PUT http://localhost:8181/v1/data/rbac/authz/acl --data-binary @data.json
```

### policy 
*.rego is the policy file
```
curl -X PUT http://localhost:8181/v1/policies/rbac.authz --data-binary @rbac.authz.rego
```

## Query to OPA server
 ```
 curl -X POST http://localhost:8181/v1/data/rbac/authz/allow --data-binary @input.json
```
- output (true means allow, false means deny)
```
{"result":true}
```

