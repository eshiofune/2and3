# ABOUT
    Python package which allows creation of simple servers and clients for communication with sockets. Supports both Python2 and Python3.
    Version: 1.0.0

# USAGE
    - To create a server: Depending on your Python version, import the Server class from the appropriate server module, subclass it and override its act_on() method which describes what it should do when it receives a request, and returns a string response. Finally, create a Server object and call its listen() method.

    - To create a client: Depending on your Python version, import the Client class from the appropriate client module, create a Client object and call its poll_server() method. You can then make use of the response it returns as required.

    By default, a Python2 client will poll the default Python3 server while a Python3 client will poll the default Python2 server (unlike in the examples below).

# EXAMPLES
    # Test server with Python2:
    from sockets.python2.server import Server
    class MyServer(Server):
        def act_on(self, data, addr):
            # Do something with data (in bytes) and return a string.
            return data
    server = MyServer(listening_address=('127.0.0.1', 11112))
    server.listen()

    # Test client with Python2. Polls the Python2 server.
    from sockets.python2.client import Client
    client = Client()
    response, addr = client.poll_server("Hello world", server=('127.0.0.1', 11112))
    print response, addr
    
    # Test server with Python3:
    from sockets.python3.server import Server
    class MyServer(Server):
        def act_on(self, data, addr):
            # Do something with data (in bytes) and return a string.
            return data.decode()
    server = MyServer(listening_address=('127.0.0.1', 11113))
    server.listen()

    # Test client with Python3. Polls the Python3 server.
    from sockets.python3.client import Client
    client = Client()
    response, addr = client.poll_server("Hello world", server=('127.0.0.1', 11113))
    print(response, addr)

# CONTRIBUTING AUTHORS
    Ehiorobo Evans (2018).