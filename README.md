# Kubernetes Course Labs

Labs and exercises to help you learn Kubernetes.

Live at https://kubernetes.courselabs.co.

# Notes

## /setup

## /labs/nodes

[Docs](labs/nodes/README.md)

    1  kubectl get nodes
    2  kubectl get pods
    3  kubectl get services
    4  kubectl describe nodes
    5  kubectl get --help
    6  git remote add fork https://github.com/ggvelev/kubernetes
    7  git status
    8  git add README.md
    9  git status
    10  git commit -m "Add personal notes"
    11  git push fork
    12  kubectl nodes
    13  kubectl get nodes
    14  kubectl get node docker-desktop -o json
    15  kubectl get node docker-desktop
    16  kubectl get node -o jsonpath='{.status.capacity.cpu}'
    17  kubectl get nodes -o jsonpath='{.status.capacity.cpu}'
    18  kubectl get node docker-desktop -o jsonpath='{.status.capacity.cpu}'
    19  kubectl labels
    20  kubectl label
    21  kubectl get node docker-desktop labels
    22  kubectl get node docker-desktop label
    23  kubectl labels --help
    24  kubectl label --help
    25  kubectl get node labels
    26  kubectl get node label
    27* kubectl get nodes
    28  kubectl get node docker-desktop -o yaml
    29  kubectl get nodes --help
    30  kubectl get nodes --show-labels
    31  kubectl get nodes --label-columns kubernetes.io/arch,kubernetes.io/os
    32  kubectl get node <your-node> -o go-template=$'{{index .metadata.labels "kubernetes.io/arch"}}'
    33  kubectl get node docker-desktop -o go-template=$'{{index .metadata.labels "kubernetes.io/arch"}}'

## /labs/pods

[Docs](labs/pods/README.md)

    1  cd labs/pods/
    2  cat specs/whoami-pod.yaml
    3  kubectl apply -f specs/whoami-pod.yaml
    4  kube get pods
    5  kubectl get pods
    6  kubectl describe pod whoami
    7  kubectl get pods --wide
    8  kubectl get pods wide
    9  kubectl get pods -o wide
    10  kubectl get po -o wide
    11  kubectl logs whoami
    12  curl localhost:80
    13  kubectl exec -it whoami -- sh
    14  kubectl exec -it whoami wsh
    15  kubectl exec -it whoami sh
    16  kubectl exec -it whoami ls
    17  kubectl exec -it whoami -- ls
    18  kubectl get pods
    19  kubectl logs whoami
    20  kubectl apply -f specs/sleep-pod.yaml
    21  kubectl logs sleep-pod
    22  kubectl get pods
    23  kubectl logs sleep
    24  kubectl exec -it sleep sh
    25  kubectl get pods
    26  kubectl describe --help
    27  kubectl describe pod sleep
    28  docker ps
    29  docker containers
    30  docker container ls
    31  kubectl exec -it sleep hostname
    32  kubectl exec -it sleep whoami
    33  kubectl exec -it sleep -- whoami
    34  kubectl exec -it sleep ping kubernetes
    35  kubectl get pods -o wide whoami
    36  kubectl exec sleep curl -s 10.1.0.6
    37  kubectl exec sleep -- curl -s '10.1.0.6'
    38  kubectl get pods -o wide whoami
    39  kubectl apply -f specs/bad-sleep-pod.yaml
    40  kubectl get pods
    41  kubectl get pods
    42  kubectl get pods
    43  kubectl get pods
    44  kubectl get pods
    45  kubectl get pods
    46  kubectl get pods
    47  kubectl get pod bad-sleep-pod --watch
    48  kubectl get pod bad-sleep --watch
    49  kubectl delete pod bad-sleep
    50  kubectl get pods

## /labs/services

[Docs](labs/services/README.md)

    1  kubectl pods
    2  kubectl get pods
    3  kubectl delete pod sleep
    4  kubectl delete pod whoami
    5  cd labs/services
    6  kubectl apply -f specs/pods
    7  kubectl get services
    8  kubectl get pods -o wide --show-labels
    9  kubectl exec sleep -- nslookup whoami
    10  kubectl apply -f specs/services/whoami-clusterip.yaml
    11  kubectl get service whoami
    12  kubectl describe svc whoami
    13  kubectl exec sleep -- nslookup whoami
    14  kubectl exec sleep -- curl -s http://whoami
    15  kubectl apply -f specs/services/whoami-clusterip.yaml
    16  kubectl exec sleep -- curl -s http://whoami
    17  kubectl get pods
    18  kubectl stop sleep
    19  kubectl pod stop sleep
    20  kubectl pod --help
    21  kubectl pods --help
    22  kubectl stop pod --help
    23  kubectl
    24  kubectl delete sleep
    25  kubectl delete pod sleep
    26  kubectl delete pod whoami
    27  kubectl get pods
    28  kubectl get pods -a
    29  kubectl get pods --all
    30  kubectl get pods
    31  kubectl get pods --help
    32  kubectl get pods -A
    33  kubectl get pods
    34  kubectl apply -f specs/pods/whoami.yaml
    35  kubectl apply -f specs/pods/sleep.yaml
    36  kubectl apply -f specs/pods/sleep.yaml -f specs/pods/whoami.yaml
    37  kubectl get pods -o wide
    38  kubectl get pods -o wide --show-labels
    39  kubectl exec sleep -- nslookup whoami
    40  kubectl apply -f specs/services/whoami-clusterip.yaml
    41  kubectl get service
    42  kubectl get services
    43  kubectl get svc
    44  kubectl describe svc whoami
    45  kubectl exec sleep -- nslookup whoami
    46  kubectl exec sleep -- curl whoami
    47  kubectl apply -f specs/services/whoami-loadbalancer.yaml -f specs/services/whoami-nodeport.yaml
    48  kube get svc -l app=whoami
    49  kubectl get svc -l app=whoami
    50  curl localhost:8010
    51  curl localhost:8080
    52  kubectl exec sleep -- curl whoami-lb
    53  kubectl exec sleep -- curl -s whoami-lb:8080
    54  kubectl exec sleep -- curl -s whoami-np:8010
    55  curl localhost:30010
    56  kubectl apply -f specs/services/whoami-lb-zeropodsmatching.yaml
    57  kubectl get svc whoami-lb
    58  kubectl describe svc whoami-lb
    59  curl localhost:8080
    60  kubectl apply -f specs/services/whoami-lb-zeropodsmatching.yaml
    61  curl localhost:8080
    62  kubectl apply -f specs/services/whoami-lb-zeropodsmatching.yaml
    63  curl localhost:8080
    64  kubectl endpoint
    65  kubectl endpoints
    66  kubectl get endpoints
    67  kubectl apply -f specs/services/whoami-lb-zeropodsmatching.yaml
    68  kubectl apply -f specs/services/whoami-lb-multiplematching.yaml
    69  kubectl get endpoints
    70  curl localhost:8080
    71  kubectl describe service whoami
    72  kubectl apply -f specs/pods/whoami.yaml
    73  kubectl describe service whoami
    74  kubectl apply -f specs/services/whoami-lb-multiplematching.yaml
    75  curl localhost:8080
    76  kubectl get endpoints
    77  kubectl apply -f specs/services/whoami-lb-multiplematching.yaml
    78  kubectl get endpoints
    79  kubectl apply -f specs/services/whoami-lb-multiplematching.yaml
    80  kubectl apply -f specs/services/whoami-lb-zeropodsmatching.yaml
    81  kubectl get endpoints
    82  kubectl get endpoints
    83  curl localhost:8080
    84  curl localhost
    85  kubectl get endpoints
    86  kubectl apply -f specs/services/whoami-lb-zeropodsmatching.yaml
    87  kubectl get pods
    88  kubectl get pods -o wide
    89  kubectl get pods -o wide --show-labels
    90  kubectl get svc
    91  kubectl apply -f specs/services/whoami-lb-zeropodsmatching.yaml
    92  kubectl get svc
    93  kubectl apply -f specs/services/whoami-lb-multiplematching.yaml
    94  kubectl get svc
    95  curl locahost:8080
    96  curl locahost:8081
    97  curl locahost:8082
    98  kubectl get po
    99  kubectl get svc
    100  kubectl get svc -o wide
    101  kubectl get endpoints
    102  kubectl get endpoints -o wide
    103  kubectl exec sleep -- nslookup whoami-lb-zeromatch
    104  kubectl exec sleep -- curl -s -m 5 whoami-lb-zeromatch
    105  kubectl exec sleep -- curl -s -m 5 whoami-lb-multimatch
    106  kubectl exec sleep -- curl -s -m 5 whoami-lb
    107  kubectl exec sleep -- curl -s -m 5 whoami-lb:8081
    108  kubectl apply -f specs/pods/whoami-2.yaml
    109  kubectl apply -f specs/pods/whoami-2.yaml
    110  kubectl get endpo
    111  kubectl get endpoints
    112  kubectl get svc
    113  kubectl get svc -w o
    114  kubectl get svc --show-labels
    115  kubectl get svc --show-labels
    116  kubectl apply --help
    117  kubectl apply -k specs/services
    118* kubectl apply -k specs/services
    119  kubectl apply -f specs/services/whoami-*
    120  kubectl apply -f specs/services/whoami-lb-zeropodsmatching.yaml -f specs/services/whoami-lb-multiplematching.yaml -f specs/services/whoami-loadbalancer.yaml
    121  kubectl get endpoints
    122  curl localhost:8080
    123  curl localhost:8081
    124  curl localhost:8082
    125  curl localhost:8080
    126  curl localhost:8080
    127  curl localhost:8080
    128  curl localhost:8080
    129  curl localhost:8080
    130  curl localhost:8080
    131  curl localhost:8080
    132  curl localhost:8080
    133  curl localhost:8080
    134  curl localhost:8080
    135  curl localhost:8080
    136  kubectl get po -o wide -l app=whoami
    137  kubectl exec sleep -- curl -v http://whoami
    138  kubectl exec sleep -- curl -v http://whoami
    139  kubectl exec sleep -- curl -v http://whoami
    140  kubectl exec sleep -- curl -v http://whoami
    141  kubectl exec sleep -- curl -v http://whoami
    142  kubectl exec sleep -- curl -v http://whoami
    143  kubectl exec sleep -- curl -v http://whoami
    144  kubectl exec sleep -- curl -v http://whoami
    145  kubectl exec sleep -- curl -v http://whoami
    146  kubectl get po,svc
    147  kubectl get po,svc -o wide
    148  curl localhost:8081
    149  curl localhost:8082
    150  curl localhost:8080
    151  kubectl get po,svc -o wide
    152  alias k=kubectl
    153  k get po
    154  k get svc
    155  k get po,svc,endpoints -o wide

## /labs/deployments

[Docs](labs/deployments/README.md)

    1  cd labs/deployments/
    2  kubectl get po --show-labels
    3  kubectl delete pod,svc -l kubernetes.courselabs.co=services
    4  kubectl get po,svc,endpoints
    5  alias k=kubectl
    6  k get po,svc
    7  k apply -f specs/deployments/whoami-v1.yaml
    8  k get po,svc
    9  k get deployment
    10  k get deployments
    11  k get po,svc
    12  k delete pod whoami
    13  k get po,svc -o wide
    14  k delete pod -l app=whoami
    15  k get po,svc
    16  k get deploy
    17  k get deploy,pods,svc
    18  k get deploy,pods,svc,endpoints
    19  k get deploy -o wide
    20  k describe deploy whoami
    21  k get svc
    22  k scale deploy whoami --replicas 3
    23  k get svc
    24  k describe deploy whoami
    25  k get po
    26* k apply -f specs/deployments/whoami-v1-scale.yaml ku
    27  k get po
    28  k get svc
    29  k get deploy
    30  k get deploy -o wide
    31  k describe deploy whoami
    32  k logs -l app=whoami
    33  k exec deploy/whoami -- hostname
    34  k get pods -o wide -l app=whoami
    35  k get pods -o wide -l app=whoami --show-labels
    36  k apply -f specs/services/
    37  k get endpoints
    38  k get endpoints -o wide
    39  k get services
    40  curl localhost:8080
    41  curl localhost:8010
    42  curl localhost:30010
    43  k get po
    44  k get deploy
    45  k get po -l app=whoami
    46  k apply -f specs/deployments/whoami-v2.yaml
    47  k get deploy
    48  k get endpoints
    49  curl localhost:8080
    50  curl localhost:8080
    51  curl localhost:8080
    52  curl localhost:8080
    53  curl localhost:8080
    54  k rollout history deploy/whoami
    55  k rollout undo deploy/whoami
    56  k get po -l app=whoami
    57  curl localhost:8080
    58  k get deploy
    59  k apply -f solution/whoami-deployments.yaml
    60  k get po
    61  k delete deploy whoami
    62  k get po
    63  g ket svc
    64  k get svc
    65  curl localhost:8080
    66  curl localhost:8010
    67  curl localhost:30010
    68  curl localhost:31008
    69  k get po -l
    70  k get po --show-labels -o wide
    71  k get deploy
    72  k apply -f solution/whoami-service-v
    73  k apply -f solution/whoami-service-v1.yaml
    74  k get deploy
    75  k get po
    76  k get endppints
    77  k get endpoints
    78  curl localhost:8020
    79  curl localhost:8010
    80  curl localhost:30020
    81  curl localhost:8020
    82  k get svc
    83  k describe deploy whoami
    84  k get deploy
    85  k describe deploy whoami-lab-v1
    86  k describe deploy whoami-lab-v2
    87  k apply -f solution/whoami-service-v1.yaml
    88  k apply -f solution/whoami-service-v2.yaml
    89  curl localhost:8080
    90  curl localhost:8020
    91  curl localhost:30010
    92  curl localhost:30020
    93  k apply -f solution/whoami-service-v1.yaml
    94  curl localhost:30020
    95  curl localhost:8020
    96  k get deploy
    97  k get deploy --show-labels
    98  k get deploy deployments
    99  k get deploy -l deployments
    100  k get deploy -o wide
    101  k apply -f solution/whoami-deployments.yaml
    102  k rollout
    103  k rollout history
    104  k rollout history deploy/whoami
    105  k rollout history deploy/whoami-v1
    106  k rollout history deploy/whoami-lab
    107  k rollout history deploy/whoami-lab-v1
    108  k rollout history deploy/whoami-lab-v2
    109  k rollout
    110  k rollout restart deploy/whoami-lab-v1
    111  k get deploy whoami-lab-v1
    112  k get deploy whoami-lab-v1 -o wide
    113  k get deploy whoami-lab-v2 -o wide
    114  k apply -f solution/whoami-service-v1.yaml
    115  k get deploy whoami-lab-v1 -o wide
    116  k get po
    117  k get svc
    118  k get endppoints
    119  k get endpoints
    120  k rollback
    121  k roll
    122  k get replicaset
    123  k rollout histor
    124  k rollout history
    125  k rollout history whoami-lab
    126  k rollout history whoami-lab-v1
    127  k rollout history whoami
    128  k rollout history whoami-lab-v1
    129  k rollout history whoami-lab-v2
    130  k rollout history whoami-deployments
    131  k deploy
    132  k get deploy
    133  k rollout history whoami-lab-v1
    134  k rollout
    135  k get deployments
    136  k rollout status whoami-lab-v1
    137  k rollout status deploy/whoami-lab-v1
    138  k rollout status deployment/whoami-lab-v1
    139  k rollout status deployment/whoami-lab-v2
    140  k rollout history deployment/whoami-lab-v2
    141  k rollout history deployment/whoami-lab-v1
    142  k deploy delete -l app=whoami-lab
    143  k delete deploy -l app=whoami-lab
    144  k delete deployment -l app=whoami-lab
    145  k delete -ll app=whoami-lab
    146  k delete -l app=whoami-lab
    147  k delete deployment -l app=whoami-lab
    148  k deploy
    149  k get deploy
    150  k delete deployment -l kubernetes.courselabs.co: deployments
    151  k delete deployment -l kubernetes.courselabs.co=deployments
    152  k get deploy,svc,po,endpoint
    153  k get deploy,svc,po,endpoints
    154  k get deploy,svc,po,endpoints
    155  k get deploy
    156  k get svc
    157  k get svc -o wide
    158  k delete svc -l app=whoami-lab
    159  k delete service -l app=whoami-lab
    160  k delete service -l app=whoami
    161  k svc
    162  k get svc
    163  k delete svc whoami-lab-lb
    164  k delete svc whoami-lab-np
    165  k get svc
    166  k get po
    167  k get endpoint
    168  k get deploy
    169  k get endpoints
    170  k apply -f solution/whoami-deployments.yaml
    171  k get deploy
    172  k get svc
    173  k get po
    174  k get po -o w
    175  k get po -o wide
    176  k get po -o wide --show-labels
    177  k get deploy
    178  k get svc
    179  k get endpoints
    180  k apply -f solution/whoami-service-v1.yaml
    181  k get svc
    182  k get svc -o wide
    183  k apply -f solution/whoami-service-v2.yaml
    184  k get svc -o wide

## /labs/configmaps

[Docs](labs/configmaps/README.md)

    2  cd labs/configmaps/
    3  l
    4  ls
    5  kubectl run configurable --image=sixeyed/configurable:21.04 --labels='kubernetes.courselabs.co=configmaps'
    6  kubectl run configurable --image=sixeyed/configurable:21.04 --labels='kubernetes.courselabs.co=configmaps'
    7  kubectl run configurable --image=sixeyed/configurable:21.04 --labels='kubernetes.courselabs.co=configmaps'
    8  alias k=kubectl
    9  kubectl run configurable --image=sixeyed/configurable:21.04 --labels='kubernetes.courselabs.co=configmaps'
    10  kubectl wait --for=condition=Ready pod configurable
    11  kubectl port-forward pod/configurable 8080:80
    12  kube delete pod configurable
    13  kubectl delete pod configurable
    14  k pods
    15  kubectl pods
    16  kubectl pods
    17  kubectl get pods
    18  kubectl apply -f specs/configurable/
    19  kubectl exec deploy/configurable -- printenv
    20  kubectl get endpoints
    21  kubectl get svc
    22  kubectl get svc --show-labels
    23  kubectl apply -f specs/configurable/config-env/
    24  kubectl get configmaps
    25  kubectl get cfg
    26  kubectl get cfgmap
    27  kubectl get conf
    28  kubectl get cm
    29  kubectl get cm --help
    30  kubectl ge po
    31  kubectl gte po
    32  kubectl get po
    33  kubectl exec configurable -- printenv
    34  kubectl exec deploy/configurable -- printenv
    35  kubectl get pods
    36  kubectl get svc
    37  kubectl get endpoints
    38  kubectl get ep
    39  kubectl get ep -o wide
    40  kubectl get svc -o wide
    41  kubectl apply -f specs/configurable/config-json/
    42  k
    43  alias k=kubectl
    44  k get deploy
    45  kubectl get deploy
    46  kubectl exec deploy/configurable -- printenv
    47  kubectl get ep
    48  kubectl get svc -o wide
    49  kubectl exec deploy/configurable ls
    50  kubectl exec deploy/configurable -- ls config
    51  kubectl exec deploy/configurable -- cat config/override.json
    52  kubectl apply -f specs/configurable/lab/
    53  kubectl apply -f specs/configurable/lab/
    54  kubectl get po
    55  kubectl get deploy
    56  kubectl exec deploy/configurable -- ls
    57  kubectl exec deploy/configurable -- ls config
    58  kubectl exec deploy/configurable -- cat config/override.json
    59  kubectl exec deploy/configurable -- printenv
    60  kubectl apply -f specs/configurable/lab/
    61  kubectl apply -f specs/configurable/lab/
    62  kubectl exec deploy/configurable -- printenv
    63  kubectl describe cm configurable-env-lab
    64  kube deploy
    65  kubectl deploy
    66  kubectl deploy help
    67  kubectl deployment --help
    68  kubectl help
    69  kubectl restart
    70  kubectl restart --help
    71  kubectl recreate --help
    72  kubectl get deploy
    73  kubectl get deploy
    74  kubectl delete deploy/configurable
    75  kubectl apply -f specs/configurable/lab/
    76  kubectl apply -f specs/configurable/lab/
    77  kubectl exec deploy/configurable -- printenv
    78  kubectl diff -f specs/configurable/lab/configmap-env.yaml
    79  kubectl diff
    80  kubectl diff --help
    81  kubectl diff -f specs/configurable/lab/configmap-json.yaml
    82  kubectl apply -f specs/configurable/lab/
    83  kubectl apply -f specs/configurable/lab/
    84  kubectl rollout
    85  kubectl rollout restart deployment/configurable
    86  kubectl apply -f specs/configurable/lab/
    87  kubectl apply -f specs/configurable/lab/
    88  kubectl apply -f specs/configurable/lab/
    89  kubectl exec deploy/configurable cat config/override.json
    90  kubectl get svc
    91  kubectl get svc -o wide
    92  kubectl rollout restart deployment/configurable
    93  kubectl apply -f specs/configurable/lab/
    94  kubectl get svc
    95  kubectl get svc -o wide
    96  kubectl get cm-o wide
    97  kubectl get cm -o wide
    98  kubectl delete -l app=configurable
    99  kubectl delete deploy,svc,cm -l app=configurable
    100  kubectl get cm,ep,deploy,po
    101  kubectl get cm,ep,deploy,po --show-labels
    102  kubectl get cm
    103  kubectl describe cm configurable
    104  kubectl describe cm configurable-env-lab
    105  kubectl get po
    106  kubectl get svc
    107  kubectl apply -f specs/configurable/lab/deployment-lab.yaml
    108  kubectl get deploy
    109  kubectl get deploy
    110  kubectl get deploy
    111  kubectl get deploy
    112  kubectl get deploy
    113  kubectl get deploy
    114  kubectl get po
    115  kubectl get po
    116* kubectl get po -
    117  kubectl apply -f specs/configurable/lab/configmap-env.yaml
    118  kubectl get po
    119  kubectl apply -f specs/configurable/lab/configmap-json.yaml
    120  kubectl get po\
    121  kubectl get po
    122  kubectl get po
    123  kubectl logs
    124  kubectl logs deploy/configurable
    125  kubectl logs deploy/configurable
    126  kubectl apply -f specs/configurable/lab/
    127  kubectl get po
    128  kubectl logs deploy/configurable
    129  kubectl apply -f specs/configurable/lab/
    130  kubectl logs deploy/configurable
    131  kubectl get po
    132  kubectl apply -f specs/configurable/lab/
    133  kubectl get po
    134  kubectl get po --watch
    135  kubectl get svc
    136  kubectl apply -f specs/configurable/services.yaml
    137  kubectl logs deploy/configurable
    138  kubectl logs deploy/configurable
    139  kubectl logs deploy/configurable -f
    140  kubectl
    141  kubectl delete configmap,deploy,svc,pod -l kubernetes.courselabs.co=configmaps

Important: when configmap gets changed and reapplied, it is up to the specific application whether it will be needed to
restart the app pod and get the new config read.

## /labs/secrets

[Docs](labs/secrets/README.md)

    1  cd labs/secrets/
    2  kubectl users
    3  kubectl get users
    4  kubectl get user
    5  kubectl apply -f specs/configurable/
    6  kubectl get cm
    7  kubectl describe cm configurable-env
    8  kubectl describe cm configurable-override
    9  kubectl get deploy
    10  kubectl get po
    11  kubectl get svc
    12  kubectl get cm
    13  k
    14  kubectl describe cm configurable-env
    15  kubectl apply -f specs/configurable/secrets-encoded/
    16  kubectl apply -f specs/configurable/secrets-plain/
    17  kubectl apply -f specs/configurable/secrets-encoded/
    18  kubectl exec deploy/configurable -- printenv
    19  kubectl get cm
    20  kubectl get secret
    21  kubectl get secrets
    22  kubectl describe secret configurable
    23  kubectl describe secret configurable
    24  kubectl get secrets
    25  kubectl get secret configurable-env-plain -o jsonpath="{.data.Configurable__Environment}" | base64 -d
    26  kubectl get secret configurable-env-plain -o jsonpath="{.data.Configurable__Environment}"
    27  kubectl get secret configurable-env-encoded -o jsonpath="{.data.Configurable__Environment}"
    28  kubectl get secret configurable-env-encoded -o jsonpath="{.data.Configurable__Environment}" | base64 -d
    29  kubectl create secret
    30  kubectl create secret generic configurable-env-file --from-env-file secrets/configurable.env
    31  kubectl create secret generic configurable-secret --from-env-file secrets/secret.json
    32  kubectl create secret generic configurable-secret --from-file secrets/secret.json
    33  kubectl get secret
    34  kubectl describe configurable-secret
    35  kubectl describe secret configurable-secret
    36  kubectl apply -f specs/configurable/secrets-file/
    37  kubectl describe secret configurable-env-file
    38  kubectl apply -f specs/configurable/secrets-file/
    39  kubectl rollout restart deploy/configurable
    40  kubectl get svc
    41  kubectl get svc -o wide
    42  kubectl create secret generic configurable-env-file --from-env-file ./labs/secrets/secrets/configurable.env
    43  kubectl create secret generic configurable-env-file --from-env-file secrets/configurable.env
    44  kubectl exec deploy/configurable -- printenv
    45  kubectl get secret
    46  kubectl exec deploy/configurable -- ls app/secrets
    47  kubectl exec deploy/configurable -- ls /app/secrets
    48  kubectl exec deploy/configurable -- ls
    49  kubectl get secret
    50  kubectl create secret generic configurable-secret-file --from-file secrets/secret.json
    51  kubectl apply -f specs/configurable/secrets-file/
    52  kubectl get secret
    53  kubectl rollout restart deploy/configurable
    54  kubectl exec deploy/configurable -- ls
    55  kubectl exec deploy/configurable -- ls secrets
    56  kubectl exec deploy/configurable -- cat secrets/secret.json
    57  kubectl rollout restart deploy/configurable
    58  kubectl apply -f specs/configurable/secrets-file/
    59  kubectl rollout restart deploy/configurable
    60  kubectl create secret generic configurable-secret-file --from-file secrets/secret.json
    61  kubectl secret
    62  kubectl rollout restart secret configurable-secret-file
    63  kubectl rollout
    64  kubectl get deploy
    65  kubectl delete deploy configurable
    66  kubectl get po,secret,
    67  kubectl get po,secret,svc
    68  kubectl get po,secret,svc --show-labels
    69  kubectl delete secret/configurable-secret-file
    70  kubectl delete secret/configurable-secret
    71  kubectl get po,secret,svc --show-labels
    72  kubectl delete secret/configurable-env-file
    73  kubectl get po
    74  kubectl get svc
    75  kubectl apply -f solution
    76  kubectl get po,svc,secret,config
    77  kubectl get po,svc,secret,configmap
    78  kubectl apply -f solution/v2-name/
    79  kubectl get secrets -l app=configurable-lab
    80  kubectl rollout undo deploy/configurable-lab
    81  kubectl delete deployment,secret -l app=configurable-lab
    82  kubectl apply -f solution
    83  kubectl apply -f solution/v2-annotation/
    84  kubectl get secrets -l app=configurable-lab
    85  kubectl apply -f labs/secrets/solution/secret.yaml
    86  kubectl apply -f solution/secret.yaml
    87  kubectl rollout undo deploy/configurable-lab
    88  kubectl apply -f specs/configurable/secrets-update/
    89  kubectl exec deploy/configurable -- cat /app/secrets/secret.json
    90  kubectl exec deploy/configurable -- cat /app/secrets/secret.json
    91  kubectl exec deploy/configurable -- cat app/secrets/secret.json
    92  kubectl exec deploy/configurable -- 'cat app/secrets/secret.json'
    93  kubectl get deploy
    94  kubectl exec deploy/configurable -- ls
    95  kubectl exec deploy/configurable -- pwd
    96  kubectl exec deploy/configurable -- cat secrets/secret.json
    97  kubectl apply -f specs/configurable/secrets-update/v1-update/
    98  kubectl exec deploy/configurable -- cat secrets/secret.json
    99  kubectl exec deploy/configurable -- cat secrets/secret.json
    100  kubectl exec deploy/configurable -- cat secrets/secret.json
    101  kubectl exec deploy/configurable -- cat secrets/secret.json
    102  kubectl exec deploy/configurable -- cat secrets/secret.json --watch
    103  kubectl exec deploy/configurable -- cat secrets/secret.json
    104  kubectl exec deploy/configurable -- cat secrets/secret.json
    105  kubectl rollout restart deploy/configurable
    106  kubectl delete all,cm,secret -l kubernetes.courselabs.co=secrets
    107  history

## /labs/persistentvolumes

[Docs](labs/persistentvolumes/README.md)

    1  cd labs/persistentvolumes/
    2  ls
    3  kubectl get po,svc
    4  kubectl apply -f specs/pi/
    5  [Docs](labs/configmaps/README.md)
    6  kubectl exec deploy/pi-proxy -- ls /tmp
    7  kubectl exec deploy/pi-proxy -- ls tmp
    8  kubectl exec deploy/pi-proxy -- ls tmp/
    9  kubectl exec deploy/pi-proxy -- ls tmp/0/
    10  kubectl exec deploy/pi-proxy -- ls tmp/0/a8
    11  kubectl exec deploy/pi-proxy -- ls tmp/0/a8/80813d968191d3997de41f64ec0aca80
    12  kubectl exec deploy/pi-proxy -- cat tmp/0/a8/80813d968191d3997de41f64ec0aca80
    13  kubectl get deploy
    14  kubectl exec deploy/pi-proxy -- kill 1
    15  kubectl get po -l app=pi-proxy
    16  kubectl exec deploy/pi-proxy -- ls tmp
    17  kubectl exec deploy/pi-proxy -- ls tmp
    18  kubectl apply -f specs/caching-proxy-emptydir/
    19  kubectl exec deploy/pi-proxy -- ls tmp
    20  kubectl exec deploy/pi-proxy -- ls tmp
    21  kubectl exec deploy/pi-proxy -- kill 1
    22  kubectl get pods
    23  kubectl exec deploy/pi-proxy --ls tmp
    24  kubectl exec deploy/pi-proxy -- ls tmp
    25  kubectl exec deploy/pi-proxy -- top
    26  kubectl exec deploy/pi-proxy -- ps
    27  kubectl exec deploy/pi-proxy -- kill 29
    28  kubectl exec deploy/pi-proxy -- ps
    29  kubectl exec deploy/pi-proxy -- kill 48
    30  kubectl exec deploy/pi-proxy -- ps
    31  kubectl get storageclass
    32  alias k='kubectl'
    33  k
    34  kget pv
    35  k get pv
    36  k get pv
    37  k get pvc
    38  k apply -f specs/caching-proxy-pvc/
    39  kubectl wait --for=condition=Ready pod -l app=pi-proxy,storage=pvc
    40  kubectl get pvc,pv -o wide
    41  kubectl exec deploy/pi-proxy -- ls tmp
    42  kubectl exec deploy/pi-proxy -- ls tmp
    43  kubectl exec deploy/pi-proxy -- kill 1
    44  kubectl exec deploy/pi-proxy -- ls tmp
    45  kubectl rollout restart deploy/pi-proxy
    46  kubectl exec deploy/pi-proxy -- ls tmp
    47  k apply -f solution/sleep-with-hostpath.yaml
    48  k get po
    49  k exec pod/sleep -- ls
    50  k exec pod/sleep -- ls /
    51  k exec pod/sleep -- ls
    52  k exec pod/sleep -- ls node-root
    53  k exec pod/sleep -- ls node-root/tmp
    54  k get po
    55  k get pv
    56  k get pvc
    57  k pv
    58  k get pvc, pv
    59  k get pvc,pv
    60  k get pvc,pv -o wide
    61  k apply -f specs/caching-proxy-pv
    62  k get pvc,pv -o wide
    63  k apply -f specs/caching-proxy-pv
    64  k get pvc,pv -o wide
    65  k get pvc,pv -o wide
    66  k get pvc,pv -o wide
    67  k describe pod -l app=pi-proxy
    68  k describe pod -l app=pi-proxy,storage=local
    69  k label node $(kubectl get nodes -o jsonpath='{.items[0].metadata.name}') labs-pvc=1
    70  k get nodes --show-labels
    71  k describe pod -l app=pi-proxy,storage=local
    72  k get nodes --show-labels
    73  k apply -f specs/caching-proxy-pv
    74  k delete pvc -l app=pi-proxy
    75  '
    76  k apply -f specs/caching-proxy-pv
    77  kubectl delete all,cm,pvc,pv -l kubernetes.courselabs.co=persistentvolumes
    78  k get nodes --show-labels
    79  k label
    80  k label --help
    81  k get nodes --show-labels
    82   kubectl label pods docker-desktop labs-pvc-
    83  kubectl describe pod -l app=pi-proxy,storage=local
    84  kubectl describe pod all
    85  kubectl describe pods
    86  kubectl pods
    87  kubectl get pods
    88  kubectl get po,svc,ep,pv,pvc
    89  k get all
    90  k get all --show-labels
    91  k get nodes
    92  k get nodes -o wide
    93  k get nodes -o wide --show-labels
    94  k label node $(kubectl get nodes -o jsonpath='{.items[0].metadata.name}') labs-pvc-
    95  k get nodes -o wide --show-labels
    96  k get storageclass
    97  k apply -f specs/caching-proxy-pv
    98  k describe pod -l app=pi-proxy,storage=local
    99  kubectl label node $(kubectl get nodes -o jsonpath='{.items[0].metadata.name}') labs-pvc=1
    100  kubectl get nodes --show-labels
    101  kubectl describe pod -l app=pi-proxy,storage=local
    102  k apply -f specs/caching-proxy-pv
    103  kubectl describe pod -l app=pi-proxy,storage=local
    104  kubectl describe pod -l app=pi-proxy,storage=local
    105  k get all
    106  kubectl get pods -l app=pi-proxy
    107  kubectl apply -f labs/persistentvolumes/specs/caching-proxy-pv
    108  kubectl apply -f specs/caching-proxy-pv
    109  kubectl get pvc,pv -l app=pi-proxy
    110  kubectl get pod -l app=pi-proxy,storage=local
    111  kubectl label node $(kubectl get nodes -o jsonpath='{.items[0].metadata.name}') labs-pvc=1
    112  kubectl get nodes --show-labels
    113  kubectl describe pod -l app=pi-proxy,storage=local
    114  kubectl label node $(kubectl get nodes -o jsonpath='{.items[0].metadata.name}') labs-pvc-
    115  kubectl delete all,cm,pvc,pv -l kubernetes.courselabs.co=persistentvolumes
    116  k get all

## /labs/namespaces

[Docs](labs/namespaces/README.md)

