# wordpress-k8
scalable wordpress with mysql and backup



          $ kubectl create -f one-storage-class.yaml
          
          
          $ kubectl create -f two-mysql-configmap.yaml
          
          
          $ kubectl create -f three-mysql-services.yaml
          
          
          $ kubectl create -f four-mysql-statefulset.yaml
          
          
 Now, when you call
          
          $ kubectl get pods
          
 you should see three pods spinning up or ready that each have two containers on them. The master pod is denoted as mysql-0 and the slaves follow as mysql-1 and mysql-2. Give the pods a few minutes to make sure the xtrabackup service is synced properly between pods, then move on to the WordPress deployment. You can check the logs of the individual containers to confirm that there are no error messages being thrown. To do this, run 
          
          $ kubectl logs -f -c <container_name> 
          
The master xtrabackup container should show the two connections from the slaves and no errors should be visible in the logs.


      $ kubectl create -f five-wordpress.yaml
      
      
      $ kubectl scale --replicas=<number of replicas> deployment/wordpress
      
      

