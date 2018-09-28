<p># javaehubrecieve recive from azure evhub <p>steps to build :
</p> clone the project edit the java files with your credentials and hubnamespace run docker build -t [name] .  create the dokcer container :</p>
<p>docker run -itd [image] java -jar ReceiveByDateTime/target/receiveusingoffset-1.0.0-jar-with-dependencies.jar 
</p>

<p> to check if the reciever works use the docker logs [containerid]
  </p>
