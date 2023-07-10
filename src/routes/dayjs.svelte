
<div class="main-div">
<h1 class="head-lines">DAYJS</h1>
<h2 class="head-lines">Why Day.js?</h2>
<p class="info">Less JavaScript to download, parse and execute, leaving more time for your code.</p>
<h4 class="head-lines">Simple</h4>
<p class="info">Day.js is a minimalist JavaScript library that parses, validates, manipulates,
     and displays dates and times for modern browsers with a largely Moment.js-compatible API.

If you use Moment.js, you already know how to use Day.js.</p>
<h4 class="head-lines">Immutable</h4>
<p class="info">All API operations that change the Day.js object will return a new instance instead.

This helps prevent bugs and avoid long debugging sessions.</p>

<h3 class="head-lines">code examples</h3>


<ul class="our-anchors">
     <h4>Day.js today's date</h4>
       <li>
       
    <code>
import dayjs from 'dayjs';

let now = dayjs();

console.log(now.format());
</code></li> 
<li>
    <h4>Creating Day.js objects</h4>
    <code>
    import dayjs from 'dayjs';

let d1 = dayjs("2018-06-03");
console.log(d1.format());

let d2 = dayjs.unix(1530471537);
console.log(d2.format());

let d3 = dayjs(new Date(2011, 11, 22));
console.log(d3.format());
    </code>
</li>
<li>
    <h4>Day.js formatting datetime</h4>
    <code>
        import dayjs from 'dayjs';

let now = dayjs();

console.log("ISO")
console.log(now.format());

console.log("\nTime")
console.log(now.format("HH:mm:ss"));
console.log(now.format("h:mm:ss a"));

console.log("\nDate")
console.log(now.format("dddd, MMMM D YYYY"));
console.log(now.format("YYYY-MM-DD"));
    </code>
</li>
<li>
    <p>Day.js calculating datetime difference</p>
    <code>
        import dayjs from 'dayjs';

const date1 = dayjs("2019-14-05");
const date2 = dayjs("2018-06-25");

let df1 = date1.diff(date2);
console.log(df1);

let df2 = date1.diff(date2, "month");
console.log(df2);

let df3 = date1.diff(date2, "month", true);
console.log(df3);

let df4 = date1.diff(date2, "day");
console.log(df4);

let df5 = date1.diff(date2, "week");
console.log(df5);
    </code>
</li>
<h4>coronavirus data code</h4>
    <li>
        
        <code>
         async getTotalCases() {
 const rows = await this.getSheetByTitle('Historical');

  const reversed = rows.reverse();

  let result;

  for (let x = 0; x < reversed.length; x++) {
   const row = reversed[x];
   const dateRow = dayjs(row['Date']).format('YYYY-MM-DD');

   if (row['Cases']) {
    result = {
     last_update: dateRow,
     cases: +row['Cases'],
     deaths: +row['Deaths'],
     recoveries: +row['Recoveries'],
     cases_today: +row['Daily Case Increase'],
     deaths_today: +row['Daily Death'],
     recoveries_today: +row['Daily Recovery'],
     admitted: +row['Admitted'],
     fatality_rate: row['Fatality Rate'],
     recovery_rate: row['Recovery Rate'],
    };
    break;
   }
  }

  return result;
 }</code></li>

 
</ul>
</div>
<style>
  
    .main-div {
        text-align: center;
        background-color: antiquewhite;
    }
    .info {
        text-align: center;
    }
    .head-lines {
        text-align: center;
    }
    .our-anchors {
        text-align: center;
        list-style-position: inside;
    }
</style>

