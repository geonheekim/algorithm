#This is how to use the mpc_system library.

+ Next is an example.

```python
from ctypes import *
import ctypes
import json

def c_str(string):
    
    data = ctypes.c_char_p(string).value
    if data is not None:
        dec_data = data.decode('utf-8')
        return dec_data 

c_func = CDLL('../../../out/cmain.so')

ret = c_func.mpc_main_init()
if ret != 0: 
    print(error)

while True:
    json_low_data = c_func.mpc_system_to_json_write()
    data = c_str(json_low_data)
    
    if data is not None:
        print(data)
    
c_func.mpc_main_exit()
```
+ The result data is {"id": "system", "key": "key_data", "data": "NULL" }.
