# jsPDF Demo

## Usage

```
// prepare the data
var head = [["ID", "Country", "Rank", "Capital"]];
var body = [[1, "Denmark", 7.526, "Copenhagen"],
            [2, "Switzerland", 	7.509, "Bern"],
            [3, "Iceland", 7.501, "Reykjavík"],
            [4, "Norway", 7.498, "Oslo"],
            [5, "Finland", 7.413, "Helsinki"]];

// generate a pdf file
var doc = new jsPDF();
doc.autoTable({head: head, body: body});
doc.output("dataurlnewwindow");
```
