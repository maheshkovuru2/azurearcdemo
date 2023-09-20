# azurearcdemo
Azure ARC Demo

**Installing Kubernetes on GCP:**

![image](https://github.com/maheshkovuru2/azurearcdemo/assets/145518364/3fef4bb2-9ea3-486c-a302-ee97235b7bc1)

![image](https://github.com/maheshkovuru2/azurearcdemo/assets/145518364/83649aaf-740d-4da5-ba86-1e4013c38b89)

![image](https://github.com/maheshkovuru2/azurearcdemo/assets/145518364/7f056fcc-1410-4610-96d5-deee7fcc9663)

![image](https://github.com/maheshkovuru2/azurearcdemo/assets/145518364/e4aa0097-d542-4714-b4fb-df1ece59e93c)

![image](https://github.com/maheshkovuru2/azurearcdemo/assets/145518364/b8b7e8fa-5f21-46f6-a424-6afcfaa0cd3d)

![image](https://github.com/maheshkovuru2/azurearcdemo/assets/145518364/f5533cfe-5cf7-4c8b-8558-7ad228eed79b)

![image](https://github.com/maheshkovuru2/azurearcdemo/assets/145518364/0c53931f-7429-4539-b49b-53f742cac0d0)

![image](https://github.com/maheshkovuru2/azurearcdemo/assets/145518364/1005a407-2492-46c8-8a50-0ccd8aa67c7d)

![image](https://github.com/maheshkovuru2/azurearcdemo/assets/145518364/90d79f2d-6a52-4160-943e-94d6c8de6db5)

![image](https://github.com/maheshkovuru2/azurearcdemo/assets/145518364/ed2727cc-eab0-417f-b017-b350dbfbee87)

![image](https://github.com/maheshkovuru2/azurearcdemo/assets/145518364/a817c554-d635-4a6b-a53b-bed590d70631)

![image](https://github.com/maheshkovuru2/azurearcdemo/assets/145518364/c9d91fc7-e0ad-429e-b2c9-8936a676f411)

![image](https://github.com/maheshkovuru2/azurearcdemo/assets/145518364/0d818ff7-e291-482a-893a-fb80d99a1bc6)

![image](https://github.com/maheshkovuru2/azurearcdemo/assets/145518364/e3f258ef-9c1d-4957-b2af-1f75c55ad8d0)

![image](https://github.com/maheshkovuru2/azurearcdemo/assets/145518364/a4c82eec-8b5e-4992-bfae-262e669df8df)

![image](https://github.com/maheshkovuru2/azurearcdemo/assets/145518364/03cf5940-85e4-4fe8-aa76-a8e42cf25772)

![image](https://github.com/maheshkovuru2/azurearcdemo/assets/145518364/33d398bc-431e-4294-8027-6dc6ef588f81)

![image](https://github.com/maheshkovuru2/azurearcdemo/assets/145518364/1a698443-ec33-4a83-8d1e-a54f2a00109c)

![image](https://github.com/maheshkovuru2/azurearcdemo/assets/145518364/f52b7338-cd98-403f-8e64-4bd179f895ba)

![image](https://github.com/maheshkovuru2/azurearcdemo/assets/145518364/3c52a957-408d-4d3d-a373-fa2b51a5f56c)

Run below commands to create service account token to connect to Names SPace and workloads in Azure Arc for the Kubernetes cluster.

**kubectl create serviceaccount arc-user -n default**

**kubectl create clusterrolebinding arc-user-binding --clusterrole cluster-admin --serviceaccount default:arc-user**

**kubectl apply -f - <<EOF
apiVersion: v1
kind: Secret
metadata:
  name: arc-user-secret
  annotations:
    kubernetes.io/service-account.name: arc-user
type: kubernetes.io/service-account-token
EOF**

**TOKEN=$(kubectl get secret arc-user-secret -o jsonpath='{$.data.token}' | base64 -d | sed 's/$/\n/g')**

**echo $TOKEN**

NOTE: You can also create a bash script with the above scripts and run it after the cluster is created in GCP/Azure/AWS.

