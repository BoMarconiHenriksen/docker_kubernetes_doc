# Persistent Volume vs Persistent Volume Claim
*Persistent Volume Claim* is not storage it's just say here are the diffrent options you have for storage inside this particular cluster.  
The developer will write in the config file the diffrent persistent volume claims thats going to be available inside the cluster.  
It's like an advertising: here is something for your pod you can get when it's created.  
The persistent volume claim can be created ahead of time and then it's called *Statically provisioned Persistent Volume*.  
If it's created on the fly it's called *Dynamically provisioned Persistent Volume*. It's only created when your pod ask for it.  
