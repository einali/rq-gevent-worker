rq-gevent-worker
================

Implement a new worker based on gevent

[![Downloads](https://pypip.in/download/rq-gevent-worker/badge.svg)](https://pypi.python.org/pypi/rq-gevent-worker/)

##Install

    $ pip install rq-gevent-worker

##Usage



##Test

    tested with rq==0.7.1
	 Gevent 1.2.7
	

##Under The Hood
TODO

##TODO

* Add a command line option to specify gevent pool size

##Note

###Crash
Official `Worker` use `os.fork()` to spawn a child process to execute a job,
so if the job cause the process crash, the worker process is still alive.

When using gevent, we use the same process to execute job, the job may
cause the whole worker process crash.

###Why not `rqworker -w <geventworker>`
update rqworker script at bin directory and 

# -*- coding: utf-8 -*-
import re
import sys
from gevent import monkey, get_hub
from gevent.hub import LoopExit
monkey.patch_all()

from rq.cli import worker

if __name__ == '__main__':
    sys.argv[0] = re.sub(r'(-script\.pyw?|\.exe)?$', '', sys.argv[0])
    sys.exit(worker())# default greenlet pool_size is 20
    #sys.exit(worker(pool_size=20))	





##Declaration

Most of the code is from [zhangliyong](https://github.com/zhangliyong/rq-gevent-worker) 
