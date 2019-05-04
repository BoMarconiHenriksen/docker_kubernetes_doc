# Limitations in Config Updates
The result of this change will be an error message.  
1. Open client-pod.yaml  
2. Change the containerPort to 9999  
We are not allowed to update ports only 4 things can be changed.  
There is a workaround and that is to use another object than pod...  
