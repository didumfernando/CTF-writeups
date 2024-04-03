# Beginner: Off-Brand Cookie Clicker 
The challenge had a website provided to us with a cookie clicker in which increments the counter everytime we click.

Upon closer examination & inspection of the html code for the webpage, we could see some embedded javascript in the html code, hinting at a possible vulnerability we could exploit there.

![imagecook](https://github.com/didumfernando/CTF-writeups/assets/118650079/ad5b804d-f177-46c9-bc89-dddc1b904c03)

As such we could manually send a request with the data as 10000000 since that will be the condition to return us the flag successfully.
```
# python library to handle requests
import requests

# data being sent over 
data = {'count': 10000000}

# POST request
req = requests.post('http://betta.utctf.live:8138/click', data=data)

# check for request's success
if req.status_code == 200:
'''getting the flag'''
    flag = req.json()['flag']
    print("Flag received: %s" % flag)
```
## Alternative solution
An alternative solution we managed to find out was by using our CMD directly to send a post request to the url provided by using 'curl' which is the command-line too to send data using various protocols but in this case we use it to make a HTTP request. Thus when we run this command on our CMD, it will send a POST request to betta.utctf.live:8138/click with form data containing a field "count" with the value "10000000".

![success](https://github.com/didumfernando/CTF-writeups/assets/118650079/a1558718-0919-4b38-8fe2-a70ad57b7060)
