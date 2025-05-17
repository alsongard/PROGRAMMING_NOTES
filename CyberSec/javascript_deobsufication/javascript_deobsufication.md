# JavaScript Deobfuscation 
Code deobfuscation is an important skill to learn for code analysis and reverse engineering.
 obfuscated code that wants to hide certain functionalities, like malware that utilizes obfuscated JavaScript code to retrieve its main payload.
 
**Objectives:**
The following topics will be discussed:
    Locating JavaScript code
    Intro to Code Obfuscation
    How to Deobfuscate JavaScript code
    How to decode encoded messages
    Basic Code Analysis
    Sending basic HTTP requests


**Example of Code obsufication:**
```
eval(function (p, a, c, k, e, d) { e = function (c) { return c.toString(36) }; if (!''.replace(/^/, String)) { while (c--) { d[c.toString(a)] = k[c] || c.toString(a) } k = [function (e) { return d[e] }]; e = function () { return '\\w+' }; c = 1 }; while (c--) { if (k[c]) { p = p.replace(new RegExp('\\b' + e(c) + '\\b', 'g'), k[c]) } } return p }('g 4(){0 5="6{7!}";0 1=8 a();0 2="/9.c";1.d("e",2,f);1.b(3)}', 17, 17, 'var|xhr|url|null|generateSerial|flag|HTB|1_4m_7h3_53r14l_g3n3r470r|new|serial|XMLHttpRequest|send|php|open|POST|true|function'.split('|'), 0, {}))
```
Note: The above type of obfuscation is known as "packing", which is usually recognizable from the six function arguments used in the initial function "function(p,a,c,k,e,d)".

**Learning how to obfuscate code**
one must learnn how to obfuscate code before deobfuscating. 
obfuscation is a way to make code harder for humans to read, though it performs the given task and may be slower in performance. To obfuscate code, we use an Obfuscation tool, which takes in code asn input.

code obsufication is done for 2 reasons:
- hide the devepers code and functionality and preventing it from being copied
- for malicious purposes, malicious attack/code not to be detected by an IPS(intrusion prevention system) or IDS(intrusion detection system)


Techniques used in Javascript Obsufication:
- using minifier: a minifier is a tool that makes the entire code to be in a single line, making  it to difficulty in readable.  Code minification is applicable other languages than js. 
Examples:
1. [jsminifier](https://www.toptal.com/developers/javascript-minifier)


- using obsufication tool
1. [obsuficationio](https://obfuscator.io/#output)
2. [javascript_obsufication_tool](https://beautifytools.com/javascript-obfuscator.php#)



**Completely hiding the code**
When using the packing obsufication method, it still shows some strings, which reveals intention of the code. using the following tools will obsuficate the entire code. 
1. [jsfuck](https://jsfuck.com/)
2. [obsuficator](https://obfuscator.io/#code)


**Deobsufication**
To deobsuficate the entire code, we need to use the following tools: 
1. [beautifier](https://beautifier.io/) 
very helpfull for deobsuficating code that has been minified.
this deobsuficate the code especially code obsuficated using packing style. though the code is more organized in terms of structure and indentaion, we require to deobsuficate the code. Entirelly.
2. [Unpacker](https://matthewfl.com/unPacker.html)


code:
```
eval(function (p, a, c, k, e, d) { e = function (c) { return c.toString(36) }; if (!''.replace(/^/, String)) { while (c--) { d[c.toString(a)] = k[c] || c.toString(a) } k = [function (e) { return d[e] }]; e = function () { return '\\w+' }; c = 1 }; while (c--) { if (k[c]) { p = p.replace(new RegExp('\\b' + e(c) + '\\b', 'g'), k[c]) } } return p }('g 4(){0 5="6{7!}";0 1=8 a();0 2="/9.c";1.d("e",2,f);1.b(3)}', 17, 17, 'var|xhr|url|null|generateSerial|flag|HTB|1_4m_7h3_53r14l_g3n3r470r|new|serial|XMLHttpRequest|send|php|open|POST|true|function'.split('|'), 0, {}))
```

code:
```
function generateSerial()
	{
	var flag="HTB
		{
		1_4m_7h3_53r14l_g3n3r470r!
	}
	";
	var xhr=new XMLHttpRequest();
	var url="/serial.php";
	xhr.open("POST",url,true);
	xhr.send(null)
}
```

To have better obfusicated tool, it is advised to use a custom tool.

client URL tool(curl) is a helpfull tool that enables us to send request to a server with different HTTP methods such as GET, POST, PUT(update), DEL
```
curl -X POST -d "params1=params" http://server-address:port-number
```

```
curl -X POST -d "params1=params" http://SERVER_ADDRESS:PORT-NUMBER/serial.php # you get N2gxNV8xNV9hX3MzY3IzN19tMzU1NGcz
```

## text encoding:
text encoding mechanisms discusses are:
- base64
in base64 the text is encoded into alphanumeric characters, that is(only numbers and text). It uses the + and - special symbols. Lastly an string/text that is encoded using a base64, the resulting encoded text, the length must be a multiple of 4.(to check the resulting encoded text  use python)
if the encoded text is not a multiple of 4, it assigns an equal sign(=) to make it a multiple of 4

examples:
```
echo "https://www.hackthebox.eu/" | base64 
```
To decode:
```
echo "aHR0cHM6Ly93d3cuaGFja3RoZWJveC5ldS8K" | base64 -d
```



- hex
hex method used the hexadecimal equivalent of the given character in the plaintext(text/string to be encoded). use ``man ascii`` to view this.
To decode the text use:
```
echo "https://hackthebox.eu/" | xxd -d
```
To decode the encoded string
```
echo "68747470733a2f2f7777772e6861636b746865626f782e65752f0a" | xxd -p -r
```

- rot13/caesar
rot13/caesar is used to encrypt data by shifting the letters by some numbers. Example by rot13(shifted by 0-13(14))
there is no specific command to decode or encode a string to rot13 cipher, however we can use the truncate command.
```
echo "https://www.hackthebox/eu" | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```
```
echo "https://www.hackthebox.eu/" | tr 'A-Za-z' 'N-ZA-Mn-za-m'
uggcf://jjj.unpxgurobk.rh/
```

there are tools that can be used to detect the cipher of your text, using tools such as ``[boxentriq](https://www.boxentriq.com/)``


### **SUMMARY**
The following is a summary of what we learned:
    First, we uncovered the HTML source code of the webpage and located the JavaScript code.
    Then, we learned about various ways to obfuscate JavaScript code.
    After that, we learned how to beautify and deobfuscate minified and obfuscated JavaScript code.
    Next, we went through the deobfuscated code and analyzed its main function
    We then learned about HTTP requests and were able to replicate the main function of the obfuscated JavaScript code.
    Finally, we learned about various methods to encode and decode strings.

