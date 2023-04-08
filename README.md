# Below are the seps to configure the statefulset with replication enable.

1. Deploy local persistent volume
   # kubectl apply -f mongo-v.yaml

2. Deploy the headless service for our statefulset
   # kubectl apply -f mongo-headless-service.yaml
 
3. Deploy mongodb statefulset with number of replicas of your preferrence
   # kubectl apply -f mongo-statefulset.yaml
   
4. Enable replication on our pods.
  # kubectl exec -it mymongo-0 -- mongosh
  # rs.initiate()
  # var cfg = rs.conf()
  # cfg.members[0].host="mymongo-0.mongo-headless:27017"
  # rs.reconfig(cfg)
  # rs.add("mymongo-1.mongo-headless:27017:27017") 

5. Enable slave for copying from PRIMARY
