# Dataweave Cheatsheet

<table>
<tr>
<th colspan=3>

__XML attribute in output__

<tr>
<th>
Input
<th>
Transformation
<th>
Output
<tr>
<td>
  
~~~~
[{
	"ID": 1,
	"code": "ER38sd",
	"price": 400,
	"departureDate": "2016/03/20",
	"origin": "MUA",
	"destination": "SFO",
	"emptySeats": 0,
	"plane": {
		"type": "Boeing 737",
		"totalSeats": 150
	}
}, {
	"ID": 2,
	"code": "ER45if",
	"price": 345.99,
	"departureDate": "2016/02/11",
	"origin": "MUA",
	"destination": "LAX",
	"emptySeats": 52,
	"plane": {
		"type": "Boeing 777",
		"totalSeats": 300
	}
}]

~~~~

<td>
  
~~~~
%dw 1.0
%output application/xml
---
flights: {(payload map {
	flight @(flightCode: $.code):
	{	
		destination: $.destination
	}
 })
}
~~~~
  
<td>
  
  
~~~~
<?xml version='1.0' encoding='windows-1252'?>
<flights>
  <flight flightCode="ER38sd">
    <destination>SFO</destination>
  </flight>
  <flight flightCode="ER45if">
    <destination>LAX</destination>
  </flight>
</flights>
~~~~
  
  
</table>
