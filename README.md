# Below are the seps to configure the statefulset with replication enable.

# Deploy local persistent volume

   kubectl apply -f mongo-v.yaml

# Deploy the headless service for our statefulset

   kubectl apply -f mongo-headless-service.yaml
 
# Deploy mongodb statefulset with number of replicas of your preferrence

   kubectl apply -f mongo-statefulset.yaml
   
# Enable replication on our pods.

  kubectl exec -it mymongo-0 -- mongosh
  rs.initiate()
  var cfg = rs.conf()
  cfg.members[0].host="mymongo-0.mongo-headless:27017"
  rs.reconfig(cfg)
  rs.add("mymongo-1.mongo-headless:27017:27017") 

# Enable slave for copying from PRIMARY

  use secondaryOk command as slaveOk is depriciated!!
