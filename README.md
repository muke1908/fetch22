A lightweight wrapper to use fetch more efficiently and easily and with better error handling, and this is promisified!

---

**Basic usage:**  

```
import fetch22 from 'fetch22';
const someFunction = async ()=> {
  const respGET = await fetch22.get('http://dummy.restapiexample.com/api/v1/employees');
  const respPOST = await fetch22.post('http://dummy.restapiexample.com/api/v1/employees', { 'dummyData': 'Mukesh'});
}
```

**Additional methods:**  
**1. Poll** - call an endpoint and handle response in interval.  
```
const endpoint = () => fetch22.get('http://dummy.restapiexample.com/api/v1/employees');

const poll = fetch22.poll(endpoint, callback, 1000);
poll.pause();                // Pause polling
poll.resume();               // Resume polling
poll.updateInterval(10000);  // Update the interval, set it to 1000ms
```

**Note:** This doesn't use `setInterval`, and it **prevents the race conditions** because, it makes the next call exactly after given time(in ms) 
from the time last response received.

**2. Retry** - Retry no of times in case request fails.  
```
  fetch22.retry(3).get('http://dummy.restapiexample.com/api/v1/employees');
```