<html>
<head>
    <link rel="stylesheet" href="css/bootstrap.min.css">
    <title>CUNY DATA608/2 - Module5 - Zachary Herold </title>
</head>
<body style='margin-top:0;margin-left:100;margin-right:0;'>
<h1> Module 5</h1>
<h2> Question 1A</h2>

<script type="text/javascript">
/* Create a function to reverse any word that you type in. 
This can be typed into either an input box or an alert box, 
and then print the result in a box or on the webpage.*/

    function reverse(){
        var word = document.getElementById('wordInput').value;
        var word_rev = word.split('').reverse().join('');
        var str = "Your word in reverse is: <br />" + word_rev;
        document.getElementById('wordInReverse').innerHTML = str;
    }
</script>
<p><i>Enter a word to be reversed</i></p>
<form>
    <label for="wordInput">Reverse the Word...</label>
    <input id="wordInput" type="text" size="20">
    <p></p>
    <input type="button" value="Reverse" onclick="reverse();">
</form>
<h3 id='wordInReverse'></h3>

<br>
<h2> Question 1B</h2>

<script type="text/javascript">
/* Create a function that takes an input number, and prints a table 
with the first 20 multiples of the number, in order 5x4 */
    
    function createMultiples(form){
        var num;
        num = form.elements["numInput"].valueAsNumber;
        //var num = document.getElementById('numInput').value;
        var mul = num;
        var table;
        table = "<table border='1px' width='25%' cellspacing='2' cellpadding='2' style='cursor:pointer;'>";
        for (var i = 1; i <= 20; i++){
            if (i % 5 == 1){
                table += "<tr>" ;
            }
            table += "<td>" + mul * i + "</td>";
            if (i % 5 == 0){
                table += "</tr>" ;
            }
        }
        table += "</table>";
        document.getElementById('result').innerHTML = table;
    }
</script>

<p><i>Enter a number to generate a multiplication table</i></p>
<form class = "table" id="input">
    <div class = "row">
        <label for="numInput">Get Multiples of...</label>
        <input type="number" id="numInput">
    </div>
</form>
<br>
<input type="button" form="input" value="Create Table" onclick="createMultiples(this.form);">
<br><br>
<div id="result"></div>
</body>
</html>
