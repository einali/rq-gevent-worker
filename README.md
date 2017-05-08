rq-gevent-worker
================

Implement a new worker based on gevent for Python 3  and  rq 0.7.1 and gevent 1.2.1 

(https://pypi.python.org/pypi/rq-gevent-worker/)


##Usage

put rq_gevent_worker.py in site-packages/rq/cli

then 
vim  your_venv/bin/rqworkr

to this 

```python

#!/home/mehdi/venvs/test_rq/bin/python

# -*- coding: utf-8 -*-
import re
import sys
from gevent import monkey, get_hub
from gevent.hub import LoopExit

from rq.cli import worker
from rq.cli.rq_gevent_worker import GeventWorker
from rq import Connection, Queue, Worker


monkey.patch_all()
if __name__ == '__main__':
    with Connection():
        q = Queue()
        GeventWorker(q).work()
#   sys.argv[0] = re.sub(r'(-script\.pyw?|\.exe)?$', '', sys.argv[0])
 #  sys.exit(GeventWorker())



```


##Test

    Tested with 
	1. rq==0.7.1
	2. Gevent 1.2.7
	3. python 3.5.2

	

##Under The Hood
TODO

##TODO

* Add a command line option to specify gevent pool size



##Declaration

Most of the code is from [zhangliyong](https://github.com/zhangliyong/rq-gevent-worker) 
