<html><head><meta content="text/html; charset=UTF-8" http-equiv="content-type"></head><body class="c30"><h1 class="c16 c20" id="h.1wgjhs3i3ced"><span>SBGNViz Collaborative Editor User Guide</span></h1><p class="c16 c35"><span>The editor allows human curators and computer agents to work on the same pathway model, and communicate through text and images. On the server side, we have an application server that keeps the model, handles communication across clients, and performs operational transformation. Model visualization and editing are handled on the client side. The editor visualizes information about cellular processes and pathways in SBGN (Systems Biology Graphical Notation) format. It allows for automatic graph layout, editing and highlighting facilities. </span></p><p class="c1"><span></span></p><p class="c1"><span></span></p><h2 class="c16 c20" id="h.2up5xl2gx913"><span>Installation</span></h2><p class="c16"><span>Install node.js, mongodb and redis servers first.</span></p><p class="c1"><span></span></p><p class="c16"><span class="c24">Node</span><span class="c18">:</span></p><p class="c1"><span class="c18"></span></p><p class="c16"><span class="c18">&gt;curl -sL </span><span class="c23"><a class="c26" href="https://www.google.com/url?q=https://deb.nodesource.com/setup_0.12&amp;sa=D&amp;ust=1456966704465000&amp;usg=AFQjCNGGRmt27os-aQCnnpnjDmM-dK8UTA">https://deb.nodesource.com/setup_0.12</a></span><span class="c18">&nbsp;| sudo -E bash -</span></p><p class="c16"><span class="c18">&gt;sudo apt-get install -y nodejs</span></p><p class="c1"><span class="c18"></span></p><p class="c16"><span class="c24">Redis</span><span class="c18">:</span></p><p class="c1"><span class="c18"></span></p><p class="c16"><span class="c18">&gt;sudo apt-get update</span></p><p class="c16"><span class="c18">&gt;sudo apt-get install build-essential</span></p><p class="c16"><span class="c18">&gt;sudo apt-get install tcl8.5</span></p><p class="c16"><span class="c18">&gt;wget </span><span class="c23"><a class="c26" href="https://www.google.com/url?q=http://download.redis.io/releases/redis-stable.tar.gz&amp;sa=D&amp;ust=1456966704468000&amp;usg=AFQjCNGwsqVTEvOoDXFJXUPfOp5HAjVP5w">http://download.redis.io/releases/redis-stable.tar.gz</a></span></p><p class="c16"><span class="c18">&gt;tar xzf redis-stable.tar.gz</span></p><p class="c16"><span class="c18">&gt;cd redis-stable</span></p><p class="c16"><span class="c18">&gt;make</span></p><p class="c1"><span class="c18"></span></p><p class="c16"><span class="c24">Mongo</span><span class="c18">:</span></p><p class="c1"><span class="c18"></span></p><p class="c16"><span class="c18">&gt;sudo apt-key adv --keyserver hkp://</span><span class="c23"><a class="c26" href="https://www.google.com/url?q=http://keyserver.ubuntu.com/&amp;sa=D&amp;ust=1456966704470000&amp;usg=AFQjCNGvhIICtXNVxHKClfjeGof6XYMC4A">keyserver.ubuntu.com:80</a></span><span class="c18">&nbsp;--recv EA312927</span></p><p class="c16"><span class="c18">&gt;echo &quot;deb </span><span class="c23"><a class="c26" href="https://www.google.com/url?q=http://repo.mongodb.org/apt/ubuntu&amp;sa=D&amp;ust=1456966704471000&amp;usg=AFQjCNEKWJoH8yIBAFiMQ-MCWVrWwM09GA">http://repo.mongodb.org/apt/ubuntu</a></span><span class="c18">&nbsp;trusty/mongodb-org/3.2 multiverse&quot; | sudo tee /etc/apt/sources.list.d/mongodb-org-3.2.list</span></p><p class="c16"><span class="c18">&gt;sudo apt-get update</span></p><p class="c16"><span class="c18">&gt;sudo apt-get install -y mongodb-org</span></p><p class="c1"><span class="c24"></span></p><p class="c16"><span class="c24">If mongo does not work:</span></p><p class="c1"><span class="c18"></span></p><p class="c16"><span class="c18">&gt;sudo apt-get install upstart-sysv</span></p><p class="c1"><span class="c18"></span></p><p class="c1"><span class="c18"></span></p><p class="c16"><span class="c18">Get project from github:</span></p><p class="c1"><span class="c18"></span></p><p class="c16"><span class="c18">&gt;git clone </span><span class="c23"><a class="c26" href="https://www.google.com/url?q=https://github.com/fdurupinar/Sbgnviz-Collaborative-Editor.git&amp;sa=D&amp;ust=1456966704473000&amp;usg=AFQjCNEHA0UHM1vmyy5RgBaDtjAfIfIBDg">https://github.com/fdurupinar/Sbgnviz-Collaborative-Editor.git</a></span></p><p class="c16"><span class="c18">&gt;cd Sbgnviz-Collaborative-Editor</span></p><p class="c16"><span class="c18">&gt;sudo rm -rf node_modules</span></p><p class="c16"><span class="c18">&gt;npm install</span></p><p class="c1"><span class="c18"></span></p><p class="c1"><span class="c18"></span></p><p class="c16"><span class="c24">Run server:</span></p><p class="c1"><span class="c18"></span></p><p class="c16"><span class="c18">&gt;node server</span></p><p class="c1"><span></span></p><p class="c16"><span>In order to open a client:</span></p><p class="c16"><span>Enter &ldquo;http://localhost:3000&rdquo; to the address bar of your browser. </span></p><h2 class="c16 c20" id="h.lzkutpoc5320"><span>System Framework</span></h2><p class="c1"><span></span></p><p class="c16"><span style="overflow: hidden; display: inline-block; margin: 0.00px 0.00px; border: 0.00px solid #000000; transform: rotate(0.00rad) translateZ(0px); -webkit-transform: rotate(0.00rad) translateZ(0px); width: 455.50px; height: 359.87px;"><img alt="" src="images/image01.png" style="width: 455.50px; height: 359.87px; margin-left: 0.00px; margin-top: 0.00px; transform: rotate(0.00rad) translateZ(0px); -webkit-transform: rotate(0.00rad) translateZ(0px);" title=""></span></p><p class="c1"><span></span></p><p class="c1"><span></span></p><p class="c1"><span></span></p><p class="c1"><span></span></p><p class="c1"><span></span></p><p class="c1"><span></span></p><p class="c1"><span></span></p><p class="c1"><span></span></p><h2 class="c16 c20" id="h.55d0en95yatx"><span>Framework Details</span></h2><p class="c16"><span style="overflow: hidden; display: inline-block; margin: 0.00px 0.00px; border: 0.00px solid #000000; transform: rotate(0.00rad) translateZ(0px); -webkit-transform: rotate(0.00rad) translateZ(0px); width: 624.00px; height: 405.74px;"><img alt="" src="images/image00.png" style="width: 624.00px; height: 405.74px; margin-left: 0.00px; margin-top: 0.00px; transform: rotate(0.00rad) translateZ(0px); -webkit-transform: rotate(0.00rad) translateZ(0px);" title=""></span><span>&nbsp;</span></p><p class="c1"><span></span></p><p class="c1"><span></span></p><p class="c1"><span></span></p><h3 class="c16 c20" id="h.ttz39lsxwuvx"><span>Computer Agent API</span></h3><p class="c1"><span></span></p><p class="c16"><span>Computer agents are connected to the node.js http server via websockets (socket.io.js). An agent is initialized with a </span><span class="c9">name (string) </span><span>&nbsp;and a unique </span><span class="c9">ID (string).</span></p><p class="c1"><span></span></p><p class="c16"><span class="c10">Constructor</span><span>: Agent (string name, string id)</span></p><p class="c1"><span></span></p><h4 class="c16 c20" id="h.1eu245k1egzd"><span>Public Attributes:</span></h4><p class="c1"><span></span></p><p class="c16"><span class="c10">agentId</span><span>: (string) A unique id</span></p><p class="c1"><span></span></p><p class="c16"><span class="c10">agentName</span><span>: (string) Agent name</span></p><p class="c1"><span></span></p><p class="c16"><span class="c10">colorCode</span><span>: A specific color to identify the agent operations. It should be a string in hsla format as: &ldquo;hsla(</span><span class="c9">H</span><span>, </span><span class="c9">S</span><span>, </span><span class="c9">L</span><span>%, 1)&rdquo;, where </span><span class="c9">H (integer)</span><span>, </span><span class="c9">S (float)</span><span>&nbsp;and </span><span class="c9">L (float)</span><span>&nbsp;are hue, saturation and lightness values.</span></p><p class="c1"><span></span></p><p class="c16"><span class="c10">selectedNode</span><span>: The node object on which the agent is performing operations. It has attributes such as position =</span><span>{x:&lt;posX&gt;,y:&lt;posY&gt;}</span><span>, width, height, borderWidth, borderHeight, backgroundColor, sbgnLabel, sbgnStatesAndInfos = {clazz:&lt;className&gt;, state = {value:&lt;stateValue&gt;,variable:&lt;stateVariable&gt;}}.</span></p><p class="c16"><span>&nbsp;</span></p><p class="c16"><span class="c10">selectedEdge</span><span>: The edge object on which the agent is performing operations. It has attributes such as cardinality, lineColor and width.</span></p><p class="c1"><span></span></p><p class="c16"><span class="c10">opHistory</span><span>: History of operations as an array of strings in the format: &ldquo;</span><span class="c9">UserName</span><span>&nbsp;(</span><span class="c9">date</span><span>):</span><span class="c9">&nbsp;Command</span><span>&rdquo;.</span></p><p class="c16"><span class="c10">chatHistory</span><span>: Chat history as an array of messages.</span></p><p class="c1"><span class="c10"></span></p><p class="c16"><span class="c10">userList</span><span>: List of connected user ids.</span></p><p class="c1"><span></span></p><h4 class="c16 c20" id="h.nt4u4u3mhl90"><span>Private Attributes:</span></h4><p class="c16"><span class="c10">room</span><span>: The document id that identifies the shared model. It is the string after http:&lt;ip&gt;:3000/ in the server address.</span></p><p class="c16"><span class="c10">socket</span><span>: The web socket between the server and agent</span></p><p class="c16"><span class="c10">pageDoc</span><span>: The document that the shared model is stored.</span></p><p class="c1"><span></span></p><h4 class="c16 c20" id="h.l0c8z5l51rt3"><span>Methods:</span></h4><p class="c1"><span></span></p><a id="t.a479165b3048e3a8701c4538bb9274ab90443c88"></a><a id="t.0"></a><table class="c34"><tbody><tr class="c15"><td class="c4" colspan="1" rowspan="1"><p class="c8"><span class="c32 c29 c10">Name</span></p></td><td class="c14" colspan="1" rowspan="1"><p class="c8"><span class="c29 c10 c32">Function</span></p></td><td class="c17" colspan="1" rowspan="1"><p class="c8"><span class="c32 c29 c10">Parameters</span></p></td><td class="c22" colspan="1" rowspan="1"><p class="c8"><span class="c32 c29 c10">Returns</span></p></td></tr><tr class="c15"><td class="c4" colspan="1" rowspan="1"><p class="c12"><span class="c3">connectToServer</span></p></td><td class="c14" colspan="1" rowspan="1"><p class="c8"><span class="c3">Connects the server and returns socket.io socket</span></p></td><td class="c17" colspan="1" rowspan="1"><p class="c8"><span class="c3">url, callback</span></p></td><td class="c22" colspan="1" rowspan="1"><p class="c8"><span class="c3">socket</span></p></td></tr><tr class="c15"><td class="c4" colspan="1" rowspan="1"><p class="c12"><span class="c3">loadModel</span></p></td><td class="c14" colspan="1" rowspan="1"><p class="c12"><span class="c3">Gets the model for the current room</span></p></td><td class="c17" colspan="1" rowspan="1"><p class="c8"><span class="c3">callback</span></p></td><td class="c22" colspan="1" rowspan="1"><p class="c6"><span class="c3"></span></p></td></tr><tr class="c15"><td class="c4" colspan="1" rowspan="1"><p class="c12"><span class="c3">loadOperationHistory</span></p></td><td class="c14" colspan="1" rowspan="1"><p class="c12"><span class="c3">Gets history of operations from the node.js server and assigns them to opHistory</span></p><p class="c6"><span class="c3"></span></p></td><td class="c17" colspan="1" rowspan="1"><p class="c12"><span class="c3">callback</span></p></td><td class="c22" colspan="1" rowspan="1"><p class="c6"><span class="c3"></span></p></td></tr><tr class="c15"><td class="c4" colspan="1" rowspan="1"><p class="c12"><span class="c3">loadUserList</span></p></td><td class="c14" colspan="1" rowspan="1"><p class="c12"><span class="c3">Gets user list from the node.js server and assigns them to userList</span></p></td><td class="c17" colspan="1" rowspan="1"><p class="c8"><span class="c3">callback</span></p></td><td class="c22" colspan="1" rowspan="1"><p class="c6"><span class="c3"></span></p></td></tr><tr class="c15"><td class="c4" colspan="1" rowspan="1"><p class="c12"><span class="c3">loadChatHistory</span></p></td><td class="c14" colspan="1" rowspan="1"><p class="c12"><span class="c3">Gets history of chat messages from the node.js server and assigns them to chatHistory</span></p></td><td class="c17" colspan="1" rowspan="1"><p class="c8"><span class="c3">callback</span></p></td><td class="c22" colspan="1" rowspan="1"><p class="c6"><span class="c3"></span></p></td></tr><tr class="c15"><td class="c4" colspan="1" rowspan="1"><p class="c12"><span class="c3">getNodeList</span></p></td><td class="c14" colspan="1" rowspan="1"><p class="c12 c28"><span class="c3"></span></p></td><td class="c17" colspan="1" rowspan="1"><p class="c8"><span class="c3">callback</span></p></td><td class="c22" colspan="1" rowspan="1"><p class="c12"><span class="c3">The node list in the shared model as an object of node ids</span></p></td></tr><tr class="c40"><td class="c4" colspan="1" rowspan="1"><p class="c12"><span class="c3">getLayoutProperties</span></p></td><td class="c14" colspan="1" rowspan="1"><p class="c12 c28"><span class="c3"></span></p></td><td class="c17" colspan="1" rowspan="1"><p class="c8"><span class="c3">callback</span></p></td><td class="c22" colspan="1" rowspan="1"><p class="c12"><span class="c3">Layout properties of the shared model as an object with attributes as: </span></p><p class="c12"><span class="c29">{</span><span class="c3">name: &lt;layout name&gt;,</span></p><p class="c12"><span class="c3">&nbsp;nodeRepulsion: &lt;node repulsion value&gt; ,</span></p><p class="c12"><span class="c3">&nbsp;nodeOverlap:&lt;node overlap percentage&gt;, </span></p><p class="c12"><span class="c3">idealEdgeLength:&lt;ideal edge length value&gt;, </span></p><p class="c12"><span class="c3">edgeElasticity:&lt;edge elasticity value&gt;, </span></p><p class="c12"><span class="c3">nestingFactor:&lt;nesting factor value&gt;, </span></p><p class="c12"><span class="c3">gravity:&lt;gravity value&gt;, </span></p><p class="c12"><span class="c3">numIter:&lt;number of iterations&gt;,</span></p><p class="c12"><span class="c3">tile:&lt;boolean value to tile disconnected&gt;, </span></p><p class="c12"><span class="c3">animate:&lt;boolean value&gt;, </span></p><p class="c12"><span class="c3">randomize:&lt;boolean value&gt;} </span></p><p class="c6"><span class="c3"></span></p></td></tr><tr class="c39"><td class="c4" colspan="1" rowspan="1"><p class="c12"><span class="c3">changeName</span></p></td><td class="c14" colspan="1" rowspan="1"><p class="c12"><span class="c3">Sends request to the server to change agent&#39;s name</span></p></td><td class="c17" colspan="1" rowspan="1"><p class="c8"><span class="c3">newName</span></p></td><td class="c22" colspan="1" rowspan="1"><p class="c6"><span class="c3"></span></p></td></tr><tr class="c15"><td class="c4" colspan="1" rowspan="1"><p class="c12"><span class="c3">getNodeRequest</span></p></td><td class="c14" colspan="1" rowspan="1"><p class="c12"><span class="c3">Requests the node with &lt;id&gt; from the server</span></p></td><td class="c17" colspan="1" rowspan="1"><p class="c8"><span class="c3">id, callback</span></p></td><td class="c22" colspan="1" rowspan="1"><p class="c8"><span class="c3">Node with id</span></p></td></tr><tr class="c15"><td class="c4" colspan="1" rowspan="1"><p class="c12"><span class="c3">getEdgeRequest</span></p></td><td class="c14" colspan="1" rowspan="1"><p class="c12"><span class="c3">Requests the edge with &lt;id&gt; from the server</span></p></td><td class="c17" colspan="1" rowspan="1"><p class="c8"><span class="c3">id, callback</span></p></td><td class="c22" colspan="1" rowspan="1"><p class="c8"><span class="c3">Edge with id</span></p></td></tr><tr class="c15"><td class="c4" colspan="1" rowspan="1"><p class="c12"><span class="c3">sendMessage</span></p></td><td class="c14" colspan="1" rowspan="1"><p class="c12"><span class="c3">Sends chat message &lt;comments&gt; as a string to &lt;targetArr&gt; as an array of targeted user ids [{id: &lt;id1&gt;},..., {id: &lt;idn&gt;}]</span></p></td><td class="c17" colspan="1" rowspan="1"><p class="c8"><span class="c3">comment, targetArr, callback</span></p></td><td class="c22" colspan="1" rowspan="1"><p class="c6"><span class="c3"></span></p></td></tr><tr class="c15"><td class="c4" colspan="1" rowspan="1"><p class="c12"><span class="c3">listen</span></p></td><td class="c14" colspan="1" rowspan="1"><p class="c12"><span class="c3">Socket listener for server requests. Can get &ldquo;operation&rdquo;, &ldquo;message&rdquo;, &ldquo;userList&rdquo; or &ldquo;imageFile&rdquo; from the server.</span></p></td><td class="c17" colspan="1" rowspan="1"><p class="c8"><span class="c3">callback</span></p></td><td class="c22" colspan="1" rowspan="1"><p class="c6"><span class="c3"></span></p></td></tr><tr class="c41"><td class="c4" colspan="1" rowspan="1"><p class="c12"><span class="c3">sendRequest</span></p></td><td class="c14" colspan="1" rowspan="1"><p class="c12"><span class="c3">Sends an operation request to the node.js server. &nbsp;Model update operations are done using this method.</span></p></td><td class="c17" colspan="1" rowspan="1"><p class="c8"><span class="c33 c37"><a class="c26" href="#h.nhfdym5d0wpf">reqName, param</a></span></p><p class="c6"><span class="c3"></span></p></td><td class="c22" colspan="1" rowspan="1"><p class="c6"><span class="c3"></span></p></td></tr></tbody></table><p class="c1"><span></span></p><p class="c1"><span></span></p><h5 class="c16 c20" id="h.nhfdym5d0wpf"><span>sendRequest:</span></h5><p class="c1 c38"><span></span></p><a id="t.5ecfa19ea20fe9e9f35d0be094051c36548ef09b"></a><a id="t.1"></a><table class="c36"><tbody><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p class="c8"><span class="c32 c10 c33">reqName</span></p></td><td class="c2" colspan="1" rowspan="1"><p class="c8"><span class="c32 c10 c33">param</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p class="c8"><span class="c7">&ldquo;agentAddImageRequest&rdquo;</span></p></td><td class="c2" colspan="1" rowspan="1"><p class="c12"><span class="c7">{img: &lt;image file&gt;, </span></p><p class="c12"><span class="c7">filePath: &lt;path of image file&gt; } </span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p class="c12"><span class="c7">&quot;agentSetLayoutProperties&quot;</span></p></td><td class="c2" colspan="1" rowspan="1"><p class="c12"><span class="c7">{name: &lt;layout name&gt;,</span></p><p class="c12"><span class="c7">&nbsp;nodeRepulsion: &lt;node repulsion value&gt; ,</span></p><p class="c12"><span class="c7">&nbsp;nodeOverlap:&lt;node overlap percentage&gt;, </span></p><p class="c12"><span class="c7">idealEdgeLength:&lt;ideal edge length value&gt;, </span></p><p class="c12"><span class="c7">edgeElasticity:&lt;edge elasticity value&gt;, </span></p><p class="c12"><span class="c7">nestingFactor:&lt;nesting factor value&gt;, </span></p><p class="c12"><span class="c7">gravity:&lt;gravity value&gt;, </span></p><p class="c12"><span class="c7">numIter:&lt;number of iterations&gt;,</span></p><p class="c12"><span class="c7">tile:&lt;boolean value to tile disconnected&gt;, </span></p><p class="c12"><span class="c7">animate:&lt;boolean value&gt;, </span></p><p class="c12"><span class="c7">randomize:&lt;boolean value&gt;} </span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p class="c8"><span class="c7">&ldquo;agentRunLayoutRequest&rdquo;</span></p></td><td class="c2" colspan="1" rowspan="1"><p class="c8"><span class="c7">-</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p class="c8"><span class="c7">&ldquo;agentAddNodeRequest&rdquo;</span></p></td><td class="c2" colspan="1" rowspan="1"><p class="c8"><span class="c7">{x: &lt;position x&gt;, </span></p><p class="c8"><span class="c7">y: &lt;position y&gt;, </span></p><p class="c8"><span class="c7">sbgnclass: &lt;sbgn class&gt;}</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p class="c12"><span class="c7">&ldquo;agentAddEdgeRequest&rdquo;</span></p></td><td class="c2" colspan="1" rowspan="1"><p class="c12"><span class="c7">{source: &lt;source node id&gt;, </span></p><p class="c12"><span class="c7">target: &lt;target node id&gt;, </span></p><p class="c8"><span class="c7">sbgnclass: &lt;sbgn class&gt;}</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p class="c12"><span class="c7">&ldquo;agentChangeNodeAttributeRequest&rdquo;</span></p></td><td class="c2" colspan="1" rowspan="1"><p class="c12"><span class="c7">{id: &lt;node id&gt;, </span></p><p class="c12"><span class="c7">attStr: &lt;node attribute name in the model&gt;</span></p><p class="c12"><span class="c7">attVal:&lt;node attribute value&gt;}</span></p><p class="c12 c28"><span class="c7"></span></p><p class="c12"><span class="c7">attStr takes the following values: &ldquo;sbgnclass&rdquo;, &ldquo;highlightColor&rdquo;, &ldquo;backgroundColor&rdquo;, &ldquo;sbgnlabel&rdquo;, &ldquo;borderColor&rdquo;, &ldquo;borderWidth&rdquo;, &ldquo;isMultimer&rdquo;, &ldquo;isCloneMarker&rdquo;, &ldquo;parent&rdquo;, &ldquo;children&rdquo;, &ldquo;width&rdquo;, &ldquo;height&rdquo;, &ldquo;sbgnbboxW&rdquo;, &ldquo;sbgnbboxH&rdquo;, &ldquo;sbgnStatesAndInfos&rdquo; </span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p class="c12"><span class="c7">&ldquo;agentChangeEdgeAttributeRequest&rdquo;</span></p></td><td class="c2" colspan="1" rowspan="1"><p class="c12"><span class="c7">{id: &lt;node id&gt;, </span></p><p class="c12"><span class="c7">attStr: &lt;edge attribute name in the model&gt;</span></p><p class="c12"><span class="c7">attVal:&lt;edge attribute value&gt;}</span></p><p class="c12 c28"><span class="c7"></span></p><p class="c12"><span class="c7">attStr takes the following values: &ldquo;lineColor&rdquo;, &ldquo;highlightColor&rdquo;, &ldquo;width&rdquo;, &ldquo;cardinality&rdquo; &nbsp;</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p class="c12"><span class="c7">&ldquo;agentMoveNodeRequest&rdquo;</span></p></td><td class="c2" colspan="1" rowspan="1"><p class="c12"><span class="c7">{id: &lt;node id&gt;, </span></p><p class="c12"><span class="c7">pos: {x:&lt;new position x&gt;, y: &lt; new position y&gt;}}</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p class="c12"><span class="c7">&ldquo;agentAddCompoundRequest&rdquo;</span></p></td><td class="c2" colspan="1" rowspan="1"><p class="c12"><span class="c7">{type: &lt;compound type as &ldquo;complex&rdquo; or &ldquo;compartment&rdquo;&gt;, </span></p><p class="c12"><span class="c7">selectedNodeArr: &lt;array of node ids&gt;}</span></p></td></tr></tbody></table><p class="c1 c38"><span></span></p><p class="c1"><span class="c0 c9 c13"></span></p><p class="c1"><span class="c0 c9 c13"></span></p><p class="c16"><span>In order to set up and run an agent:</span></p><p class="c1"><span></span></p><p class="c16"><span class="c0 c9 c10 c21">agent </span><span class="c0">= </span><span class="c0 c10 c25">new </span><span class="c0 c9">Agent</span><span class="c0">(</span><span class="c0 c11">agentName</span><span class="c0">, </span><span class="c0 c11">agentId</span><span class="c0">);</span></p><p class="c16"><span class="c0 c10 c25">var </span><span class="c0 c11">socket </span><span class="c0">= </span><span class="c0 c9 c10 c21">agent</span><span class="c0">.</span><span class="c0 c19">connectToServer</span><span class="c0">(</span><span class="c0 c11">serverIp</span><span class="c0">, </span><span class="c0 c10 c25">function</span><span class="c0">(){</span></p><p class="c16 c27"><span class="c0 c9 c13">//callback operations</span></p><p class="c16"><span class="c0">});</span></p><p class="c16"><span class="c0 c11">socket</span><span class="c0">.</span><span class="c0 c19">on</span><span class="c0">(</span><span class="c0 c31 c10">&#39;connect&#39;</span><span class="c0">, </span><span class="c0 c10 c25">function</span><span class="c0">(){</span></p><p class="c16"><span class="c0">&nbsp; &nbsp;</span><span class="c0 c9 c10 c21">agent</span><span class="c0">.</span><span class="c0 c19">loadModel</span><span class="c0">(</span><span class="c0 c10 c25">function</span><span class="c0">() {</span></p><p class="c16"><span class="c0">&nbsp; &nbsp; &nbsp; &nbsp;</span><span class="c0 c9 c10 c21">agent</span><span class="c0">.</span><span class="c0 c19">loadOperationHistory</span><span class="c0">(</span><span class="c0 c10 c25">function</span><span class="c0">(){</span></p><p class="c16"><span class="c0">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;</span><span class="c0 c9 c10 c21">agent</span><span class="c0">.</span><span class="c0 c19">loadChatHistory</span><span class="c0">(</span><span class="c0 c10 c25">function</span><span class="c0">(){ &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; </span></p><p class="c16 c27"><span class="c0 c9 c13">//callback operations</span><span class="c0">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; </span></p><p class="c16 c27"><span class="c0">});</span></p><p class="c16"><span class="c0">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;});</span></p><p class="c16"><span class="c0">&nbsp; &nbsp; &nbsp; &nbsp;});</span></p><p class="c16"><span class="c0">&nbsp; &nbsp;</span><span class="c0 c9 c10 c21">agent</span><span class="c0">.</span><span class="c0 c19">listen</span><span class="c0">(</span><span class="c0 c10 c25">function</span><span class="c0">(){</span></p><p class="c16"><span class="c0">&nbsp; &nbsp; &nbsp; &nbsp;</span><span class="c0 c11">socket</span><span class="c0">.</span><span class="c0 c19">on</span><span class="c0">(</span><span class="c0 c31 c10">&#39;operation&#39;</span><span class="c0">, </span><span class="c0 c10 c25">function</span><span class="c0">(data){</span></p><p class="c16"><span class="c0">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; </span><span class="c0 c9 c13">//callback operations</span></p><p class="c16"><span class="c0">&nbsp; &nbsp; &nbsp; &nbsp;});</span></p><p class="c16"><span class="c0">&nbsp; &nbsp; &nbsp; &nbsp;</span><span class="c0 c11">socket</span><span class="c0">.</span><span class="c0 c19">on</span><span class="c0">(</span><span class="c0 c31 c10">&#39;message&#39;</span><span class="c0">, </span><span class="c0 c10 c25">function</span><span class="c0">(data){</span></p><p class="c16"><span class="c0">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;</span><span class="c0 c9 c13">//callback operations</span></p><p class="c16"><span class="c0">&nbsp; &nbsp; &nbsp; &nbsp;});</span></p><p class="c16"><span class="c0">&nbsp; &nbsp; &nbsp; &nbsp;</span><span class="c0 c11">socket</span><span class="c0">.</span><span class="c0 c19">on</span><span class="c0">(</span><span class="c0 c10 c31">&#39;userList&#39;</span><span class="c0">, </span><span class="c0 c10 c25">function</span><span class="c0">(data){</span></p><p class="c16"><span class="c0">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;</span><span class="c0 c9 c13">//callback operations</span></p><p class="c16"><span class="c0">&nbsp; &nbsp; &nbsp; &nbsp;});</span></p><p class="c16"><span class="c0">&nbsp; &nbsp; &nbsp; &nbsp;</span><span class="c0 c11">socket</span><span class="c0">.</span><span class="c0 c19">on</span><span class="c0">(</span><span class="c0 c31 c10">&#39;imageFile&#39;</span><span class="c0">, </span><span class="c0 c10 c25">function</span><span class="c0">(data){</span></p><p class="c16"><span class="c0">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;</span><span class="c0 c9 c13">//callback operations</span></p><p class="c16"><span class="c0">&nbsp; &nbsp; &nbsp; &nbsp;});</span></p><p class="c16"><span class="c0">&nbsp; &nbsp;});</span></p><p class="c16"><span class="c0">});</span></p><p class="c1"><span></span></p><p class="c1"><span></span></p></body></html>