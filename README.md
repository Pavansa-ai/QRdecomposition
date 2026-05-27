# Algorithm for QR Decomposition
## Aim:
To implement QR decomposition algorithm using the Gram-Schmidt method.
## Equipment’s required:
1.	Hardware – PCs
2.	Anaconda – Python 3.7 Installation / Moodle-Code Runner
## Algorithm:
1.	Intialize the matrix Q and u
2.	The vector u and e is given by

    ![eqn1](./ex4.jpg)

    ![eqn2](./ex6.jpg)

    ![eqn3](./ex3.jpg)

3.	Obtain the Q matrix   
    ![eqn4](./ex1.jpg)
4.	Construct the upper triangular matrix R
    ![eqn5](./ex2.jpg)



## Program:
### Gram-Schmidt Method
```


''' 
Program to QR decomposition using the Gram-Schmidt method
Developed by: S.PAVAN
RegisterNumber: 212225040296
'''

import os
os.environ["OPENBLAS_NUM_THREADS"] = "1"
import numpy as np
def QR_Decomposition(A):
    n,m = A.shape
    
    Q = np.zeros((n,n))
    R = np.zeros((n,m))
    for i in range(n):
        u = A[:,i].copy()
        
        for j in range(i):
            R[j,i] = np.dot(Q[:,j],A[:,i])
            u = u - R[j,i] * Q[:,j]
            
        R[i,i] = np.linalg.norm(u)
        Q[:,i] = u / R[i,i]
        
    for i in range(n):
        for j in range(i+1,m):
            R[i,j] = np.dot(Q[:,i],A[:,j])
            
    print("The Q Matrix is\n",Q)    
    print("The R Matrix is\n",R)
    
    
        
        
a = np.array(eval(input()))
QR_Decomposition(a)




```

## Output
```
<img width="1404" height="941" alt="image" src="https://github.com/user-attachments/assets/e1ccc27a-e098-434e-ba92-885de5d4eaa0" />

```

## Result
Thus the QR decomposition algorithm using the Gram-Schmidt process is written and verified the result.
