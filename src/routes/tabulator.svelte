<div class="main-div">
<h1 class="head-line">The Virtual DOM and Table Rendering</h1>
<p class="info">
    Before you build your first table, it might be useful to know a bit about
    how Tabulator works.
</p>
<h2 class="head-line">Virtual DOM</h2>
<p class="info">
    Tabulator uses a virtual DOM to enable it to process 100,000's of rows
    without a performance overhead. The virtual DOM works by only building the
    rows that are visible on the screen. As you scroll through the table, rows
    are created and destroyed as they enter/leave the of the visible area of the
    table. This also means that it is a bad idea to try to use code outside of
    Tabulator to directly alter or bind events to DOM elements inside the table,
    because there is a good chance that the element you are trying to manipulate
    will be destroyed on the next scroll. Tabulator has a wide range of
    callbacks, formatters and other functions that allow you to manipulate the
    table contents in a way that is safe and wont be affected by the rows being
    recreated. In order for the virtual DOM to work, Tabulator needs to know how
    big the table is. This means that you must set a height for the table
    element to engage the virtual DOM, this can be in the CSS, an inline style,
    or using the height property in the table constructor. If there is no height
    set on the table the Tabulator cannot use the virtual DOM, and the table
    will be rendered with no scroll bar, taking up as much space as is needed to
    show all rows at once. In this mode it will be very slow to render large
    numbers of rows.
</p>
<h2 class="head-line">Table Visibility</h2>
<p class="info">
    Because Tabulator builds its elements on the fly, it needs to be visible
    when it is populated with data to be able to make the calculations required
    to layout the table correctly, because hidden elements have no dimension in
    the DOM. If you initialise a table or call the setData function while the
    table is hidden you may find graphical errors in the table when you next
    make it visible. To get round this issue you can call the redraw function on
    the table when you make it visible, which will force Tabulator to
    recalculate the layout of all the cells in the table.
</p>
<h2 class="head-line">Example Setup</h2>
<p class="info">1 Create your DOM element</p>
<code><div id="example-table"></div></code>


<p class="info">2 Define some data for the table</p>
<code>

 var tabledata = [
 	{id:1, name:"Oli Bob", age:"12", col:"red", dob:""},
 	{id:2, name:"Mary May", age:"1", col:"blue", dob:"14/05/1982"},
 	{id:3, name:"Christine Lobowski", age:"42", col:"green", dob:"22/05/1982"},
 	{id:4, name:"Brendon Philips", age:"125", col:"orange", dob:"01/08/1980"},
 	{id:5, name:"Margret Marmajuke", age:"16", col:"yellow", dob:"31/01/1999"},
 ];
</code>
<p class="info">3 Turn element into a Tabulator by passing a constructor object to the tabulator jQuery widget</p>
<code>
    //create Tabulator on DOM element with id "example-table"
var table = new Tabulator("#example-table", {
 	height:205, // set height of table (in CSS or here), this enables the Virtual DOM and improves render speed dramatically (can be any valid css height value)
 	data:tabledata, //assign data to table
 	layout:"fitColumns", //fit columns to width of table (optional)
 	columns:[ //Define Table Columns
	 	{title:"Name", field:"name", width:150},
	 	{title:"Age", field:"age", hozAlign:"left", formatter:"progress"},
	 	{title:"Favourite Color", field:"col"},
	 	{title:"Date Of Birth", field:"dob", sorter:"date", hozAlign:"center"},
 	],
});

//trigger an alert message when the row is clicked
table.on("rowClick", function(e, row){ 
	alert("Row " + row.getData().id + " Clicked!!!!");
});
</code>
</div>

<style>
  
    .main-div {
        text-align: center;
        background-color: beige;
    }
    .info {
        text-align: center;
    }
    .head-line {
        color: green;
        text-align: center;
    }
    .our-anchors {
        text-align: center;
        list-style-position: inside;
    }
</style>


