# IoT-lab4
## OM2M/REST API & Node-RED

### High Level Architecture
<img src="https://i.imgur.com/wMRux8f.png" width=50% height=50% />

### RESTful Operations on the Resource Tree using PostMan
> Creating Application, Descriptor Container, Data Container, Descriptor ContentInstance, Data ContentInstance

* Step1: Start the OM2M IN-CSE
  * IN-CSE product directory : `org.eclipse.om2m/org.eclipse.om2m.site.in-cse/target/products/in-cse/linux/gtk/x86_64`
  * Open a terminal, go to the product directory and input the command: `shstart.sh`
  * After starting it successfully, you will see “CSE Started”
 * Step2: Start the OM2M MN-CSE
  * MN-CSE product directory : `org.eclipse.om2m/org.eclipse.om2m.site.mn-cse/target/products/mn-cse/linux/gtk/x86_64`
  * Open another terminal, go to the product directory and input the command: `shstart.sh`
  * After starting it successfully, you will see “CSE Started”
 * Step 3: Open postman
  * Retrieve a resource: 
  <table>
    <tr><td> URL</td><td> http://127.0.0.1:8282/~/mn-cse </td></tr>
    <tr><td>Method</td><td>GET</td></tr>
    <tr><td> Header </td><td> X-M2M-Origin : admin:admin </td></tr>
    <tr><td> Body </td><td> (empty)</td></tr>
  </table>
  
   * Create a "MY_SENSOR" Application:
   <table>
    <tr><td> URL</td><td> http://127.0.0.1:8282/~/mn-cse </td></tr>
    <tr><td>Method</td><td>POST</td></tr>
    <tr><td> Header </td><td> X-M2M-Origin: admin:admin <br> Content-Type: application/xml;ty=2 <br> X-M2M-NM: MY_SENSOR </td></tr>
    <tr><td> Body </td><td> &ltom2m:ae xmlns:om2m="http://www.onem2m.org/xml/protocols"&gt <br> &emsp;  &ltapi&gt app-sensor &lt/api&gt <br> &emsp; &ltlbl&gt Type/sensor Category/temperature Location/home &lt/lbl&gt <br> &emsp; &ltrr&gt false &lt/rr&gt <br> &lt/om2m:ae&gt </td></tr>
  </table>
  
### RESTful Operations on the Resource Tree using Node-RED
> Creating a Middle Node-Application Entity with Node-RED    
> Extending the Middle Node-Application Entity with HTTP Server Capabilities   
> Creating a subscription resource to a container in Middle Node-Application Entity using Node-RED.  

* Step1: Start the Node-RED
  * Open a new terminal and input the command: `sudo node-red -vv`
  * Open http://localhost:1880
