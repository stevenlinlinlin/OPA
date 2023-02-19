# Open Policy Agent 
We use Open Policy Agent to implement RBAC.
## reference
select from CNCF sandbox project (https://www.cncf.io/projects/)
## Introduction
documentation: https://www.openpolicyagent.org/docs/latest/

## The steps : 
## 1. 在終端機上下載OPA

```
brew install opa
```

## 2. 下載上面的四個RBAC的code，先執行command:
```
opa test -v *.rego
```
* 檢測規則是否是符合邏輯的

## 3. 若檢查all pass後
```
opa run --server
```

## 4. 另外開啟三個終端機分頁代表不同的位址

## 5. 再不同的分頁中依序輸入下列指令

（a)
```
curl -X PUT http://localhost:8181/v1/data/rbac/authz/acl --data-binary @data.json
```
* 輸入data到server

 (b)
```
curl -X PUT http://localhost:8181/v1/policies/rbac.authz --data-binary @rbac.authz.rego
```
* 把我們訂定的規則輸入到server

 (c)
 ```
 curl -X POST http://localhost:8181/v1/data/rbac/authz/allow --data-binary @input.json
```
* 測試我們的input得到他是否可以得到許可

* 以 true/false代表

## 6. 可以在data.json中可以任意更改所需要的授權等級
