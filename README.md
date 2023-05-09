# Assignment 8 - CS-361

## Microservice Request and Receive Instructions: 


## Requests:
* To request data we will need to set up ZeroMQ on the Client side. This is in python. 

```import zmq``` - First we will import the ZeroMQ library

```context = zmq.Context()``` - Second we will create a ZeroMQ context which is used to manage the sockets that will be used

```socket = context.socket(zmq.REQ)``` - Third we will create a ZeroMQ socket of the type REQUEST which means this socket wil lsend requests to other sockets and wait for replies back

```socket.connect("tcp://localhost:5555")``` - Fourth we will connect the socket to the microservice, in this case tcp://localhost:5555

```socket.send_string("f"SEARCH_{search_name}")``` - Fifth we will send a message to Micro service, the send_string method converts the message and sends it over the socket

```code = socket.recv_string()``` - Lastly we will need to get a response back from the microservice, the value of code will be the response from the microservice

An example call is below:

        context = zmq.Context()
        socket = context.socket(zmq.REQ)
        socket.connect("tcp://localhost:5555")  
        socket.send_string(f"SEARCH_{search_name}")
        code = socket.recv_string() 

## Receive:
* To receive data we will need to set up the ZeroMQ server. The microservice will be processing the request, performing the search and sending a response back to our client. 

```ZMQ.Context context = ZMQ.context(1);``` - Creating an object to represent the ZeroMQ context

```ZMQ.Socket socket = context.socket(ZMQ.REP)``` - Creating a socket resposne

```socket.bind("tcp://*:5555");``` - Binding the sockett to the desired port 

```System.out.println("Connected to Socket- tcp://*:5555, Microservice Running!");``` - Letting us know that the microservice is up and running without any issues

An example call is below: 
        
        ZMQ.Context context = ZMQ.context(1);
        ZMQ.Socket socket = context.socket(ZMQ.REP);
        socket.bind("tcp://*:5555");
        System.out.println("Connected to Socket- tcp://*:5555, Microservice Running!");
        
        
  ## UML Diagram 
  
  ![UML](https://user-images.githubusercontent.com/76978336/236994431-f06f1532-15b6-4ac3-a1c9-648a1db22403.PNG)
