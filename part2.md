<!DOCTYPE html>
<html>
<head>
    <meta http-equiv="Content-type" content="text/html"; charset=utf-8"/>
    <title>CUNY DATA608/2 - Zachary Herold </title>
    <link rel="stylesheet" href="css/bootstrap.min.css">
</head>
<body>
    <style type="text/css">
        td { 
            padding: 0px;
            border: 1px solid green;
        }
        table { 
            border-spacing: 6px;
            border-collapse: separate;
        }
    </style>   
</body>
<body>
<script type="text/javascript">

    function Upload() {
        var fileUpload = document.getElementById("fileUpload");
        var regex = /^([a-zA-Z0-9\s_\\.\-:])+(.csv|.txt)$/;
        if (regex.test(fileUpload.value.toLowerCase())) {
            if (typeof (FileReader) != "undefined") {
                var reader = new FileReader();
                reader.onload = function (e) {
                    var table = document.createElement("table");
                    table.setAttribute("class", "table.upload");
                    //table.className="tbl";
                    var rows = e.target.result.split("\n");
                    for (var i = 0; i < rows.length; i++) {
                        var cells = rows[i].split(",");
                        if (cells.length > 1) {
                            var row = table.insertRow(-1);
                            for (var j = 0; j < cells.length; j++) {
                                var cell = row.insertCell(-1);
                                cell.innerHTML = cells[j];
                            }
                        }
                    }
                    var dvCSV = document.getElementById("dvCSV");
                    dvCSV.innerHTML = "";
                    dvCSV.appendChild(table);
                }
                reader.readAsText(fileUpload.files[0]);
            } else {
                alert("This browser does not support HTML5.");
            }
        } else {
            alert("Please upload a valid CSV file.");
        }
    }
    // from https://www.aspsnippets.com/Articles/Import-CSV-File-to-HTML-Table-using-JavaScript.aspx

    function searchTable() {
        var input, filter, found, table, tr, td, i, j;
        input = document.getElementById("myInput");
        filter = input.value.toUpperCase();
        table = document.getElementById("dvCSV");
        tr = table.getElementsByTagName("tr");
        for (i = 0; i < tr.length; i++) {
            td = tr[i].getElementsByTagName("td");
            for (j = 0; j < td.length; j++) {
                if (td[j].innerHTML.toUpperCase().indexOf(filter) > -1) {
                    found = true;
                }
            }
            if (found) {
                tr[i].style.display = "";
                found = false;
            } else {
                tr[i].style.display = "none";
            }
        }
    }
    //from https://stackoverflow.com/questions/9127498/how-to-perform-a-real-time-search-and-filter-on-a-html-table
    //solution by Tarik
</script>

<h1> Module 5 - Part 2</h1>
<input type="file" id="fileUpload" />
<input type="button" id="upload" value="Upload" onclick="Upload()" />
<hr />
<div id="dvCSV">
</div>
<br>
<div class = "search">
    <label for="myInput">Search an Element</label>
    <input id='myInput' onkeyup='searchTable()' type='text'>
</div>

</body>
</html>