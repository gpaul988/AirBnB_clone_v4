# AirBnB clone - Web dynamic

## Authors

Graham S. Paul - [Github](https://github.com/gpaul988) / [Twitter](https://twitter.com/grahamspaul1) / [Gmail](gpaul988@gmail.com)

## Requirements

### General

* Allowed editors: vi, vim, emacs
* All your files will be interpreted on Chrome (version 57.0)
* All your files should end with a new line
* A README.md file, at the root of the folder of the project, is mandatory
* Your code should be semistandard compliant with the flag --global $: semistandard *.js --global $
* All your JavaScript must be in the folder scripts
* You must use JQuery version 3.x
* You are not allowed to use var
* HTML should not reload for each action: DOM manipulation, update values, fetch data…

## More Info

### Import JQuery

<pre><code>&lt;head&gt;
    &lt;script src="https://code.jquery.com/jquery-3.2.1.min.js"&gt;&lt;/script&gt;
&lt;/head&gt;
</code></pre>

### Before starting the project…

<p>You will work on a codebase using <a href="/rltoken/VmGDpw_DCN16OJt_UoqsDQ" title="Flasgger" target="_blank">Flasgger</a>, you will need to install it locally first before starting the RestAPI:</p>

<pre><code>$ sudo apt-get install -y python3-lxml
$ sudo pip3 install flask_cors # if it was not installed yet
$ sudo pip3 install flasgger
</code></pre>

<p>If the RestAPI is not starting, please read the error message. 
Based on the(ses) error message(s), you will have to troubleshoot potential dependencies issues. </p>
<p>Here some solutions:</p>

### <code>jsonschema</code> exception

<pre><code>$ sudo pip3 uninstall -y jsonschema 
$ sudo pip3 install jsonschema==3.0.1
</code></pre>

### <code>No module named 'pathlib2'</code>

<pre><code>$ sudo pip3 install pathlib2
</code></pre>

## Expose ports from your Vagrant

<p>In your <code>Vagrantfile</code>, add this line for each port forwarded</p>

<pre><code># I expose the port 5001 of my vm to the port 5001 on my computer
config.vm.network :forwarded_port, guest: 5001, host: 5001 
</code></pre>

<p>if you need to expose other ports, same line but you will need to replace the “guest port” (inside your vagrant) and your “host port” (outside your vagrant, used from your browser for example)</p>
<p>It’s important in your project, to use the AirBnB API with the port <code>5001</code></p>
<p>
<img src="https://s3.amazonaws.com/intranet-projects-files/concepts/74/hbnb_step5.png" alt="" loading="lazy" style=""></p>

## Mandatory Tasks

#### 0. Last clone!
<div data-role="task1844" data-position="1" id="task-num-0">
      <div class="panel panel-default task-card " id="task-1844">
  <span id="user_id" data-id="209955"></span>

  <div class="panel-heading panel-heading-actions">
 

  <div class="panel-body">
    <span id="user_id" data-id="209955"></span>
A new codebase again? Yes!
<p>For this project you will fork this <a href="/rltoken/18CpThAKqBP5uviO1DSSGw" title="codebase" target="_blank">codebase</a>:</p>

<ul>
<li>Update the repository name to <code>AirBnB_clone_v4</code></li>
<li>Update the <code>README.md</code>:

<ul>
<li>Add yourself as an author of the project</li>
<li>Add new information about your new contribution</li>
<li>Make it better!</li>
</ul></li>
<li>If you’re the owner of this codebase, create a new repository called <code>AirBnB_clone_v4</code> and copy over all files from <code>AirBnB_clone_v3</code> </li>
<li>If you didn’t install Flasgger from the previous project, it’s time! <code>sudo pip3 install flasgger</code></li>
</ul>

  </div>

  <div class="panel-body">
    <span id="user_id" data-id="209955"></span>
    <p>A new codebase again? Yes!</p>

<p>For this project you will fork this <a href="/rltoken/18CpThAKqBP5uviO1DSSGw" title="codebase" target="_blank">codebase</a>:</p>

<ul>
<li>Update the repository name to <code>AirBnB_clone_v4</code></li>
<li>Update the <code>README.md</code>:

<ul>
<li>Add yourself as an author of the project</li>
<li>Add new information about your new contribution</li>
<li>Make it better!</li>
</ul></li>
<li>If you’re the owner of this codebase, create a new repository called <code>AirBnB_clone_v4</code> and copy over all files from <code>AirBnB_clone_v3</code> </li>
<li>If you didn’t install Flasgger from the previous project, it’s time! <code>sudo pip3 install flasgger</code></li>
</ul>

  </div><div class="list-group">
   
  </div>

 

#### 1. Cash only
<div class="panel-body">
    <span id="user_id" data-id="209955"></span>

  Write a script that starts a Flask web application:

<ul>
<li>Based on <code>web_flask</code>, copy: <code>web_flask/static</code>, <code>web_flask/templates/100-hbnb.html</code>, <code>web_flask/__init__.py</code> and <code>web_flask/100-hbnb.py</code> into the <code>web_dynamic</code> folder</li>
<li>Rename <code>100-hbnb.py</code> to <code>0-hbnb.py</code></li>
<li>Rename <code>100-hbnb.html</code> to <code>0-hbnb.html</code></li>
<li>Update <code>0-hbnb.py</code> to replace the existing route to <code>/0-hbnb/</code></li>
</ul>

<p><strong>If <code>100-hbnb.html</code> is not present, use <code>8-hbnb.html</code> instead</strong></p>

<pre><code>guillaume@ubuntu:~/AirBnB_v4$ HBNB_MYSQL_USER=hbnb_dev HBNB_MYSQL_PWD=hbnb_dev_pwd HBNB_MYSQL_HOST=localhost HBNB_MYSQL_DB=hbnb_dev_db HBNB_TYPE_STORAGE=db python3 -m web_dynamic.0-hbnb
* Running on http://0.0.0.0:5000/ (Press CTRL+C to quit)
....
</code></pre>

<p>One problem now is the asset caching done by Flask.</p>

<p>To avoid that, you will add a query string to each asset:</p>

<p>In <code>0-hbnb.py</code>, add a variable <code>cache_id</code> to the <code>render_template</code>. The value of this variable must be an UUID (<code>uuid.uuid4()</code>)</p>

<p>In <code>0-hbnb.html</code>, add this variable <code>cache_id</code> as query string to each <code>&lt;link&gt;</code> tag URL</p>

<pre><code>guillaume@ubuntu:~/AirBnB_v4$ curl -s -XGET http://0.0.0.0:5000/0-hbnb/ | head -6
&lt;!DOCTYPE HTML&gt;
&lt;html lang="en"&gt;
  &lt;head&gt;
    &lt;meta charset="UTF-8" /&gt;
    &lt;link rel="stylesheet" type="text/css" href="../static/styles/4-common.css?e211c9eb-7d17-4f12-85eb-4d50fa50cb1d" /&gt;
    &lt;link rel="stylesheet" type="text/css" href="../static/styles/3-header.css?e211c9eb-7d17-4f12-85eb-4d50fa50cb1d" /&gt;
guillaume@ubuntu:~/AirBnB_v4$ curl -s -XGET http://0.0.0.0:5000/0-hbnb/ | head -6
&lt;!DOCTYPE HTML&gt;
&lt;html lang="en"&gt;
  &lt;head&gt;
    &lt;meta charset="UTF-8" /&gt;
    &lt;link rel="stylesheet" type="text/css" href="../static/styles/4-common.css?f834413e-0aa9-4767-b64a-c92db9cb1f82" /&gt;
    &lt;link rel="stylesheet" type="text/css" href="../static/styles/3-header.css?f834413e-0aa9-4767-b64a-c92db9cb1f82" /&gt;
guillaume@ubuntu:~/AirBnB_v4$ 
</code></pre>

  </div>

#### 2. Select some Amenities to be comfortable!
<div class="panel-body">
    <span id="user_id" data-id="209955"></span>
For the moment the filters section is static, let’s make it dynamic!

<p>Replace the route <code>0-hbnb</code> with <code>1-hbnb</code> in the file <code>1-hbnb.py</code> (based on <code>0-hbnb.py</code>)</p>

<p>Create a new template <code>1-hbnb.html</code> (based on <code>0-hbnb.html</code>) and update it:</p>

<ul>
<li>Import JQuery in the <code>&lt;head&gt;</code> tag</li>
<li>Import the JavaScript <code>static/scripts/1-hbnb.js</code> in the <code>&lt;head&gt;</code> tag

<ul>
<li>In 1-hbnb.html and the following HTML files, add this variable cache_id as query string to the above <code>&lt;script&gt;</code> tag</li>
</ul></li>
<li>Add a <code>&lt;input type="checkbox"&gt;</code> tag to the <code>li</code> tag of each amenity </li>
<li>The new checkbox must be at 10px on the left of the Amenity name</li>
<li>Add to the <code>input</code> tags of each amenity (<code>&lt;li&gt;</code> tag) the attribute <code>data-id=":amenity_id"</code> =&gt; this will allow us to retrieve the Amenity ID from the DOM</li>
<li>Add to the <code>input</code> tags of each amenity (<code>&lt;li&gt;</code> tag) the attribute <code>data-name=":amenity_name"</code> =&gt; this will allow us to retrieve the Amenity name from the DOM</li>
</ul>

<p>Write a JavaScript script (<code>static/scripts/1-hbnb.js</code>):</p>

<ul>
<li>Your script must be executed only when DOM is loaded</li>
<li>You must use JQuery</li>
<li>Listen for changes on each <code>input</code> checkbox tag:

<ul>
<li>if the checkbox is checked, you must store the Amenity ID in a variable (dictionary or list)</li>
<li>if the checkbox is unchecked, you must remove the Amenity ID from the variable </li>
<li>update the <code>h4</code> tag inside the <code>div</code> Amenities with the list of Amenities checked </li>
</ul></li>
</ul>

<p>As example:</p>

<p><img src="https://s3.amazonaws.com/alx-intranet.hbtn.io/uploads/medias/2020/9/8e3c27078d62806b8ad1c1a682fbb3a48636ab89.jpg?X-Amz-Algorithm=AWS4-HMAC-SHA256&amp;X-Amz-Credential=AKIARDDGGGOUSBVO6H7D%2F20231105%2Fus-east-1%2Fs3%2Faws4_request&amp;X-Amz-Date=20231105T182243Z&amp;X-Amz-Expires=86400&amp;X-Amz-SignedHeaders=host&amp;X-Amz-Signature=d1088382eb89a8f96d107686537bfcfcb2c99536847887adbdd3781a0a4f2137" alt="" loading="lazy" style="">
<img src="https://s3.amazonaws.com/alx-intranet.hbtn.io/uploads/medias/2020/9/4e5cecdd82a70f07cd283ef8e242ad325c95b564.jpg?X-Amz-Algorithm=AWS4-HMAC-SHA256&amp;X-Amz-Credential=AKIARDDGGGOUSBVO6H7D%2F20231105%2Fus-east-1%2Fs3%2Faws4_request&amp;X-Amz-Date=20231105T182243Z&amp;X-Amz-Expires=86400&amp;X-Amz-SignedHeaders=host&amp;X-Amz-Signature=ddf82528e35d4dec6bb59480c27994074359eb9da6d06ad1030a962850abbcaf" alt="" loading="lazy" style="">
<img src="https://s3.amazonaws.com/alx-intranet.hbtn.io/uploads/medias/2020/9/fb54e3081e229654db6e71ba919db753a791dcc3.jpg?X-Amz-Algorithm=AWS4-HMAC-SHA256&amp;X-Amz-Credential=AKIARDDGGGOUSBVO6H7D%2F20231105%2Fus-east-1%2Fs3%2Faws4_request&amp;X-Amz-Date=20231105T182243Z&amp;X-Amz-Expires=86400&amp;X-Amz-SignedHeaders=host&amp;X-Amz-Signature=8de3055fcf7fa283e674149e7a0d10f5644f86a15f603b030877ede1b4421c78" alt="" loading="lazy" style=""></p>

  </div>

#### 3. API status
<div class="panel-body">
    <span id="user_id" data-id="209955"></span>
Before requesting the HBNB API, it’s better to know the status of this one.

<p>Update the API entry point (<code>api/v1/app.py</code>) by replacing the current CORS <code>CORS(app, origins="0.0.0.0")</code> by <code>CORS(app, resources={r"/api/v1/*": {"origins": "*"}})</code>.</p>

<p>Change the route <code>1-hbnb</code> to <code>2-hbnb</code> in the file <code>2-hbnb.py</code> (based on <code>1-hbnb.py</code>)</p>

<p>Create a new template <code>2-hbnb.html</code> (based on <code>1-hbnb.html</code>) and update it:</p>

<ul>
<li>Import the JavaScript <code>static/scripts/2-hbnb.js</code> in the <code>&lt;head&gt;</code> tag (instead of <code>1-hbnb.js</code>)</li>
<li>Add a new <code>div</code> element in the <code>header</code> tag:

<ul>
<li>Attribute ID should be <code>api_status</code></li>
<li>Align to the right</li>
<li>Circle of 40px diameter</li>
<li>Center vertically</li>
<li>At 30px of the right border</li>
<li>Background color #cccccc</li>
</ul></li>
<li>Also add a class <code>available</code> for this new element in <code>web_dynamic/static/styles/3-header.css</code>:

<ul>
<li>Background color #ff545f</li>
</ul></li>
</ul>

<p>Write a JavaScript script (<code>static/scripts/2-hbnb.js</code>): </p>

<ul>
<li>Based on <code>1-hbnb.js</code></li>
<li>Request <code>http://0.0.0.0:5001/api/v1/status/</code>:

<ul>
<li>If in the status is “OK”, add the class <code>available</code> to the <code>div#api_status</code> </li>
<li>Otherwise, remove the class <code>available</code> to the <code>div#api_status</code> </li>
</ul></li>
</ul>

<p>To start the API in the port 5001:</p>

<pre><code>guillaume@ubuntu:~/AirBnB_v4$ HBNB_MYSQL_USER=hbnb_dev HBNB_MYSQL_PWD=hbnb_dev_pwd HBNB_MYSQL_HOST=localhost HBNB_MYSQL_DB=hbnb_dev_db HBNB_TYPE_STORAGE=db HBNB_API_PORT=5001 python3 -m api.v1.app
...
</code></pre>

<p>For example:</p>

<p><img src="https://s3.amazonaws.com/alx-intranet.hbtn.io/uploads/medias/2020/9/b68cd1e385963da099899f51ee5f3a6bbf0adcb3.jpg?X-Amz-Algorithm=AWS4-HMAC-SHA256&amp;X-Amz-Credential=AKIARDDGGGOUSBVO6H7D%2F20231105%2Fus-east-1%2Fs3%2Faws4_request&amp;X-Amz-Date=20231105T182243Z&amp;X-Amz-Expires=86400&amp;X-Amz-SignedHeaders=host&amp;X-Amz-Signature=3289b29909adb7a15742fa61b711d56bfba198af0e43f286219b79dd22c6be04" alt="" loading="lazy" style="">
<img src="https://s3.amazonaws.com/alx-intranet.hbtn.io/uploads/medias/2020/9/62fbb2d674fca4a843458e61cf3b05ee9f68ad04.jpg?X-Amz-Algorithm=AWS4-HMAC-SHA256&amp;X-Amz-Credential=AKIARDDGGGOUSBVO6H7D%2F20231105%2Fus-east-1%2Fs3%2Faws4_request&amp;X-Amz-Date=20231105T182243Z&amp;X-Amz-Expires=86400&amp;X-Amz-SignedHeaders=host&amp;X-Amz-Signature=fd4d1d758475c53f5d58d05a79865d248a9afe9f1e0e2d026843870ce985b8c5" alt="" loading="lazy" style=""></p>

  </div>

#### 4. Fetch places
<div class="panel-body">
    <span id="user_id" data-id="209955"></span>
Replace the route <code>2-hbnb</code> with <code>3-hbnb</code> in the file <code>3-hbnb.py</code> (based on <code>2-hbnb.py</code>)

<p>Create a new template <code>3-hbnb.html</code> (based on <code>2-hbnb.html</code>) and update it:</p>

<ul>
<li>Import the JavaScript <code>static/scripts/3-hbnb.js</code> in the <code>&lt;head&gt;</code> tag (instead of <code>2-hbnb.js</code>)</li>
<li>Remove the entire Jinja section of displaying all places (all <code>article</code> tags)</li>
</ul>

<p>Write a JavaScript script (<code>static/scripts/3-hbnb.js</code>): </p>

<ul>
<li>Based on <code>2-hbnb.js</code></li>
<li>Request <code>http://0.0.0.0:5001/api/v1/places_search/</code>: 

<ul>
<li>Description of this endpoint <a href="/rltoken/EkC2rNKurYIznWBiJYPtgA" title="here" target="_blank">here</a>. <strong>If this endpoint is not available, you will have to add it to the API</strong> (you can work all together for creating this endpoint)</li>
<li>Send a <code>POST</code> request with <code>Content-Type: application/json</code> and an empty dictionary in the body - cURL version: <code>curl "http://0.0.0.0:5001/api/v1/places_search" -XPOST -H "Content-Type: application/json" -d '{}'</code></li>
<li>Loop into the result of the request and create an <code>article</code> tag representing a <code>Place</code> in the <code>section.places</code>. (you can remove the Owner tag in the place description)</li>
</ul></li>
</ul>

<p>The final result must be the same as previously, but now, places are loaded from the front-end, not from the back-end!</p>

  </div>

#### 5. Filter places by Amenity
<div class="panel-body">
    <span id="user_id" data-id="209955"></span>
Replace the route <code>3-hbnb</code> with <code>4-hbnb</code> in the file <code>4-hbnb.py</code> (based on <code>3-hbnb.py</code>)

<p>Create a new template <code>4-hbnb.html</code> (based on <code>3-hbnb.html</code>) and update it:</p>

<ul>
<li>Import the JavaScript <code>static/scripts/4-hbnb.js</code> in the <code>&lt;head&gt;</code> tag (instead of <code>3-hbnb.js</code>)</li>
</ul>

<p>Write a JavaScript script (<code>static/scripts/4-hbnb.js</code>): </p>

<ul>
<li>Based on <code>3-hbnb.js</code></li>
<li>When the <code>button</code> tag is clicked, a new POST request to <code>places_search</code> should be made with the list of Amenities checked</li>
</ul>

<p>Now you have the first filter implemented, enjoy!</p>

  </div>

#### 6. States and Cities
<div class="panel-body">
    <span id="user_id" data-id="209955"></span>

Now, reproduce the same steps with the State and City filter:

<p>Replace the route <code>4-hbnb</code> to <code>100-hbnb</code> in the file <code>100-hbnb.py</code> (based on <code>4-hbnb.py</code>)</p>

<p>Create a new template <code>100-hbnb.html</code> (based on <code>4-hbnb.html</code>) and update it:</p>

<ul>
<li>Import the JavaScript <code>static/scripts/100-hbnb.js</code> in the <code>&lt;head&gt;</code> tag (instead of <code>4-hbnb.js</code>)</li>
<li>Add to all <code>li</code> tags of each state a new tag: <code>&lt;input type="checkbox"&gt;</code></li>
<li>Add to all <code>li</code> tags of each cities a new tag:  <code>&lt;input type="checkbox"&gt;</code></li>
<li>The new checkbox must be at 10px on the left of the State or City name</li>
<li>Add to all <code>input</code> tags of each states (<code>&lt;li&gt;</code> tag) the attribute <code>data-id=":state_id"</code> </li>
<li>Add to all <code>input</code> tags of each states (<code>&lt;li&gt;</code> tag) the attribute <code>data-name=":state_name"</code> </li>
<li>Add to all <code>input</code> tags of each cities (<code>&lt;li&gt;</code> tag) the attribute <code>data-id=":city_id"</code> </li>
<li>Add to all <code>input</code> tags of each cities (<code>&lt;li&gt;</code> tag) the attribute <code>data-name=":city_name"</code> </li>
</ul>

<p>Write a JavaScript script (<code>static/scripts/100-hbnb.js</code>): </p>

<ul>
<li>Based on <code>4-hbnb.js</code></li>
<li>Listen to changes on each <code>input</code> checkbox tag:

<ul>
<li>if the checkbox is checked, you must store the State or City ID in a variable (dictionary or list)</li>
<li>if the checkbox is unchecked, you must remove the State or City ID from the variable </li>
<li>update the <code>h4</code> tag inside the <code>div</code> Locations with the list of States or Cities checked </li>
</ul></li>
<li>When the <code>button</code> tag is clicked, a new POST request to <code>places_search</code> should be made with the list of Amenities, Cities and States checked</li>
</ul>

  </div>

#### 7. Reviews
<div class="panel-body">
    <span id="user_id" data-id="209955"></span>
Let’s add a new feature: show and hide reviews!

<p>Replace the route <code>100-hbnb</code> to <code>101-hbnb</code> in the file <code>101-hbnb.py</code> (based on <code>100-hbnb.py</code>)</p>

<p>Create a new template <code>101-hbnb.html</code> (based on <code>100-hbnb.html</code>) and update it:</p>

<ul>
<li>Import the JavaScript <code>static/scripts/101-hbnb.js</code> in the <code>&lt;head&gt;</code> tag (instead of <code>101-hbnb.js</code>)</li>
<li>Design the list of reviews from this <a href="/rltoken/6QUObzD76iV79Sc0rFcAQQ" title="task" target="_blank">task</a></li>
<li>Add a <code>span</code> element at the right of the <code>H2</code> “Reviews” with value “show” (add all necessary attributes to do this feature)</li>
</ul>

<p>Write a JavaScript script (<code>static/scripts/101-hbnb.js</code>): </p>

<ul>
<li>Based on <code>100-hbnb.js</code></li>
<li>When the <code>span</code> next to the Reviews <code>h2</code> is clicked by the user: 

<ul>
<li>Fetch, parse, display reviews and change the text to “hide”</li>
<li>If the text is “hide”: remove all Review elements from the DOM</li>
<li>This button should work like a toggle to fetch/display and hide reviews</li>
</ul></li>
</ul>

  </div>