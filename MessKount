// Written by (C) Rafsun Masud Prince known 
if (window.location.hostname != "www.messenger.com") {
	alert("Bạn không truy cập trang messenger.com . Vui lòng truy cập trang messenger.com để sử dụng !");
	throw new Error("You are not on Messenger. Please visit www.messenger.com then try again.");
}

(function(d, s, id) {
  var js, fjs = d.getElementsByTagName(s)[0];
  if (d.getElementById(id)) return;
  js = d.createElement(s); js.id = id;
  js.src = "//connect.facebook.net/en_GB/sdk.js#xfbml=1&version=v2.9&appId=286459691717778";
  fjs.parentNode.insertBefore(js, fjs);
}(document, 'script', 'facebook-jssdk'));

var script = document.createElement("script");
script.src = "https://apis.google.com/js/platform.js";
script.type = "text/javascript";
document.getElementsByTagName("head")[0].appendChild(script);

var curr = "";
var children = document.getElementById('js_5');
var elem = document.createElement("span");
elem.setAttribute("id", "message_count_container");
elem.innerHTML = "";
if (children == null) {
	alert("Bạn hãy chờ trang messenger load xong rồi hãy dán nhé ! Vui lòng f5 lại trang và thử lại !");
	throw new Error("The source is null! Something is wrong. Please report this error!");
}
children.appendChild(elem);

children = document.getElementsByClassName('_5742')[0];
elem = document.createElement("span");
elem.setAttribute("id", "message_count_container");

if (children == null) {
	alert("Bạn hãy chờ trang messenger load xong rồi hãy dán nhé ! Vui lòng f5 lại trang và thử lại !");
	throw new Error("The source is null! Something is wrong. Please report this error!");
}
children.appendChild(elem);

function numberWithCommas(x) {
    return x.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",");
}

function loadData(url) {
  var xhttp = new XMLHttpRequest();
  xhttp.onreadystatechange = function() {
    if (this.readyState == 4 && this.status == 200) {
      updateResult(this.responseText);
    }
  };
  xhttp.open("GET", url, true);
  xhttp.send();
}

function updateResult(source){
	var start_string = 'require("InitialJSLoader").handleServerJS(';
	var start = source.indexOf(start_string);
	var end = source.indexOf(',"j0")');
	var new_html = source.substr(start+start_string.length,end-start-start_string.length);
	source = new_html;
	if (source == null) {
		alert("The source is null! Something is wrong. Please report this error!");
		throw new Error("The source is null! Something is wrong. Please report this error!");
	}
	var vanityX = window.location.href.replace("https://www.messenger.com/t/","");
	var jobj = JSON.parse(source);
	var final_jobj = -1;
	for ( i = 0; i < jobj.require.length; i++)
	{
		var sess = jobj.require[i];
		if (sess[3] != undefined)
		{
			if (sess[3][1] != undefined)
			{
				if (sess[3][1].mercuryPayload != undefined)
				{
					final_jobj = sess[3][1].mercuryPayload;
					break;
				}
				else 
					continue;
			}
			else 
				continue;
		}
		else 
			continue;
	}
	var threadobj = final_jobj.threads; 
	var participantsobj = final_jobj.participants; 
	var id = "";
	for ( i = 0; i < participantsobj.length; i++)
	{
		if (participantsobj[i].vanity == vanityX)
		{
			id = participantsobj[i].fbid;
			break;
		}
		else if (participantsobj[i].fbid == vanityX)
		{
			id = participantsobj[i].fbid;
			break;
		}
		else
			continue;
	}
	if (id == "")
		id = vanityX;
	var message_count = "Không Có Tin Nhắn";
	for ( i = 0; i < threadobj.length; i++)
	{
		if (threadobj[i].thread_fbid == id)
		{
			message_count = threadobj[i].message_count;
			break;
		}
		else if (threadobj[i].thread_fbid == vanityX)
		{
			message_count = threadobj[i].message_count;
			break;
		}
		else
			continue;
	}
	message_count = numberWithCommas(message_count);
	document.getElementById("message_count_container").innerHTML = " ("+message_count+")";
}  

var time = setInterval(function() {
        while( window.location.href != curr)
		{
			document.getElementById("message_count_container").innerHTML = " ("+"Đợi Tí..."+")";
			loadData(window.location.href);
			curr = window.location.href;
		}
}, 10);
