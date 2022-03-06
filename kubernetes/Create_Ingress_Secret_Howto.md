Get name of Ingress Subdomain and name of Ingress secret
$ibmcloud ks cluster get --cluster mycluster-eu-de-1-bx2.4x16 | grep Ingress

Ingress Subdomain:              mycluster-eu-de-1-702185-93c663195df361da1284682bc210eb37-0000.eu-de.containers.appdomain.cloud   

Ingress Secret:                 mycluster-eu-de-1-702185-93c663195df361da1284682bc210eb37-0000 


Get Secret CRN of Ingress Secret in namespace default
$ ibmcloud ks ingress secret get -c mycluster-eu-de-1-bx2.4x16 --name mycluster-eu-de-1-702185-93c663195df361da1284682bc210eb37-0000 --namespace default

CRN:            crn:v1:bluemix:public:cloudcerts:eu-de:a/1151e19f6a5246d7bd1d048986d54636:9701ffaa-96b9-4295-ab25-6f4b73cf61b7:certificate:98d34baaaa944ed59567ad9ce83e0fc1  


Create Ingress Secret in namespace prod:
$ ibmcloud ks ingress secret create --cluster mycluster-eu-de-1-bx2.4x16 --cert-crn crn:v1:bluemix:public:cloudcerts:eu-de:a/1151e19f6a5246d7bd1d048986d54636:9701ffaa-96b9-4295-ab25-6f4b73cf61b7:certificate:98d34baaaa944ed59567ad9ce83e0fc1 --name mycluster-eu-de-1-702185-93c663195df361da1284682bc210eb37-0000 --namespace node-red

create secret
$ kubectl apply -f community-ingress-resource.yaml -n node-red

