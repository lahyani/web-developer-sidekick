# web-developer-sidekick #

Web Developer Sidekick allows recognition of website environments and display useful data such as credentials, ip address, database connections...etc

Once **Web Developer Sidekick** installed you have to go to configuration page (**about:addons**) and click **Options**. Now you can set the addon parameters. The extension use YAML notations to read the parameters. 
![Options Page](https://addons.cdn.mozilla.net/user-media/previews/full/193/193122.png?modified=1511928151)
Here some parameters descriptions:

**Autohide**: If check it will hide the badge after **Duration** parameter value 

**Duration** : This parameter is used to auto hide the badge. But it also used to slidedown the badge once the MouseEvent "mouseount" is fired.

**Position** : The badge position: A drop down to select the badge position. Accepted values are: Top left, top right, bottom left and bottom right. 

**Domain rules** : The mandatory structure for _Domain Rules_ is: 

<pre>  
version: "1"
rules:
  - condition:
    - ".org"
    - ".com"
    - ".net"
    type: "in_array"
    title: "Awesome Web Site"
    version: "1"
    environment: "production"
    summary:
      tabId: "summary"
      title: "Summary"
      display: true
      data:
        - header: ""
          list:
            - project: "Web site"
              ip_address: "http://127.0.0.1"
              description: "This is a demo.\nText mode only"
</pre>
The mandatory fields for any rule are: 
**type**: It can be "contains_string", "in_array", "matches_regex". 

**condition**: This field is used with the type to determine if current URL matches the conditions. For example: 

<pre>
rules:   
  - condition: "www.firefox.com"   
    type: "contains_string" 
</pre> 

If you navigate to www.firefox.com. The badge will be displayed. But For site example.org the badge will disappear beacause it don't match the condition. ![Display Environment](https://addons.cdn.mozilla.net/user-media/previews/full/193/193118.png?modified=1511928152)

**title**:The tab title. 

**version**: Not yet used 

**environment**: the environment for the given rule and condition. 

**data**: This contains the data to display. See **Data Fields** section below for details

**tabs**: Contains a list of tabs to display. See **Tab Fields** for details.

# Data Fields #
It contains a list of data to display. Each item has a header field (it can be empty) and a **list** field. The list has a couple of pair key-value. The parser will take display the key on the left as a label and the value on the right. If you don't won't to display the label add a field hide_label:true just after the header field.

# Tab Fields #
Comming soon!
