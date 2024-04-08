
# install the crd
>>  kubectl apply -f installation/crd.yaml

# install istio setup
>> kubectl apply -f installation/setup.yaml
## components in setup



# create secret for kiali
>> kubectl apply -f installation/kiali-secret.yaml

# Locally port forward of kiali Dashboard
>>  kubectl port-forward service/kiali  8080:20001 -n istio-system >/dev/null &


## We need to set labels to namespace after then it will be monitor by service mesh
  labels:
    istio-injection: enabled
>> kubectl apply -f installation/istio-injection.yaml


##########################################################


# Launching a application
>> kubectl apply -f Application/application1.yaml

# For accessing the product page , we can attach ingress
>> kubectl apply -f Application/ingress1.yaml
