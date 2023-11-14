@def title = "Introduction to Simple Linux Utility for Resource Management (Slurm)"
@def date = "11/05/2023"
@def tags = ["slurm", "julia"]

## Get Task ID from Your Script

* From R:


```r
param<-Sys.getenv(“SLURM_ARRAY_TASK_ID”)
```

* From Matlab:

```matlab
param=getenv(‘SLURM_ARRAY_TASK_ID’);
```

* From python:

```python
import os

param = os.getenv(‘SLURM_ARRAY_TASK_ID’)
```