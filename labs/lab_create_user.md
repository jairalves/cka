## Create a new user called john. Grant him access to the cluster. John should have permission to create, list, get, update and delete pods in the development namespace .

Generate csr

openssl genrsa -out john.key 2048
openssl req -new -key john.key -out john.csr -subj "/CN=john"

# Criacao de role e role binding de forma imperativa

$ kubectl create role developer --resource=pods --verb=create,list,get,update,delete --namespace=development

$ kubectl create rolebinding developer-role-binding --role=developer --user=john --namespace=development

# Teste de forma imperativa

$ kubectl auth can-i update pods --as=john --namespace=development

