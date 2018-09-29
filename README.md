<h1>Building the Reciever</h1> 
<p># javaehubrecieve recive from azure evhub <p>steps to build :
</p> clone the project edit the java files with your credentials and hubnamespace run docker build -t [name] .  create the dokcer container :</p>
<p>docker run -itd [image] java -jar ReceiveByDateTime/target/receiveusingoffset-1.0.0-jar-with-dependencies.jar 
</p>

<p> to check if the reciever works use the docker logs [containerid]
  </p>
<p> docker logs 216b11cb5efb --follow </p>
<p>
  you should see : 
  SLF4J: Failed to load class "org.slf4j.impl.StaticLoggerBinder".
SLF4J: Defaulting to no-operation (NOP) logger implementation
SLF4J: See http://www.slf4j.org/codes.html#StaticLoggerBinder for further details.
date-time receiver created...
Offset: 5488, SeqNo: 30, EnqueueTime: 2018-09-28T09:46:16.931Z| Message Payload: Sending just ONE at timestamp 2018-09-28 09:46:16.0664853 +0000 UTC
ReceivedBatch Size: 1
Offset: 5672, SeqNo: 31, EnqueueTime: 2018-09-28T10:20:03.269Z| Message Payload: Sending just ONE at timestamp 2018-09-28 10:20:04.702560947 +0000 UTC
ReceivedBatch Size: 1
Offset: 5856, SeqNo: 32, EnqueueTime: 2018-09-28T10:20:05.362Z| Message Payload: Sending just ONE at timestamp 2018-09-28 10:20:04.702560947 +0000 UTC
ReceivedBatch Size: 1
ReceivedBatch Size: 0

</p>
<h1> Building the sender</h1>
</p> clone the project edit the java files with your credentials and hubnamespace run docker build -t [name] .  create the dokcer container :</p>
<p>docker run -itd [image] java -jar SimpleSend/target/simplesend-1.0.0-jar-with-dependencies.jar  
</p>

<p> once message is send you will see :
  2018-09-29T08:08:53.854Z: Send Complete...

  </p>
<p> check the reciever to see if the message arrived docker logs 216b11cb5efb --follow </p>
<p>
